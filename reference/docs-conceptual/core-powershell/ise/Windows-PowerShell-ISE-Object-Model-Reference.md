---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell ISE 개체 모델 참조"
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: e5d4ae03158d9b5b0efd98db1272bc13872181ac
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="8547e-103">Windows PowerShell ISE 개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="8547e-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="8547e-104">개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="8547e-104">Object Model Reference</span></span>
 <span data-ttu-id="8547e-105">이 섹션에서는 Windows PowerShell® ISE(통합 스크립팅 환경)에서 다양한 개체를 정의하는 기본 클래스에 대한 참조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8547e-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="8547e-106">계층 구조에 구성되어 있는 개체를 보려면 [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md)(ISE 개체 모델 계층 구조)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8547e-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="8547e-107">[ISEAddOnTool 개체](The-ISEAddOnTool-Object.md)
 예제: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span><span class="sxs-lookup"><span data-stu-id="8547e-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md)
 Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="8547e-108">[ISEAddOnTool 개체](The-ISEAddOnTool-Object.md)
  [ISEEditor 개체](The-ISEEditor-Object.md)
 예제: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span><span class="sxs-lookup"><span data-stu-id="8547e-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md)
  [The ISEEditor Object](The-ISEEditor-Object.md)
 Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="8547e-109">[ISEFile 개체](The-ISEFile-Object.md)
 예제: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span><span class="sxs-lookup"><span data-stu-id="8547e-109">[The ISEFile Object](The-ISEFile-Object.md)
 Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="8547e-110">[ISEFileCollection 개체](The-ISEFileCollection-Object.md)
 예제: $psISE.PowerShellTabs.Files.</span><span class="sxs-lookup"><span data-stu-id="8547e-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md)
 Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="8547e-111">[ISEMenuItem 개체](The-ISEMenuItem-Object.md)
 예제: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span><span class="sxs-lookup"><span data-stu-id="8547e-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md)
 Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="8547e-112">[ISEMenuItemCollection 개체](The-ISEMenuItemCollection-Object.md)
 예제: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span><span class="sxs-lookup"><span data-stu-id="8547e-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md)
 Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="8547e-113">[ISEOptions 개체](The-ISEOptions-Object.md)
 예제: $psISE.Options, $psISE.Options.DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="8547e-113">[The ISEOptions Object](The-ISEOptions-Object.md)
 Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="8547e-114">[ObjectModelRoot 개체](The-ObjectModelRoot-Object.md)
 예제: $psISE 루트 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8547e-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md)
 Example: The root $psISE object.</span></span>

 <span data-ttu-id="8547e-115">[PowerShellTab 개체](The-PowerShellTab-Object.md)
 예제: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span><span class="sxs-lookup"><span data-stu-id="8547e-115">[The PowerShellTab Object](The-PowerShellTab-Object.md)
 Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="8547e-116">[PowerShellTabCollection 개체](The-PowerShellTabCollection-Object.md)
 예제: $psISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="8547e-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md)
 Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="8547e-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8547e-117">See Also</span></span>
- [<span data-ttu-id="8547e-118">Windows PowerShell ISE 스크립팅 개체 모델</span><span class="sxs-lookup"><span data-stu-id="8547e-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
