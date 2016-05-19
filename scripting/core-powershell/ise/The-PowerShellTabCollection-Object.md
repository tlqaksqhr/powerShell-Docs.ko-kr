---
title: PowerShellTabCollection 개체
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
---
# PowerShellTabCollection 개체
  **PowerShellTab** 컬렉션 개체는 **PowerShellTab** 개체의 컬렉션입니다. 각 **PowerShellTab** 개체는 별도의 런타임 환경으로 작동합니다. Microsoft.PowerShell.Host.ISE.PowerShellTabs 클래스의 인스턴스입니다. 예제는 **$psISE.PowerShellTabs** 개체입니다.

## 메서드

### Add\(\)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 새 PowerShell 탭을 컬렉션에 추가합니다. 새로 추가된 탭을 반환합니다.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 **psTab** 매개 변수로 지정되는 탭을 제거합니다.

 **psTab**
 제거할 PowerShell 탭입니다.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 **psTab** 매개 변수에서 지정하는 PowerShell 탭을 선택하여 현재 사용 중인 PowerShell 탭으로 만듭니다.

 **psTab**
 선택할 PowerShell 탭입니다.

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

## 참고 항목
 [PowerShellTab 개체](The-PowerShellTab-Object.md) 
 [Windows PowerShell ISE 스크립팅 개체 모델](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 개체 모델 참조](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 개체 모델 계층 구조](../ise/The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


