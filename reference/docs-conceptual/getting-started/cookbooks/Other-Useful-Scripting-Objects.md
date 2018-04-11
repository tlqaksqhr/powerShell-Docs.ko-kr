---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 기타 유용한 스크립팅 개체
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="58773-103">기타 유용한 스크립팅 개체</span><span class="sxs-lookup"><span data-stu-id="58773-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="58773-104">다음 개체에서는 Windows PowerShell ISE의 추가 스크립팅 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="58773-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="58773-105">**$psISE** 계층 구조에 포함되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58773-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="58773-106">유용한 스크립팅 개체</span><span class="sxs-lookup"><span data-stu-id="58773-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="58773-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="58773-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="58773-108">Windows PowerShell ISE가 콘솔 응용 프로그램과 상호 작용하는 방식에는 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58773-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="58773-109">사용자의 개입을 필요로 하는 명령이나 자동화 스크립트는 Windows PowerShell 콘솔에서 작동하는 방식으로 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58773-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="58773-110">이러한 명령이나 스크립트가 Windows PowerShell ISE 명령 창에서 실행되는 것을 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58773-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="58773-111">**$psUnsupportedConsoleApplications** 개체는 그러한 명령의 목록을 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="58773-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="58773-112">이 목록에 있는 명령을 실행하려 할 경우, 지원되지 않는다는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="58773-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="58773-113">다음 스크립트는 목록에 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="58773-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="58773-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="58773-114">$psLocalHelp</span></span>

<span data-ttu-id="58773-115">로컬의 컴파일된 HTML 도움말 파일에 있는 도움말 항목과 연결된 링크 간에 상황에 맞는 매핑을 유지 관리하는 사전 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="58773-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="58773-116">특정 항목에 대한 로컬 도움말을 찾는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58773-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="58773-117">이 목록에서 항목을 추가하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58773-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="58773-118">다음 코드 예제에서는 **$psLocalHelp**에 들어 있는 몇 가지 키-값 쌍 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58773-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="58773-119">샘플 출력</span><span class="sxs-lookup"><span data-stu-id="58773-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="58773-120">키 : Add-Computer</span><span class="sxs-lookup"><span data-stu-id="58773-120">Key : Add-Computer</span></span>|<span data-ttu-id="58773-121">값 : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="58773-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="58773-122">키 : Add-Content</span><span class="sxs-lookup"><span data-stu-id="58773-122">Key : Add-Content</span></span>|<span data-ttu-id="58773-123">값 : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="58773-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="58773-124">다음 스크립트는 목록에 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="58773-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="58773-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="58773-125">$psOnlineHelp</span></span>

<span data-ttu-id="58773-126">도움말 항목의 항목 제목과 거기에 연결된 외부 URL 간에 상황에 맞는 매핑을 유지 관리하는 사전 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="58773-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="58773-127">웹에서 특정 항목에 대한 도움말을 찾는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58773-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="58773-128">이 목록에서 항목을 추가하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58773-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="58773-129">샘플 출력</span><span class="sxs-lookup"><span data-stu-id="58773-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="58773-130">키 : Add-Computer</span><span class="sxs-lookup"><span data-stu-id="58773-130">Key : Add-Computer</span></span>|<span data-ttu-id="58773-131">값 : http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="58773-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="58773-132">키 : Add-Content</span><span class="sxs-lookup"><span data-stu-id="58773-132">Key : Add-Content</span></span>|<span data-ttu-id="58773-133">값 : http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="58773-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="58773-134">다음 스크립트는 목록에 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="58773-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="58773-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58773-135">See Also</span></span>

- [<span data-ttu-id="58773-136">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="58773-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)