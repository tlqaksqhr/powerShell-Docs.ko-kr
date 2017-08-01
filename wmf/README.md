---
title: WMF(Windows Management Framework)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="windows-management-framework"></a><span data-ttu-id="576cd-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="576cd-103">Windows Management Framework</span></span>

<span data-ttu-id="576cd-104">WMF(Windows Management Framework)는 다양한 Windows 및 Windows Server에서 일관된 관리 인터페이스를 제공하는 배달 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="576cd-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="576cd-105">WMF를 설치하면 고객은 환경에 함께 설치한 여러 OS를 원활히 상호 운용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="576cd-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="576cd-106">WMF는 지정된 릴리스의 Windows 및 Windows Server에 있는 관리 기능에 대한 업데이트를 Windows 및 Windows Server의 하위 버전(일반적으로 2개의 하위 버전)에서 설치할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="576cd-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="576cd-107">WMF 설치는 다음 기능을 추가 및/또는 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="576cd-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="576cd-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="576cd-108">Windows PowerShell</span></span>
- <span data-ttu-id="576cd-109">Windows PowerShell DSC(원하는 상태 구성)</span><span class="sxs-lookup"><span data-stu-id="576cd-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="576cd-110">Windows PowerShell ISE(통합 스크립트 환경)</span><span class="sxs-lookup"><span data-stu-id="576cd-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="576cd-111">WinRM(Windows Remote Management)</span><span class="sxs-lookup"><span data-stu-id="576cd-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="576cd-112">WMI(Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="576cd-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="576cd-113">Windows PowerShell 웹 서비스(관리 OData IIS 확장)</span><span class="sxs-lookup"><span data-stu-id="576cd-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="576cd-114">소프트웨어 인벤토리 로깅(SIL)</span><span class="sxs-lookup"><span data-stu-id="576cd-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="576cd-115">서버 관리자 CIM 공급자</span><span class="sxs-lookup"><span data-stu-id="576cd-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="576cd-116">WMF 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="576cd-116">WMF Release Notes</span></span>
<span data-ttu-id="576cd-117">PowerShell 및 지정된 WMF의 다른 구성 요소에서 향상된 다양한 기능에 대해 알아보려면 아래 링크에서 릴리스 정보를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="576cd-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>


