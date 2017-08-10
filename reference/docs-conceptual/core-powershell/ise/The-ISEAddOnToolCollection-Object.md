---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEAddOnToolCollection 개체"
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: 09088c9e7307a26b86e82f2dc10d2648213c6bd2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="e0c0d-103">ISEAddOnToolCollection 개체</span><span class="sxs-lookup"><span data-stu-id="e0c0d-103">The ISEAddOnToolCollection Object</span></span>
  <span data-ttu-id="e0c0d-104">**ISEAddOnToolCollection** 개체는 **ISEAddOnTool** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="e0c0d-105">예제는 **$psISE.CurrentPowerShellTab.VerticalAddOnTools** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="e0c0d-106">메서드</span><span class="sxs-lookup"><span data-stu-id="e0c0d-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="e0c0d-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="e0c0d-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>
  <span data-ttu-id="e0c0d-108">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e0c0d-109">컬렉션에 새 추가 기능 도구를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="e0c0d-110">새로 추가된 추가 기능 도구를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="e0c0d-111">이 명령을 실행하려면 먼저 로컬 컴퓨터에 추가 기능 도구를 설치하고 어셈블리를 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

 <span data-ttu-id="e0c0d-112">**Name** – 문자열. Windows PowerShell ISE에 추가되는 추가 기능 도구의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

 <span data-ttu-id="e0c0d-113">**ControlType** – 형식. 추가되는 컨트롤을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-113">**ControlType** -Type Specifies the control that is added.</span></span>

 <span data-ttu-id="e0c0d-114">**\[IsVisible\]** – 선택적 부울. **$true**로 설정되면, 추가 기능 도구가 연결된 도구 창에 즉시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```PowerShell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="e0c0d-115">Remove\( Item\)</span><span class="sxs-lookup"><span data-stu-id="e0c0d-115">Remove\( Item \)</span></span>
  <span data-ttu-id="e0c0d-116">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e0c0d-117">컬렉션에서 지정된 추가 기능 도구를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-117">Removes the specified add-on tool from the collection.</span></span>

 <span data-ttu-id="e0c0d-118">**Item** – Microsoft.PowerShell.Host.ISE.ISEAddOnTool. Windows PowerShell ISE에서 제거할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```PowerShell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="e0c0d-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="e0c0d-119">SetSelectedPowerShellTab\( psTab \)</span></span>
  <span data-ttu-id="e0c0d-120">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e0c0d-121">**psTab** 매개 변수가 지정하는 PowerShell을 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="e0c0d-122">**psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab. 선택할 PowerShell 탭입니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```PowerShell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a><span data-ttu-id="e0c0d-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="e0c0d-123">Remove\( psTab \)</span></span>
  <span data-ttu-id="e0c0d-124">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e0c0d-125">**psTab** 매개 변수가 지정하는 PowerShell 탭을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="e0c0d-126">**psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab. 제거할 PowerShell 탭입니다.</span><span class="sxs-lookup"><span data-stu-id="e0c0d-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```PowerShell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="e0c0d-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0c0d-127">See Also</span></span>
- [<span data-ttu-id="e0c0d-128">PowerShellTab 개체</span><span class="sxs-lookup"><span data-stu-id="e0c0d-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="e0c0d-129">Windows PowerShell ISE 스크립팅 개체 모델</span><span class="sxs-lookup"><span data-stu-id="e0c0d-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="e0c0d-130">Windows PowerShell ISE 개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="e0c0d-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="e0c0d-131">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="e0c0d-131">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
