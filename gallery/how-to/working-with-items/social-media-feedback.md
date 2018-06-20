---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 소셜 미디어나 댓글을 통해 피드백 제공
ms.openlocfilehash: a8e6097de4a565b504189b0b0488c45b6d78a8b6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188142"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="c2b6d-103">소셜 미디어나 댓글을 통해 피드백 제공</span><span class="sxs-lookup"><span data-stu-id="c2b6d-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="c2b6d-104">Powershell 갤러리에서 사용자는 두 가지 방식을 통해 항목에 대한 공개 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-104">The Powershell Gallery supports two approaches for users to provide public feedback on an item:</span></span>

- <span data-ttu-id="c2b6d-105">왼쪽 모서리의 링크를 사용하여 Facebook, LinkedIn 또는 Twitter 소셜 미디어 사이트에서 항목을 "공유"합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-105">Use the links on the left edge to "share" an item in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="c2b6d-106">댓글 기능을 사용하여 항목에 대한 댓글을 게시합니다. 그러면 작성자가 게시한 항목에 대한 댓글을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-106">Use the Comment feature to post comments on an item, and to allow Authors to watch for comments on items they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="c2b6d-107">소셜 미디어 피드백</span><span class="sxs-lookup"><span data-stu-id="c2b6d-107">Social Media Feedback</span></span>

<span data-ttu-id="c2b6d-108">PowerShell 갤러리에 있는 각 항목의 페이지 왼쪽에는 Facebook, LinkedIn 및 Twitter의 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-108">On the left side of the page for each item in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="c2b6d-109">이러한 링크를 클릭하면 소셜 미디어 사이트가 열리므로 항목 링크를 빠르게 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the item.</span></span>

<span data-ttu-id="c2b6d-110">사용자는 선택한 사이트에 로그인해야 PowerShell 갤러리 항목을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery item.</span></span>

<span data-ttu-id="c2b6d-111">다른 사람들에게 추천하려는 항목이 있는 경우 소셜 미디어에서 공유하면 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-111">Users are encouraged to do this if they find that an item is something they would recommend to others.</span></span>
<span data-ttu-id="c2b6d-112">PowerShell 갤러리에서는 각 소셜 미디어 사이트에서 "공유"된 항목을 확인하여 해당 항목이 각 소셜 미디어 사이트에서 공유된 횟수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-112">The PowerShell Gallery will check each social media site for "shares" of the item, and display how many times that item has been shared in each of the social media sites.</span></span>
<span data-ttu-id="c2b6d-113">이 경우 해당 항목이 공유된 횟수만 표시되므로, 다른 사용자들은 해당 횟수를 항목의 "좋아요" 수로 해석하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-113">Since this shows only the count of times something has been shared, it will be intepreted other users as "liking" the item.</span></span>


## <a name="comments"></a><span data-ttu-id="c2b6d-114">설명</span><span class="sxs-lookup"><span data-stu-id="c2b6d-114">Comments</span></span>

<span data-ttu-id="c2b6d-115">PowerShell 갤러리는 LiveFyre 서비스를 통해 항목에 대한 사용자의 댓글 게시를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-115">The PowerShell Gallery uses the LiveFyre service to allow users to comment on items.</span></span>
<span data-ttu-id="c2b6d-116">항목에 대한 권장 사항이나 피드백이 있는 사용자는 이 기능을 통해 모든 항목 페이지 방문자에게 표시되는 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-116">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the item page.</span></span>
<span data-ttu-id="c2b6d-117">항목 소유자는 이 피드백을 팔로우하여 댓글이 게시되면 알림을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-117">Item owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="c2b6d-118">댓글 시스템은 Microsoft에서 관리하지 않는 별도의 서비스인 LiveFyre를 통해 제공되므로 고유한 로그인 정보가 있어야 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-118">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="c2b6d-119">처음으로 댓글을 남기거나 항목 중 하나의 댓글을 팔로우하도록 선택하면 LiveFyre 계정을 만들라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-119">The first time you choose to leave a comment or Follow comments on one of your items, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="c2b6d-120">LiveFyre 계정을 만들어서 로그인한 후에 항목에 대한 피드백을 제공하는 댓글을 작성하여 "댓글 게시..."를 클릭하면 됩니다. 하지만 댓글이 즉시 표시되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-120">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the item, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="c2b6d-121">갤러리 항목에 대한 댓글은 PowerShell 갤러리 관리자가 중재하며, 게시한 모든 댓글은 중재자가 검토한 후에 다른 사용자들이 볼 수 있도록 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-121">Comments for gallery items are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="c2b6d-122">이처럼 댓글을 중재하는 이유는 PowerShell 갤러리 [사용 약관](https://www.powershellgallery.com/policies/Terms)에 맞는 공개 댓글을 게시하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-122">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="c2b6d-123">항목 소유자는 LiveFyre에 게시되는 댓글을 팔로우하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-123">Item owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="c2b6d-124">LiveFyre 계정은 필수 항목이며, LiveFyre에서 항목을 게시하는 데 사용하는 것과 같은 전자 메일 주소를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-124">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your item in LiveFyre.</span></span>
<span data-ttu-id="c2b6d-125">댓글을 팔로우하려면 LiveFyre에 로그인한 다음 소유자로 등재된 항목으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-125">To Follow comments, log into LiveFyre, and navigate to any item where you are listed as an Owner.</span></span>
<span data-ttu-id="c2b6d-126">각 항목 아래쪽의 댓글 상자 밑에 "+팔로우"가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-126">Below the Comment box at the bottom of each item you will see "+Follow".</span></span>
<span data-ttu-id="c2b6d-127">이 단추를 클릭하면 항목에 대해 새 댓글이 게시될 때마다 LiveFyre에서 등록된 전자 메일 주소로 전자 메일을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b6d-127">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the item.</span></span>