- [<span data-ttu-id="576cd-118">WMF 5.1(Preview)</span><span class="sxs-lookup"><span data-stu-id="576cd-118">WMF 5.1 (Preview)</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="576cd-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="576cd-119">WMF 5.0</span></span>](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="576cd-120">Windows 운영 체제에서의 WMF 가용성</span><span class="sxs-lookup"><span data-stu-id="576cd-120">WMF Availability Across Windows Operating Systems</span></span>

><span data-ttu-id="576cd-121">TODO: 열 머리글에 특정 WMF DLC에 대한 링크 추가</span><span class="sxs-lookup"><span data-stu-id="576cd-121">TODO: Add links to specific WMF DLC on the column header</span></span>

| <span data-ttu-id="576cd-122">운영 체제 버전</span><span class="sxs-lookup"><span data-stu-id="576cd-122">Operating System Version</span></span> | [<span data-ttu-id="576cd-123">WMF 5.1 Preview*</span><span class="sxs-lookup"><span data-stu-id="576cd-123">WMF 5.1 Preview*</span></span>]() | [<span data-ttu-id="576cd-124">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="576cd-124">WMF 5.0</span></span>]() | [<span data-ttu-id="576cd-125">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="576cd-125">WMF 4.0</span></span>]() |  [<span data-ttu-id="576cd-126">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="576cd-126">WMF 3.0</span></span>]() | [<span data-ttu-id="576cd-127">WMF 2.0</span><span class="sxs-lookup"><span data-stu-id="576cd-127">WMF (2.0)</span></span>]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="576cd-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="576cd-128">Windows Server 2016</span></span> | <span data-ttu-id="576cd-129">함께 제공*</span><span class="sxs-lookup"><span data-stu-id="576cd-129">Ships in-box*</span></span> | <span data-ttu-id="576cd-130">함께 제공*</span><span class="sxs-lookup"><span data-stu-id="576cd-130">Ships in-box*</span></span> |  |  |  |
| <span data-ttu-id="576cd-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="576cd-131">Windows 10</span></span> | <span data-ttu-id="576cd-132">함께 제공*</span><span class="sxs-lookup"><span data-stu-id="576cd-132">Ships in-box*</span></span> | <span data-ttu-id="576cd-133">함께 제공*</span><span class="sxs-lookup"><span data-stu-id="576cd-133">Ships in-box*</span></span>  | | | |  
| <span data-ttu-id="576cd-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="576cd-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="576cd-135">??</span><span class="sxs-lookup"><span data-stu-id="576cd-135">??</span></span> | <span data-ttu-id="576cd-136">예</span><span class="sxs-lookup"><span data-stu-id="576cd-136">Yes</span></span> | <span data-ttu-id="576cd-137">함께 제공</span><span class="sxs-lookup"><span data-stu-id="576cd-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="576cd-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="576cd-138">Windows 8.1</span></span> | <span data-ttu-id="576cd-139">??</span><span class="sxs-lookup"><span data-stu-id="576cd-139">??</span></span> | <span data-ttu-id="576cd-140">예</span><span class="sxs-lookup"><span data-stu-id="576cd-140">Yes</span></span> |  <span data-ttu-id="576cd-141">함께 제공</span><span class="sxs-lookup"><span data-stu-id="576cd-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="576cd-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="576cd-142">Windows Server 2012</span></span> | <span data-ttu-id="576cd-143">??</span><span class="sxs-lookup"><span data-stu-id="576cd-143">??</span></span> | <span data-ttu-id="576cd-144">예</span><span class="sxs-lookup"><span data-stu-id="576cd-144">Yes</span></span> | <span data-ttu-id="576cd-145">예</span><span class="sxs-lookup"><span data-stu-id="576cd-145">Yes</span></span> |  <span data-ttu-id="576cd-146">함께 제공</span><span class="sxs-lookup"><span data-stu-id="576cd-146">Ships in-box</span></span> | |
| <span data-ttu-id="576cd-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="576cd-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="576cd-148">함께 제공</span><span class="sxs-lookup"><span data-stu-id="576cd-148">Ships in-box</span></span> | |
| <span data-ttu-id="576cd-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="576cd-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="576cd-150">??</span><span class="sxs-lookup"><span data-stu-id="576cd-150">??</span></span> | <span data-ttu-id="576cd-151">예</span><span class="sxs-lookup"><span data-stu-id="576cd-151">Yes</span></span> | <span data-ttu-id="576cd-152">예</span><span class="sxs-lookup"><span data-stu-id="576cd-152">Yes</span></span> |  <span data-ttu-id="576cd-153">예</span><span class="sxs-lookup"><span data-stu-id="576cd-153">Yes</span></span>| <span data-ttu-id="576cd-154">함께 제공</span><span class="sxs-lookup"><span data-stu-id="576cd-154">Ships in-box</span></span> |
| <span data-ttu-id="576cd-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="576cd-155">Windows 7 SP1</span></span>  | <span data-ttu-id="576cd-156">??</span><span class="sxs-lookup"><span data-stu-id="576cd-156">??</span></span> | <span data-ttu-id="576cd-157">예</span><span class="sxs-lookup"><span data-stu-id="576cd-157">Yes</span></span> | <span data-ttu-id="576cd-158">예</span><span class="sxs-lookup"><span data-stu-id="576cd-158">Yes</span></span> | <span data-ttu-id="576cd-159">예</span><span class="sxs-lookup"><span data-stu-id="576cd-159">Yes</span></span> | <span data-ttu-id="576cd-160">함께 제공</span><span class="sxs-lookup"><span data-stu-id="576cd-160">Ships in-box</span></span> |
| <span data-ttu-id="576cd-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="576cd-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="576cd-162">예</span><span class="sxs-lookup"><span data-stu-id="576cd-162">Yes</span></span> | <span data-ttu-id="576cd-163">예</span><span class="sxs-lookup"><span data-stu-id="576cd-163">Yes</span></span> |
| <span data-ttu-id="576cd-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="576cd-164">Windows Vista</span></span> | | | | | <span data-ttu-id="576cd-165">예</span><span class="sxs-lookup"><span data-stu-id="576cd-165">Yes</span></span> |
| <span data-ttu-id="576cd-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="576cd-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="576cd-167">예</span><span class="sxs-lookup"><span data-stu-id="576cd-167">Yes</span></span> |
| <span data-ttu-id="576cd-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="576cd-168">Windows XP</span></span> | | | |  | <span data-ttu-id="576cd-169">예</span><span class="sxs-lookup"><span data-stu-id="576cd-169">Yes</span></span> |

><span data-ttu-id="576cd-170">TODO: 위의 표에서 * 설명</span><span class="sxs-lookup"><span data-stu-id="576cd-170">TODO: Explain * in the above table</span></span>
