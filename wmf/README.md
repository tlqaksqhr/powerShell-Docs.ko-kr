---
title: WMF(Windows Management Framework)
ms.date: 2017-02-14
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 749dd8b19592cb5f40a5aed32d28edeb5cb2dfc9
ms.sourcegitcommit: bb2c52577a519c0599a0b3c961f749fe0df70a45
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="windows-management-framework"></a><span data-ttu-id="1efc5-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="1efc5-103">Windows Management Framework</span></span>

<span data-ttu-id="1efc5-104">WMF(Windows Management Framework)는 다양한 Windows 및 Windows Server에서 일관된 관리 인터페이스를 제공하는 배달 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="1efc5-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="1efc5-105">WMF를 설치하면 고객은 환경에 함께 설치한 여러 OS를 원활히 상호 운용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc5-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="1efc5-106">WMF는 지정된 릴리스의 Windows 및 Windows Server에 있는 관리 기능에 대한 업데이트를 Windows 및 Windows Server의 하위 버전(일반적으로 2개의 하위 버전)에서 설치할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efc5-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="1efc5-107">WMF 설치는 다음 기능을 추가 및/또는 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1efc5-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="1efc5-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1efc5-108">Windows PowerShell</span></span>
- <span data-ttu-id="1efc5-109">Windows PowerShell DSC(원하는 상태 구성)</span><span class="sxs-lookup"><span data-stu-id="1efc5-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="1efc5-110">Windows PowerShell ISE(통합 스크립트 환경)</span><span class="sxs-lookup"><span data-stu-id="1efc5-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="1efc5-111">WinRM(Windows Remote Management)</span><span class="sxs-lookup"><span data-stu-id="1efc5-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="1efc5-112">WMI(Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="1efc5-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="1efc5-113">Windows PowerShell 웹 서비스(관리 OData IIS 확장)</span><span class="sxs-lookup"><span data-stu-id="1efc5-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="1efc5-114">소프트웨어 인벤토리 로깅(SIL)</span><span class="sxs-lookup"><span data-stu-id="1efc5-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="1efc5-115">서버 관리자 CIM 공급자</span><span class="sxs-lookup"><span data-stu-id="1efc5-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="1efc5-116">WMF 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="1efc5-116">WMF Release Notes</span></span>

<span data-ttu-id="1efc5-117">PowerShell 및 지정된 WMF의 다른 구성 요소에서 향상된 다양한 기능에 대해 알아보려면 아래 링크에서 릴리스 정보를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1efc5-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>

