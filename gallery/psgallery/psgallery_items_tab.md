---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 8704091542de5c19817ab0b4f77fd98987084b5d
ms.sourcegitcommit: 1a0a0928c1e3cae4e8df8d79b0737bd7ed6b4e47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="items-tab"></a><span data-ttu-id="9841d-103">항목 탭</span><span class="sxs-lookup"><span data-stu-id="9841d-103">Items Tab</span></span>

<span data-ttu-id="9841d-104">[항목 탭](https://www.powershellgallery.com/items)에는 PowerShell 갤러리에서 사용 가능한 모든 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="9841d-105">항목을 필터링, 정렬 및 검색하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="9841d-106">특정 항목에 대한 자세한 정보를 보려면 해당 항목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="9841d-107">필터 기준</span><span class="sxs-lookup"><span data-stu-id="9841d-107">Filter By</span></span>

<span data-ttu-id="9841d-108">“필터 기준” 아래의 드롭다운에서는 다음을 기준으로 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="9841d-109">시험판 포함</span><span class="sxs-lookup"><span data-stu-id="9841d-109">Include Prerelease</span></span>
* <span data-ttu-id="9841d-110">안정적인 항목만</span><span class="sxs-lookup"><span data-stu-id="9841d-110">Stable Only</span></span>

<span data-ttu-id="9841d-111">“시험판” 및 “안정적인 항목”에 대한 내용은 PowerShell 팀 블로그의 [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/)(PowerShellGet 및 PowerShell 갤러리에 추가된 시험판 버전)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9841d-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="9841d-112">드롭다운의 확인란을 사용하여 다음을 기준으로 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="9841d-113">항목 종류</span><span class="sxs-lookup"><span data-stu-id="9841d-113">Item Types</span></span>
  - <span data-ttu-id="9841d-114">모듈</span><span class="sxs-lookup"><span data-stu-id="9841d-114">Module</span></span>
  - <span data-ttu-id="9841d-115">스크립트</span><span class="sxs-lookup"><span data-stu-id="9841d-115">Script</span></span>
* <span data-ttu-id="9841d-116">범주</span><span class="sxs-lookup"><span data-stu-id="9841d-116">Categories</span></span>
  - <span data-ttu-id="9841d-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9841d-117">Cmdlet</span></span>
  - <span data-ttu-id="9841d-118">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="9841d-118">DSC Resource</span></span>
  - <span data-ttu-id="9841d-119">기능</span><span class="sxs-lookup"><span data-stu-id="9841d-119">Function</span></span>
  - <span data-ttu-id="9841d-120">역할 기능</span><span class="sxs-lookup"><span data-stu-id="9841d-120">Role Capability</span></span>
  - <span data-ttu-id="9841d-121">Workflow</span><span class="sxs-lookup"><span data-stu-id="9841d-121">Workflow</span></span>

<span data-ttu-id="9841d-122">PowerShell 갤러리의 모듈만 보려면 [항목 종류]에서 [모듈]을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="9841d-123">마찬가지로 PowerShell 갤러리에서 스크립트만 보려면 [항목 종류]에서 [스크립트]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="9841d-124">필터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-124">Filters are inclusive.</span></span>
> <span data-ttu-id="9841d-125">예: cmdlet과 함수를 둘 다 포함하는 항목은 [Cmdlet] 또는 [함수](또는 둘 다)를 선택한 경우에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="9841d-126">둘 다 선택하지 않으면 항목이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="9841d-127">마찬가지로, 모든 범주를 선택하면 이러한 범주 중 하나를 포함하는 항목만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="9841d-128">**이러한 범주에 속하지 않는 항목은 표시되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="9841d-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="9841d-129">정렬 기준</span><span class="sxs-lookup"><span data-stu-id="9841d-129">Sort By</span></span>

<span data-ttu-id="9841d-130">[정렬 기준] 드롭다운에서 다음을 기준으로 결과를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="9841d-131">인기도 - 인기도는 다운로드 횟수에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="9841d-132">A-Z - 항목 이름을 기준으로 사전순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="9841d-133">최근 - 게시 날짜순으로 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="9841d-134">검색 상자</span><span class="sxs-lookup"><span data-stu-id="9841d-134">Search Box</span></span>

<span data-ttu-id="9841d-135">검색 상자에서 키워드로 항목을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9841d-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="9841d-136">자세한 내용은 [갤러리 검색 구문](psgallery_search_syntax.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9841d-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>
