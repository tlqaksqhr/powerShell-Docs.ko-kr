---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Windows PowerShell ISE 개체 모델 참조"
ms.technology: powershell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 8bcb8620d668abb4d5026e3940fc322cbcfcd523
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="windows-powershell-ise-object-model-reference"></a>Windows PowerShell ISE 개체 모델 참조
  
## <a name="object-model-reference"></a>개체 모델 참조
 이 섹션에서는 Windows PowerShell® ISE(통합 스크립팅 환경)에서 다양한 개체를 정의하는 기본 클래스에 대한 참조를 제공합니다. 계층 구조에 구성되어 있는 개체를 보려면 [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md)(ISE 개체 모델 계층 구조)를 참조하세요.

 [ISEAddOnTool 개체](The-ISEAddOnTool-Object.md)
 예제: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [ISEAddOnTool 개체](The-ISEAddOnTool-Object.md)
  [ISEEditor 개체](The-ISEEditor-Object.md)
 예제: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [ISEFile 개체](The-ISEFile-Object.md)
 예제: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [ISEFileCollection 개체](The-ISEFileCollection-Object.md)
 예제: $psISE.PowerShellTabs.Files.

 [ISEMenuItem 개체](The-ISEMenuItem-Object.md)
 예제: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [ISEMenuItemCollection 개체](The-ISEMenuItemCollection-Object.md)
 예제: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [ISEOptions 개체](The-ISEOptions-Object.md)
 예제: $psISE.Options, $psISE.Options.DefaultOptions

 [ObjectModelRoot 개체](The-ObjectModelRoot-Object.md)
 예제: $psISE 루트 개체입니다.

 [PowerShellTab 개체](The-PowerShellTab-Object.md)
 예제: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [PowerShellTabCollection 개체](The-PowerShellTabCollection-Object.md)
 예제: $psISE.PowerShellTabs.

## <a name="see-also"></a>참고 항목
- [Windows PowerShell ISE 스크립팅 개체 모델](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
