---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShellTabCollection 개체"
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="29df7-103">PowerShellTabCollection 개체</span><span class="sxs-lookup"><span data-stu-id="29df7-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="29df7-104">**PowerShellTab** 컬렉션 개체는 **PowerShellTab** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="29df7-105">각 **PowerShellTab** 개체는 별도의 런타임 환경으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="29df7-106">Microsoft.PowerShell.Host.ISE.PowerShellTabs 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="29df7-107">예제는 **$psISE.PowerShellTabs** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="29df7-108">메서드</span><span class="sxs-lookup"><span data-stu-id="29df7-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="29df7-109">추가\(\)</span><span class="sxs-lookup"><span data-stu-id="29df7-109">Add\(\)</span></span>
  <span data-ttu-id="29df7-110">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="29df7-111">새 PowerShell 탭을 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="29df7-112">새로 추가된 탭을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="29df7-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="29df7-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="29df7-114">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="29df7-115">**psTab** 매개 변수로 지정되는 탭을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="29df7-116">**psTab**
 제거할 PowerShell 탭입니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-116">**psTab**
 The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="29df7-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="29df7-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="29df7-118">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="29df7-119">**psTab** 매개 변수에서 지정하는 PowerShell 탭을 선택하여 현재 사용 중인 PowerShell 탭으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="29df7-120">**psTab**
 선택할 PowerShell 탭입니다.</span><span class="sxs-lookup"><span data-stu-id="29df7-120">**psTab**
 The PowerShell tab to select.</span></span>

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a><span data-ttu-id="29df7-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29df7-121">See Also</span></span>
- [<span data-ttu-id="29df7-122">PowerShellTab 개체</span><span class="sxs-lookup"><span data-stu-id="29df7-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="29df7-123">Windows PowerShell ISE 스크립팅 개체 모델</span><span class="sxs-lookup"><span data-stu-id="29df7-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="29df7-124">Windows PowerShell ISE 개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="29df7-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="29df7-125">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="29df7-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
