---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "종단 간 - Active Directory"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 5954eb797df43de6f132a434ecad7049ee0221fb
ms.openlocfilehash: 204909c16d5e3e2099f6ba4247929d61445cd654

---

# 종단 간 - Active Directory
프로그램의 범위가 증가했다고 가정해 보겠습니다.
이제 Active Directory 작업을 수행하기 위해 JEA를 도메인 컨트롤러에 추가해야 합니다.
지원 센터 직원들이 JEA를 사용하여 계정의 잠금을 해제하고, 암호를 다시 설정하고, 다른 유사한 작업을 수행하려고 합니다.

다른 사용자 그룹에 완전히 새로운 명령 집합을 노출해야 합니다.
뿐만 아니라 노출해야 하는 기존 Active Directory 스크립트 집합이 있습니다.
이 섹션에서는 이 작업에 대한 세션 구성과 역할 기능을 작성하는 단계를 안내합니다.

## 필수 구성 요소
이 섹션을 단계별로 수행하려면 도메인 컨트롤러에서 작업해야 합니다.
도메인 컨트롤러에 액세스할 수 없는 경우 걱정하지 마세요.
익숙한 다른 시나리오나 역할을 대상으로 작업하여 이 섹션의 내용을 파악해 보세요.
새 도메인 컨트롤러를 신속하게 설정하려면 [도메인 컨트롤러 만들기 부록](#creating-a-domain-controller)을 참조하세요.

## 새로운 역할 기능 및 세션 구성을 만드는 단계

새로운 역할 기능을 만드는 작업은 처음에는 어렵게 느껴질 수 있지만 매우 간단한 단계로 분할할 수 있습니다.

1.  사용하도록 설정해야 하는 작업 식별
2.  필요에 따라 해당 작업 제한
3.  해당 작업이 JEA와 작동하는지 확인
4.  해당 작업을 역할 기능 파일에 배치
5.  해당 역할 기능을 노출하는 세션 구성 등록

## 1단계: 노출해야 하는 작업 식별
새로운 역할 기능이나 세션 구성을 만들기 전에 사용자가 JEA 끝점을 통해 수행해야 하는 모든 작업과 PowerShell을 통해 해당 작업을 수행하는 방법을 식별해야 합니다.
여기에는 상당한 양의 요구 사항 수집과 연구가 포함됩니다.
이 프로세스에 착수하는 방법은 조직과 목표에 따라 달라집니다.
요구 사항 수집과 연구를 실제 프로세스의 중요한 부분으로 요구해야 합니다.
이는 JEA 채택 프로세스의 가장 어려운 단계일 수 있습니다.

### 리소스 찾기
Active Directory 관리 끝점을 만드는 방법에 대한 연구에서 발견했을 수도 있는 온라인 리소스 집합은 다음과 같습니다.
-   [Active Directory PowerShell 개요](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [Active Directory에 대한 PowerShell CMD 가이드](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### 목록 만들기
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

## 2단계: 필요에 따라 작업 제한

이제 작업 목록이 있으므로 각 명령의 기능에 대해 자세히 알아봐야 합니다.
이렇게 하는 데는 두 가지 중요한 이유가 있습니다.

1.  의도한 것보다 많은 기능을 사용자에게 제공하기가 쉽습니다.
예를 들어 `Set-ADUser`는 매우 강력하고 유연한 명령입니다.
이 명령으로 수행할 수 있는 모든 작업을 지원 센터 사용자에게 노출하는 것을 원하지 않을 수 있습니다.  

2.  훨씬 나쁜 경우로, JEA의 제한을 빠져나가도록 사용자에게 허용하는 명령을 노출할 수 있습니다.
이 경우 JEA는 보안 경계로 기능하지 않습니다.
명령을 선택할 때 주의하세요.
예를 들어 Invoke-Expression은 사용자가 제한 없는 코드를 실행하도록 허용합니다.
이 주제에 대한 자세한 내용은 명령을 제한하는 경우의 고려 사항 섹션을 참조하세요.

각 명령을 검토한 후 다음을 제한하도록 결정합니다.

1.  `Set-ADUser` 는 -Title 매개 변수를 사용하는 경우에만 실행되도록 허용되어야 합니다.

2.  `Add-ADGroupMember` 및 `Remove-ADGroupMember`는 특정 그룹에만 사용해야 합니다.

### 3단계: 작업이 JEA와 작동하는지 확인
이러한 cmdlet을 실제로 사용하는 것은 제한된 JEA 환경에서 간단하지 않을 수 있습니다.
JEA는 특히 사용자가 변수를 사용하지 못하게 하는 *NoLanguage* 모드에서 실행됩니다.
최종 사용자에게 원활한 환경을 보장하기 위해 몇 가지 사항을 확인해야 합니다.

예를 들어 `Set-ADAccountPassword`를 고려합니다.
-NewPassword 매개 변수에는 보안 문자열이 필요합니다.
흔히 사용자는 보안 문자열을 만들어 변수로 전달합니다(아래 참조).

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

그러나 *NoLanguage* 모드에서는 변수를 사용하지 못합니다.
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

### 참고: 모듈에 함수 추가
두 번째 방법을 사용하는 경우 `Reset-ContosoUserPassword`라는 PowerShell 함수를 작성합니다.
이 함수는 사용자의 암호를 다시 설정할 때 발생해야 하는 모든 작업을 수행합니다.
조직에서는 여기에 복잡한 고급 작업의 수행이 포함될 수 있습니다.
여기에서는 예를 보여 줄 뿐이므로 이 함수는 암호를 다시 설정하고 사용자가 로그온할 때 암호를 변경하도록 요구합니다.
이 함수는 지난 섹션에서 만든 Contoso_AD_Module 모듈에 포함될 것입니다.

1. PowerShell ISE에서 "Contoso_AD_Module.psm1"을 엽니다.
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
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

## 4단계: 역할 기능 파일 편집
[역할 기능 만들기](#role-capability-creation) 섹션에서 비어 있는 역할 기능 파일을 만들었습니다.
이 섹션에서는 해당 파일에 값을 입력합니다.

PowerShell ISE에서 역할 기능 파일을 열어 시작합니다.
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

2.  명령이 cmdlet인지, 아니면 함수인지 모르겠는 경우 `Get-Command`를 실행하고 "CommandType" 속성을 확인합니다.

3.  ValidatePattern은 허용 가능한 값 집합을 정의하기가 쉽지 않은 경우 정규식을 사용하여 매개 변수 인수를 제한할 수 있도록 합니다.
단일 매개 변수에 대해 ValidatePattern과 ValidateSet을 둘 다 정의할 수는 없습니다.

## 5단계: 새 세션 구성 등록
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
Description = 'An endpoint for Active Directory tasks.'

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
## 테스트
관리자가 아닌 사용자의 자격 증명을 가져옵니다.
```PowerShell
$HelpDeskCred = Get-Credential
```
[사용자 및 그룹 설정](creating-a-domain-controller.md#set-up-users-and-groups) 섹션을 따른 경우 자격 증명은 다음과 같습니다.
-   사용자 이름 = "HelpDeskUser"
-   암호 = "pa$$w0rd"

비관리자 자격 증명을 사용하여 ADHelpdesk 끝점에 원격으로 연결합니다.
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
## 주요 개념
**NoLanguage 모드**: PowerShell이 "NoLanguage" 모드에 있는 경우 사용자는 명령을 실행할 수만 있고 언어 요소를 사용할 수 없습니다.
자세한 내용은 `Get-Help about_Language_Modes`를 실행하십시오.

**PowerShell 함수**: PowerShell 함수는 이름으로 호출할 수 있는 PowerShell 코드 조각입니다.
자세한 내용은 `Get-Help about_Functions`를 실행하십시오.

**ValidateSet/ValidatePattern**: 명령을 노출할 때 특정 매개 변수에 대한 유효한 인수를 제한할 수 있습니다.
ValidateSet은 유효한 인수의 특정 목록입니다.
ValidatePattern은 해당 매개 변수에 대한 인수가 일치해야 하는 정규식입니다.




<!--HONumber=Jul16_HO1-->


