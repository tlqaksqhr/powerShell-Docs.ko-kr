---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Install-Module
ms.openlocfilehash: c066f4b34a03206cc0f31e9d40144fd719d9e305
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2017
---
# <a name="install-module"></a><span data-ttu-id="c3d42-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="c3d42-103">Install-Module</span></span>

<span data-ttu-id="c3d42-104">온라인 리포지토리에서 로컬 컴퓨터에 PowerShell 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-104">Installs the PowerShell modules from online repositories to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="c3d42-105">설명</span><span class="sxs-lookup"><span data-stu-id="c3d42-105">Description</span></span>

<span data-ttu-id="c3d42-106">Install-Module cmdlet은 온라인 갤러리에서 하나 이상의 모듈을 다운로드하고 유효성을 검사한 다음 로컬 컴퓨터의 지정된 설치 범위에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-106">Install-Module cmdlet downloads one or more modules from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="c3d42-107">Install-Module cmdlet은 온라인 갤러리에서 지정된 조건을 충족하는 모듈을 하나 이상 가져오며, 검색 결과가 유효한 모듈인지 확인하고, 모듈 폴더를 설치 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-107">The Install-Module cmdlet gets one or more modules that meet specified criteria from an online gallery, verifies that search results are valid modules, and copies module folders to the installation location.</span></span>

<span data-ttu-id="c3d42-108">범위를 정의하지 않거나 Scope 매개 변수 값이 AllUsers이면 %systemdrive%:\Program Files\WindowsPowerShell\Modules에 모듈이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-108">When no scope is defined, or when the value of the Scope parameter is AllUsers, the module is installed to %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span></span> <span data-ttu-id="c3d42-109">Scope 값이 CurrentUser이면 $home\Documents\WindowsPowerShell\Modules에 모듈이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-109">When the value of Scope is CurrentUser, the module is installed to $home\Documents\WindowsPowerShell\Modules.</span></span>

<span data-ttu-id="c3d42-110">지정된 모듈의 최소 버전 및 정확한 버전에 따라 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-110">You can filter your results based on minimum and exact versions of specified modules.</span></span>

- <span data-ttu-id="c3d42-111">Windows PowerShell 5.0 이상에서 Side-by-side 버전 지원</span><span class="sxs-lookup"><span data-stu-id="c3d42-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
- <span data-ttu-id="c3d42-112">모듈 종속성 설치 지원</span><span class="sxs-lookup"><span data-stu-id="c3d42-112">Module dependency installation support</span></span>
- <span data-ttu-id="c3d42-113">**신뢰할 수 없음 프롬프트:** 신뢰할 수 없는 리포지토리의 모듈을 설치하려면 사용자 승인이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-113">**Untrusted prompt:**User acceptance is required for installing the modules from an untrusted repository.</span></span>
- <span data-ttu-id="c3d42-114">-Force는 설치된 모듈을 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-114">-Force reinstalls the installed module</span></span>
- <span data-ttu-id="c3d42-115">RequiredVersion은 PowerShell 버전 5.0 이상에서 지정된 버전을 기존 버전과 함께 SxS로 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-115">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

### <a name="scope"></a><span data-ttu-id="c3d42-116">Scope</span><span class="sxs-lookup"><span data-stu-id="c3d42-116">Scope</span></span>
<span data-ttu-id="c3d42-117">모듈의 설치 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-117">Specifies the installation scope of the module.</span></span> <span data-ttu-id="c3d42-118">이 매개 변수에 허용되는 값은 AllUsers 및 CurrentUser입니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-118">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="c3d42-119">기본 설치 범위는 AllUsers입니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-119">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="c3d42-120">AllUsers 범위를 지정하면 컴퓨터의 모든 사용자가 액세스할 수 있는 위치, 즉 "$env:SystemDrive\Program Files\WindowsPowerShell\Modules"에 모듈을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-120">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span></span>

<span data-ttu-id="c3d42-121">CurrentUser 범위를 지정하면 현재 사용자만 모듈을 사용할 수 있도록 "$home\Documents\WindowsPowerShell\Modules"에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-121">The CurrentUser scope lets modules be installed only to "$home\Documents\WindowsPowerShell\Modules", so that the module is available only to the current user.</span></span>

## <a name="notes"></a><span data-ttu-id="c3d42-122">참고</span><span class="sxs-lookup"><span data-stu-id="c3d42-122">Notes</span></span>

<span data-ttu-id="c3d42-123">이 cmdlet은 Windows PowerShell 3.0 이상 버전의 Windows PowerShell, Windows 7 또는 Windows 2008 R2 이상 버전의 Windows에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-123">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="c3d42-124">설치된 모듈을 가져올 수 없는 경우(즉, 동일한 이름의 .psm1, .psd1 또는 .dll이 폴더 안에 없는 경우) 명령에 Force 매개 변수를 추가하지 않으면 설치에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-124">If an installed module cannot be imported (that is, if it does not have a .psm1, .psd1, or .dll of the same name within the folder), installation fails unless you add the Force parameter to your command.</span></span>

