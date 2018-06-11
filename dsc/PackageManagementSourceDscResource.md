---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: DSC PackageManagementSource 리소스
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753773"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="b8b42-103">DSC PackageManagementSource 리소스</span><span class="sxs-lookup"><span data-stu-id="b8b42-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="b8b42-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="b8b42-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="b8b42-105">Windows PowerShell DSC(필요한 상태 구성)의 **PackageManagementSource** 리소스는 대상 노드에서 패키지 관리 원본을 등록하거나 등록 취소하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="b8b42-106">**이 방법으로 등록된 패키지 관리 원본은 시스템 계정이나 DSC 엔진에서 사용할 수 있는 시스템 컨텍스트에서 등록됩니다.**</span><span class="sxs-lookup"><span data-stu-id="b8b42-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="b8b42-107">이 리소스를 사용하려면 http://PowerShellGallery.com에서 제공하는 **PackageManagement** 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8b42-108">다음 속성 정보가 올바르려면 **PackageManagement** 모듈이 버전 1.1.7.0 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8b42-109">구문</span><span class="sxs-lookup"><span data-stu-id="b8b42-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="b8b42-110">속성</span><span class="sxs-lookup"><span data-stu-id="b8b42-110">Properties</span></span>

|  <span data-ttu-id="b8b42-111">속성</span><span class="sxs-lookup"><span data-stu-id="b8b42-111">Property</span></span>  |  <span data-ttu-id="b8b42-112">설명</span><span class="sxs-lookup"><span data-stu-id="b8b42-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="b8b42-113">이름</span><span class="sxs-lookup"><span data-stu-id="b8b42-113">Name</span></span>| <span data-ttu-id="b8b42-114">시스템에서 등록하거나 등록 취소할 패키지 원본의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="b8b42-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="b8b42-115">ProviderName</span></span>| <span data-ttu-id="b8b42-116">패키지 원본과 상호 운용할 수 있는 OneGet 공급자의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="b8b42-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="b8b42-117">SourceLocation</span></span>| <span data-ttu-id="b8b42-118">패키지 원본의 URI를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="b8b42-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="b8b42-119">Ensure</span></span>| <span data-ttu-id="b8b42-120">패키지 원본을 등록할지 또는 등록 취소할지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="b8b42-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="b8b42-121">InstallationPolicy</span></span>| <span data-ttu-id="b8b42-122">기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="b8b42-123">패키지 원본을 신뢰할 수 있는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="b8b42-124">"Untrusted"와 "Trusted" 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="b8b42-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="b8b42-125">SourceCredential</span></span>| <span data-ttu-id="b8b42-126">원격 소스에 있는 패키지에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="b8b42-127">예제</span><span class="sxs-lookup"><span data-stu-id="b8b42-127">Example</span></span>

<span data-ttu-id="b8b42-128">이 예제에서는 **PackageManagementSource** DSC 리소스를 사용하여 http://nuget.org 패키지 원본을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b42-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```