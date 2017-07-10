---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Install-Module
ms.openlocfilehash: 37e07cd32e7b2fd4a7a8e6cab179aecc3251baf3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="install-module" class="xliff"></a>
# Install-Module

온라인 리포지토리에서 로컬 컴퓨터에 PowerShell 모듈을 설치합니다.

<a id="description" class="xliff"></a>
## 설명

Install-Module cmdlet은 온라인 갤러리에서 하나 이상의 모듈을 다운로드하고 유효성을 검사한 다음 로컬 컴퓨터의 지정된 설치 범위에 설치합니다.

Install-Module cmdlet은 온라인 갤러리에서 지정된 조건을 충족하는 모듈을 하나 이상 가져오며, 검색 결과가 유효한 모듈인지 확인하고, 모듈 폴더를 설치 위치에 복사합니다.

범위를 정의하지 않거나 Scope 매개 변수 값이 AllUsers이면 %systemdrive%:\Program Files\WindowsPowerShell\Modules에 모듈이 설치됩니다. Scope 값이 CurrentUser이면 $home\Documents\WindowsPowerShell\Modules에 모듈이 설치됩니다.

지정된 모듈의 최소 버전 및 정확한 버전에 따라 결과를 필터링할 수 있습니다.

- Windows PowerShell 5.0 이상에서 Side-by-side 버전 지원
- 모듈 종속성 설치 지원
- **신뢰할 수 없음 프롬프트:** 신뢰할 수 없는 리포지토리의 모듈을 설치하려면 사용자 승인이 필요합니다.
- -Force는 설치된 모듈을 다시 설치합니다.
- RequiredVersion은 PowerShell 버전 5.0 이상에서 지정된 버전을 기존 버전과 함께 SxS로 설치합니다.

<a id="scope" class="xliff"></a>
### Scope
모듈의 설치 범위를 지정합니다. 이 매개 변수에 허용되는 값은 AllUsers 및 CurrentUser입니다.

기본 설치 범위는 AllUsers입니다.

AllUsers 범위를 지정하면 컴퓨터의 모든 사용자가 액세스할 수 있는 위치, 즉 "$env:SystemDrive\Program Files\WindowsPowerShell\Modules"에 모듈을 설치할 수 있습니다.

CurrentUser 범위를 지정하면 현재 사용자만 모듈을 사용할 수 있도록 "$home\Documents\WindowsPowerShell\Modules"에 설치할 수 있습니다.

<a id="notes" class="xliff"></a>
## 참고

이 cmdlet은 Windows PowerShell 3.0 이상 버전의 Windows PowerShell, Windows 7 또는 Windows 2008 R2 이상 버전의 Windows에서 실행됩니다.

설치된 모듈을 가져올 수 없는 경우(즉, 동일한 이름의 .psm1, .psd1 또는 .dll이 폴더 안에 없는 경우) 명령에 Force 매개 변수를 추가하지 않으면 설치에 실패합니다.

컴퓨터의 모듈 버전이 Name 매개 변수에 지정된 값과 일치하고 MinimumVersion 또는 RequiredVersion 매개 변수를 추가하지 않은 경우 Install-Module은 해당 모듈을 설치하지 않고 자동으로 계속됩니다. MinimumVersion 또는 RequiredVersion 매개 변수를 지정했으며 기존 모듈이 해당 매개 변수의 값과 일치하지 않는 경우 오류가 발생합니다. 더 구체적으로, 현재 설치된 모듈의 버전이 MinimumVersion 매개 변수 값보다 작거나 RequiredVersion 매개 변수 값과 다르면 오류가 발생합니다. 설치된 모듈의 버전이 MinimumVersion 매개 변수 값보다 크거나 RequiredVersion 매개 변수 값과 같으면 Install-Module은 모듈을 설치하지 않고 계속됩니다.

온라인 갤러리에 지정된 이름과 일치하는 모듈이 없는 경우 Install-Module에서 오류가 반환됩니다.

여러 모듈을 설치하려면 모듈 이름 배열을 쉼표로 구분하여 지정합니다. 여러 모듈 이름을 지정하는 경우 MinimumVersion 또는 RequiredVersion을 추가할 수 없습니다.

기본적으로 모듈은 Windows PowerShell DSC(필요한 상태 구성) 리소스를 설치할 때 혼동을 방지하기 위해 Program Files 폴더에 설치됩니다. 여러 개의 PSGetItemInfo 개체를 Install-Module에 파이프할 수 있습니다. 이는 단일 명령으로 설치할 여러 모듈을 지정하는 또 다른 방법이기도 합니다.

악성 코드를 포함하는 모듈이 실행되지 않도록 설치된 모듈을 설치 시 자동으로 가져오지 않습니다. 보안상, 모듈의 cmdlet 또는 함수를 처음 실행하기 전에 먼저 모듈 코드를 평가하는 것이 좋습니다.


<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 구문
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 온라인 도움말 참조

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=398573)

<a id="example-commands" class="xliff"></a>
## 예제 명령

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name 
```

<a id="install-module-cmdlet-in-pipeline-operations" class="xliff"></a>
## 파이프라인 작업의 Install-Module cmdlet

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

<a id="side-by-side-version-support-on-powershell-50-or-newer" class="xliff"></a>
## PowerShell 5.0 이상의 Side-by-Side 버전 지원

PowerShellGet은 Windows PowerShell 5.0 이상에서 실행되는 Install-Module, Update-Module 및 Publish-Module cmdlet에서 SxS(side-by-side) 모듈 버전을 지원합니다.

<a id="install-module-examples" class="xliff"></a>
### Install-Module 예제

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

<a id="install-module-with-its-dependencies" class="xliff"></a>
## 종속성과 함께 모듈 설치

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

<a id="error-scenarios" class="xliff"></a>
## 오류 시나리오

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```

