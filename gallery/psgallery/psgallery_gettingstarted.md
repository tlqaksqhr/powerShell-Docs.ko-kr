---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: 2117712b0081db4a21f8480b458a499ed84dc512
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2018
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="7d4b1-103">PowerShell 갤러리 시작</span><span class="sxs-lookup"><span data-stu-id="7d4b1-103">Get Started with the PowerShell Gallery</span></span>

## <a name="what-is-the-powershell-gallery"></a><span data-ttu-id="7d4b1-104">PowerShell 갤러리란?</span><span class="sxs-lookup"><span data-stu-id="7d4b1-104">What is the PowerShell Gallery?</span></span>

<span data-ttu-id="7d4b1-105">PowerShell 갤러리는 PowerShell 콘텐츠에 대한 중앙 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-105">The PowerShell Gallery is the central repository for PowerShell content.</span></span>
<span data-ttu-id="7d4b1-106">PowerShell 갤러리에서 PowerShell 명령 및 DSC(필요한 상태 구성) 리소스가 포함된 유용한 PowerShell 모듈을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-106">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span> <span data-ttu-id="7d4b1-107">PowerShell 워크플로가 포함된 경우도 있으며 일련의 작업을 간략하게 설명하고 해당 작업 순서를 제공하는 PowerShell 스크립트를 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-107">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span>
<span data-ttu-id="7d4b1-108">이러한 항목 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-108">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="requirements"></a><span data-ttu-id="7d4b1-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7d4b1-109">Requirements</span></span>

<span data-ttu-id="7d4b1-110">PowerShell 갤러리에서 시스템으로 항목을 다운로드하려면 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-110">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module.</span></span> <span data-ttu-id="7d4b1-111">다음 중 하나에서 PowerShellGet 모듈을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-111">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="7d4b1-112">PowerShell 갤러리에서 항목을 다운로드하기 위해 로그인할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-112">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

