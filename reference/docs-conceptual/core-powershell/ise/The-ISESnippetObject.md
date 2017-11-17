---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISESnippet 개체"
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="3ea42-103">ISESnippet 개체</span><span class="sxs-lookup"><span data-stu-id="3ea42-103">The ISESnippetObject</span></span>
  <span data-ttu-id="3ea42-104">**ISESnippet** 개체는 Microsoft.PowerShell.Host.ISE.ISESnippet 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="3ea42-105">**$psISE.CurrentPowerShellTab.Snippets** 컬렉션의 멤버는 모두 **ISESnippet** 개체의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="3ea42-106">코드 조각을 만드는 가장 쉬운 방법은 [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="3ea42-107">속성</span><span class="sxs-lookup"><span data-stu-id="3ea42-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="3ea42-108">Author</span><span class="sxs-lookup"><span data-stu-id="3ea42-108">Author</span></span>
  <span data-ttu-id="3ea42-109">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="3ea42-110">코드 조각 작성자의 이름을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="3ea42-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="3ea42-111">CodeFragment</span></span>
  <span data-ttu-id="3ea42-112">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="3ea42-113">편집기에 삽입할 코드 조각을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="3ea42-114">바로 가기</span><span class="sxs-lookup"><span data-stu-id="3ea42-114">Shortcut</span></span>
  <span data-ttu-id="3ea42-115">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="3ea42-116">메뉴 항목에 대한 Windows 바로 가기 키를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3ea42-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="3ea42-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ea42-117">See Also</span></span>
- [<span data-ttu-id="3ea42-118">ISESnippetCollection 개체</span><span class="sxs-lookup"><span data-stu-id="3ea42-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="3ea42-119">Windows PowerShell ISE 스크립팅 개체 모델</span><span class="sxs-lookup"><span data-stu-id="3ea42-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="3ea42-120">Windows PowerShell ISE 개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="3ea42-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="3ea42-121">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="3ea42-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
