---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: 의사 결정자를 위한 필요한 상태 구성 개요
ms.openlocfilehash: 8b410420ef30b066a32864a0d08a12a8485eaa4b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="8d5b4-103">의사 결정자를 위한 필요한 상태 구성 개요</span><span class="sxs-lookup"><span data-stu-id="8d5b4-103">Desired State Configuration Overview for Decision Makers</span></span>

<span data-ttu-id="8d5b4-104">이 문서에서는 PowerShell DSC(필요한 상태 구성) 사용의 비즈니스 혜택에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-104">This document describes the business benefits of using PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="8d5b4-105">기술 가이드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-105">It is not a technical guide.</span></span>

## <a name="what-is-desired-state-configuration"></a><span data-ttu-id="8d5b4-106">필요한 상태 구성이란?</span><span class="sxs-lookup"><span data-stu-id="8d5b4-106">What Is Desired State Configuration?</span></span>

<span data-ttu-id="8d5b4-107">Windows PowerShell DSC(필요한 상태 구성)는 개방형 표준에 따라 Windows에 기본 제공되는 구성 관리 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-107">Windows PowerShell Desired State Configuration (DSC) is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="8d5b4-108">DSC는 확장 중은 물론, 배포 수명 주기의 각 단계(개발, 테스트, 사전 프로덕션, 프로덕션)에서 안정적이고 일관되게 작동할 수 있을 만큼 유연합니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-108">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), as well as during scale-out.</span></span>