-   [<span data-ttu-id="7d4b1-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="7d4b1-113">Windows 10</span></span>](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [<span data-ttu-id="7d4b1-114">Windows Management Framework 5.0</span><span class="sxs-lookup"><span data-stu-id="7d4b1-114">Windows Management Framework 5.0</span></span>](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [<span data-ttu-id="7d4b1-115">MSI 설치 관리자(PowerShell 3 및 4용)</span><span class="sxs-lookup"><span data-stu-id="7d4b1-115">MSI Installer (for PowerShell 3 and 4)</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="7d4b1-116">PowerShellGet이 PowerShell 갤러리를 사용하려면 [NuGet 공급자](http://go.microsoft.com/fwlink/?LinkId=722208)도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-116">PowerShellGet also requires the [NuGet provider](http://go.microsoft.com/fwlink/?LinkId=722208) to work with the PowerShell Gallery.</span></span> <span data-ttu-id="7d4b1-117">NuGet 공급자가 다음 위치 중 하나에 없을 경우 PowerShellGet을 처음 사용할 때 NuGet 공급자를 자동으로 설치하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-117">You will be prompted to install the NuGet provider automatically upon first use of PowerShellGet if the NuGet provider is not in one of the following locations:</span></span>

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

<span data-ttu-id="7d4b1-118">또는 `Install-PackageProvider -Name NuGet -Force`를 실행하여 NuGet 공급자의 다운로드 및 설치를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-118">Or, you can run `Install-PackageProvider -Name NuGet -Force` to automate the download and installation of the NuGet provider.</span></span>

  
<span data-ttu-id="7d4b1-119">2.8.5.201 이전 버전의 NuGet이 있는 경우 다음 PowerShell cmdlet을 호출하여 최신 버전의 NuGet을 설치하고 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-119">If you have a version older than 2.8.5.201 of NuGet, you will need to call the following PowerShell cmdlets to install and switch to the latest version of NuGet.</span></span>

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  <span data-ttu-id="7d4b1-120">위의 설치 위치에서 이전 버전의 NuGet을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-120">Delete the older version of NuGet from the above installed location.</span></span>

<span data-ttu-id="7d4b1-121">자세한 내용은 <http://oneget.org/>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-121">For more information, see <http://oneget.org/> .</span></span>

  
<span data-ttu-id="7d4b1-122">참고: 패키지 형식이 변경되었으므로 최신 버전의 PowerShellGet 및 PackageManagement로 업데이트하여 최근에 업데이트된 항목을 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-122">Note: Due to changes in packaging formats, we recommend you update to the latest version of PowerShellGet and PackageManagement to install items that have been updated recently.</span></span> <span data-ttu-id="7d4b1-123">PowerShellGet은 Windows 10에 포함되어 있습니다. 자세한 내용은 [여기](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-123">PowerShellGet is included in Windows 10, which you can learn more about [here](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).</span></span>
<span data-ttu-id="7d4b1-124">PowerShellGet은 [여기](http://go.microsoft.com/fwlink/?LinkId=398175)서 다운로드할 수 있는 WMF(Windows Management Framework) 5.0의 일부이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-124">PowerShellGet is also part of the Windows Management Framework (WMF) 5.0, which you can download [here](http://go.microsoft.com/fwlink/?LinkId=398175).</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="7d4b1-125">PowerShell 갤러리에서 항목 검색</span><span class="sxs-lookup"><span data-stu-id="7d4b1-125">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="7d4b1-126">이 웹 사이트에서 **검색** 컨트롤을 사용하거나 모듈 및 스크립트 페이지를 검색하여 PowerShell 갤러리에서 항목을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-126">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="7d4b1-127">항목 유형에 따라 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 및 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) cmdlet을 `-Repository PSGallery`와 함께 사용하여 PowerShell 갤러리에서 항목을 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-127">You can also find items from the PowerShell Gallery by running the [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="7d4b1-128">[Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 및 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)의 다음 매개 변수를 사용하여 갤러리의 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-128">Filtering results from the Gallery can be done by using the following parameters of [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>

- <span data-ttu-id="7d4b1-129">이름</span><span class="sxs-lookup"><span data-stu-id="7d4b1-129">Name</span></span>
- <span data-ttu-id="7d4b1-130">AllVersions</span><span class="sxs-lookup"><span data-stu-id="7d4b1-130">AllVersions</span></span>
- <span data-ttu-id="7d4b1-131">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="7d4b1-131">MinimumVersion</span></span>
- <span data-ttu-id="7d4b1-132">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="7d4b1-132">RequiredVersion</span></span>
- <span data-ttu-id="7d4b1-133">태그</span><span class="sxs-lookup"><span data-stu-id="7d4b1-133">Tag</span></span>
- <span data-ttu-id="7d4b1-134">Includes</span><span class="sxs-lookup"><span data-stu-id="7d4b1-134">Includes</span></span>
- <span data-ttu-id="7d4b1-135">DscResource</span><span class="sxs-lookup"><span data-stu-id="7d4b1-135">DscResource</span></span>
- <span data-ttu-id="7d4b1-136">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="7d4b1-136">RoleCapability</span></span>
- <span data-ttu-id="7d4b1-137">명령</span><span class="sxs-lookup"><span data-stu-id="7d4b1-137">Command</span></span>
- <span data-ttu-id="7d4b1-138">필터</span><span class="sxs-lookup"><span data-stu-id="7d4b1-138">Filter</span></span>

<span data-ttu-id="7d4b1-139">갤러리에서 특정 DSC 리소스를 검색하는 데만 관심이 있는 경우 [Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) cmdlet을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-139">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) cmdlet.</span></span>
<span data-ttu-id="7d4b1-140">[Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196)는 갤러리에 포함된 DSC 리소스에 대한 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-140">[Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) returns data on DSC resources contained in the Gallery.</span></span> <span data-ttu-id="7d4b1-141">DSC 리소스는 항상 모듈의 일부로 제공되기 때문에 여전히 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663)을 실행하여 이러한 DSC 리소스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-141">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="7d4b1-142">PowerShell 갤러리에 있는 항목에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="7d4b1-142">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="7d4b1-143">관심 있는 항목을 식별했으면 자세히 알아보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-143">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="7d4b1-144">이렇게 하려면 갤러리에서 해당 항목의 특정 페이지를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-144">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="7d4b1-145">이 페이지에서 항목과 함께 업로드된 메타데이터를 모두 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-145">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="7d4b1-146">항목에 대한 이 메타데이터는 항목의 작성자가 제공하며 Microsoft에서 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-146">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="7d4b1-147">항목의 소유자는 항목을 게시하는 데 사용되는 갤러리 계정에 강하게 연결되어 있으며 작성자 필드보다 더 신뢰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-147">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="7d4b1-148">좋은 의도에서 게시되지 않은 것 같은 항목을 발견할 경우 해당 항목의 페이지에서 **신고하기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-148">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="7d4b1-149">[Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 또는 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)를 실행하는 경우 반환된 PSGetModuleInfo 개체에서 이 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-149">If you're running [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) or [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322), you can view this data in the returned PSGetModuleInfo object.</span></span>
<span data-ttu-id="7d4b1-150">예를 들어 `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member`를 실행하면 갤러리의 PSReadLine 모듈에 대한 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-150">For example, running `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="7d4b1-151">PowerShell 갤러리에서 항목 다운로드</span><span class="sxs-lookup"><span data-stu-id="7d4b1-151">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="7d4b1-152">PowerShell 갤러리에서 항목을 다운로드하는 경우 다음 프로세스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-152">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="7d4b1-153">검사</span><span class="sxs-lookup"><span data-stu-id="7d4b1-153">Inspect</span></span>

<span data-ttu-id="7d4b1-154">검사를 위해 갤러리에서 항목을 다운로드하려면 항목 유형에 따라 [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) 또는 [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-154">To download an item from the Gallery for inspection, run either the [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) or [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) cmdlet, depending on the item type.</span></span> <span data-ttu-id="7d4b1-155">이렇게 하면 설치하지 않고 로컬에 항목을 저장한 다음 항목 내용을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-155">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="7d4b1-156">저장된 항목을 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-156">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="7d4b1-157">이러한 항목 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-157">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span> <span data-ttu-id="7d4b1-158">설치 전에 이 갤러리에 있는 항목의 내용과 코드를 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-158">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="7d4b1-159">좋은 의도에서 게시되지 않은 것 같은 항목을 발견할 경우 해당 항목의 페이지에서 **신고하기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-159">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="7d4b1-160">설치</span><span class="sxs-lookup"><span data-stu-id="7d4b1-160">Install</span></span>

<span data-ttu-id="7d4b1-161">사용을 위해 갤러리에서 항목을 설치하려면 항목 유형에 따라 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 또는 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-161">To install an item from the Gallery for use, run either the [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) or [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) cmdlet, depending on the item type.</span></span>

<span data-ttu-id="7d4b1-162">[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663)은 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Modules`에 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-162">[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span> <span data-ttu-id="7d4b1-163">이 경우 관리자 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-163">This requires an administrator account.</span></span> <span data-ttu-id="7d4b1-164">`-Scope
CurrentUser` 매개 변수를 추가하는 경우 모듈은 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-164">If you add the `-Scope
CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="7d4b1-165">[Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)는 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Scripts`에 스크립트를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-165">[Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span> <span data-ttu-id="7d4b1-166">이 경우 관리자 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-166">This requires an administrator account.</span></span> <span data-ttu-id="7d4b1-167">`-Scope
CurrentUser` 매개 변수를 추가하는 경우 스크립트는 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-167">If you add the `-Scope
CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="7d4b1-168">기본적으로 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 및 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)는 최신 버전의 항목을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-168">By default, [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installs the most current version of an item.</span></span> <span data-ttu-id="7d4b1-169">이전 버전의 항목을 설치하려면 `-RequiredVersion` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-169">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="7d4b1-170">배포 게스트 클러스터에</span><span class="sxs-lookup"><span data-stu-id="7d4b1-170">Deploy</span></span>

<span data-ttu-id="7d4b1-171">PowerShell 갤러리의 항목을 Azure Automation에 배포하려면 항목 세부 정보 페이지에서 **Azure Automation에 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-171">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="7d4b1-172">Azure 관리 포털로 리디렉션되며, 여기서 Azure 계정 자격 증명을 사용하여 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-172">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="7d4b1-173">종속성과 함께 항목을 배포하면 모든 종속성이 Azure Automation에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-173">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="7d4b1-174">항목 메타데이터에 **AzureAutomationNotSupported** 태그를 추가하면 'Azure Automation에 배포' 단추를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-174">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="7d4b1-175">Azure Automation에 대한 자세한 내용은 [Azure Automation 웹 사이트](http://azure.microsoft.com/services/automation/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-175">To learn more about Azure Automation, see the [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="7d4b1-176">PowerShell 갤러리에서 항목 업데이트</span><span class="sxs-lookup"><span data-stu-id="7d4b1-176">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="7d4b1-177">PowerShell 갤러리에서 설치된 항목을 업데이트하려면 [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) 또는 [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-177">To update items installed from the PowerShell Gallery, run either the [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) or [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) cmdlet.</span></span> <span data-ttu-id="7d4b1-178">추가 매개 변수 없이 실행하면 [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576)이 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663)을 실행하여 설치된 각 모듈을 업데이트하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-178">When run without any additional parameters, [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) attempts to update each module installed by running [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663).</span></span>
<span data-ttu-id="7d4b1-179">모듈을 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-179">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="7d4b1-180">마찬가지로, 추가 매개 변수 없이 실행하면 [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787)는 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)를 실행하여 설치된 각 스크립트를 업데이트하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-180">Similarly, when run without any additional parameters, [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) also attempts to update each script installed by running [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327).</span></span>
<span data-ttu-id="7d4b1-181">스크립트를 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-181">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="7d4b1-182">PowerShell 갤러리에서 설치한 항목 나열</span><span class="sxs-lookup"><span data-stu-id="7d4b1-182">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="7d4b1-183">PowerShell 갤러리에서 설치한 모듈을 찾으려면 [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-183">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) cmdlet.</span></span> <span data-ttu-id="7d4b1-184">이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 모듈을 모두 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-184">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="7d4b1-185">마찬가지로, PowerShell 갤러리에서 설치한 스크립트를 찾으려면 [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-185">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) cmdlet.</span></span> <span data-ttu-id="7d4b1-186">이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 스크립트를 모두 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-186">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

