---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC PackageManagement 리소스
ms.openlocfilehash: e6eea9f0bae42e131976dacb9813da759ff31239
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="b6122-103">DSC PackageManagement 리소스</span><span class="sxs-lookup"><span data-stu-id="b6122-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="b6122-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b6122-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b6122-105">Windows PowerShell DSC(필요한 상태 구성)의 **PackageManagement** 리소스는 대상 노드에서 패키지 관리 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="b6122-106">이 리소스를 사용하려면 http://PowerShellGallery.com에서 제공하는 **PackageManagement** 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6122-107">구문</span><span class="sxs-lookup"><span data-stu-id="b6122-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="b6122-108">속성</span><span class="sxs-lookup"><span data-stu-id="b6122-108">Properties</span></span>
|  <span data-ttu-id="b6122-109">속성</span><span class="sxs-lookup"><span data-stu-id="b6122-109">Property</span></span>  |  <span data-ttu-id="b6122-110">설명</span><span class="sxs-lookup"><span data-stu-id="b6122-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="b6122-111">이름</span><span class="sxs-lookup"><span data-stu-id="b6122-111">Name</span></span>| <span data-ttu-id="b6122-112">설치하거나 제거할 패키지의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-112">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="b6122-113">원본</span><span class="sxs-lookup"><span data-stu-id="b6122-113">Source</span></span>| <span data-ttu-id="b6122-114">패키지를 찾을 수 있는 패키지 원본의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="b6122-115">이는 Register-PackageSource 또는 PackageManagementSource DSC 리소스에 등록된 원본 또는 URI일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="b6122-116">DSC 리소스 MSFT_PackageManagementSource도 패키지 원본을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>|
| <span data-ttu-id="b6122-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="b6122-117">Ensure</span></span>| <span data-ttu-id="b6122-118">패키지를 설치할지 또는 제거할지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="b6122-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b6122-119">RequiredVersion</span></span>| <span data-ttu-id="b6122-120">설치할 패키지의 정확한 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="b6122-121">이 매개 변수를 지정하지 않으면 이 DSC 리소스는 MaximumVersion 매개 변수로 지정된 최대 버전도 만족하는 패키지의 사용 가능한 최신 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>|
| <span data-ttu-id="b6122-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b6122-122">MinimumVersion</span></span>| <span data-ttu-id="b6122-123">설치할 패키지의 최소 허용 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="b6122-124">이 매개 변수를 추가하지 않으면 이 DSC 리소스는 MaximumVersion 매개 변수로 지정된 최대 지정 버전도 만족하는 패키지의 사용 가능한 가장 높은 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>|
| <span data-ttu-id="b6122-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b6122-125">MaximumVersion</span></span>| <span data-ttu-id="b6122-126">설치할 패키지의 최대 허용 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="b6122-127">이 매개 변수를 지정하지 않으면 이 DSC 리소스는 패키지의 사용 가능한 가장 높은 번호가 지정된 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>|
| <span data-ttu-id="b6122-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="b6122-128">SourceCredential</span></span> | <span data-ttu-id="b6122-129">지정된 패키지 공급자 또는 원본에 대한 패키지를 설치하는 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|
| <span data-ttu-id="b6122-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="b6122-130">ProviderName</span></span>| <span data-ttu-id="b6122-131">패키지 검색 범위를 지정할 패키지 공급자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="b6122-132">Get-PackageProvider cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>|
| <span data-ttu-id="b6122-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="b6122-133">AdditionalParameters</span></span>| <span data-ttu-id="b6122-134">Hashtable로 전달되는 공급자별 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="b6122-135">예를 들어 NuGet 공급자의 경우 DestinationPath와 같은 추가 매개 변수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="b6122-136">추가 매개 변수</span><span class="sxs-lookup"><span data-stu-id="b6122-136">Additional Parameters</span></span>
<span data-ttu-id="b6122-137">다음 표에는 AdditionalParameters 속성에 대한 옵션이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="b6122-138">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b6122-138">Parameter</span></span>  | <span data-ttu-id="b6122-139">설명</span><span class="sxs-lookup"><span data-stu-id="b6122-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="b6122-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="b6122-140">DestinationPath</span></span>| <span data-ttu-id="b6122-141">기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="b6122-142">패키지를 설치할 파일 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="b6122-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="b6122-143">InstallationPolicy</span></span>| <span data-ttu-id="b6122-144">기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="b6122-145">패키지 원본을 신뢰할 수 있는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="b6122-146">"Untrusted"와 "Trusted" 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="b6122-147">예제</span><span class="sxs-lookup"><span data-stu-id="b6122-147">Example</span></span>

<span data-ttu-id="b6122-148">이 예제에서는 **PackageManagement** DSC 리소스를 사용하여 **JQuery** NuGet 패키지 및 **GistProvider** PowerShell 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="b6122-149">이 예제에서는 먼저 필요한 패키지 원본을 사용할 수 있는지를 확인한 다음 **JQuery** 및 **GistProvider** 패키지(각각 NuGet 및 PowerShell)의 필요한 상태를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b6122-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceUri   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```