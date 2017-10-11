---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "gallery,powershell,cmdlet,psgallery,psget,갤러리"
title: "PowerShell 갤러리"
ms.openlocfilehash: 83a1f4e20b985a502637aee9d50ecc1d3f9a4616
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2017
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="bb5f6-103">PowerShell 갤러리</span><span class="sxs-lookup"><span data-stu-id="bb5f6-103">The PowerShell Gallery</span></span>

<span data-ttu-id="bb5f6-104">PowerShell 갤러리는 PowerShell 콘텐츠에 대한 중앙 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="bb5f6-105">갤러리에서 새로운 PowerShell 명령 또는 DSC(필요한 상태 구성) 리소스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="bb5f6-106">PowerShellGet 개요</span><span class="sxs-lookup"><span data-stu-id="bb5f6-106">PowerShellGet Overview</span></span>

<span data-ttu-id="bb5f6-107">PowerShellGet 모듈에는 https://www.PowerShellGallery.com 및 다른 개인 리포지토리에서 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 PowerShell 아티팩트를 검색, 설치, 업데이트 및 게시하기 위한 cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-107">PowerShellGet module contains cmdlets for discovering, installing, updating and publishing the PowerShell artifacts like Modules, DSC Resources, Role Capabilities and Scripts from the https://www.PowerShellGallery.com and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="bb5f6-108">갤러리 시작</span><span class="sxs-lookup"><span data-stu-id="bb5f6-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="bb5f6-109">갤러리에서 항목을 설치하려면 Windows 10, WMF(Windows Management Framework) 5.0 또는 MSI 기반 설치 관리자(PowerShell 3 및 4용)에서 사용할 수 있는 최신 버전의 PowerShellGet 모듈이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="bb5f6-110">[**Windows 10 다운로드**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="bb5f6-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="bb5f6-111">[**WMF 5.0 다운로드**](http://go.microsoft.com/fwlink/?LinkId=398175)</span><span class="sxs-lookup"><span data-stu-id="bb5f6-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="bb5f6-112">**MSI 설치 관리자 다운로드**</span><span class="sxs-lookup"><span data-stu-id="bb5f6-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="bb5f6-113">최신 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 모듈을 사용할 경우 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="bb5f6-114">[Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 및 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)를 사용하여 갤러리에서 항목 검색</span><span class="sxs-lookup"><span data-stu-id="bb5f6-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="bb5f6-115">[Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) 및 [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)를 사용하여 갤러리의 항목을 시스템에 저장</span><span class="sxs-lookup"><span data-stu-id="bb5f6-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="bb5f6-116">[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 및 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)를 사용하여 갤러리에서 항목 설치</span><span class="sxs-lookup"><span data-stu-id="bb5f6-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="bb5f6-117">[Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) 및 [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)를 사용하여 갤러리에 항목 업로드</span><span class="sxs-lookup"><span data-stu-id="bb5f6-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="bb5f6-118">[Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)를 사용하여 사용자 지정 리포지토리 추가</span><span class="sxs-lookup"><span data-stu-id="bb5f6-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="bb5f6-119">갤러리와 함께 PowerShellGet 명령을 사용하는 방법에 대한 자세한 내용은 [시작](psgallery/psgallery_gettingstarted.md) 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="bb5f6-120">*Update-Help -Module PowerShellGet*을 실행하여 이러한 명령에 대한 로컬 도움말을 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="bb5f6-121">지원되는 운영 체제</span><span class="sxs-lookup"><span data-stu-id="bb5f6-121">Supported Operating Systems</span></span>

<span data-ttu-id="bb5f6-122">**PowerShellGet** 모듈을 사용하려면 **PowerShell 3.0 이상**이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="bb5f6-123">따라서 **PowerShellGet**에는 다음 운영 체제 중 하나가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="bb5f6-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="bb5f6-124">Windows 10</span></span>
- <span data-ttu-id="bb5f6-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="bb5f6-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="bb5f6-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="bb5f6-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="bb5f6-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="bb5f6-127">Windows 7 SP1</span></span>
- <span data-ttu-id="bb5f6-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="bb5f6-128">Windows Server 2016</span></span>
- <span data-ttu-id="bb5f6-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="bb5f6-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="bb5f6-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="bb5f6-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="bb5f6-131">**PowerShellGet**을 사용하려면 .NET Framework 4.5 이상도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="bb5f6-132">.NET Framework 4.5 이상은 [여기](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="bb5f6-133">궁금한 점이 있나요?</span><span class="sxs-lookup"><span data-stu-id="bb5f6-133">Got a question?</span></span> <span data-ttu-id="bb5f6-134">피드백이 있습니까?</span><span class="sxs-lookup"><span data-stu-id="bb5f6-134">Have feedback?</span></span>

<span data-ttu-id="bb5f6-135">PowerShell 갤러리 및 PowerShellGet에 대한 자세한 내용은 [시작](psgallery/psgallery_gettingstarted.md) 페이지에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="bb5f6-136">[UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell)를 사용하여 피드백을 제공하고 문제를 신고하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5f6-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

