---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEMenuItem 개체"
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 33de866d706ec2b0894c5bfe49e07fee142b95c0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="c038e-103">ISEMenuItem 개체</span><span class="sxs-lookup"><span data-stu-id="c038e-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="c038e-104">**ISEMenuItem** 개체는 Microsoft.PowerShell.Host.ISE.ISEMenuItem 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="c038e-105">**추가 기능** 메뉴의 모든 메뉴 개체는 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="c038e-106">속성</span><span class="sxs-lookup"><span data-stu-id="c038e-106">Properties</span></span>

###  <span data-ttu-id="c038e-107"><a name="DisplayName"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="c038e-107"><a name="DisplayName"></a> DisplayName</span></span>
  <span data-ttu-id="c038e-108">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="c038e-109">메뉴 항목의 표시 이름을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <span data-ttu-id="c038e-110"><a name="Action"></a> 작업</span><span class="sxs-lookup"><span data-stu-id="c038e-110"><a name="Action"></a> Action</span></span>
  <span data-ttu-id="c038e-111">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="c038e-112">스크립트 블록을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="c038e-113">메뉴 항목을 클릭하면 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <span data-ttu-id="c038e-114"><a name="Shortcut"></a> Shortcut</span><span class="sxs-lookup"><span data-stu-id="c038e-114"><a name="Shortcut"></a> Shortcut</span></span>
  <span data-ttu-id="c038e-115">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="c038e-116">메뉴 항목에 대한 Windows 입력 바로 가기 키를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <span data-ttu-id="c038e-117"><a name="Submenus"></a> 하위 메뉴</span><span class="sxs-lookup"><span data-stu-id="c038e-117"><a name="Submenus"></a> Submenus</span></span>
  <span data-ttu-id="c038e-118">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="c038e-119">메뉴 항목의 [하위 메뉴 목록](The-ISEMenuItemCollection-Object.md)을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="c038e-120">스크립팅 예제</span><span class="sxs-lookup"><span data-stu-id="c038e-120">Scripting example</span></span>
 <span data-ttu-id="c038e-121">추가 기능 메뉴와 스크립트 가능한 해당 속성의 사용에 대해 보다 잘 이해하려면 다음 스크립팅 예제를 자세히 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c038e-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a><span data-ttu-id="c038e-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c038e-122">See Also</span></span>
- [<span data-ttu-id="c038e-123">ISEMenuItemCollection 개체</span><span class="sxs-lookup"><span data-stu-id="c038e-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="c038e-124">Windows PowerShell ISE 스크립팅 개체 모델</span><span class="sxs-lookup"><span data-stu-id="c038e-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="c038e-125">Windows PowerShell ISE 개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="c038e-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="c038e-126">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="c038e-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
