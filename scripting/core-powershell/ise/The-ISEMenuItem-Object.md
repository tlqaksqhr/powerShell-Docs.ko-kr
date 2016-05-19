---
title: ISEMenuItem 개체
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
---
# ISEMenuItem 개체
  **ISEMenuItem** 개체는 Microsoft.PowerShell.Host.ISE.ISEMenuItem 클래스의 인스턴스입니다. **추가 기능** 메뉴의 모든 메뉴 개체는 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 클래스의 인스턴스입니다.

## 속성

###  <a name="DisplayName"></a> DisplayName
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 메뉴 항목의 표시 이름을 가져오는 읽기 전용 속성입니다.

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <a name="Action"></a> 작업
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 스크립트 블록을 가져오는 읽기 전용 속성입니다. 메뉴 항목을 클릭하면 작업을 호출합니다.

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <a name="Shortcut"></a> 바로 가기
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 메뉴 항목에 대한 Windows 입력 바로 가기 키를 가져오는 읽기 전용 속성입니다.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <a name="Submenus"></a> 하위 메뉴
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 메뉴 항목의 [하위 메뉴 목록](The-ISEMenuItemCollection-Object.md)을 가져오는 읽기 전용 속성입니다.

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## 스크립팅 예제
 추가 기능 메뉴와 스크립트 가능한 해당 속성의 사용에 대해 보다 잘 이해하려면 다음 스크립팅 예제를 자세히 읽습니다.

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu – a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## 참고 항목
 [ISEMenuItemCollection 개체](The-ISEMenuItemCollection-Object.md) 
 [Windows PowerShell ISE 스크립팅 개체 모델](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 개체 모델 참조](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


