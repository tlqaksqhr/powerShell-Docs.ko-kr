---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "데모 끝점 다시 만들기"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: dabb5023012e90ace3fbc5f347c17821abd92595

---

# 데모 끝점 다시 만들기
이 섹션에서는 위의 섹션에서 사용한 데모 끝점의 정확한 복제본을 생성하는 방법을 살펴봅니다.
여기에서는 PowerShell 세션 구성 및 역할 기능을 비롯하여 JEA를 이해하는 데 필요한 핵심 개념을 소개합니다.

## PowerShell 세션 구성
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
대부분의 세션 구성은 Windows와 함께 제공되지만 "JEA_Demo" 세션 구성은 [필수 조건](prerequisites.md) 섹션에서 설정되었습니다.
관리자 PowerShell 프롬프트에서 다음 명령을 실행하여 등록된 모든 세션 구성을 확인할 수 있습니다.

```PowerShell
Get-PSSessionConfiguration
```

## PowerShell 세션 구성 파일
새로운 *PowerShell 세션 구성 파일*을 등록하여 세션 구성을 새로 만들 수 있습니다.
세션 구성 파일의 확장명은 ".pssc"입니다.
New-PSSessionConfigurationFile cmdlet을 사용하여 세션 구성 파일을 생성할 수 있습니다.

다음으로, JEA에 대한 새 세션 구성을 만들고 등록하겠습니다.

## PowerShell 세션 구성 생성 및 수정
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
*RestrictedRemoteServer*는 원격 관리에 필요한 최소 설정을 정의합니다.
기본적으로 *RestrictedRemoteServer* 끝점은 Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host 및 Out-Default를 노출합니다.
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

## PowerShell 세션 구성 적용

세션 구성 파일에서 끝점을 만들려면 파일을 등록해야 합니다.
이렇게 하려면 다음과 같은 몇 가지 정보가 필요합니다.

1. 세션 구성 파일의 경로.
2. 등록된 세션 구성의 이름. 이 이름은 사용자가 `Enter-PSSession` 또는 `New-PSSession`을 사용하여 끝점에 연결할 때 "ConfigurationName" 매개 변수에 제공하는 이름과 동일합니다.

로컬 컴퓨터에서 세션 구성을 등록하려면 다음 명령을 실행합니다.

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

축하합니다! JEA 끝점을 설정했습니다.

## 끝점 테스트
[JEA 사용](using-jea.md) 섹션에 나열된 단계를 새 끝점에 대해 다시 실행하여 의도한 대로 작동하는지 확인합니다.
Enter-PSSession에 구성 이름을 제공할 때 새 끝점의 이름(JEADemo2)을 사용해야 합니다.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## 주요 개념
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




<!--HONumber=Jun16_HO4-->


