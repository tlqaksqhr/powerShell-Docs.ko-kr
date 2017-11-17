---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="unlisting-items"></a><span data-ttu-id="ff237-103">목록에서 항목 제거</span><span class="sxs-lookup"><span data-stu-id="ff237-103">Unlisting items</span></span>

<span data-ttu-id="ff237-104">**옵션으로 노출되지 않는 항목을 PowerShell 갤러리에서 제거해야 하는 것은 무엇 때문일까요?**</span><span class="sxs-lookup"><span data-stu-id="ff237-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="ff237-105">PowerShell 갤러리에서는 사용자가 항목을 영구적으로 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span> <span data-ttu-id="ff237-106">따라서 다른 사용자가 이후의 가능한 손상에 대해 염려하지 않고 항목을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span> <span data-ttu-id="ff237-107">예를 들어 Pester 모듈이 Azure 모듈을 사용하는데 Azure 모듈이 갤러리에서 제거되면 사용자가 Pester 모듈을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="ff237-108">그러나 항목을 제거하는 대신 목록에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="ff237-109">**PowerShell 갤러리의 목록에서 항목을 제거하면 어떻게 될까요?**</span><span class="sxs-lookup"><span data-stu-id="ff237-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="ff237-110">PowerShell 갤러리의 목록에서 모듈 또는 스크립트와 같은 항목을 제거하면 항목 탭에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab.</span></span>
<span data-ttu-id="ff237-111">또한 목록에 없는 항목은 검색 표시줄을 사용하여 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-111">In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="ff237-112">목록에 없는 항목을 다운로드하려면 항목의 정확한 이름 및 버전을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-112">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="ff237-113">이 때문에 목록에서 항목을 제거하는 경우 해당 항목을 사용하는 다른 모듈이나 스크립트가 손상되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-113">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="ff237-114">목록에서 항목을 제거하려면 항목 세부 정보 페이지로 이동한 다음 '항목 삭제'를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-114">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="ff237-115">'목록에 표시' 확인란의 선택을 취소하고 저장을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-115">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="ff237-116">**항목을 제거하려면 어떻게 하나요?**</span><span class="sxs-lookup"><span data-stu-id="ff237-116">**How can I remove an item?**</span></span>

<span data-ttu-id="ff237-117">항목을 삭제해야 하는 시나리오가 발생하면 PowerShell 갤러리 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="ff237-117">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="ff237-118">유효한 삭제 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-118">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="ff237-119">저작권 침해 문제</span><span class="sxs-lookup"><span data-stu-id="ff237-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="ff237-120">항목에 잠재적으로 유해한 콘텐츠가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="ff237-120">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="ff237-121">항목에 중요한 데이터가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="ff237-121">Item contains sensitive data.</span></span>

<span data-ttu-id="ff237-122">PowerShell 갤러리 관리자에게 항목 삭제 요청을 제출하려면 항목 세부 정보 페이지로 이동한 다음 고객 지원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ff237-122">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>  