<span data-ttu-id="c3d42-125">컴퓨터의 모듈 버전이 Name 매개 변수에 지정된 값과 일치하고 MinimumVersion 또는 RequiredVersion 매개 변수를 추가하지 않은 경우 Install-Module은 해당 모듈을 설치하지 않고 자동으로 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-125">If a version of the module on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span> <span data-ttu-id="c3d42-126">MinimumVersion 또는 RequiredVersion 매개 변수를 지정했으며 기존 모듈이 해당 매개 변수의 값과 일치하지 않는 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-126">If the MinimumVersion or RequiredVersion parameters are specified, and the existing module does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="c3d42-127">더 구체적으로, 현재 설치된 모듈의 버전이 MinimumVersion 매개 변수 값보다 작거나 RequiredVersion 매개 변수 값과 다르면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-127">To be more specific: if the version of the currently-installed module is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="c3d42-128">설치된 모듈의 버전이 MinimumVersion 매개 변수 값보다 크거나 RequiredVersion 매개 변수 값과 같으면 Install-Module은 모듈을 설치하지 않고 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-128">If the version of the installed module is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span>

<span data-ttu-id="c3d42-129">온라인 갤러리에 지정된 이름과 일치하는 모듈이 없는 경우 Install-Module에서 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-129">Install-Module returns an error if no module exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="c3d42-130">여러 모듈을 설치하려면 모듈 이름 배열을 쉼표로 구분하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-130">To install multiple modules, specify an array of the module names, separated by commas.</span></span> <span data-ttu-id="c3d42-131">여러 모듈 이름을 지정하는 경우 MinimumVersion 또는 RequiredVersion을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-131">You cannot add MinimumVersion or RequiredVersion if you specify multiple module names.</span></span>

<span data-ttu-id="c3d42-132">기본적으로 모듈은 Windows PowerShell DSC(필요한 상태 구성) 리소스를 설치할 때 혼동을 방지하기 위해 Program Files 폴더에 설치됩니다. 여러 개의 PSGetItemInfo 개체를 Install-Module에 파이프할 수 있습니다. 이는 단일 명령으로 설치할 여러 모듈을 지정하는 또 다른 방법이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-132">By default, modules are installed to the Program Files folder, to prevent confusion when you are installing Windows PowerShell Desired State Configuration (DSC) resources.You can pipe multiple PSGetItemInfo objects to Install-Module; this is another way of specifying multiple modules to install in a single command.</span></span>

<span data-ttu-id="c3d42-133">악성 코드를 포함하는 모듈이 실행되지 않도록 설치된 모듈을 설치 시 자동으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-133">To help prevent running modules that contain malicious code, installed modules are not automatically imported by installation.</span></span> <span data-ttu-id="c3d42-134">보안상, 모듈의 cmdlet 또는 함수를 처음 실행하기 전에 먼저 모듈 코드를 평가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-134">As a security best practice, evaluate module code before running any cmdlets or functions in a module for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="c3d42-135">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="c3d42-135">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="c3d42-136">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="c3d42-136">Cmdlet online help reference</span></span>

[<span data-ttu-id="c3d42-137">Install-Module</span><span class="sxs-lookup"><span data-stu-id="c3d42-137">Install-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a><span data-ttu-id="c3d42-138">예제 명령</span><span class="sxs-lookup"><span data-stu-id="c3d42-138">Example commands</span></span>

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install a specific prerelease version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -AllowPrerelease

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

## <a name="install-module-cmdlet-in-pipeline-operations"></a><span data-ttu-id="c3d42-139">파이프라인 작업의 Install-Module cmdlet</span><span class="sxs-lookup"><span data-stu-id="c3d42-139">Install-Module cmdlet in pipeline operations</span></span>

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

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="c3d42-140">PowerShell 5.0 이상의 Side-by-Side 버전 지원</span><span class="sxs-lookup"><span data-stu-id="c3d42-140">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="c3d42-141">PowerShellGet은 Windows PowerShell 5.0 이상에서 실행되는 Install-Module, Update-Module 및 Publish-Module cmdlet에서 SxS(side-by-side) 모듈 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d42-141">PowerShellGet supports the side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>

### <a name="install-module-examples"></a><span data-ttu-id="c3d42-142">Install-Module 예제</span><span class="sxs-lookup"><span data-stu-id="c3d42-142">Install-Module examples</span></span>

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

## <a name="install-module-with-its-dependencies"></a><span data-ttu-id="c3d42-143">종속성과 함께 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="c3d42-143">Install module with its dependencies</span></span>

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

## <a name="error-scenarios"></a><span data-ttu-id="c3d42-144">오류 시나리오</span><span class="sxs-lookup"><span data-stu-id="c3d42-144">Error scenarios</span></span>

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

