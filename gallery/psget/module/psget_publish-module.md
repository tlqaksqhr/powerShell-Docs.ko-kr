---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Publish-Module
ms.openlocfilehash: 8b73be2814678ce143cc5b53e2b8103b3297eb6a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="publish-module"></a>Publish-Module

로컬 컴퓨터에서 지정된 모듈을 온라인 갤러리에 게시합니다.

## <a name="description"></a>설명

**Publish-Module** cmdlet은 갤러리에 사용자 프로필의 일부로 저장된 API 키를 사용하여 온라인 NuGet 기반 갤러리에 모듈을 게시합니다. 모듈의 이름 또는 모듈을 포함하는 폴더의 경로를 통해 게시할 모듈을 지정할 수 있습니다.

이름으로 모듈을 지정하는 경우 **Publish-Module**은 `Get-Module -ListAvailable <Name>`을 실행하면 검색되는 첫 번째 모듈을 게시합니다. 게시할 모듈의 최소 버전을 지정하면 **Publish-Module**은 버전이 지정한 최소 버전과 같거나 그 이상인 첫 번째 모듈을 게시합니다.

모듈을 게시하려면 모듈에 대한 갤러리 페이지에 표시되는 메타데이터가 필요합니다. 필수 메타데이터에는 모듈 이름, 버전, 설명, 만든 이 등이 포함됩니다. 대부분의 메타데이터는 모듈 매니페스트에서 가져오지만 일부 메타데이터는 *Tag, ReleaseNote, IconUri, ProjectUri,* *LicenseUri* 등의 **Publish-Module** 매개 변수에 지정해야 합니다. 이러한 매개 변수는 NuGet 기반 갤러리의 필드와 일치하기 때문입니다.

RequiredVersion 매개 변수를 사용하면 게시할 모듈의 정확한 버전을 지정할 수 있습니다.
또한 Path 매개 변수는 버전 폴더가 포함된 모듈 기본 경로를 지원합니다.
Publish-Module cmdlet의 Force 스위치 매개 변수는 메시지를 표시하지 않고 NuGet.exe를 부트스트랩합니다.

## <a name="cmdlet-syntax"></a>Cmdlet 구문
```powershell
Get-Command -Name Publish-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet 온라인 도움말 참조

[Publish-Module](http://go.microsoft.com/fwlink/?LinkID=398575)

## <a name="example-commands"></a>예제 명령

```powershell
ContosoServer module with different versions to be published.
PS C:\\windows\\system32> Get-Module -Name ContosoServer -ListAvailable
Directory: C:\\Program Files\\WindowsPowerShell\\Modules
ModuleType Version Name ExportedCommands
---------- ------- ---- ----------------
Manifest 2.8 ContosoServer Get-ContosoServer
Manifest 2.0 ContosoServer Get-ContosoServer
Manifest 1.5 ContosoServer Get-ContosoServer
Manifest 1.0 ContosoServer Get-ContosoServer
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.0 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.5 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Path "C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0" -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
_------ ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
2.0 ContosoServer LocalRepo ContosoServer module
```

## <a name="publishing-a-module-with-dependencies"></a>종속성과 함께 모듈 게시

### <a name="create-a-module-with-dependencies-and-version-range-specified-in-requiredmodules-property-of-its-module-manifest"></a>모듈 매니페스트의 RequiredModules 속성에 종속성 및 버전 범위를 지정하여 모듈을 만듭니다.

**참고:**
  - \*은(는) MaximumVersion에서만 지원되며 버전 문자열의 끝에도 있어야 합니다.
  - \*은(는) version 개체에서 999999999로 대체됩니다.

```powershell
PS C:\windows\system32> $requiredModules = @( @{ModuleName = 'RequiredModule1'; ModuleVersion = '0.1'; MaximumVersion = '1.9'; }, @{ModuleName = 'RequiredModule2'; MaximumVersion = '1.*'; })

PS C:\windows\system32> cd C:\MyModules\ModuleWithDependencies