- [<span data-ttu-id="1efc5-118">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="1efc5-118">WMF 5.1</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="1efc5-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="1efc5-119">WMF 5.0</span></span>](5.0/releasenotes.md)
- [<span data-ttu-id="1efc5-120">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="1efc5-120">WMF 4.0</span></span>](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [<span data-ttu-id="1efc5-121">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="1efc5-121">WMF 3.0</span></span>](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="1efc5-122">Windows 운영 체제에서의 WMF 가용성</span><span class="sxs-lookup"><span data-stu-id="1efc5-122">WMF Availability Across Windows Operating Systems</span></span>

| <span data-ttu-id="1efc5-123">운영 체제 버전</span><span class="sxs-lookup"><span data-stu-id="1efc5-123">Operating System Version</span></span> | [<span data-ttu-id="1efc5-124">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="1efc5-124">WMF 5.1</span></span>](https://aka.ms/wmf51download) | [<span data-ttu-id="1efc5-125">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="1efc5-125">WMF 5.0</span></span>](https://aka.ms/wmf5download) | [<span data-ttu-id="1efc5-126">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="1efc5-126">WMF 4.0</span></span>](https://aka.ms/wmf4download) |  [<span data-ttu-id="1efc5-127">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="1efc5-127">WMF 3.0</span></span>](https://aka.ms/wmf3download) | [<span data-ttu-id="1efc5-128">WMF 2.0</span><span class="sxs-lookup"><span data-stu-id="1efc5-128">WMF 2.0</span></span>](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="1efc5-129">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="1efc5-129">Windows Server 2016</span></span> | <span data-ttu-id="1efc5-130">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-130">Ships in-box</span></span> |  |  |  |  |
| <span data-ttu-id="1efc5-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1efc5-131">Windows 10</span></span> | <span data-ttu-id="1efc5-132">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-132">Ships in-box</span></span> | <span data-ttu-id="1efc5-133">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-133">Ships in-box</span></span>  | | | |  
| <span data-ttu-id="1efc5-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="1efc5-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="1efc5-135">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-135">Yes</span></span> | <span data-ttu-id="1efc5-136">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-136">Yes</span></span> | <span data-ttu-id="1efc5-137">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="1efc5-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="1efc5-138">Windows 8.1</span></span> | <span data-ttu-id="1efc5-139">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-139">Yes</span></span> | <span data-ttu-id="1efc5-140">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-140">Yes</span></span> |  <span data-ttu-id="1efc5-141">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="1efc5-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="1efc5-142">Windows Server 2012</span></span> | <span data-ttu-id="1efc5-143">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-143">Yes</span></span> | <span data-ttu-id="1efc5-144">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-144">Yes</span></span> | <span data-ttu-id="1efc5-145">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-145">Yes</span></span> |  <span data-ttu-id="1efc5-146">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-146">Ships in-box</span></span> | |
| <span data-ttu-id="1efc5-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="1efc5-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="1efc5-148">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-148">Ships in-box</span></span> | |
| <span data-ttu-id="1efc5-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="1efc5-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="1efc5-150">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-150">Yes</span></span> | <span data-ttu-id="1efc5-151">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-151">Yes</span></span> | <span data-ttu-id="1efc5-152">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-152">Yes</span></span> |  <span data-ttu-id="1efc5-153">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-153">Yes</span></span>| <span data-ttu-id="1efc5-154">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-154">Ships in-box</span></span> |
| <span data-ttu-id="1efc5-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="1efc5-155">Windows 7 SP1</span></span>  | <span data-ttu-id="1efc5-156">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-156">Yes</span></span> | <span data-ttu-id="1efc5-157">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-157">Yes</span></span> | <span data-ttu-id="1efc5-158">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-158">Yes</span></span> | <span data-ttu-id="1efc5-159">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-159">Yes</span></span> | <span data-ttu-id="1efc5-160">함께 제공</span><span class="sxs-lookup"><span data-stu-id="1efc5-160">Ships in-box</span></span> |
| <span data-ttu-id="1efc5-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="1efc5-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="1efc5-162">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-162">Yes</span></span> | <span data-ttu-id="1efc5-163">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-163">Yes</span></span> |
| <span data-ttu-id="1efc5-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="1efc5-164">Windows Vista</span></span> | | | | | <span data-ttu-id="1efc5-165">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-165">Yes</span></span> |
| <span data-ttu-id="1efc5-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="1efc5-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="1efc5-167">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-167">Yes</span></span> |
| <span data-ttu-id="1efc5-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="1efc5-168">Windows XP</span></span> | | | |  | <span data-ttu-id="1efc5-169">예</span><span class="sxs-lookup"><span data-stu-id="1efc5-169">Yes</span></span> |

<span data-ttu-id="1efc5-170">**"함께 제공"**: `specified WMF` 기능은 표시된 버전의 Windows 및 Windows Server에 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc5-170">**"Ships in-box"**: The features of the `specified WMF` were shipped in the indicated version of  Windows and Windows Server.</span></span>
<span data-ttu-id="1efc5-171">따라서 표시된 운영 체제 버전에는 `specified WMF`를 설치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1efc5-171">Hence, the `specified WMF` doesn't need to be installed on the indicated operating system versions.</span></span>
