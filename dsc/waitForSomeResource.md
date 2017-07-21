---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC WaitForSome 리소스"
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="1e3fe-103">DSC WaitForSome 리소스</span><span class="sxs-lookup"><span data-stu-id="1e3fe-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="1e3fe-104">적용 대상: Windows PowerShell 5.0 이상</span><span class="sxs-lookup"><span data-stu-id="1e3fe-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="1e3fe-105">**WaitForAny** DSC(Desired State Configuration) 리소스를 [DSC 구성](configurations.md)의 노드 블록 내에서 사용하면 다른 노드의 구성에 대한 종속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="1e3fe-106">**ResourceName** 속성으로 지정된 리소스가 **NodeName** 속성으로 정의된 최소 노드 수(**NodeCount**를 통해 지정함)에서 필요한 상태이면 이 리소스가 정상적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="1e3fe-107">구문</span><span class="sxs-lookup"><span data-stu-id="1e3fe-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="1e3fe-108">속성</span><span class="sxs-lookup"><span data-stu-id="1e3fe-108">Properties</span></span>

|  <span data-ttu-id="1e3fe-109">속성</span><span class="sxs-lookup"><span data-stu-id="1e3fe-109">Property</span></span>  |  <span data-ttu-id="1e3fe-110">설명</span><span class="sxs-lookup"><span data-stu-id="1e3fe-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="1e3fe-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="1e3fe-111">ResourceName</span></span>| <span data-ttu-id="1e3fe-112">사용할 리소스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="1e3fe-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="1e3fe-113">NodeName</span></span>| <span data-ttu-id="1e3fe-114">사용할 리소스의 대상 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="1e3fe-115">NodeCount</span><span class="sxs-lookup"><span data-stu-id="1e3fe-115">NodeCount</span></span>| <span data-ttu-id="1e3fe-116">이 리소스를 정상적으로 적용하려면 필요한 상태여야 하는 최소 노드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-116">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="1e3fe-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="1e3fe-117">RetryIntervalSec</span></span>| <span data-ttu-id="1e3fe-118">다시 시도할 때까지의 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-118">The number of seconds before retrying.</span></span> <span data-ttu-id="1e3fe-119">최소값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="1e3fe-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="1e3fe-120">RetryCount</span></span>| <span data-ttu-id="1e3fe-121">최대 다시 시도 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="1e3fe-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1e3fe-122">ThrottleLimit</span></span>| <span data-ttu-id="1e3fe-123">동시에 연결하는 컴퓨터의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="1e3fe-124">기본값은 new-cimsession 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="1e3fe-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1e3fe-125">DependsOn</span></span> | <span data-ttu-id="1e3fe-126">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1e3fe-127">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="1e3fe-128">예제</span><span class="sxs-lookup"><span data-stu-id="1e3fe-128">Example</span></span>

<span data-ttu-id="1e3fe-129">이 리소스를 사용하는 방법의 예제를 보려면 [노드 간 종속성 지정](crossNodeDependencies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-129">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

