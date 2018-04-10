---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: 항목 소유자 관리
ms.openlocfilehash: e550b74ebde00cfbb154dbf4fb1fa4ae0582e029
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="managing-item-owners"></a><span data-ttu-id="10c43-103">항목 소유자 관리</span><span class="sxs-lookup"><span data-stu-id="10c43-103">Managing Item Owners</span></span>

<span data-ttu-id="10c43-104">PowerShell 갤러리에 있는 항목의 소유권은 갤러리에 항목을 게시한 사람이 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="10c43-105">초기 항목 게시 외에 이 메타데이터를 관리해야 하는 경우도 있으므로 항목 자체는 변경할 수 없지만 소유자 메타데이터는 변경할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="10c43-106">모든 항목 소유자는 피어입니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-106">All item owners are peers.</span></span>
<span data-ttu-id="10c43-107">즉, 모든 항목 소유자가 항목의 새로운 버전을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="10c43-108">또한 모든 항목 소유자가 다른 항목 소유자를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="10c43-109">모든 소유자가 동일한 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="10c43-110">항목의 초기 소유자 설정</span><span class="sxs-lookup"><span data-stu-id="10c43-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="10c43-111">PowerShell 갤러리에 새 항목을 게시할 때 항목을 게시한 사용자가 초기 소유자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="10c43-112">Publish-Module cmdlet에서 사용된 API 키의 소유자로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="10c43-113">소유자 추가</span><span class="sxs-lookup"><span data-stu-id="10c43-113">Adding Owners</span></span>

<span data-ttu-id="10c43-114">PowerShell 갤러리에 항목을 게시한 후 추가 사용자를 항목의 소유자로 쉽게 초대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="10c43-115">항목의 현재 소유자인 계정을 사용하여 PowerShell 갤러리에 [로그온](https://powershellgallery.com/users/account/LogOn)합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="10c43-116">'항목' 탭을 사용하거나, 검색하거나, 사용자 이름, [**내 항목 관리**](https://www.powershellgallery.com/account/Packages)를 차례로 클릭하여 항목 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="10c43-117">항목의 소유자로 로그온한 경우 왼쪽에 클릭할 '소유자 관리' 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="10c43-118">소유자로 추가할 사람의 사용자 이름을 입력하고 '추가'를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="10c43-119">항목의 소유자가 되도록 초대하는 메일이 새 공동 소유자에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="10c43-120">해당 사용자가 링크를 클릭하면 소유자인 다른 사용자를 제거하는 기능을 포함하여 항목에 대한 모든 권한을 가진 전체 공동 소유자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="10c43-121">**참고**: 새 소유자가 소유권을 확인하기 전에는 항목의 소유자로 나열되지 *습니다*.</span><span class="sxs-lookup"><span data-stu-id="10c43-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="10c43-122">**소유자 관리** 페이지를 보고 있는 경우 현재 소유자에 "승인 보류 중" 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="10c43-123">다른 소유자를 제거할 수 있는 것과 마찬가지로 해당 초대를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="10c43-124">이 초대 프로세스는 사용자가 다른 사용자를 항목의 소유자로 거짓 추가하는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="10c43-125">"Authors" 메타데이터는 순수 자유형 텍스트이며 "Owners"만 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="10c43-126">소유자 제거</span><span class="sxs-lookup"><span data-stu-id="10c43-126">Removing Owners</span></span>
<span data-ttu-id="10c43-127">항목에 여러 소유자가 있고 한 소유자를 제거해야 하는 경우 프로세스는 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="10c43-128">항목의 현재 소유자인 계정을 사용하여 PowerShell 갤러리에 [로그온](https://powershellgallery.com/users/account/LogOn)합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="10c43-129">항목 탭을 사용하거나, 검색하거나, 사용자 이름, [**내 항목 관리**](https://www.powershellgallery.com/account/Packages)를 차례로 클릭하여 항목 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="10c43-130">항목의 소유자로 로그온한 경우 왼쪽에 클릭할 '소유자 관리' 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="10c43-131">제거할 소유자 옆에 있는 '제거' 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="10c43-132">항목 소유권 이전</span><span class="sxs-lookup"><span data-stu-id="10c43-132">Transferring Item Ownership</span></span>
<span data-ttu-id="10c43-133">항목 소유권을 한 사용자에서 다른 사용자로 이전하라는 지원 요청을 받는 경우도 있지만, 이 작업은 대부분 직접 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="10c43-134">소유권을 한 사용자에서 다른 사용자로 이전하는 프로세스는 단순히 위의 두 가지 기능이 조합된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="10c43-135">현재 소유자가 새 사용자를 공동 소유자로 초대하고 새 사용자가 초대를 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="10c43-136">새 사용자가 소유자 목록에서 기존 사용자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="10c43-137">이 요청은 두 가지 형태로 제공되었지만 프로세스는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-137">This request has come in under a couple forms but the process works the same.</span></span>

* <span data-ttu-id="10c43-138">항목 소유권이 한 개발자에서 다른 개발자로 변경되는 경우</span><span class="sxs-lookup"><span data-stu-id="10c43-138">The item ownership is changing from one developer to another</span></span>
* <span data-ttu-id="10c43-139">항목이 실수로 잘못된 계정을 사용하여 게시된 경우</span><span class="sxs-lookup"><span data-stu-id="10c43-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="10c43-140">분리된 항목</span><span class="sxs-lookup"><span data-stu-id="10c43-140">Orphaned Items</span></span>
<span data-ttu-id="10c43-141">마지막 시나리오는 자주 발생하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="10c43-142">항목이 분리되었으며 유일한 항목 소유자 계정을 사용하여 새 소유자를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="10c43-143">이 시나리오의 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-143">Here are some examples of this scenario:</span></span>

* <span data-ttu-id="10c43-144">소유자 계정이 더 이상 존재하지 않는 메일 주소와 연결되어 있고 사용자가 암호를 잊어버린 경우</span><span class="sxs-lookup"><span data-stu-id="10c43-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
* <span data-ttu-id="10c43-145">등록된 소유자가 항목을 생성하는 회사를 퇴사했으며 항목 소유권을 업데이트하도록 연락할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="10c43-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
* <span data-ttu-id="10c43-146">일부 항목에만 영향을 미친 버그로 인해 갤러리에서 항목의 소유자가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="10c43-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="10c43-147">PowerShell 갤러리 관리자는 모든 항목에 대한 '소유자 관리' 링크에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="10c43-148">항목의 정당한 소유자가 소유권 권한을 얻기 위해 현재 소유자에게 문의할 수 없는 경우 갤러리의 '신고하기' 링크를 사용하여 PowerShell 갤러리 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="10c43-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="10c43-149">그러면 프로세스에 따라 항목의 소유권을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="10c43-150">항목의 소유자로 확인되면 직접 항목에 대한 '소유자 관리' 링크를 사용하여 소유자로 초대하는 메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="10c43-151">이 작업은 사용자가 소유자로 확인된 후에만 수행되며 상황에 따라 프로세스가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="10c43-152">대체로 항목의 프로젝트 URL을 사용하여 프로젝트 소유자에게 문의하지만 Twitter, 메일 또는 다른 수단으로 프로젝트 소유자에게 문의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10c43-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>