# JEA(Just Enough Administration): 소개

## 목차
이 문서를 읽은 후에는 JEA(Just Enough Administration) 배포의 제작, 배포, 사용, 유지 관리 및 감사를 수행할 수 있습니다.
이 소개 가이드에서 다루는 항목은 다음과 같습니다.

1.  [소개](#introduction): JEA에 대해 관심을 가져야 하는 이유 간단히 검토

2.  [필수 조건](#prerequisites): 환경 설정

3.  [JEA 사용](#using-jea): 운영자의 JEA 사용 경험을 이해하는 것에서 시작

4.  [데모 다시 만들기](#remake-the-demo-endpoint): 처음부터 JEA 세션 구성 만들기

5.  [역할 기능](#role-capabilities): 역할 기능 파일을 사용하여 JEA 기능을 사용자 지정하는 방법 알아보기

6.  [종단 간 - Active Directory](#end-to-end---active-directory): Active Directory를 관리하기 위한 완전히 새로운 끝점 만들기

7.  [다중 컴퓨터 배포 및 유지 관리](#multi-machine-deployment-and-maintenance): 확장에 따라 배포와 작성이 변경되는 방식 알아보기

8.  [JEA에 대한 보고](#reporting-on-jea): 모든 JEA 작업 및 인프라에 대한 감사 및 보고 방법 알아보기

9.  [부록](#appendix): 중요한 기술 및 논의 사항

## 소개

### 동기
누군가에게 시스템에 대한 액세스 권한을 부여하는 경우 해당 사용자에게 신뢰 경계를 확장하는 것입니다.
이는 위험하며 관리자가 공격 노출 영역이 됩니다.
내부자 공격과 자격 증명 도난은 실제로 흔하게 벌어지는 문제입니다.

이는 전혀 새로운 문제가 아닙니다.
최소 권한의 원칙에 아주 익숙할 수도 있고, 특정 형태의 RBAC(역할 기반 액세스 제어)를 제공하는 응용 프로그램과 함께 RBAC를 사용할 수도 있습니다.
그러나 이러한 솔루션의 유효성과 관리 효율성은 해당 솔루션의 넓은 범위와 부정확성에 따라 흔히 제한됩니다.
또한 RBAC 적용 범위에는 간격이 있습니다.
예를 들어 Windows에서 권한 있는 액세스는 주로 이진 스위치인데 Administrators 그룹에 사용자를 추가할 때 불필요한 권한을 부여할 수밖에 없습니다.

JEA(Just Enough Administration)는 PowerShell 원격을 통해 RBAC 플랫폼을 제공합니다.
*JEA를 사용하면 관리자 권한을 부여하지 않고 특정 사용자가 서버에서 특정 관리 작업을 수행하도록 허용할 수 있습니다.*
이에 따라 기존 RBAC 솔루션 간의 간격이 채워지고 해당 설정의 관리가 단순화됩니다.

## 필수 구성 요소

### 초기 상태
이 섹션을 시작하기 전에 다음을 확인하세요.

1. 시스템에서 JEA를 사용할 수 있습니다. 현재 지원되는 운영 체제와 필요한 다운로드에 대한 [추가 정보](./README.md)를 확인하세요.
2. JEA를 시도하고 있는 컴퓨터에 대한 관리 권한을 갖고 있습니다.
3. 컴퓨터가 도메인에 가입되어 있습니다.
도메인이 없는 경우 서버에서 새 도메인을 신속하게 설정하려면 [도메인 컨트롤러 만들기](#creating-a-domain-controller) 섹션을 참조하세요.

### PowerShell 원격 사용
JEA를 사용한 관리는 PowerShell 원격을 통해 발생합니다.
관리자 PowerShell 창에서 다음을 실행하여 PowerShell 원격이 사용되도록 설정되어 있고 올바르게 구성되어 있는지 확인합니다.

```PowerShell
Enable-PSRemoting 
```

PowerShell 원격에 대해 잘 모르는 경우 `Get-Help about_Remote`를 실행하여 이 중요한 기본 개념에 대해 알아보는 것이 좋습니다.

### 사용자 또는 그룹 식별
JEA의 작동을 보여 주기 위해 이 가이드 전체에서 사용할 관리자가 아닌 사용자 및 그룹을 식별해야 합니다.
  
기존 도메인을 사용하는 경우 권한 없는 사용자 및 그룹을 식별하거나 만드세요.
이러한 관리자가 아닌 사용자에게 JEA에 대한 액세스 권한을 부여할 것입니다.
스크립트의 위쪽에 `$NonAdministrator` 변수가 표시되면 관리자가 아닌 선택한 사용자 또는 그룹에 이 변수를 할당합니다. 

처음부터 새 도메인을 만든 경우 이 작업은 훨씬 쉽습니다.
부록의 [사용자 및 그룹 설정](#set-up-users-and-groups) 섹션을 사용하여 관리자가 아닌 사용자 및 그룹을 만드세요.
`$NonAdministrator`의 기본값은 해당 섹션에서 만든 그룹이 됩니다.

### 유지 관리 역할 기능 파일 설정
PowerShell에서 다음 명령을 실행하여 다음 섹션에 사용할 데모 역할 기능 파일을 만듭니다.
이 가이드의 뒷부분에서 이 파일의 기능에 대해 살펴볼 것입니다.

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions = 
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory 

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams 
```
  
### 데모 세션 구성 파일 만들기 및 등록
다음 명령을 실행하여 다음 섹션에 사용할 데모 세션 구성 파일을 만들고 등록합니다.
이 가이드의 뒷부분에서 이 파일의 기능에 대해 살펴볼 것입니다.

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```
 
### PowerShell 모듈 로깅 사용(선택 사항)
다음 단계에서는 시스템에서 모든 PowerShell 작업에 대한 로깅을 사용하도록 설정합니다.
이 기능은 JEA가 작동하도록 하기 위해 반드시 사용하도록 설정해야 하는 것은 아니지만 [JEA에 대한 보고](#reporting-on-jea) 섹션에서 유용합니다.

1. 로컬 그룹 정책 편집기를 엽니다.
2. "컴퓨터 구성\관리 템플릿\Windows 구성 요소\Windows PowerShell"로 이동합니다.
3. "모듈 로깅 켜기"를 두 번 클릭합니다.
4. "사용"을 클릭합니다.
5. 옵션 섹션에서 모듈 이름 옆의 "표시"를 클릭합니다.
6. 팝업 창에 "*"를 입력합니다. 이렇게 하면 PowerShell에서 모든 모듈의 명령을 로깅합니다.
7. 확인을 클릭하고 정책을 적용합니다.

참고: 그룹 정책을 통해 시스템 차원의 PowerShell 기록을 사용하도록 설정할 수도 있습니다.

**축하합니다. 이제 데모 끝점을 사용하여 컴퓨터를 구성했으며 JEA를 시작할 준비가 되었습니다.**

## JEA 사용
이 섹션에서는 최종 사용자의 *JEA 사용* 경험을 이해하는 데 중점을 둡니다.
필수 조건 섹션에서 데모 JEA 끝점을 만들었습니다.
여기에서는 이 데모를 사용하여 JEA의 작동을 보여 줄 것입니다.
이후 섹션에서는 이 과정을 거꾸로 살펴보면서 최종 사용자 경험을 가능하게 한 작업과 파일을 소개합니다.

### 관리자가 아닌 사용자로 JEA 사용
JEA의 작동을 보여 주기 위해 관리자가 아닌 사용자인 것처럼 PowerShell 원격을 사용해야 합니다.
새 PowerShell 창에서 다음 명령을 실행합니다.   

```PowerShell
$NonAdminCred = Get-Credential
```

메시지가 표시되면 관리자가 아닌 계정에 대한 자격 증명을 입력합니다.
[사용자 및 그룹 설정](#set-up-users-and-groups) 섹션을 따른 경우 자격 증명은 다음과 같습니다.
-   사용자 이름 = "OperatorUser"
-   암호 = "pa$$w0rd"

다음 명령을 실행하여 제공한 자격 증명을 사용해 데모 끝점에 연결합니다.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred 
```

이제 로컬 컴퓨터에서 대화형 원격 PowerShell 세션에 들어갔습니다. "Credential" 매개 변수를 사용하여 OperatorUser(또는 사용한 계정)*인 것처럼* 연결했습니다.
프롬프트에서 `[localhost]: PS>`로 변경된 것은 원격 세션을 대상으로 작업하고 있음을 나타냅니다.  

원격 명령 프롬프트에서 다음을 실행하여 사용할 수 있는 명령을 표시합니다.

```PowerShell
Get-Command 
```

표시되는 명령은 일반적인 PowerShell 창에서 사용할 수 있는 명령(흔히 몇천 개의 명령이 포함될 수 있음)의 매우 제한된 하위 집합입니다.
특히 7가지 기본 JEA cmdlet(Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default, Select-Object)과 유지 관리 역할 기능 파일에 명시적으로 포함된 두 명령만 표시됩니다.

다음으로, 유지 관리 역할 기능 파일에 포함된 사용자 지정 함수를 호출하여 이 세션이 작동하고 있는 사용자 컨텍스트를 살펴보겠습니다.

```PowerShell
Get-UserInfo
```
 
이 함수의 출력에서는 "ConnectedUser"뿐만 아니라 "RunAsUser"가 표시됩니다.
연결된 사용자는 원격 세션에 연결한 계정(예: 사용자의 계정)입니다.
연결된 사용자에게는 관리자 권한이 없어도 됩니다.
"실행" 계정은 권한 있는 작업을 실제로 수행하는 계정입니다.
한 사용자로 연결하고 다른 권한 있는 사용자로 실행하면 관리 권한을 제공하지 않고도 권한 없는 사용자가 특정 관리 작업을 수행하도록 허용할 수 있습니다.

이를 보여 주기 위해 다음 명령을 실행합니다.

```PowerShell
Restart-Service -Name Spooler -Verbose
```

일반적으로 Restart-Service를 실행하려면 관리자 권한이 필요합니다.
그러나 JEA 가상 계정이 있으면 권한 없는 자격 증명을 사용하여 실행할 수 있습니다.

따라서 JEA는 이미 사용하는 명령을 이용하여 작업을 수행할 수 있도록 합니다.
하지만 사용하도록 허용되지 *않아야 하는* 명령의 경우는 어떨까요?
JEA 세션에서 `Restart-Computer` 등의 다른 명령을 실행해 보면 JEA에서 그러한 명령이 실행되지 못하게 하는 것을 확인할 수 있습니다.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException 
```

마지막으로, 제한된 JEA 끝점에서 나오려면 다음 명령을 실행합니다.

```PowerShell
Exit-PSSession
```

이렇게 하면 원격 PowerShell 세션에서 연결이 끊어집니다.

## 데모 끝점 다시 만들기
이 섹션에서는 위의 섹션에서 사용한 데모 끝점의 정확한 복제본을 생성하는 방법을 살펴봅니다.
여기에서는 PowerShell 세션 구성 및 역할 기능을 비롯하여 JEA를 이해하는 데 필요한 핵심 개념을 소개합니다. 

### PowerShell 세션 구성
위의 섹션에서 JEA를 사용할 때 다음 명령을 실행하여 시작했습니다.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

대부분의 매개 변수가 쉽게 이해되지만 *ConfigurationName* 매개 변수는 처음에 혼동을 줄 수 있습니다.
이 매개 변수는 연결되어 있는 PowerShell 세션 구성을 지정합니다. 

*PowerShell 세션 구성*은 PowerShell 끝점을 멋지게 표현한 용어입니다.
이 용어는 사용자가 연결하고 PowerShell 기능에 액세스하는 "장소"를 비유적으로 나타낸 것입니다.
세션 구성을 설정하는 방법에 따라 세션 구성은 연결하는 사용자에게 서로 다른 기능을 제공할 수 있습니다.
JEA의 경우 PowerShell을 제한된 기능 집합으로 제한하고 권한 있는 가상 계정으로 실행하는 데 세션 구성을 사용합니다.

컴퓨터에서 각각 약간 다르게 설정된 PowerShell 세션 구성을 이미 여러 개 등록했습니다.
대부분의 세션 구성은 Windows와 함께 제공되지만 "JEA_Demo" 세션 구성은 [필수 조건](#prerequisites) 섹션에서 설정되었습니다.
관리자 PowerShell 프롬프트에서 다음 명령을 실행하여 등록된 모든 세션 구성을 확인할 수 있습니다.

```PowerShell
Get-PSSessionConfiguration
```

### PowerShell 세션 구성 파일
새로운 *PowerShell 세션 구성 파일*을 등록하여 세션 구성을 새로 만들 수 있습니다.
세션 구성 파일의 확장명은 ".pssc"입니다.
New-PSSessionConfigurationFile cmdlet을 사용하여 세션 구성 파일을 생성할 수 있습니다.

다음으로, JEA에 대한 새 세션 구성을 만들고 등록하겠습니다. 

### PowerShell 세션 구성 생성 및 수정
다음 명령을 실행하여 PowerShell 세션 구성 "기본" 파일을 생성합니다.

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **팁:** 가장 일반적인 구성 설정만 기본 파일에 기본적으로 포함됩니다.
> 생성된 PSSC에 적용 가능한 모든 설정을 포함하려면 `-Full` 매개 변수를 사용합니다.

PowerShell ISE 또는 원하는 텍스트 편집기에서 파일을 엽니다.

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc" 
```

파일의 다음 필드를 아래의 값으로 업데이트합니다(자신의 비관리자 보안 그룹에서 대체해야 함). 

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

해당하는 각 항목의 의미는 다음과 같습니다.

1.  *SessionType* 필드는 이 끝점과 함께 사용할 미리 설정된 기본 설정을 정의합니다.
*RestrictedRemoteServer*는 원격 관리에 필요한 최소 설정을 정의합니다. 기본적으로 *RestrictedRemoteServer* 끝점은 Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host 및 Out-Default를 노출합니다.
이 끝점은 *ExecutionPolicy*를 *RemoteSigned*로 설정하고, *LanguageMode*를 *NoLanguage*로 설정합니다.
이러한 설정을 통해 끝점을 구성하기 위한 최소한의 안전한 시작점을 얻을 수 있습니다.

2.  *RoleDefinitions* 필드는 역할 기능을 특정 그룹에 할당합니다.
이 필드는 누가 권한 있는 계정으로 무엇을 수행할 수 있는지를 정의합니다.
이 필드를 통해 그룹 구성원 자격에 따라 연결하는 사용자가 사용할 수 있는 기능을 지정할 수 있습니다.
이는 JEA의 RBAC 기능의 핵심입니다.
이 예에서는 미리 만든 "데모" RoleCapability를 "Contoso\JEA_NonAdmin_Operator" 그룹의 구성원에게 노출합니다.

3.  *RunAsVirtualAccount* 필드는 PowerShell이 이 끝점에서 가상 계정"으로 실행"되어야 함을 나타냅니다.
기본적으로 가상 계정은 기본 제공 Administrators 그룹의 구성원입니다.
도메인 컨트롤러에서는 기본적으로 Domain Administrators 그룹의 구성원이기도 합니다.
이 가이드의 뒷부분에서는 가상 계정의 권한을 사용자 지정하는 방법을 살펴봅니다.

4.  *TranscriptDirectory* 필드는 "Over-the-Shoulder" PowerShell 기록이 각 원격 세션 후 저장되는 위치를 정의합니다.
이러한 기록을 통해 각 세션에서 수행된 작업을 읽으며 검사할 수 있습니다.
PowerShell 기록에 대한 자세한 내용은 이 [블로그 게시물](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)을 참조하세요.
참고: 일반 Windows Eventing에서도 각 사용자가 PowerShell로 실행한 작업에 대한 정보를 캡처합니다.
기록은 좀 더 읽기 쉬울 뿐입니다.

마지막으로, 변경 내용을 *JEADemo2.pssc*에 저장합니다.

### PowerShell 세션 구성 적용 

세션 구성 파일에서 끝점을 만들려면 파일을 등록해야 합니다.
이렇게 하려면 다음과 같은 몇 가지 정보가 필요합니다.

1. 세션 구성 파일의 경로.
2. 등록된 세션 구성의 이름. 이 이름은 사용자가 `Enter-PSSession` 또는 `New-PSSession`을 사용하여 끝점에 연결할 때 "ConfigurationName" 매개 변수에 제공하는 이름과 동일합니다.

로컬 컴퓨터에서 세션 구성을 등록하려면 다음 명령을 실행합니다.

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

축하합니다! JEA 끝점을 설정했습니다.

### 끝점 테스트
[JEA 사용](#using-jea) 섹션에 나열된 단계를 새 끝점에 대해 다시 실행하여 의도한 대로 작동하는지 확인합니다.
Enter-PSSession에 구성 이름을 제공할 때 새 끝점의 이름(JEADemo2)을 사용해야 합니다.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

### 주요 개념
**PowerShell 세션 구성**: *PowerShell 끝점*이라고도 하며 사용자가 연결하고 PowerShell 기능에 액세스하는 "장소"를 비유적으로 나타낸 것입니다.
`Get-PSSessionConfiguration`을 실행하여 시스템에 등록된 세션 구성을 나열할 수 있습니다.
특정한 방식으로 구성된 PowerShell 세션 구성을 *JEA 끝점*이라고 할 수 있습니다.

**PowerShell 세션 구성 파일(.pssc)**: 등록된 경우 PowerShell 세션 구성에 대한 설정을 정의하는 파일입니다.
이 파일에는 끝점에 연결할 수 있는 사용자 역할, "실행" 가상 계정 등에 대한 지정이 포함되어 있습니다.     

**역할 정의**: 연결하는 사용자에게 부여된 역할 기능을 정의하는 세션 구성 파일의 필드입니다.
이 필드는 *누가* 권한 있는 계정으로 *무엇*을 수행할 수 있는지를 정의합니다.
이는 JEA의 RBAC 기능의 핵심입니다.

**SessionType**: 세션 구성에 대한 기본 설정을 나타내는 세션 구성 파일의 필드입니다.
JEA 끝점의 경우 이 필드를 RestrictedRemoteServer로 설정해야 합니다.

**PowerShell 기록**: PowerShell 세션의 "Over-the-Shoulder" 뷰가 포함된 파일입니다.
TranscriptDirectory 필드를 사용하여 JEA 세션에 대한 기록을 생성하도록 PowerShell을 설정할 수 있습니다.
기록에 대한 자세한 내용은 이 [블로그 게시물](https://technet.microsoft.com/en-us/magazine/ff687007.aspx)을 참조하세요.

## 역할 기능

### 개요
위의 섹션에서 "RoleDefinitions" 필드는 어떤 그룹이 어떤 역할 기능에 액세스할 수 있는지를 정의한다는 것을 배웠습니다.
이때 "역할 기능은 무엇일까?"라는 의문이 들었을 수 있습니다.
이 섹션에는 이 의문에 대한 답을 제공합니다.  

## PowerShell 역할 기능 소개
PowerShell 역할 기능은 사용자가 JEA 끝점에서 수행할 수 있는 "작업"을 정의합니다.
역할 기능은 표시되는 명령, 표시되는 응용 프로그램 등의 허용 목록을 열거합니다.
역할 기능은 확장명이 ".psrc"인 파일로 정의됩니다.

## 역할 기능 내용
이전에 사용한 데모 역할 기능 파일을 검사하고 수정하여 작업을 시작하겠습니다.
사용자 환경 전체에 세션 구성을 배포했지만 사용자에게 노출된 기능을 변경해야 한다는 피드백을 받았다고 가정해 보겠습니다.
운영자는 컴퓨터를 다시 시작하는 기능을 필요로 하며 네트워크 설정에 대한 정보도 얻을 수 있기를 원합니다.
또한 제한 없이 "Restart-Service"를 실행하도록 사용자에게 허용하는 것은 받아들일 수 없다는 통보를 보안 팀에서 받았습니다.
따라서 운영자가 다시 시작할 수 있는 서비스를 제한해야 합니다.

이렇게 변경하려면 관리자로 PowerShell ISE를 실행하여 시작하고 다음 파일을 엽니다.

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

이제 파일에서 다음 줄을 찾아 업데이트합니다. 

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

여기에는 다음과 같은 몇 가지 흥미로운 예가 포함되어 있습니다.

1.  운영자가 -Name 매개 변수와 함께만 Restart-Service를 사용할 수 있도록 Restart-Service를 제한했으며 운영자는 이 매개 변수에 인수로 "Spooler"만 제공하도록 허용됩니다.
원하는 경우 "ValidateSet" 대신 "ValidatePattern"을 사용하는 정규식을 이용하여 인수를 제한할 수도 있습니다.

2.  NetTCPIP 모듈에서 "Get" 동사가 포함된 모든 명령을 노출했습니다.
일반적으로 "Get" 명령은 시스템 상태를 변경하지 않으므로 이는 비교적 안전한 조치입니다.
하지만 JEA를 통해 노출하는 모든 명령을 면밀하게 검사하는 것이 좋습니다.

3.  VisibleExternalCommands를 사용하여 실행 파일(ipconfig)을 노출했습니다.
이 필드를 사용하여 전체 PowerShell 스크립트를 노출할 수도 있습니다.
사용자의 경로에 배치된 유사한 이름의(잠재적으로 악성인) 프로그램이 대신 실행되지 않도록 하기 위해 항상 외부 명령의 전체 경로를 제공해야 합니다.

파일을 저장한 다음 데모 끝점에 다시 연결하여 변경 사항이 적용되었는지 확인합니다.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
역할 기능 파일만 수정했기 때문에 세션 구성을 다시 등록할 필요가 없습니다.
PowerShell에서는 사용자가 연결할 때 업데이트된 역할 기능을 자동으로 찾습니다.
세션이 시작될 때 역할 기능이 로드되므로 기존 세션은 역할 기능 파일의 업데이트로 영향을 받지 않습니다.

이제 -WhatIf 매개 변수와 함께 Restart-Computer를 실행하여 컴퓨터를 다시 시작할 수 있는지 확인합니다(실제로 컴퓨터를 다시 시작하고 싶지 않은 경우).

```PowerShell
Restart-Computer -WhatIf 
```

"ipconfig"를 실행할 수 있는지 확인합니다.

```PowerShell
ipconfig
```

마지막으로, Restart-Service가 Spooler 서비스에만 작동하는지 확인합니다.

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail 
```

완료하면 세션을 종료합니다.

```PowerShell
Exit-PSSession 
```

### 역할 기능 만들기
다음 섹션에서는 AD 지원 센터 사용자에 대한 JEA 끝점을 만듭니다.
준비하기 위해 다음 섹션에서 입력할 비어 있는 역할 기능 파일을 만듭니다.
역할 기능은 세션이 시작될 때 확인되기 위해 유효한 PowerShell 모듈에 있는 "RoleCapabilities" 폴더 내에 만들어야 합니다.

PowerShell 모듈은 기본적으로 PowerShell 기능의 패키지이며,
PowerShell 함수, cmdlet, DSC 리소스, 역할 기능 등을 포함할 수 있습니다.
PowerShell 콘솔에서 `Get-Help about_Modules`를 실행하여 모듈에 대한 정보를 찾을 수 있습니다.

비어 있는 역할 기능 파일로 새 PowerShell 모듈을 만들려면 다음 명령을 실행합니다.  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File 

# Create a RoleCapabilities folder in the AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```

축하합니다. 비어 있는 역할 기능 파일을 만들었습니다.
이 파일은 다음 섹션에서 사용됩니다.

### 주요 개념
**역할 기능(.psrc)**: 사용자가 JEA 끝점에서 수행할 수 있는 "작업"을 정의하는 파일입니다.
이 파일은 표시되는 명령, 표시되는 콘솔 응용 프로그램 등의 허용 목록을 열거합니다.
PowerShell에서 역할 기능을 검색하도록 하려면 유효한 PowerShell 모듈의 "RoleCapabilities" 폴더에 역할 기능을 배치해야 합니다.

**PowerShell 모듈**: PowerShell 기능의 패키지이며,
PowerShell 함수, cmdlet, DSC 리소스, 역할 기능 등을 포함할 수 있습니다.
PowerShell 모듈이 자동으로 로드되려면 `$env:PSModulePath`의 경로 아래에 있어야 합니다. 

## 종단 간 - Active Directory
프로그램의 범위가 증가했다고 가정해 보겠습니다.
이제 Active Directory 작업을 수행하기 위해 JEA를 도메인 컨트롤러에 추가해야 합니다.
지원 센터 직원들이 JEA를 사용하여 계정의 잠금을 해제하고, 암호를 다시 설정하고, 다른 유사한 작업을 수행하려고 합니다.

다른 사용자 그룹에 완전히 새로운 명령 집합을 노출해야 합니다.
뿐만 아니라 노출해야 하는 기존 Active Directory 스크립트 집합이 있습니다.
이 섹션에서는 이 작업에 대한 세션 구성과 역할 기능을 작성하는 단계를 안내합니다.

### 필수 구성 요소
이 섹션을 단계별로 수행하려면 도메인 컨트롤러에서 작업해야 합니다.
도메인 컨트롤러에 액세스할 수 없는 경우 걱정하지 마세요.
익숙한 다른 시나리오나 역할을 대상으로 작업하여 이 섹션의 내용을 파악해 보세요.
새 도메인 컨트롤러를 신속하게 설정하려면 [도메인 컨트롤러 만들기 부록](#creating-a-domain-controller)을 참조하세요.

### 새로운 역할 기능 및 세션 구성을 만드는 단계

새로운 역할 기능을 만드는 작업은 처음에는 어렵게 느껴질 수 있지만 매우 간단한 단계로 분할할 수 있습니다.

1.  사용하도록 설정해야 하는 작업 식별
2.  필요에 따라 해당 작업 제한
3.  해당 작업이 JEA와 작동하는지 확인
4.  해당 작업을 역할 기능 파일에 배치
5.  해당 역할 기능을 노출하는 세션 구성 등록

### 1단계: 노출해야 하는 작업 식별
새로운 역할 기능이나 세션 구성을 만들기 전에 사용자가 JEA 끝점을 통해 수행해야 하는 모든 작업과 PowerShell을 통해 해당 작업을 수행하는 방법을 식별해야 합니다.
여기에는 상당한 양의 요구 사항 수집과 연구가 포함됩니다.
이 프로세스에 착수하는 방법은 조직과 목표에 따라 달라집니다.
요구 사항 수집과 연구를 실제 프로세스의 중요한 부분으로 요구해야 합니다.
이는 JEA 채택 프로세스의 가장 어려운 단계일 수 있습니다.

#### 리소스 찾기
Active Directory 관리 끝점을 만드는 방법에 대한 연구에서 발견했을 수도 있는 온라인 리소스 집합은 다음과 같습니다.
-   [Active Directory PowerShell 개요](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) 
-   [Active Directory에 대한 PowerShell CMD 가이드](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

#### 목록 만들기
다음은 이 섹션의 나머지 부분에서 수행할 10가지 작업 집합입니다.
이는 예일 뿐이라는 점을 명심하세요. 조직 요구 사항은 다를 수 있습니다.

|작업                                                         |PowerShell 명령                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|계정 잠금 해제                                                 |`Unlock-ADAccount`                                             |
|암호 다시 설정                                                 |`Set-ADAccountPassword` 및 `Set-ADUser -ChangePasswordAtLogon`|
|사용자의 직함 변경                                          |`Set-ADUser -Title`                                            |  
|잠겨 있거나, 사용하지 않도록 설정되거나, 비활성 상태 등인 AD 계정 찾기 |`Search-ADAccount`                                             | 
|그룹에 사용자 추가                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        | 
|그룹에서 사용자 제거                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     | 
|사용자 계정 사용                                          |`Enable-ADAccount`                                             |
|사용자 계정 사용 안 함                                         |`Disable-ADAccount`                                            |

### 2단계: 필요에 따라 작업 제한

이제 작업 목록이 있으므로 각 명령의 기능에 대해 자세히 알아봐야 합니다.
이렇게 하는 데는 두 가지 중요한 이유가 있습니다.

1.  의도한 것보다 많은 기능을 사용자에게 노출하기가 쉽습니다.
예를 들어 `Set-ADUser`는 매우 강력하고 유연한 명령입니다.
이 명령으로 수행할 수 있는 모든 작업을 지원 센터 사용자에게 노출하는 것을 원하지 않을 수 있습니다.  

2.  훨씬 나쁜 경우로, JEA의 제한을 빠져나가도록 사용자에게 허용하는 명령을 노출할 수 있습니다.
이 경우 JEA는 보안 경계로 기능하지 않습니다.
명령을 선택할 때 주의하세요.
예를 들어 Invoke-Expression은 사용자가 제한 없는 코드를 실행하도록 허용합니다.
이 주제에 대한 자세한 내용은 명령을 제한하는 경우의 고려 사항 섹션을 참조하세요.

각 명령을 검토한 후 다음을 제한하도록 결정합니다.

1.  `Set-ADUser` 는 "-Title" 매개 변수를 사용하는 경우에만 실행되도록 허용되어야 합니다. 

2.  `Add-ADGroupMember` 및 `Remove-ADGroupMember`는 특정 그룹에만 사용해야 합니다.

### 3단계: 작업이 JEA와 작동하는지 확인
이러한 cmdlet을 실제로 사용하는 것은 제한된 JEA 환경에서 간단하지 않을 수 있습니다.
JEA는 특히 사용자가 변수를 사용하지 못하게 하는 *언어 없음* 모드에서 실행됩니다.
최종 사용자에게 원활한 환경을 보장하기 위해 몇 가지 사항을 확인해야 합니다.

예를 들어 `Set-ADAccountPassword`를 고려합니다.
"-NewPassword" 매개 변수에는 보안 문자열이 필요합니다.
흔히 사용자는 보안 문자열을 만들어 변수로 전달합니다(아래 참조).

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

그러나 언어 없음 모드에서는 변수의 사용을 금지합니다.
두 가지 방법으로 이 제한을 해결할 수 있습니다.

1.  사용자가 변수를 할당하지 않고 명령을 실행하도록 요구할 수 있습니다.
이렇게 구성하기는 쉽지만 끝점을 사용하는 운영자에게 어려움을 줄 수 있습니다.
암호를 다시 설정할 때마다 다음과 같이 입력하고 싶은 사람이 누가 있을까요?
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  최종 사용자에게 노출하는 스크립트나 함수에 복잡한 사항을 포함할 수 있습니다.
노출하는 스크립트와 함수는 제한 없는 컨텍스트에서 실행됩니다. 어떠한 문제도 없이 변수를 사용하고 다른 명령을 호출하는 함수를 작성할 수 있습니다.
이 방법은 최종 사용자 환경을 간소화하고, 오류를 방지하고, 필요한 PowerShell 지식을 줄이고, 실수로 노출하는 초과 기능을 줄입니다.
유일한 단점은 함수 작성 및 유지 관리의 비용입니다.

#### 참고: 모듈에 함수 추가
두 번째 방법을 사용하는 경우 `Reset-ContosoUserPassword`라는 PowerShell 함수를 작성합니다.
이 함수는 사용자의 암호를 다시 설정할 때 발생해야 하는 모든 작업을 수행합니다.
조직에서는 여기에 복잡한 고급 작업의 수행이 포함될 수 있습니다.
여기에서는 예를 보여 줄 뿐이므로 이 함수는 암호를 다시 설정하고 사용자가 로그온할 때 암호를 변경하도록 요구합니다.
이 함수는 지난 섹션에서 만든 Contoso_AD_Module 모듈에 포함될 것입니다.

1. PowerShell ISE에서 "Contoso_AD_Module.psm1"을 엽니다.
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' 
```

2. Crtl+J를 눌러 코드 조각 메뉴를 엽니다.

3. "function"을 찾을 때까지 아래로 이동하고 Enter 키를 누릅니다.
함수의 가장 기본적인 뼈대가 생성됩니다.

4. 함수의 이름을 "Reset-ContosoUserPassword"로 바꿉니다.  

5. 매개 변수 중 하나의 이름을 "Identity"로 변경하고 두 번째 매개 변수를 삭제합니다.

6. 다음을 함수 본문에 복사합니다.
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. 파일을 저장합니다.
최종적인 결과는 다음과 같아야 합니다.
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
} 
```
이제 사용자가 `Reset-ContosoUserPassword`를 호출하기만 하면 되고 보안 문자열을 인라인으로 만드는 구문을 기억할 필요가 없습니다.

### 4단계: 역할 기능 파일 편집
[역할 기능 만들기](#role-capability-creation) 섹션에서 비어 있는 역할 기능 파일을 만들었습니다.
이 섹션에서는 해당 파일에 값을 입력합니다.

ISE에서 역할 기능 파일을 열어 시작합니다.
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```
다음과 같이 변경하여 파일을 업데이트합니다.
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters = 
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters = 
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}
  
# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }   
VisibleFunctions = 'Reset-ContosoUserPassword'
```

위에서 몇 가지 사항에 유의해야 합니다.
1.  PowerShell에서 역할 기능에 필요한 모듈을 자동으로 로드하려고 시도합니다.
모듈이 자동으로 로드되지 않는 문제가 발생하는 경우 "ModulesToImport" 필드에서 모듈 이름을 명시적으로 나열해야 할 수 있습니다.

2.  명령이 cmdlet인지, 아니면 함수인지 모르겠는 경우 `Get-Command`를 실행하고 "CommandType"을 확인합니다.

3.  ValidatePattern은 허용 가능한 값 집합을 정의하기가 쉽지 않은 경우 정규식을 사용하여 매개 변수 인수를 제한할 수 있도록 합니다.
단일 매개 변수에 대해 ValidatePattern과 ValidateSet을 둘 다 정의할 수는 없습니다.

### 5단계: 새 세션 구성 등록
다음으로, "JEA_NonAdmin_HelpDesk" AD 그룹의 구성원에게 역할 기능을 노출할 새로운 세션 구성 파일을 만듭니다. 

PowerShell ISE에서 비어 있는 새 세션 구성 파일을 만들고 열어서 시작합니다.
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc" 
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
PSSC 파일에서 다음 필드를 수정합니다.
자신의 환경에서 작업하는 경우 "CONTOSO\JEA_NonAdmins_Helpdesk"를 관리자가 아닌 자신의 사용자 또는 그룹으로 대체해야 합니다.
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for active directory tasks.' 

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }} 
```
세션 구성을 저장하고 등록합니다.
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc" 
```
### 테스트
관리자가 아닌 사용자의 자격 증명을 가져옵니다.
```PowerShell
$HelpDeskCred = Get-Credential
```
사용자 및 그룹 설정 섹션을 따른 경우 자격 증명은 다음과 같습니다.
-   사용자 이름 = "HelpDeskUser"
-   암호 = "pa$$w0rd"

비관리자 자격 증명을 사용하여 AD 지원 센터 끝점에 원격으로 연결합니다.
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred 
```
Set-ADUser를 사용하여 사용자의 직함을 다시 설정합니다.
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer 
```
직함이 변경되었는지 확인합니다.
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title 
```
이제 Add-ADGroupMember를 사용하여 TestGroup에 사용자를 추가합니다.
참고: TestGroup을 미리 만들어 놓아야 합니다.
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose 
```
세션을 종료합니다.
```PowerShell
Exit-PSSession
```
### 주요 개념
**NoLanguage 모드**: PowerShell이 "NoLanguage" 모드에 있는 경우 사용자는 명령을 실행할 수만 있고 언어 요소를 사용할 수 없습니다.
자세한 내용은 `Get-Help about_Language_Modes`를 실행하십시오.

**PowerShell 함수**: PowerShell 함수는 이름으로 호출할 수 있는 PowerShell 코드 조각입니다.
자세한 내용은 `Get-Help about_Functions`를 실행하십시오.

**ValidateSet/ValidatePattern**: 명령을 노출할 때 특정 매개 변수에 대한 유효한 인수를 제한할 수 있습니다.
ValidateSet은 유효한 명령의 특정 목록입니다.
ValidatePattern은 해당 매개 변수에 대한 인수가 일치해야 하는 정규식입니다.

## 다중 컴퓨터 배포 및 유지 관리
이 시점에서 JEA를 로컬 시스템에 여러 번 배포했습니다.
프로덕션 환경은 두 대 이상의 컴퓨터로 구성될 수 있으므로 각 컴퓨터에서 반복해야 하는 배포 프로세스의 중요 단계를 연습해야 합니다.

### 상위 수준 단계:
1.  역할 기능이 포함된 모듈을 각 노드에 복사합니다.
2.  세션 구성 파일을 각 노드에 복사합니다.
3.  세션 구성과 함께 `Register-PSSessionConfiguration`을 실행합니다.
4.  세션 구성과 도구 키트의 복사본을 안전한 위치에 보관합니다.
수정 작업을 할 때 "단일 데이터 소스(single source of truth)"를 마련하는 것이 좋습니다.

### 예제 스크립트
배포를 위한 예제 스크립트는 다음과 같습니다.
해당 환경에서 이 스크립트를 사용하려면 실제 파일 공유 및 모듈의 이름/경로를 사용해야 합니다.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
### 기능 수정
많은 컴퓨터를 처리할 때 수정 내용을 일관된 방식으로 배포하는 것이 중요합니다.
JEA에 DSC 리소스가 있으면 환경이 동기화되도록 하는 데 도움이 됩니다.
그 전까지는 세션 구성의 마스터 복사본을 보관하고 수정할 때마다 다시 배포하는 것이 좋습니다.

### 기능 제거
시스템에서 JEA 구성을 제거하려면 각 컴퓨터에서 다음 명령을 사용합니다.
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo 
```
## JEA에 대한 보고
JEA는 권한 없는 사용자가 권한 있는 컨텍스트에서 실행하도록 허용하기 때문에 로깅과 감사가 매우 중요합니다.
이 섹션에서는 로깅과 보고에 유용하게 사용할 수 있는 도구를 실행합니다.

### JEA 작업에 대한 보고
#### Over-the-Shoulder 기록
PowerShell 세션에서 발생하고 있는 상황을 대략적으로 파악하는 가장 빠른 방법은 입력하는 사용자의 어깨너머로 보는 것입니다.
입력한 명령, 해당 명령의 출력 및 모두 정상인지를 확인할 수 있습니다.
정상이 아닌 경우에는 적어도 문제 상황을 알게 됩니다.
PowerShell 기록은 사건 뒤에 유사한 보기를 제공하도록 설계되었습니다.

세션 구성에서 "TranscriptDirectory" 필드를 사용할 때 PowerShell에서는 주어진 세션에서 수행된 모든 작업의 기록을 자동으로 생성합니다.
이 문서의 세션에서는 "$env:ProgramData\JEAConfiguration\Transcripts"에서 기록을 찾을 수 있습니다.

기록에는 "연결된" 사용자, "실행" 사용자, 세션에서 실행된 명령 등에 대한 정보가 포함됩니다.
PowerShell 기록에 대한 자세한 내용은 [이 블로그 게시물](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)을 참조하세요.

#### PowerShell 이벤트 로그
모듈 로깅을 켠 경우 모든 PowerShell 작업은 일반 Windows 이벤트 로그에도 기록됩니다.
이벤트 로그는 기록과 비교할 때 다루기가 약간 더 복잡하지만 제공하는 세부 정보의 수준은 유용할 수 있습니다.

"PowerShell" 작업 로그에서 이벤트 ID 4104는 모듈 로깅을 사용하도록 설정한 경우 호출된 각 명령을 기록합니다.

#### 기타 이벤트 로그
PowerShell 로그 및 기록과 달리, 다른 로깅 메커니즘은 "연결된 사용자"를 캡처하지 않습니다.
수행된 작업을 맞춰보기 위해 다른 로그와 PowerShell 로그 간의 상관 관계를 파악해야 합니다.

"Windows 원격 관리" 작업 로그에서 이벤트 ID 193은 이 상관 관계 파악에 도움을 주기 위해 연결하는 사용자의 SID 및 이름뿐만 아니라 실행 가상 계정의 SID를 기록합니다.
또한 실행 가상 계정 이름의 끝에 연결하는 사용자의 도메인 및 사용자 이름이 포함되어 있음을 확인할 수도 있습니다.

### JEA 구성에 대한 보고
#### Get-PSSessionConfiguration
사용자 환경의 상태에 대해 정확하게 보고하기 위해 컴퓨터에서 설정한 JEA 끝점 수를 알아야 합니다.
`Get-PSSessionConfiguration` 은 이 작업을 수행합니다.
 
#### Get-PSSessionCapability
JEA 끝점을 통한 지정된 사용자의 기능에 대해 수동으로 보고하는 것은 꽤 복잡할 수 있습니다.
몇 가지 역할 기능을 검사해야 할 수 있습니다.
다행히도 "Get-PSSessionCapability" cmdlet이 이 작업을 수행합니다.

이를 테스트하려면 관리자 PowerShell 프롬프트에서 다음 명령을 실행합니다.
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```
## 결론 
이 가이드를 완료한 후에는 JEA 끝점을 직접 만들기 위한 도구와 용어 모음을 갖게 됩니다. 읽어 주셔서 감사합니다.

## 부록

## 이 가이드 전체에서 사용된 주요 개념
**PowerShell 원격**: PowerShell 원격을 사용하면 원격 컴퓨터에 대해 PowerShell 명령을 실행할 수 있습니다.
한 대 이상의 컴퓨터를 대상으로 작업하고 임시 또는 영구 연결을 사용할 수 있습니다.
이 데모에서는 대화형 세션으로 로컬 컴퓨터에 원격으로 연결했습니다.
JEA는 PowerShell 원격을 통해 사용할 수 있는 기능을 제한합니다.
PowerShell 원격에 대한 자세한 내용을 보려면 `Get-Help about_Remote`를 실행하세요.

**"실행" 사용자**: JEA를 사용할 때 관리자가 아닌 사용자가 권한 있는 "가상 계정으로 실행"합니다.
가상 계정은 원격 세션의 기간 동안만 지속됩니다.
즉, 가상 계정은 사용자가 끝점에 연결할 때 만들어지고 사용자가 세션을 종료할 때 제거됩니다.
기본적으로 가상 계정은 로컬 Administrators 그룹의 구성원이고,
도메인 컨트롤러에서는 Domain Admins의 구성원입니다.
가상 계정은 만들어진 컴퓨터에 로컬이며 해당 컴퓨터 외부에서는 권한이 없습니다.
즉, Active Directory에서 등록되어 있지 않습니다(RID가 할당되지 않음).
또한 허용되는 명령/스크립트가 로컬 컴퓨터 외부의 리소스에 액세스하려는 경우 가상 계정 ID가 아니라 컴퓨터의 ID로 해당 리소스에 액세스하게 됩니다.

**"연결된" 사용자**: JEA 끝점에 연결되고 역할이 할당된 관리자가 아닌 사용자입니다.
이 사용자가 실행하는 모든 명령은 실행 사용자 또는 가상 계정의 컨텍스트에서 실행됩니다.


### 도메인 컨트롤러 만들기

이 문서에서는 컴퓨터가 도메인에 가입되어 있다고 가정합니다.
가입할 도메인이 현재 없는 경우 이 섹션은 DSC를 사용하여 도메인 컨트롤러를 신속하게 설정하는 데 도움이 될 수 있습니다.

#### 필수 구성 요소

1.  컴퓨터가 내부 네트워크에 있습니다.
2.  컴퓨터가 기존 도메인에 가입되어 있지 않습니다.
3.  컴퓨터에서 Windows Server 2016이 실행되고 있거나 WMF 5.0이 설치되어 있습니다.

#### xActiveDirectory 설치
컴퓨터가 인터넷에 연결되어 있는 경우 관리자 권한 PowerShell 창에서 다음 명령을 실행합니다.
```PowerShell
Install-Module xActiveDirectory -Force 
```
인터넷에 연결되어 있지 않은 경우에는 xActiveDirectory를 다른 컴퓨터에 설치한 다음 xActiveDirectory 폴더를 컴퓨터의 "C:\Program Files\WindowsPowerShell\Modules" 폴더에 복사합니다.

설치에 성공했는지 확인하려면 다음 명령을 실행합니다.
```PowerShell
Get-Module xActiveDirectory -ListAvailable
``` 

#### DSC를 사용하여 도메인 설정
PowerShell에서 다음 스크립트를 복사하여 컴퓨터를 새 도메인의 도메인 컨트롤러로 만듭니다.
**작성자의 참고 사항: 사용 중이 아닌 자격 증명을 제공하는 경우 알려진 문제가 있습니다.  안전을 위해 로컬 관리자 암호를 잊어버리지 마세요.**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force 

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }
    
}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
컴퓨터가 몇 차례 다시 시작됩니다.
"Domain has been created."가 포함된 "C:\temp.txt"라는 파일이 표시되면 프로세스가 완료된 것입니다. 

#### 사용자 및 그룹 설정
다음 명령은 도메인에서 Operator 및 Helpdesk 그룹과 해당 그룹의 구성원인 관리자가 아닌 사용자를 설정합니다.
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

### 블랙리스트에 올리기
JEA를 사용하여 작업해 본 후 명령을 블랙리스트에 올리는 것이 가능한지 궁금할 수 있습니다.
이는 이해할 수 있는 요청이지만 블랙리스트에 올리는 기능은 다음과 같은 이유로 JEA에 대해 현재 계획되어 있지 않습니다.

1.  수행해야 하는 작업으로만 운영자를 제한하도록 JEA를 설계했습니다.
블랙 리스트는 이와 반대입니다.

2.  PowerShell 명령 작성자는 JEA를 염두에 두고 PowerShell 명령을 설계하지 않았습니다.
Windows Server 2016을 새로 설치한 경우 약 1520개의 명령을 즉시 사용할 수 있습니다.
이러한 명령에 대한 위협 모델에는 사용자가 권한이 더 많은 계정으로 명령을 실행할 것이라는 가능성이 포함되어 있지 않습니다.
예를 들어 특정 명령은 설계상 코드 주입을 고려합니다(예: 핵심 PowerShell 모듈의 Add-Type 및 Invoke-Command).
JEA는 Microsoft에서 알고 있는 특정 명령을 노출할 때 경고할 수 있지만, Microsoft에서는 새로운 위협 모델을 기초로 Windows의 다른 모든 명령을 다시 평가하지는 않았습니다.
JEA를 통해 노출하는 명령의 기능을 이해해야 합니다.  

3.  또한 JEA가 코드 주입에 취약한 모든 명령을 차단한다고 해도 악의적인 사용자가 블랙 리스트에 있는 작업을 다른 관련 명령으로 수행할 수 없다는 보장은 없습니다.
노출할 명령을 모두 이해하지 않는 한 특정 작업이 가능하지 않다고 보장하는 것은 불가능합니다.
허용 목록을 사용하든 블랙 리스트를 사용하든 간에 노출할 명령을 이해하는 것은 사용자의 책임입니다.
블랙 리스트로 노출할 명령 수는 관리할 수 없으므로 JEA는 대신 허용 목록을 사용하여 구현되었습니다.

### 명령을 제한하는 경우의 고려 사항
이 단계에 대해 유의할 한 가지 중요한 사항이 있습니다.
JEA를 통해 노출된 모든 기능이 관리자 제한 영역에 위치해야 합니다.
관리자가 아닌 사용자는 JEA 끝점을 통해 사용된 스크립트를 수정할 수 없어야 합니다.

이와 관련하여 JEA 사용자에게 자신의 JEA 세션 내에서 JEA 구성 및 허용된 스크립트를 덮어쓰는 기능을 제공하지 않아야 합니다.
`Copy-Item`과 같은 명령을 노출하는 경우에는 특히 주의하세요.

### 일반적인 역할 기능 문제
이 프로세스를 직접 진행할 때 몇 가지 일반적인 문제가 발생할 수 있습니다.
새 끝점을 수정하거나 만들 때 이러한 문제를 식별하고 수정하는 방법을 설명하는 간단한 지침은 다음과 같습니다.

#### 함수와 Cmdlet
PowerShell에서 작성된 PowerShell 명령이 PowerShell 함수이고,
특수화된 .NET 클래스로 작성된 PowerShell 명령이 PowerShell Cmdlet입니다.
`Get-Command`를 실행하여 명령 유형을 확인할 수 있습니다.

#### VisibleProviders 
명령에 필요한 공급자를 노출해야 합니다.
가장 일반적인 공급자는 FileSystem 공급자이지만 레지스트리 공급자 등의 다른 공급자도 노출해야 할 수 있습니다.
공급자에 대한 소개는 [Hey, Scripting Guy 블로그 게시물](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)을 참조하세요.
공급자를 노출할 때 JEA 세션에서 공급자를 직접 노출하는 대신 기본 공급자와 작동하는 함수를 직접 정의하는 것이 효과적인 경우가 많습니다.
이러한 방식으로 사용자가 파일, 레지스트리 키 등을 사용하여 작업하도록 계속 허용할 수 있지만 사용자 지정 유효성 검사 논리를 사용하여 작업할 수 있는 파일 및 레지스트리 키 **항목*에 대한 제어를 유지할 수 있습니다.

<!--HONumber=Jun16_HO1-->


