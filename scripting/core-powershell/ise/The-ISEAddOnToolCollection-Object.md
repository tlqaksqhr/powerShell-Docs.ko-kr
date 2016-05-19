---
title: ISEAddOnToolCollection 개체
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
---
# ISEAddOnToolCollection 개체
  **ISEAddOnToolCollection** 개체는 **ISEAddOnTool** 개체의 컬렉션입니다. 예제는 **$psISE.CurrentPowerShellTab.VerticalAddOnTools** 개체입니다.

## 메서드

### Add\( Name, ControlType, \[IsVisible\] \)
  Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다. 

 컬렉션에 새 추가 기능 도구를 추가합니다. 새로 추가된 추가 기능 도구를 반환합니다. 이 명령을 실행하려면 먼저 로컬 컴퓨터에 추가 기능 도구를 설치하고 어셈블리를 로드해야 합니다.

 **Name** – 문자열
 Windows PowerShell ISE에 추가되는 추가 기능 도구의 표시 이름을 지정합니다.

 **ControlType** –형식
 추가되는 컨트롤을 지정합니다.

 **\[IsVisible\]** – 선택적 부울
 **$true**로 설정되면, 추가 기능 도구가 연결된 도구 창에 즉시 표시됩니다.

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### Remove\( Item \)
  Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다. 

 컬렉션에서 지정된 추가 기능 도구를 제거합니다.

 **Item** – Microsoft.PowerShell.Host.ISE.ISEAddOnTool
 Windows PowerShell ISE에서 제거할 개체를 지정합니다.

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### SetSelectedPowerShellTab\( psTab \)
  Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다. 

 **psTab** 매개 변수가 지정하는 PowerShell을 탭을 선택합니다.

 **psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab
 선택할 PowerShell 탭입니다.

```

      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"

```

### Remove\( psTab \)
  Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다. 

 **psTab** 매개 변수가 지정하는 PowerShell 탭을 제거합니다.

 **psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab
 제거할 PowerShell 탭입니다.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## 참고 항목
 [PowerShellTab 개체](The-PowerShellTab-Object.md) 
 [Windows PowerShell ISE 스크립팅 개체 모델](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 개체 모델 참조](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


