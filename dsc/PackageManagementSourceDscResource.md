---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC PackageManagementSource 리소스"
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="bc427-103">DSC PackageManagementSource 리소스</span><span class="sxs-lookup"><span data-stu-id="bc427-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="bc427-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bc427-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bc427-105">Windows PowerShell DSC(필요한 상태 구성)의 **PackageManagementSource** 리소스는 대상 노드에서 패키지 관리 원본을 등록하거나 등록 취소하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="bc427-106">**이 방법으로 등록된 패키지 관리 원본은 시스템 계정이나 DSC 엔진에서 사용할 수 있는 시스템 컨텍스트에서 등록됩니다.**</span><span class="sxs-lookup"><span data-stu-id="bc427-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="bc427-107">이 리소스를 사용하려면 http://PowerShellGallery.com에서 제공하는 **PackageManagement** 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc427-108">구문</span><span class="sxs-lookup"><span data-stu-id="bc427-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="bc427-109">속성</span><span class="sxs-lookup"><span data-stu-id="bc427-109">Properties</span></span>
|  <span data-ttu-id="bc427-110">속성</span><span class="sxs-lookup"><span data-stu-id="bc427-110">Property</span></span>  |  <span data-ttu-id="bc427-111">설명</span><span class="sxs-lookup"><span data-stu-id="bc427-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="bc427-112">이름</span><span class="sxs-lookup"><span data-stu-id="bc427-112">Name</span></span>| <span data-ttu-id="bc427-113">시스템에서 등록하거나 등록 취소할 패키지 원본의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>| 
| <span data-ttu-id="bc427-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="bc427-114">Ensure</span></span>| <span data-ttu-id="bc427-115">패키지 원본을 등록할지 또는 등록 취소할지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-115">Determines whether the package source is to be registered or unregistered.</span></span>| 
| <span data-ttu-id="bc427-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="bc427-116">InstallationPolicy</span></span>| <span data-ttu-id="bc427-117">패키지 원본을 신뢰할 수 있는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="bc427-118">"Untrusted"와 "Trusted" 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-118">One of: "Untrusted", "Trusted".</span></span>| 
| <span data-ttu-id="bc427-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="bc427-119">ProviderName</span></span>| <span data-ttu-id="bc427-120">패키지 원본과 상호 운용할 수 있는 OneGet 공급자의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>| 
| <span data-ttu-id="bc427-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="bc427-121">SourceUri</span></span>| <span data-ttu-id="bc427-122">패키지 원본의 URI를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-122">Specifies the URI of the package source.</span></span>| 
| <span data-ttu-id="bc427-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="bc427-123">SourceCredential</span></span>| <span data-ttu-id="bc427-124">원격 소스에 있는 패키지에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-124">Provides access to the package on a remote source.</span></span>| 

## <a name="example"></a><span data-ttu-id="bc427-125">예제</span><span class="sxs-lookup"><span data-stu-id="bc427-125">Example</span></span>

<span data-ttu-id="bc427-126">이 예제에서는 **PackageManagementSource** DSC 리소스를 사용하여 http://nuget.org 패키지 원본을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="bc427-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

