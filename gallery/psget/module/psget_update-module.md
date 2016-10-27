---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: "psget_update 모듈"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: c7eb34252ad912c83168bc763425e0dc76e27813

---

# Update-Module

온라인 갤러리에서 지정된 모듈의 최신 버전을 로컬 컴퓨터에 다운로드하여 설치합니다.

## 설명

Update-Module cmdlet은 로컬 컴퓨터에서 Install-Module을 실행하여 온라인 갤러리에서 설치된 Windows PowerShell 모듈의 최신 버전을 설치합니다.

필요한 버전을 지정하지 않으면 기본적으로 온라인 갤러리에서 사용할 수 있는 지정된 모듈의 최신 버전이 설치됩니다. 모듈 이름을 지정하여 설치된 기존 모듈을 업데이트할 수 있습니다. Update-Module은 $env:PSModulePath에서 업데이트할 모듈을 검색합니다.

Name 매개 변수 없이 Update-Module을 실행하면 로컬 컴퓨터에서 업데이트할 수 있는 모든 모듈이 업데이트됩니다.

### 참고

- 이 cmdlet은 Windows PowerShell 3.0 이상 버전의 Windows PowerShell, Windows 7 또는 Windows 2008 R2 이상 버전의 Windows에서 실행됩니다.
- Name 매개 변수를 사용하여 지정한 모듈이 Install-Module을 통해 설치되지 않은 경우 오류가 발생합니다. Install-Module을 실행하여 온라인 갤러리에서 설치한 모듈에서만 Update-Module을 실행할 수 있습니다.
- Update-Module이 사용 중인 이진 파일을 업데이트하려고 하면 Update-Module에서 문제 프로세스를 식별하고, 프로세스를 중지한 후 Update-Module을 다시 시도하도록 사용자에게 알리는 오류가 반환됩니다.
- PowerShell 5.0 이상 버전에서 Update-Module은 모듈을 업데이트할 때 최신(또는 지정된) 버전의 모듈을 추가하므로 이제 이전 버전과 최신 버전이 동일한 디렉터리에 나란히 포함됩니다. 해당 메시지를 표시하고 이러한 명령의 출력 예를 보여 주는 것이 좋습니다.


## Cmdlet 구문
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## Cmdlet 온라인 도움말 참조

[Update-Module](http://go.microsoft.com/fwlink/?LinkID=398576)


## 예제 명령

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  종속성이 있는 TestDepWithNestedRequiredModules1 모듈을 업데이트합니다.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```




<!--HONumber=Oct16_HO2-->


