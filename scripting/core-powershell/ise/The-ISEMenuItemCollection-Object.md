---
title: ISEMenuItemCollection 개체
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
---
# ISEMenuItemCollection 개체
  **ISEMenuItemCollection** 개체는 **ISEMenuItem** 개체의 컬렉션이며, Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection 클래스의 인스턴스입니다. 예제는 Windows PowerShellÂ® ISE(통합 스크립팅 환경)에서 **추가 기능** 메뉴를 사용자 지정하는 데 사용되는 **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 개체입니다.

## 메서드

### Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 메뉴 항목을 컬렉션에 추가합니다.

 **DisplayName**
 추가할 메뉴의 표시 이름입니다.

 **작업**
 이 메뉴 항목과 연결되는 동작을 지정하는 **System.Management.Automation.ScriptBlock** 개체입니다.

 **바로 가기**
 작업에 대한 바로 가기 키입니다.

 **Returns**
 방금 추가된 ISEMenuItem 개체입니다.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### Clear\(\)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 메뉴 항목에서 모든 하위 메뉴를 제거합니다.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## 참고 항목
 [ISEMenuItem 개체](The-ISEMenuItem-Object.md) 
 [Windows PowerShell ISE 스크립팅 개체 모델](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 개체 모델 참조](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


