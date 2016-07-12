---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "사전 요구 사항"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: ac9231a475ba84e9051bbd06a65f3f20c9e49846

---

# 필수 구성 요소

## 초기 상태
이 섹션을 시작하기 전에 다음을 확인하세요.

1. 시스템에서 JEA를 사용할 수 있습니다. 현재 지원되는 운영 체제와 필요한 다운로드에 대한 [추가 정보](./README.md)를 확인하세요.
2. JEA를 시도하고 있는 컴퓨터에 대한 관리 권한을 갖고 있습니다.
3. 컴퓨터가 도메인에 가입되어 있습니다.
도메인이 없는 경우 서버에서 새 도메인을 신속하게 설정하려면 [도메인 컨트롤러 만들기](#creating-a-domain-controller) 섹션을 참조하세요.

## PowerShell 원격 사용
JEA를 사용한 관리는 PowerShell 원격을 통해 발생합니다.
관리자 PowerShell 창에서 다음을 실행하여 PowerShell 원격이 사용되도록 설정되어 있고 올바르게 구성되어 있는지 확인합니다.

```PowerShell
Enable-PSRemoting
```

PowerShell 원격에 대해 잘 모르는 경우 `Get-Help about_Remote`를 실행하여 이 중요한 기본 개념에 대해 알아보는 것이 좋습니다.

## 사용자 또는 그룹 식별
JEA의 작동을 보여 주기 위해 이 가이드 전체에서 사용할 관리자가 아닌 사용자 및 그룹을 식별해야 합니다.

기존 도메인을 사용하는 경우 권한 없는 사용자 및 그룹을 식별하거나 만드세요.
이러한 관리자가 아닌 사용자에게 JEA에 대한 액세스 권한을 부여할 것입니다.
스크립트의 위쪽에 `$NonAdministrator` 변수가 표시되면 관리자가 아닌 선택한 사용자 또는 그룹에 이 변수를 할당합니다.

처음부터 새 도메인을 만든 경우 이 작업은 훨씬 쉽습니다.
부록의 [사용자 및 그룹 설정](creating-a-domain-controller.md#set-up-users-and-groups) 섹션을 사용하여 관리자가 아닌 사용자 및 그룹을 만드세요.
`$NonAdministrator`의 기본값은 해당 섹션에서 만든 그룹이 됩니다.

## 유지 관리 역할 기능 파일 설정
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

## 데모 세션 구성 파일 만들기 및 등록
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

## PowerShell 모듈 로깅 사용(선택 사항)
다음 단계에서는 시스템에서 모든 PowerShell 작업에 대한 로깅을 사용하도록 설정합니다.
이 기능은 JEA가 작동하도록 하기 위해 반드시 사용하도록 설정해야 하는 것은 아니지만 [JEA에 대한 보고](reporting-on-jea.md) 섹션에서 유용합니다.

1. 로컬 그룹 정책 편집기를 엽니다.
2. "컴퓨터 구성\관리 템플릿\Windows 구성 요소\Windows PowerShell"로 이동합니다.
3. "모듈 로깅 켜기"를 두 번 클릭합니다.
4. "사용"을 클릭합니다.
5. 옵션 섹션에서 모듈 이름 옆의 "표시"를 클릭합니다.
6. 팝업 창에 "\*"를 입력합니다. 이렇게 하면 PowerShell에서 모든 모듈의 명령을 로깅합니다.
7. 확인을 클릭하고 정책을 적용합니다.

참고: 그룹 정책을 통해 시스템 차원의 PowerShell 기록을 사용하도록 설정할 수도 있습니다.

**축하합니다. 이제 데모 끝점을 사용하여 컴퓨터를 구성했으며 JEA를 시작할 준비가 되었습니다.**




<!--HONumber=Jul16_HO1-->


