---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-RoleCapability
ms.openlocfilehash: 89aacd604d54f6a5e9752790be65cc3bcc77c8e1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="find-rolecapability"></a><span data-ttu-id="1153b-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1153b-103">Find-RoleCapability</span></span>

<span data-ttu-id="1153b-104">모듈에서 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="1153b-105">설명</span><span class="sxs-lookup"><span data-stu-id="1153b-105">Description</span></span>
<span data-ttu-id="1153b-106">Find-RoleCapability cmdlet은 모듈에서 PowerShell 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="1153b-107">Find-RoleCapability는 등록된 리포지토리에서 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-107">Find-RoleCapability searches modules in registered repositories.</span></span>
<span data-ttu-id="1153b-108">이 cmdlet은 찾은 각 역할 기능에 대해 PSGetRoleCapabilityInfo 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="1153b-109">역할 기능이 포함된 모듈을 설치하려면 Install-Module cmdlet에 PSGetRoleCapabilityInfo 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="1153b-110">PowerShell 역할 기능은 사용자가 JEA(Just Enough Administration) 끝점에서 사용자가 사용할 수 있는 명령, 응용 프로그램 등을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="1153b-111">역할 기능은 확장명이 .psrc인 파일에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="1153b-112">Find-RoleCapability는 버전 매개 변수(MinimumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="1153b-113">이러한 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="1153b-114">이 버전 매개 변수는 와일드카드 없이 단일 모듈 이름과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="1153b-115">RequiredVersion 매개 변수를 지정하지 않으면 Find-RoleCapability는 지정된 최소 버전과 같거나 그 이상인 최신 버전의 모듈 또는 최소 버전이 지정되지 않은 경우 최신 버전의 모듈을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="1153b-116">RequiredVersion 매개 변수를 지정하면 Find-RoleCapability는 지정된 버전과 정확하게 일치하는 버전의 모듈만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="1153b-117">Find-RoleCapability는 -Tag 매개 변수를 사용하여 모듈 메타데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="1153b-118">Find-RoleCapability는 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="1153b-119">Find-RoleCapability는 등록된 모든 또는 일부 리포지토리의 모듈을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1153b-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="1153b-120">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="1153b-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="1153b-121">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="1153b-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="1153b-122">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1153b-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="1153b-123">예제 명령</span><span class="sxs-lookup"><span data-stu-id="1153b-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```