PS C:\MyModules\ModuleWithDependencies> New-ModuleManifest -Path .\ModuleWithDependencies.psd1 -ModuleVersion 1.0 -RequiredModules $requiredModules -Description 'ModuleWithDependencies demo module'
```

### <a name="publish-modulewithdependencies-module-with-dependencies-to-the-repository"></a>종속성과 함께 ModuleWithDependencies 모듈을 리포지토리에 게시합니다.

```powershell
PS C:\MyModules\ModuleWithDependencies> Publish-Module -Path C:\MyModules\ModuleWithDependencies -Repository LocalRepo
```

### <a name="find-modulewithdependencies-module-with-its-dependencies-by-specifying--includedependencies"></a>-IncludeDependencies를 지정하여 종속성과 함께 ModuleWithDependencies 모듈을 찾습니다.

```powershell
PS C:\MyModules\ModuleWithDependencies> Find-Module -Name ModuleWithDependencies -Repository LocalRepo -IncludeDependencies

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="install-the-modulewithdependencies-module-with-dependencies"></a>종속성과 함께 ModuleWithDependencies 모듈을 설치합니다.
버전 범위는 종속성을 설치하는 동안 적용됩니다.

```powershell
PS C:\windows\system32> Get-InstalledModule
PS C:\windows\system32>
PS C:\windows\system32> Install-Module -Name ModuleWithDependencies -Repository LocalRepo
PS C:\windows\system32>
PS C:\windows\system32> Get-InstalledModule

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="contents-of-modulewithdependencies2-module-manifest-file"></a>ModuleWithDependencies2 모듈 매니페스트 파일의 내용

```powershell
@{
# Version number of this module.
ModuleVersion = '2.0'
# ID used to uniquely identify this module
GUID = '0eae34da-99dd-4608-8d28-c614fe7b0841'
# Author of this module
Author = 'manikb'
# Company or vendor of this module
CompanyName = 'Unknown'
# Copyright statement for this module
Copyright = '(c) 2015 manikb. All rights reserved.'
# Description of the functionality provided by this module
Description = 'ModuleWithDependencies2 module'
# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @('RequiredModule1',
@{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'RequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'RequiredModule4'; ModuleVersion = '1.1'; MaximumVersion = '2.0'; },
@{ModuleName = 'RequiredModule5'; MaximumVersion = '1.5'; })
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @('NestedRequiredModule1',
@{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'NestedRequiredModule4'; ModuleVersion = '0.7'; MaximumVersion = '2.4'; },
@{ModuleName = 'NestedRequiredModule5'; MaximumVersion = '1.6'; },'ModuleWithDependencies2.psm1')
# Functions to export from this module
FunctionsToExport = '\*'
# Cmdlets to export from this module
CmdletsToExport = '\*'
# Variables to export from this module
VariablesToExport = '\*'
# Aliases to export from this module
AliasesToExport = '\*'
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
      # Tags applied to this module. These help with module discovery in online galleries.
      Tags = 'Tag1', 'Tag2', 'Tag-ModuleWithDependencies2-2.0'
      # A URL to the license for this module.
      LicenseUri = 'http://modulewithdependencies2.com/license'
      # A URL to the main website for this project.
      ProjectUri = 'http://modulewithdependencies2.com/'
      # A URL to an icon representing this module.
      IconUri = 'http://modulewithdependencies2.com/icon'
      # ReleaseNotes of this module
      ReleaseNotes = 'ModuleWithDependencies2 release notes'
    } # End of PSData hashtable
} # End of PrivateData hashtable
}
```


### <a name="external-dependencies"></a>외부 종속성
일부 모듈 종속성은 외부에서 관리할 수 있으며, 이 경우 모듈 매니페스트의 PSData 섹션에 있는 ExternalModuleDependencies 항목에 종속성을 추가해야 합니다.

리포지토리에서 'SnippetPx'를 사용할 수 없는 경우 아래 오류가 발생합니다.
```powershell
Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
```