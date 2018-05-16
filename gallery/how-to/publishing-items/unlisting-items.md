---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: 목록에서 항목 제거
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="95e77-103">목록에서 항목 제거</span><span class="sxs-lookup"><span data-stu-id="95e77-103">Unlisting items</span></span>

<span data-ttu-id="95e77-104">**옵션으로 노출되지 않는 항목을 PowerShell 갤러리에서 제거해야 하는 것은 무엇 때문일까요?**</span><span class="sxs-lookup"><span data-stu-id="95e77-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="95e77-105">PowerShell 갤러리에서는 사용자가 항목을 영구적으로 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="95e77-106">따라서 다른 사용자가 이후의 가능한 손상에 대해 염려하지 않고 항목을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="95e77-107">예를 들어 Pester 모듈이 Azure 모듈을 사용하는데 Azure 모듈이 갤러리에서 제거되면 사용자가 Pester 모듈을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="95e77-108">그러나 항목을 제거하는 대신 목록에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="95e77-109">**PowerShell 갤러리의 목록에서 항목을 제거하면 어떻게 될까요?**</span><span class="sxs-lookup"><span data-stu-id="95e77-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="95e77-110">PowerShell 갤러리의 목록에서 모듈 또는 스크립트와 같은 항목을 제거하면 항목 탭에서 제거됩니다. 또한 목록에 없는 항목은 검색 표시줄을 사용하여 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="95e77-111">목록에 없는 항목을 다운로드하려면 항목의 정확한 이름 및 버전을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="95e77-112">이 때문에 목록에서 항목을 제거하는 경우 해당 항목을 사용하는 다른 모듈이나 스크립트가 손상되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="95e77-113">목록에서 항목을 제거하려면 항목 세부 정보 페이지로 이동한 다음 '항목 삭제'를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="95e77-114">'목록에 표시' 확인란의 선택을 취소하고 저장을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="95e77-115">**항목을 제거하려면 어떻게 하나요?**</span><span class="sxs-lookup"><span data-stu-id="95e77-115">**How can I remove an item?**</span></span>

<span data-ttu-id="95e77-116">항목을 삭제해야 하는 시나리오가 발생하면 PowerShell 갤러리 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="95e77-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="95e77-117">유효한 삭제 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="95e77-118">저작권 침해 문제</span><span class="sxs-lookup"><span data-stu-id="95e77-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="95e77-119">항목에 잠재적으로 유해한 콘텐츠가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="95e77-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="95e77-120">항목에 중요한 데이터가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="95e77-120">Item contains sensitive data.</span></span>

<span data-ttu-id="95e77-121">PowerShell 갤러리 관리자에게 항목 삭제 요청을 제출하려면 항목 세부 정보 페이지로 이동한 다음 고객 지원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95e77-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>