---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a><span data-ttu-id="51f33-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="51f33-103">Find-DscResource</span></span>

<span data-ttu-id="51f33-104">모듈에서 DSC 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="51f33-105">설명</span><span class="sxs-lookup"><span data-stu-id="51f33-105">Description</span></span>

<span data-ttu-id="51f33-106">Find-DscResource cmdlet은 등록된 리포지토리에서 지정된 조건과 일치하는, 모듈에 포함된 [DSC(필요한 상태 구성)](https://msdn.microsoft.com/PowerShell/dsc/overview) 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="51f33-107">이 cmdlet이 찾는 각 모듈에 대해 Find-DscResource는 PSGetDscResourceInfo 개체를 반환하며, 이 개체를 Install-Module에 파이프하면 이 cmdlet이 반환하는 리소스가 포함된 모듈을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="51f33-108">DSC는 소프트웨어 서비스에 대한 구성 데이터를 배포 및 관리하고 이러한 서비스가 실행되는 환경을 관리할 수 있도록 해주는 Windows PowerShell의 새로운 관리 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="51f33-109">DSC(필요한 상태 구성) 리소스에서는 DSC 구성에 대한 구성 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="51f33-110">리소스는 구성할 수 있는 속성(스키마)을 노출하고 LCM(로컬 구성 관리자)이 "그대로 수행"하기 위해 호출하는 PowerShell 스크립트 함수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="51f33-111">리소스는 파일만큼 일반적이거나 IIS 서버만큼 특별한 것을 모델링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="51f33-112">같은 리소스들의 그룹은 모든 필수 파일을 이식 가능한 구조로 정리하고, 리소스를 사용하려고 한 방법을 식별하는 메타데이터를 포함하는 DSC 모듈에 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="51f33-113">Find-DscResource는 버전 매개 변수(MinimumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="51f33-114">이러한 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="51f33-115">이 버전 매개 변수는 와일드카드 없이 단일 모듈 이름과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="51f33-116">RequiredVersion 매개 변수를 지정하지 않으면 Find-DscResource는 지정된 최소 버전과 같거나 그 이상인 최신 버전의 모듈 또는 최소 버전이 지정되지 않은 경우 최신 버전의 모듈을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="51f33-117">RequiredVersion 매개 변수를 지정하면 Find-DscResource는 지정된 버전과 정확하게 일치하는 버전의 모듈만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="51f33-118">Find-DscResource는 -Tag 매개 변수를 사용하여 모듈 메타데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="51f33-119">Find-DscResource는 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="51f33-120">Find-DscResource는 등록된 모든 또는 일부 리포지토리의 모듈을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51f33-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="51f33-121">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="51f33-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="51f33-122">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="51f33-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="51f33-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="51f33-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="51f33-124">예제 명령</span><span class="sxs-lookup"><span data-stu-id="51f33-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```