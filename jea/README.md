---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "추가 정보"
ms.technology: powershell
ms.openlocfilehash: b0ef4ff685b82e1a4e9ab83a45736720df7b39a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="just-enough-administration"></a><span data-ttu-id="ed3b2-103">JEA(Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="ed3b2-103">Just Enough Administration</span></span>
<span data-ttu-id="ed3b2-104">JEA(Just Enough Administration)는 PowerShell로 관리할 수 있는 모든 것에 대한 위임된 관리를 가능하게 하는 보안 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="ed3b2-105">JEA를 사용하면 다음이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-105">With JEA, you can:</span></span>
- <span data-ttu-id="ed3b2-106">**컴퓨터의 관리자 수 감소**: 일반 사용자를 대신하여 권한 있는 작업을 수행하는 가상 계정을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="ed3b2-107">**사용자가 수행할 수 있는 작업 제한**: 사용자가 실행할 수 있는 cmdlet, 함수 및 외부 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="ed3b2-108">**사용자가 수행하고 있는 작업을 보다 효과적으로 이해**: 사용자가 세션 중에 실행한 명령을 정확하게 보여 주는 "Over-the-Shoulder" 기록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-108">**Better understand what your users are doing** with "over the shoulder" transcriptions that show you exactly what commands a user executed during a session.</span></span>

<span data-ttu-id="ed3b2-109">**JEA가 중요한 이유는 무엇일까요?**</span><span class="sxs-lookup"><span data-stu-id="ed3b2-109">**Why is this important?**</span></span>  
<span data-ttu-id="ed3b2-110">DNS 서버가 Active Directory 도메인 컨트롤러와 함께 있는 일반적인 시나리오를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-110">Consider the common scenario where your DNS servers are co-located with your Active Directory Domain Controllers.</span></span>
<span data-ttu-id="ed3b2-111">DNS 관리자는 DNS 서버의 문제를 해결하기 위해 로컬 관리자 권한이 있어야 하지만 이를 위해서는 권한 수준이 높은 "Domain Admins" 보안 그룹의 구성원으로 DNS 관리자를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-111">Your DNS administrators need to have local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="ed3b2-112">이 접근 방식을 통해 DNS 관리자는 효과적으로 전체 도메인을 제어하고 해당 컴퓨터의 모든 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-112">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="ed3b2-113">JEA가 설정된 경우 작업을 수행하기 위해 필요한 모든 명령에 대한 액세스 권한만 제공하는 역할을 DNS 관리자에 대해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-113">With JEA in place, you can configure a role for your DNS administrators that gives them access to all the commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="ed3b2-114">즉, 손상된 DNS 캐시를 복구하는 데 적합한 액세스 권한만 제공하여 Active Directory에 액세스하거나 파일 시스템을 검색하거나 잠재적으로 위험한 스크립트를 실행할 수 있는 권한을 실수로 제공하는 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-114">This means you can provide the appropriate access to repair a poisoned DNS cache without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="ed3b2-115">JEA 세션이 일회성 권한 있는 가상 계정을 사용하도록 구성된 경우 DNS 관리자는 *권한 없는* 자격 증명을 사용하여 서버에 연결하고 권한 있는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-115">Better yet, when the JEA session is configured to use one-time privileged virtual accounts, your DNS administrators can connect to the server using *unprivileged* credentials and still be able to run privileged commands.</span></span>

## <a name="availability"></a><span data-ttu-id="ed3b2-116">가용성</span><span class="sxs-lookup"><span data-stu-id="ed3b2-116">Availability</span></span>
<span data-ttu-id="ed3b2-117">JEA는 Windows Server 2016과 함께 개발되고 있으며 Windows Management Framework 업데이트를 통해 이전 버전의 Windows에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-117">JEA is being developed in parallel to Windows Server 2016, and is available on older versions of Windows through Windows Management Framework updates.</span></span>
<span data-ttu-id="ed3b2-118">JEA의 현재 릴리스는 다음과 같은 플랫폼에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-118">The current release of JEA is available on the following platforms:</span></span>

<span data-ttu-id="ed3b2-119">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="ed3b2-119">**Windows Server**</span></span>
- <span data-ttu-id="ed3b2-120">Windows Server 2016 Technical Preview 4 이상</span><span class="sxs-lookup"><span data-stu-id="ed3b2-120">Windows Server 2016 Technical Preview 4 and higher</span></span>
- <span data-ttu-id="ed3b2-121">[Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)이 설치된 Windows Server 2012 R2, 2012 및 2008 R2\*</span><span class="sxs-lookup"><span data-stu-id="ed3b2-121">Windows Server 2012 R2, 2012, and 2008 R2\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="ed3b2-122">**Windows 클라이언트**</span><span class="sxs-lookup"><span data-stu-id="ed3b2-122">**Windows Client**</span></span>
- <span data-ttu-id="ed3b2-123">11월 업데이트(1511)가 설치된 Windows 10</span><span class="sxs-lookup"><span data-stu-id="ed3b2-123">Windows 10 with the November Update (1511) installed</span></span>
- <span data-ttu-id="ed3b2-124">[Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)이 설치된 Windows 8.1, 8 및 7\*</span><span class="sxs-lookup"><span data-stu-id="ed3b2-124">Windows 8.1, 8, and 7\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="ed3b2-125">\* JEA 세션의 가상 계정에 대한 지원은 Windows Server 2008 R2 또는 Windows 7에서 현재 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-125">\* Support for virtual accounts in JEA sessions is currently not available on Windows Server 2008 R2 or Windows 7.</span></span>


## <a name="explore-the-experience-guide"></a><span data-ttu-id="ed3b2-126">환경 탐색 가이드</span><span class="sxs-lookup"><span data-stu-id="ed3b2-126">Explore the experience guide</span></span>
<span data-ttu-id="ed3b2-127">사용자 고유의 JEA 끝점을 제작하고, 배포하고, 사용하는 방법을 알아볼 준비가 되었나요?</span><span class="sxs-lookup"><span data-stu-id="ed3b2-127">Ready to learn how to author, deploy, and use your own JEA endpoint?</span></span>

<span data-ttu-id="ed3b2-128">이 가이드에서는 미리 만들어진 JEA 끝점으로 신속하게 시작하여 최종 사용자가 어떻게 경험하는지를 파악하게 하고 끝점을 처음부터 다시 제작하는 과정을 안내하여 세션 구성 및 역할 기능과 같은 개념을 보여 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-128">This guide gets you started quickly with a pre-built JEA endpoint to get an idea of what the end-user experience is like, then walks you through recreating an endpoint from scratch to help demonstrate concepts like session configurations and Role Capabilities.</span></span>

1.  <span data-ttu-id="ed3b2-129">[소개](introduction.md) </span><span class="sxs-lookup"><span data-stu-id="ed3b2-129">[Introduction](introduction.md) </span></span>  
<span data-ttu-id="ed3b2-130">JEA에 대해 관심을 가져야 하는 이유 간단히 검토</span><span class="sxs-lookup"><span data-stu-id="ed3b2-130">Briefly review why you should care about JEA</span></span>

2.  [<span data-ttu-id="ed3b2-131">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ed3b2-131">Prerequisites</span></span>](prerequisites.md)  
<span data-ttu-id="ed3b2-132">환결 설정 방법 설명</span><span class="sxs-lookup"><span data-stu-id="ed3b2-132">Explains how to set up your environment</span></span>

3.  [<span data-ttu-id="ed3b2-133">JEA 사용</span><span class="sxs-lookup"><span data-stu-id="ed3b2-133">Using JEA</span></span>](using-jea.md)  
<span data-ttu-id="ed3b2-134">운영자의 JEA 사용 경험을 이해하는 것에서 시작하도록 지원</span><span class="sxs-lookup"><span data-stu-id="ed3b2-134">Helps you start by understanding the operator experience of using JEA</span></span>

4.  [<span data-ttu-id="ed3b2-135">데모 다시 만들기</span><span class="sxs-lookup"><span data-stu-id="ed3b2-135">Remake the Demo</span></span>](remake-the-demo-endpoint.md)  
<span data-ttu-id="ed3b2-136">처음부터 JEA 세션 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="ed3b2-136">Create a JEA Session Configuration from scratch</span></span>

5.  [<span data-ttu-id="ed3b2-137">역할 기능</span><span class="sxs-lookup"><span data-stu-id="ed3b2-137">Role Capabilities</span></span>](role-capabilities.md)  
<span data-ttu-id="ed3b2-138">역할 기능 파일을 사용하여 JEA 기능을 사용자 지정하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="ed3b2-138">Learn about how to customize JEA capabilities with Role Capability Files</span></span>

6.  [<span data-ttu-id="ed3b2-139">종단 간 - Active Directory</span><span class="sxs-lookup"><span data-stu-id="ed3b2-139">End to End - Active Directory</span></span>](end-to-end---active-directory.md)  
<span data-ttu-id="ed3b2-140">Active Directory를 관리하기 위한 완전히 새로운 끝점 만들기</span><span class="sxs-lookup"><span data-stu-id="ed3b2-140">Make a whole new endpoint for managing Active Directory</span></span>

7.  [<span data-ttu-id="ed3b2-141">다중 컴퓨터 배포 및 유지 관리</span><span class="sxs-lookup"><span data-stu-id="ed3b2-141">Multi-machine Deployment and Maintenance</span></span>](multi-machine-deployment-and-maintenance.md)  
<span data-ttu-id="ed3b2-142">확장에 따라 배포와 작성이 변경되는 방식 알아보기</span><span class="sxs-lookup"><span data-stu-id="ed3b2-142">Discover how deployment and authoring changes with scale</span></span>

8.  [<span data-ttu-id="ed3b2-143">JEA에 대한 보고</span><span class="sxs-lookup"><span data-stu-id="ed3b2-143">Reporting on JEA</span></span>](reporting-on-jea.md)  
<span data-ttu-id="ed3b2-144">모든 JEA 작업 및 인프라에 대한 감사 및 보고 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="ed3b2-144">Discover how to audit and report on all JEA actions and infrastructure</span></span>

9.  <span data-ttu-id="ed3b2-145">부록</span><span class="sxs-lookup"><span data-stu-id="ed3b2-145">Appendixes</span></span>
  - [<span data-ttu-id="ed3b2-146">이 가이드 전체에서 사용된 주요 개념</span><span class="sxs-lookup"><span data-stu-id="ed3b2-146">Key Concepts Used Throughout This Guide</span></span>](key-concepts-used-throughout-this-guide.md)  
  -  [<span data-ttu-id="ed3b2-147">도메인 컨트롤러 만들기</span><span class="sxs-lookup"><span data-stu-id="ed3b2-147">Creating a Domain Controller</span></span>](creating-a-domain-controller.md)  
  -  [<span data-ttu-id="ed3b2-148">블랙리스트에 올리기</span><span class="sxs-lookup"><span data-stu-id="ed3b2-148">On Blacklisting</span></span>](on-blacklisting.md)  
  -  [<span data-ttu-id="ed3b2-149">명령을 제한하는 경우의 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ed3b2-149">Considerations When Limiting Commands</span></span>](considerations-when-limiting-commands.md)  
  -  [<span data-ttu-id="ed3b2-150">일반적인 역할 기능 문제</span><span class="sxs-lookup"><span data-stu-id="ed3b2-150">Common Role Capability Pitfalls</span></span>](common-role-capability-pitfalls.md)

## <a name="start-authoring-your-own-jea-endpoints"></a><span data-ttu-id="ed3b2-151">사용자 고유의 JEA 끝점 제작 시작</span><span class="sxs-lookup"><span data-stu-id="ed3b2-151">Start authoring your own JEA endpoints</span></span>
<span data-ttu-id="ed3b2-152">JEA 끝점을 제작하는 것은 쉽습니다. JEA 사용 시스템과 텍스트 편집기(예: PowerShell ISE)만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-152">It's easy to author a JEA endpoint -- all you need is a JEA-enabled system and a text editor (like PowerShell ISE).</span></span>
<span data-ttu-id="ed3b2-153">시작하기 위한 한 가지 유용한 팁은 다른 인수 없이 [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) 및 [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx)를 사용하여 기본 파일을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-153">One helpful tip to get started is to create skeleton files using [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) and [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) without any other arguments.</span></span>
<span data-ttu-id="ed3b2-154">이러한 기본 파일에는 적용 가능한 모든 구성 필드와 함께 각 필드의 용도에 대해 설명하는 유용한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-154">These skeleton files contain all of the applicable configuration fields along with helpful comments to explain what each field can be used for.</span></span>

<span data-ttu-id="ed3b2-155">JEA 끝점을 훨씬 쉽게 제작하려면 세션 구성 및 역할 기능 파일을 제작할 수 있는 GUI를 제공하는 [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-155">To make authoring JEA endpoints even easier, check out the [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) which provides a GUI with which you can author Session Configuration and Role Capability files.</span></span>
<span data-ttu-id="ed3b2-156">이 도구는 사용자가 작업을 수행하기 위해 일반적으로 실행하는 명령으로 시작할 수 있도록 PowerShell 로그를 기반으로 역할 기능을 생성하는 것까지 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ed3b2-156">It even supports generating Role Capabilities based on PowerShell logs to start you off with the commands your users regularly run to get their jobs done.</span></span>

