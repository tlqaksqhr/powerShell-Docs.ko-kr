---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell 필요한 상태 구성 시작
ms.openlocfilehash: a449382c979e680ea311c887c86cb675ba6162b7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="71e76-103">PowerShell 필요한 상태 구성 시작</span><span class="sxs-lookup"><span data-stu-id="71e76-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="71e76-104">이 가이드에서는 PowerShell 필요한 상태 구성 문서 작성을 시작하고 문서를 컴퓨터에 적용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="71e76-105">PowerShell cmdlet, 모듈 및 함수에 대한 기본 지식이 있는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span>


## <a name="create-a-configuration"></a><span data-ttu-id="71e76-106">구성 만들기</span><span class="sxs-lookup"><span data-stu-id="71e76-106">Create a Configuration</span></span> ##

<span data-ttu-id="71e76-107">[**구성**](https://msdn.microsoft.com/powershell/dsc/configurations)은 환경을 설명하는 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="71e76-108">환경은 일반적으로 가상 컴퓨터나 물리적 컴퓨터인 "**노드**"로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span>

<span data-ttu-id="71e76-109">구성은 다양한 형태를 도입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="71e76-110">새 구성을 만드는 가장 쉬운 방법은 .ps1(PowerShell 스크립트) 파일을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="71e76-111">이렇게 하려면 원하는 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="71e76-112">PowerShell ISE는 DSC를 기본적으로 이해하므로 좋은 선택입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="71e76-113">다음을 PS1로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="71e76-114">구성의 부분</span><span class="sxs-lookup"><span data-stu-id="71e76-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="71e76-115">**구성**은 PowerShell 4.0에 추가된 키워드로서,</span><span class="sxs-lookup"><span data-stu-id="71e76-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="71e76-116">필요한 상태 구성에서 사용하는 특별한 종류의 PowerShell 함수를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="71e76-117">이 예제에서 함수는 myFirstConfiguration이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-117">In this example, the function is named myFirstConfiguration.</span></span>

<span data-ttu-id="71e76-118">다음 줄은 모듈을 가져오는 것과 비슷한 import 문입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="71e76-119">이에 대해서는 나중에 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-119">It will be discussed later on.</span></span>

<span data-ttu-id="71e76-120">"Node"는 이 구성이 작업을 수행하는 컴퓨터 이름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="71e76-121">이 구성을 로컬로 편집하더라도, 구성이 원격 노드에 도달하여 원격 노드를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span>

<span data-ttu-id="71e76-122">노드는 컴퓨터 이름이나 IP 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="71e76-123">단일 구성 문서에 여러 노드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="71e76-124">[구성 데이터](https://msdn.microsoft.com/powershell/dsc/configdata)를 사용하면 동일한 구성을 여러 노드에 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="71e76-125">이 경우에 노드는 로컬 컴퓨터라는 의미의 "localhost"입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-125">In this case, the node is "localhost" - which means the local computer.</span></span>

<span data-ttu-id="71e76-126">다음 항목은 한 [**리소스**](https://msdn.microsoft.com/powershell/dsc/resources)입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="71e76-127">리소스는 구성의 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="71e76-128">각 리소스는 컴퓨터의 한 측면에 대한 구현 논리를 정의하는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="71e76-129">PowerShell에서 **Get-DscResource**를 실행하여 컴퓨터에서 모든 리소스를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="71e76-130">리소스가 로컬 컴퓨터에 있어야 하며 리소스를 이 구성의 두 번째 줄에 있는 **Import-DscResource**가 있는 구성에서 사용하려면 먼저 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span>

<span data-ttu-id="71e76-131">**구성 시행**</span><span class="sxs-lookup"><span data-stu-id="71e76-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="71e76-132">위의 스크립트가 저장되어 있고 실행되는 경우, 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="71e76-133">이것은 구성이 단순히 함수이고 위의 스크립트가 함수를 정의하기만 하고 함수를 실행하지는 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="71e76-134">함수를 정의했으면 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="71e76-135">구성 함수는 실행되면 구성이 유효한지 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="71e76-136">실행하려면 먼저 구문 오류가 없어야 하고 리소스에 모든 필수 매개 변수가 정의되어 있어야 하며, 모든 리소스를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="71e76-137">구성이 실행되면 구성에 있는 모든 노드에 대해 **.MOF 파일**을 포함하는 구성의 이름으로 폴더가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="71e76-138">.MOF 파일은 네트워크를 통해 통신하는 PowerShell DSC에 의해 사용되는 표준 기반 관리 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="71e76-139">구성 시행:</span><span class="sxs-lookup"><span data-stu-id="71e76-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="71e76-140">이 스크립트는 구성에 있는 노드에 도달하여 구성 작업을 수행하는 PowerShell 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="71e76-141">작업의 출력을 보려면 -Wait를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="71e76-141">To see the output of the job, use -Wait.</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```