<span data-ttu-id="8d5b4-109">DSC의 중심은 "[구성](https://msdn.microsoft.com/powershell/dsc/configurations)"입니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-109">DSC centers around "[configurations](https://msdn.microsoft.com/powershell/dsc/configurations)".</span></span>
<span data-ttu-id="8d5b4-110">구성은 특정한 특징을 가진 컴퓨터("노드")로 구성된 환경을 읽기 쉽게 설명한 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-110">A configuration is an easy-to-read document that describes an environment made up of computers ("nodes") with specific characteristics.</span></span>
<span data-ttu-id="8d5b4-111">이 특성은 특정 Windows 기능을 사용할 수 있도록 할 만큼 간단하거나 SharePoint를 배포할 만큼 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-111">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="8d5b4-112">DSC에서는 모니터링 및 보고 기능도 기본적으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-112">DSC also has monitoring and reporting built in.</span></span>
<span data-ttu-id="8d5b4-113">시스템이 더 이상 호환하지 않는 경우 DSC에서는 경고를 발생시키고 시스템을 수정하는 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-113">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-desired-state-configuration"></a><span data-ttu-id="8d5b4-114">필요한 상태 구성을 사용할 때의 이점</span><span class="sxs-lookup"><span data-stu-id="8d5b4-114">Benefits of Using Desired State Configuration</span></span>

<span data-ttu-id="8d5b4-115">구성은 쉽게 읽고 저장하고 업데이트하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-115">Configurations are designed to be easily read, stored, and updated.</span></span>
<span data-ttu-id="8d5b4-116">구성에서는 대상 장치를 해당 상태에 배치하는 방법에 대한 지침을 작성하는 대신 대상 장치가 있어야 하는 상태를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-116">Configurations declare the state target devices should be in, instead of writing instructions for how to put them in that state.</span></span>
<span data-ttu-id="8d5b4-117">따라서 DSC를 통해 구성에 대해 배우고, 구성을 채택하고, 구현하고 유지 관리하는 데에 훨씬 적은 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-117">This makes it much less costly to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="8d5b4-118">구성을 만드는 것은 복잡한 배포 단계를 단일 위치에서 "단일 데이터 소스(single source of truth)"로 캡처함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-118">Creating configurations means that complex deployment steps are captured as a "single source of truth" in a single location.</span></span>
<span data-ttu-id="8d5b4-119">이렇게 하면 특정 컴퓨터 집합의 반복된 배포의 오류 발생률이 훨씬 낮아지고,</span><span class="sxs-lookup"><span data-stu-id="8d5b4-119">This makes repeated deployments of a specific set of machines much less error-prone.</span></span>
<span data-ttu-id="8d5b4-120">결국 더 빠르고 안정적으로 배포할 수 있어 복잡한 배포의 소요 시간이 짧아집니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-120">In turn, making deployments faster and more reliable which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="8d5b4-121">[PowerShell 갤러리](https://powershellgallery.com)를 통해 구성을 공유할 수도 있습니다. 즉 완료해야 할 작업에 대한 일반적인 시나리오 및 모범 사례가 이미 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-121">Configurations are also shareable via the [PowerShell Gallery](https://powershellgallery.com) meaning common scenarios and best practices might already exist for the work you need done.</span></span>


## <a name="desired-state-configuration-and-devops"></a><span data-ttu-id="8d5b4-122">필요한 상태 구성 및 DevOps</span><span class="sxs-lookup"><span data-stu-id="8d5b4-122">Desired State Configuration and DevOps</span></span>

<span data-ttu-id="8d5b4-123">[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)는 내부 사용자든 외부 사용자든 최종 사용자에게 가치를 제공하는 데 중점을 둔 빠른 배포와 반복이 가능한 사용자, 프로세스 및 도구의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-123">[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) is a combination of people, process, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span>
<span data-ttu-id="8d5b4-124">DSC는 DevOps를 염두에 두고 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-124">DSC was designed with DevOps in mind.</span></span>
<span data-ttu-id="8d5b4-125">단일 구성으로 환경을 정의하면 개발자가 요구 사항을 구성으로 인코드하고, 해당 구성을 소스 제어에 체크 인할 수 있고, 운영 팀은 오류가 발생하기 쉬운 수동 프로세스를 거치지 않고 쉽게 코드를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-125">Having a single configuration define an environment means that developers can encode their requirements into a configuration, check that configuration into source control, and operations teams can easily deploy code without having to go through error-prone manual processes.</span></span>

<span data-ttu-id="8d5b4-126">구성은 [데이터 기반](https://msdn.microsoft.com/powershell/dsc/configdata)이기도 해서 운영 팀이 개발자의 개입 없이 환경을 식별하고 변경기 더 쉽도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-126">Configurations are also [data-driven](https://msdn.microsoft.com/powershell/dsc/configdata), which makes it easier for ops teams to identify and change environments without developer intervention.</span></span>

## <a name="desired-state-configuration-on--and-off-premises"></a><span data-ttu-id="8d5b4-127">Desired State Configuration 온-프레미스 및 오프-프레미스</span><span class="sxs-lookup"><span data-stu-id="8d5b4-127">Desired State Configuration On- and Off-Premises</span></span>

<span data-ttu-id="8d5b4-128">DSC를 사용하여 온-프레미스 배포와 오프-프레미스 배포를 모두 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-128">DSC can be used to manage both on-premises and off-premises deployments.</span></span>
<span data-ttu-id="8d5b4-129">온-프레미스 솔루션의 경우 DSC에는 컴퓨터를 중앙 집중식으로 관리하고 컴퓨터 상태를 보고하는 데 사용할 수 있는 [끌어오기 서버](https://msdn.microsoft.com/powershell/dsc/pullserver)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-129">For on-premises solutions, DSC has a [pull server](https://msdn.microsoft.com/powershell/dsc/pullserver) that can be used to centralize management of machines and report on their status.</span></span>
<span data-ttu-id="8d5b4-130">클라우드 솔루션의 경우 DSC는 Windows를 사용할 수 있는 곳이라면 어디서든 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-130">For cloud solutions, DSC is usable wherever Windows is usable.</span></span>
<span data-ttu-id="8d5b4-131">DSC의 보고를 중앙에 집중하는 [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/)와 같은 필요한 상태 구성을 기반으로 하는 Azure의 특정 제공 기능도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-131">There are also specific offerings from Azure built on Desired State Configuration, such as [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), which centralizes reporting of DSC.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="8d5b4-132">DSC 및 호환성</span><span class="sxs-lookup"><span data-stu-id="8d5b4-132">DSC and Compatibility</span></span>

<span data-ttu-id="8d5b4-133">DSC는 Windows Server 2012 R2에서 도입되었지만 WMF(Windows Management Framework) 패키지를 통해 이전 운영 체제에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-133">Although DSC was introduced in Windows Server 2012 R2, it is available for downlevel operating systems via the Windows Management Framework (WMF) package.</span></span>
<span data-ttu-id="8d5b4-134">WMF에 대한 자세한 정보는 [PowerShell homepage(PowerShell 홈페이지)](https://msdn.microsoft.com/en-us/powershell/)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-134">More information about the WMF can be found on the [PowerShell homepage](https://msdn.microsoft.com/en-us/powershell/).</span></span>

<span data-ttu-id="8d5b4-135">DSC는 Linux를 관리하는 데에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-135">DSC can also be used to manage Linux.</span></span> <span data-ttu-id="8d5b4-136">자세한 내용은 [Linux용 DSC 시작](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d5b4-136">For more information, see [Getting Started with DSC for Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).</span></span>