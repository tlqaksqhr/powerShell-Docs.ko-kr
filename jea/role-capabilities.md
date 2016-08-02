---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "역할 기능"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 81fd386d58576a8930093b4f18ce36a4ff6cecd0
ms.openlocfilehash: a3dd4a217f5b1fd80e97adf802c65073ca015bbc

---

# 역할 기능

## 개요
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

## 역할 기능 만들기
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

# Create a RoleCapabilities folder in the Contoso_AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```

축하합니다. 비어 있는 역할 기능 파일을 만들었습니다.
이 파일은 다음 섹션에서 사용됩니다.

## 주요 개념
**역할 기능(.psrc)**: 사용자가 JEA 끝점에서 수행할 수 있는 "작업"을 정의하는 파일입니다.
이 파일은 표시되는 명령, 표시되는 콘솔 응용 프로그램 등의 허용 목록을 열거합니다.
PowerShell에서 역할 기능을 검색하도록 하려면 유효한 PowerShell 모듈의 "RoleCapabilities" 폴더에 역할 기능을 배치해야 합니다.

**PowerShell 모듈**: PowerShell 기능의 패키지이며,
PowerShell 함수, cmdlet, DSC 리소스, 역할 기능 등을 포함할 수 있습니다.
PowerShell 모듈이 자동으로 로드되려면 `$env:PSModulePath`의 경로 아래에 있어야 합니다.




<!--HONumber=Jul16_HO1-->


