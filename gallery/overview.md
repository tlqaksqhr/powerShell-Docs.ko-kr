---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery,psget,갤러리
title: PowerShell 갤러리
ms.openlocfilehash: cffb2f0182ffe9072f9fbbc7f4cdfcf28de276db
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="1e062-103">PowerShell 갤러리</span><span class="sxs-lookup"><span data-stu-id="1e062-103">The PowerShell Gallery</span></span>

<span data-ttu-id="1e062-104">PowerShell 갤러리는 PowerShell 콘텐츠에 대한 중앙 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="1e062-105">PowerShell 갤러리에서 PowerShell 명령 및 DSC(필요한 상태 구성) 리소스가 포함된 유용한 PowerShell 모듈을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="1e062-106">PowerShell 워크플로가 포함된 경우도 있으며 일련의 작업을 간략하게 설명하고 해당 작업 순서를 제공하는 PowerShell 스크립트를 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="1e062-107">이러한 항목 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="1e062-108">PowerShellGet 개요</span><span class="sxs-lookup"><span data-stu-id="1e062-108">PowerShellGet Overview</span></span>

<span data-ttu-id="1e062-109">PowerShellGet 모듈에는 [PowerShell 갤러리](https://www.PowerShellGallery.com) 및 다른 개인 리포지토리에서 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 PowerShell 아티팩트를 검색, 설치, 업데이트 및 게시하기 위한 cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="1e062-110">갤러리 시작</span><span class="sxs-lookup"><span data-stu-id="1e062-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="1e062-111">갤러리에서 항목을 설치하려면 최신 버전의 PowerShellGet 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="1e062-112">자세한 지침은 [PowerShellGet](installing-psget.md) 설치를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e062-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="1e062-113">갤러리와 함께 PowerShellGet 명령을 사용하는 방법에 대한 자세한 내용은 [시작](getting-started.md) 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e062-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="1e062-114">*Update-Help -Module PowerShellGet*을 실행하여 이러한 명령에 대한 로컬 도움말을 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="1e062-115">지원되는 운영 체제</span><span class="sxs-lookup"><span data-stu-id="1e062-115">Supported Operating Systems</span></span>

<span data-ttu-id="1e062-116">**PowerShellGet** 모듈을 사용하려면 **PowerShell 3.0 이상**이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="1e062-117">따라서 **PowerShellGet**에는 다음 운영 체제 중 하나가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="1e062-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1e062-118">Windows 10</span></span>
- <span data-ttu-id="1e062-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="1e062-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="1e062-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="1e062-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="1e062-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="1e062-121">Windows 7 SP1</span></span>
- <span data-ttu-id="1e062-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="1e062-122">Windows Server 2016</span></span>
- <span data-ttu-id="1e062-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="1e062-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="1e062-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="1e062-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="1e062-125">**PowerShellGet**을 사용하려면 .NET Framework 4.5 이상도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="1e062-126">.NET Framework 4.5 이상은 [여기](https://msdn.microsoft.com/library/5a4x27ek.aspx)에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="1e062-127">궁금한 점이 있나요?</span><span class="sxs-lookup"><span data-stu-id="1e062-127">Got a question?</span></span> <span data-ttu-id="1e062-128">피드백이 있습니까?</span><span class="sxs-lookup"><span data-stu-id="1e062-128">Have feedback?</span></span>

<span data-ttu-id="1e062-129">PowerShell 갤러리 및 PowerShellGet에 대한 자세한 내용은 [시작](getting-started.md) 페이지에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e062-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="1e062-130">[UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell)를 사용하여 피드백을 제공하고 문제를 신고하세요.</span><span class="sxs-lookup"><span data-stu-id="1e062-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>