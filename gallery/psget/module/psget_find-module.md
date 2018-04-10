---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Module
ms.openlocfilehash: 03dff4454a31638df564568ef51eec158685c8e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="find-module"></a><span data-ttu-id="6d199-103">Find-Module</span><span class="sxs-lookup"><span data-stu-id="6d199-103">Find-Module</span></span>
<span data-ttu-id="6d199-104">온라인 갤러리에서 지정된 조건과 일치하는 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-104">Finds modules from an online gallery that match specified criteria.</span></span>

## <a name="description"></a><span data-ttu-id="6d199-105">설명</span><span class="sxs-lookup"><span data-stu-id="6d199-105">Description</span></span>
<span data-ttu-id="6d199-106">Find-Module은 등록된 리포지토리에서 지정된 조건과 일치하는 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-106">Find-Module discovers the modules from registered repositories that matches the specified criteria.</span></span>
<span data-ttu-id="6d199-107">찾은 각 모듈에 대해 Find-Module은 PSRepositoryItemInfo 개체를 반환하며, 필요에 따라 이 개체를 Install-Module에 파이프하여 모듈을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-107">For each module found, Find-Module returns a PSRepositoryItemInfo object which can optionally be piped to Install-Module for installing the modules.</span></span>

- <span data-ttu-id="6d199-108">Find-Module은 -Command, -DscResource, -RoleCapability 및 -Includes 매개 변수를 사용하여 모듈 콘텐츠를 기준으로 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-108">Find-Module can filter based on module contents with the -Command, -DscResource, -RoleCapability and -Includes parameters.</span></span>
- <span data-ttu-id="6d199-109">Find-Module은 버전 매개 변수(MinimumVersion, MaximumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-109">Find-Module can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="6d199-110">이러한 매개 변수는 MinmimumVersion 및 MaximumVersion을 제외하고 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="6d199-111">이 버전 매개 변수는 와일드카드 없이 단일 모듈 이름과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-111">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="6d199-112">RequiredVersion 매개 변수를 지정하지 않으면 Find-Module은 지정된 최소 버전과 같거나 그 이상인 최신 버전의 모듈 또는 최소 버전이 지정되지 않은 경우 최신 버전의 모듈을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-112">If the RequiredVersion parameter is not specified, Find-Module returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="6d199-113">RequiredVersion 매개 변수를 지정하면 Find-Module은 지정된 버전과 정확하게 일치하는 버전의 모듈만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-113">If the RequiredVersion parameter is specified, Find-Module only returns the version of module that exactly matches the specified version.</span></span>
- <span data-ttu-id="6d199-114">Find-Module은 -Tag 매개 변수를 사용하여 모듈 메타데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-114">Find-Module can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="6d199-115">Find-Module은 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-115">Find-Module can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="6d199-116">Find-Module은 등록된 모든 또는 일부 리포지토리의 모듈을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d199-116">Find-Module can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="6d199-117">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="6d199-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="6d199-118">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="6d199-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="6d199-119">Find-Module</span><span class="sxs-lookup"><span data-stu-id="6d199-119">Find-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398574)

## <a name="example-commands"></a><span data-ttu-id="6d199-120">예제 명령</span><span class="sxs-lookup"><span data-stu-id="6d199-120">Example commands</span></span>
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion.
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module with a specific prerelease version
Find-Module -Name AzureRM -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```