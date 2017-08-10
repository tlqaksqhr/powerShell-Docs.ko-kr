---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISE 개체 모델 계층 구조"
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: 0d0370ed9f64464038e643ae2cd241891fa74f33
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="d4098-103">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="d4098-103">The ISE Object Model Hierarchy</span></span>
  <span data-ttu-id="d4098-104">이 항목에서는 Windows PowerShell ISE(통합 스크립팅 환경)에 속하는 개체의 계층 구조를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="d4098-105">Windows PowerShell ISE는 Windows PowerShell 3.0 및 Windows PowerShell 4.0에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="d4098-106">개체를 클릭하여 개체를 정의하는 클래스에 대한 참조 설명서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

##  <span data-ttu-id="d4098-107"><a name="psISE"></a> **$psISE 개체**</span><span class="sxs-lookup"><span data-stu-id="d4098-107"><a name="psISE"></a> **$psISE Object**</span></span>
 <span data-ttu-id="d4098-108">**$psISE** 개체는 Windows PowerShell ISE 개체 계층 구조의 [루트 개체](The-ObjectModelRoot-Object.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="d4098-109">최상위 수준에 있는 이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-109">Located at the top level, it makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="d4098-110">**[$psISE.CurrentFile](#currentfile)**</span><span class="sxs-lookup"><span data-stu-id="d4098-110">**[$psISE.CurrentFile](#currentfile)**</span></span>

-   <span data-ttu-id="d4098-111">**[$psISE.CurrentPowerShellTab](#currentpowershelltab)**</span><span class="sxs-lookup"><span data-stu-id="d4098-111">**[$psISE.CurrentPowerShellTab](#currentpowershelltab)**</span></span>

-   <span data-ttu-id="d4098-112">**[$psISE.CurrentVisibleHorizontalTool](#CurrentVisibleHorizontalTool)**</span><span class="sxs-lookup"><span data-stu-id="d4098-112">**[$psISE.CurrentVisibleHorizontalTool](#CurrentVisibleHorizontalTool)**</span></span>

-   <span data-ttu-id="d4098-113">**[$psISE.CurrentVisibleVerticalTool](#CurrentVisibleVerticalTool)**</span><span class="sxs-lookup"><span data-stu-id="d4098-113">**[$psISE.CurrentVisibleVerticalTool](#CurrentVisibleVerticalTool)**</span></span>

-   <span data-ttu-id="d4098-114">**[$psISE.Options](#options)**</span><span class="sxs-lookup"><span data-stu-id="d4098-114">**[$psISE.Options](#options)**</span></span>

-   <span data-ttu-id="d4098-115">**[$psISE.PowerShellTabs](#powershelltabs)**</span><span class="sxs-lookup"><span data-stu-id="d4098-115">**[$psISE.PowerShellTabs](#powershelltabs)**</span></span>

##  <span data-ttu-id="d4098-116"><a name="CurrentFile"></a> **[$psISE.CurrentFile](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-116"><a name="CurrentFile"></a> **[$psISE.CurrentFile](The-ISEFile-Object.md)**</span></span>
 <span data-ttu-id="d4098-117">**$psISE.CurrentFile** 개체는 [ISEFile](The-ISEFile-Object.md) 클래스의 인스턴스로서, 이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-117">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="d4098-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md#Displayname)**</span><span class="sxs-lookup"><span data-stu-id="d4098-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md#Displayname)**</span></span>

-   <span data-ttu-id="d4098-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  이 개체는 [ISEEditor](The-ISEEditor-Object.md) 클래스의 인스턴스로서, 이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="d4098-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span><span class="sxs-lookup"><span data-stu-id="d4098-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span></span>

    -   <span data-ttu-id="d4098-121">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span><span class="sxs-lookup"><span data-stu-id="d4098-121">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span></span>

    -   <span data-ttu-id="d4098-122">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span><span class="sxs-lookup"><span data-stu-id="d4098-122">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span></span>

    -   <span data-ttu-id="d4098-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span><span class="sxs-lookup"><span data-stu-id="d4098-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span></span>

    -   <span data-ttu-id="d4098-124">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span><span class="sxs-lookup"><span data-stu-id="d4098-124">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span></span>

    -   <span data-ttu-id="d4098-125">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span><span class="sxs-lookup"><span data-stu-id="d4098-125">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span></span>

    -   <span data-ttu-id="d4098-126">**[Text](The-ISEEditor-Object.md#Text)**</span><span class="sxs-lookup"><span data-stu-id="d4098-126">**[Text](The-ISEEditor-Object.md#Text)**</span></span>

-   <span data-ttu-id="d4098-127">**[Encoding](The-ISEFile-Object.md#Encoding)**</span><span class="sxs-lookup"><span data-stu-id="d4098-127">**[Encoding](The-ISEFile-Object.md#Encoding)**</span></span>

-   <span data-ttu-id="d4098-128">**[FullPath](The-ISEFile-Object.md#FullPath)**</span><span class="sxs-lookup"><span data-stu-id="d4098-128">**[FullPath](The-ISEFile-Object.md#FullPath)**</span></span>

-   <span data-ttu-id="d4098-129">**[IsSaved](The-ISEFile-Object.md#IsSaved)**</span><span class="sxs-lookup"><span data-stu-id="d4098-129">**[IsSaved](The-ISEFile-Object.md#IsSaved)**</span></span>

-   <span data-ttu-id="d4098-130">**[IsUntitled](The-ISEFile-Object.md#IsUntitled)**</span><span class="sxs-lookup"><span data-stu-id="d4098-130">**[IsUntitled](The-ISEFile-Object.md#IsUntitled)**</span></span>

##  <span data-ttu-id="d4098-131"><a name="CurrentPowerShellTab"></a> **[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-131"><a name="CurrentPowerShellTab"></a> **[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span></span>
 <span data-ttu-id="d4098-132">**$psISE.CurrentPowerShellTab** 개체는 [PowerShellTab](The-PowerShellTab-Object.md) 클래스의 인스턴스로서, 이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-132">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="d4098-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  이 개체는 [ISEMenuItem](The-ISEMenuItem-Object.md) 클래스의 인스턴스로서, 이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  This object is an instance of the [ISEMenuItem](The-ISEMenuItem-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="d4098-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Action](The-ISEMenuItem-Object.md#Action)**</span><span class="sxs-lookup"><span data-stu-id="d4098-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Action](The-ISEMenuItem-Object.md#Action)**</span></span>

    -   <span data-ttu-id="d4098-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName](The-ISEMenuItem-Object.md#DisplayName)**</span><span class="sxs-lookup"><span data-stu-id="d4098-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName](The-ISEMenuItem-Object.md#DisplayName)**</span></span>

    -   <span data-ttu-id="d4098-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Shortcut](The-ISEMenuItem-Object.md#Shortcut)**</span><span class="sxs-lookup"><span data-stu-id="d4098-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Shortcut](The-ISEMenuItem-Object.md#Shortcut)**</span></span>

    -   <span data-ttu-id="d4098-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span></span>

-   <span data-ttu-id="d4098-138">**[$psISE.CurrentPowerShellTab.CanInvoke](The-PowerShellTab-Object.md#CanExecute)**</span><span class="sxs-lookup"><span data-stu-id="d4098-138">**[$psISE.CurrentPowerShellTab.CanInvoke](The-PowerShellTab-Object.md#CanExecute)**</span></span>

-   <span data-ttu-id="d4098-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  이 개체는 [ISEEditor](The-ISEEditor-Object.md) 클래스의 인스턴스로서, 이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="d4098-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span><span class="sxs-lookup"><span data-stu-id="d4098-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span></span>

    -   <span data-ttu-id="d4098-141">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span><span class="sxs-lookup"><span data-stu-id="d4098-141">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span></span>

    -   <span data-ttu-id="d4098-142">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span><span class="sxs-lookup"><span data-stu-id="d4098-142">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span></span>

    -   <span data-ttu-id="d4098-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span><span class="sxs-lookup"><span data-stu-id="d4098-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span></span>

    -   <span data-ttu-id="d4098-144">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span><span class="sxs-lookup"><span data-stu-id="d4098-144">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span></span>

    -   <span data-ttu-id="d4098-145">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span><span class="sxs-lookup"><span data-stu-id="d4098-145">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span></span>

    -   <span data-ttu-id="d4098-146">**[Text](The-ISEEditor-Object.md#Text)**</span><span class="sxs-lookup"><span data-stu-id="d4098-146">**[Text](The-ISEEditor-Object.md#Text)**</span></span>

-   <span data-ttu-id="d4098-147">**[$psISE.CurrentPowerShellTab.DisplayName](The-PowerShellTab-Object.md#Displayname)**</span><span class="sxs-lookup"><span data-stu-id="d4098-147">**[$psISE.CurrentPowerShellTab.DisplayName](The-PowerShellTab-Object.md#Displayname)**</span></span>

-   <span data-ttu-id="d4098-148">**[$psISE.CurrentPowerShellTab.ExpandedScript](The-PowerShellTab-Object.md#ExpandedScript)**</span><span class="sxs-lookup"><span data-stu-id="d4098-148">**[$psISE.CurrentPowerShellTab.ExpandedScript](The-PowerShellTab-Object.md#ExpandedScript)**</span></span>

-   <span data-ttu-id="d4098-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span></span>

-   <span data-ttu-id="d4098-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="d4098-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#HorizontalAddOnToolsPaneOpened)**</span><span class="sxs-lookup"><span data-stu-id="d4098-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#HorizontalAddOnToolsPaneOpened)**</span></span>

-   <span data-ttu-id="d4098-152">**[$psISE.CurrentPowerShellTab.Prompt](The-PowerShellTab-Object.md#Prompt)**</span><span class="sxs-lookup"><span data-stu-id="d4098-152">**[$psISE.CurrentPowerShellTab.Prompt](The-PowerShellTab-Object.md#Prompt)**</span></span>

-   <span data-ttu-id="d4098-153">**[$psISE.CurrentPowerShellTab.ShowCommands](The-PowerShellTab-Object.md#ShowCommands)**</span><span class="sxs-lookup"><span data-stu-id="d4098-153">**[$psISE.CurrentPowerShellTab.ShowCommands](The-PowerShellTab-Object.md#ShowCommands)**</span></span>

-   <span data-ttu-id="d4098-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span></span>

-   <span data-ttu-id="d4098-155">**[$psISE.CurrentPowerShellTab.StatusText](The-PowerShellTab-Object.md#StatusText)**</span><span class="sxs-lookup"><span data-stu-id="d4098-155">**[$psISE.CurrentPowerShellTab.StatusText](The-PowerShellTab-Object.md#StatusText)**</span></span>

-   <span data-ttu-id="d4098-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="d4098-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#VerticalAddOnToolsPaneOpened)**</span><span class="sxs-lookup"><span data-stu-id="d4098-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#VerticalAddOnToolsPaneOpened)**</span></span>

-   <span data-ttu-id="d4098-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="d4098-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

##  <span data-ttu-id="d4098-160"><a name="CurrentVisibleHorizontalTool"></a> **$psISE.CurrentVisibleHorizontalTool**</span><span class="sxs-lookup"><span data-stu-id="d4098-160"><a name="CurrentVisibleHorizontalTool"></a> **$psISE.CurrentVisibleHorizontalTool**</span></span>
 <span data-ttu-id="d4098-161">**$psISE.CurrentVisibleHorizontalTool** 개체는 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-161">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="d4098-162">현재 Windows PowerShell ISE 창의 위쪽 가장자리에 도킹되어 있는 설치된 추가 기능 도구를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-162">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="d4098-163">이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-163">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="d4098-164">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span><span class="sxs-lookup"><span data-stu-id="d4098-164">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span></span>

-   <span data-ttu-id="d4098-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span><span class="sxs-lookup"><span data-stu-id="d4098-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span></span>

-   <span data-ttu-id="d4098-166">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span><span class="sxs-lookup"><span data-stu-id="d4098-166">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span></span>

##  <span data-ttu-id="d4098-167"><a name="CurrentVisibleVerticalTool"></a> **$psISE.CurrentVisibleVerticalTool**</span><span class="sxs-lookup"><span data-stu-id="d4098-167"><a name="CurrentVisibleVerticalTool"></a> **$psISE.CurrentVisibleVerticalTool**</span></span>
 <span data-ttu-id="d4098-168">**$psISE.CurrentVisibleHorizontalTool** 개체는 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-168">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="d4098-169">현재 Windows PowerShell ISE 창의 오른쪽 가장자리에 도킹되어 있는 설치된 추가 기능 도구를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-169">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="d4098-170">이 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-170">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="d4098-171">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span><span class="sxs-lookup"><span data-stu-id="d4098-171">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span></span>

-   <span data-ttu-id="d4098-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span><span class="sxs-lookup"><span data-stu-id="d4098-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span></span>

-   <span data-ttu-id="d4098-173">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span><span class="sxs-lookup"><span data-stu-id="d4098-173">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span></span>

##  <span data-ttu-id="d4098-174"><a name="Options"></a> **$psISE.Options**</span><span class="sxs-lookup"><span data-stu-id="d4098-174"><a name="Options"></a> **$psISE.Options**</span></span>
 <span data-ttu-id="d4098-175">**$psISE.Options** 개체를 사용하면 스크립팅에 다음 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-175">The **$psISE.Options** object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="d4098-176">**[$psISE.Options.AutoSaveMinuteInterval](The-ISEOptions-Object.md#asmi)**</span><span class="sxs-lookup"><span data-stu-id="d4098-176">**[$psISE.Options.AutoSaveMinuteInterval](The-ISEOptions-Object.md#asmi)**</span></span>

-   <span data-ttu-id="d4098-177">**[$psISE.Options.ConsolePaneBackgroundColor](The-ISEOptions-Object.md#cpbc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-177">**[$psISE.Options.ConsolePaneBackgroundColor](The-ISEOptions-Object.md#cpbc)**</span></span>

-   <span data-ttu-id="d4098-178">**[$psISE.Options.ConsolePaneTextForegroundColor](The-ISEOptions-Object.md#conpfc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-178">**[$psISE.Options.ConsolePaneTextForegroundColor](The-ISEOptions-Object.md#conpfc)**</span></span>

-   <span data-ttu-id="d4098-179">**[$psISE.Options.ConsolePaneTextBackgroundColor](The-ISEOptions-Object.md#conptbc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-179">**[$psISE.Options.ConsolePaneTextBackgroundColor](The-ISEOptions-Object.md#conptbc)**</span></span>

-   <span data-ttu-id="d4098-180">**[$psISE.Options.ConsoleTokenColors](The-ISEOptions-Object.md#contc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-180">**[$psISE.Options.ConsoleTokenColors](The-ISEOptions-Object.md#contc)**</span></span>

-   <span data-ttu-id="d4098-181">**[$psISE.Options.DebugBackgroundColor](The-ISEOptions-Object.md#dbc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-181">**[$psISE.Options.DebugBackgroundColor](The-ISEOptions-Object.md#dbc)**</span></span>

-   <span data-ttu-id="d4098-182">**[$psISE.Options.DebugForegroundColor](The-ISEOptions-Object.md#dfc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-182">**[$psISE.Options.DebugForegroundColor](The-ISEOptions-Object.md#dfc)**</span></span>

-   <span data-ttu-id="d4098-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span></span>

-   <span data-ttu-id="d4098-184">**[$psISE.Options.ErrorBackgroundColor](The-ISEOptions-Object.md#ebc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-184">**[$psISE.Options.ErrorBackgroundColor](The-ISEOptions-Object.md#ebc)**</span></span>

-   <span data-ttu-id="d4098-185">**[$psISE.Options.ErrorForegroundColor](The-ISEOptions-Object.md#efc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-185">**[$psISE.Options.ErrorForegroundColor](The-ISEOptions-Object.md#efc)**</span></span>

-   <span data-ttu-id="d4098-186">**[$psISE.Options.FontName](The-ISEOptions-Object.md#fn)**</span><span class="sxs-lookup"><span data-stu-id="d4098-186">**[$psISE.Options.FontName](The-ISEOptions-Object.md#fn)**</span></span>

-   <span data-ttu-id="d4098-187">**[$psISE.Options.Fontsize](The-ISEOptions-Object.md#fs)**</span><span class="sxs-lookup"><span data-stu-id="d4098-187">**[$psISE.Options.Fontsize](The-ISEOptions-Object.md#fs)**</span></span>

-   <span data-ttu-id="d4098-188">**[$psISE.Options.IntellisenseTimeoutInSeconds](The-ISEOptions-Object.md#itis)**</span><span class="sxs-lookup"><span data-stu-id="d4098-188">**[$psISE.Options.IntellisenseTimeoutInSeconds](The-ISEOptions-Object.md#itis)**</span></span>

-   <span data-ttu-id="d4098-189">**[$psISE.Options.MRUCount](The-ISEOptions-Object.md#mc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-189">**[$psISE.Options.MRUCount](The-ISEOptions-Object.md#mc)**</span></span>

-   <span data-ttu-id="d4098-190">**[$psISE.Options.ScriptPaneBackgroundColor](The-ISEOptions-Object.md#spbc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-190">**[$psISE.Options.ScriptPaneBackgroundColor](The-ISEOptions-Object.md#spbc)**</span></span>

-   <span data-ttu-id="d4098-191">**[$psISE.Options.ScriptPaneForegroundColor](The-ISEOptions-Object.md#spfc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-191">**[$psISE.Options.ScriptPaneForegroundColor](The-ISEOptions-Object.md#spfc)**</span></span>

-   <span data-ttu-id="d4098-192">**[$psISE.Options.SelectedScriptPaneState](The-ISEOptions-Object.md#ssps)**</span><span class="sxs-lookup"><span data-stu-id="d4098-192">**[$psISE.Options.SelectedScriptPaneState](The-ISEOptions-Object.md#ssps)**</span></span>

-   <span data-ttu-id="d4098-193">**[$psISE.Options.ShowDefaultSnippets](The-ISEOptions-Object.md#sds)**</span><span class="sxs-lookup"><span data-stu-id="d4098-193">**[$psISE.Options.ShowDefaultSnippets](The-ISEOptions-Object.md#sds)**</span></span>

-   <span data-ttu-id="d4098-194">**[$psISE.Options.ShowIntellisenseInConsolePane](The-ISEOptions-Object.md#siicp)**</span><span class="sxs-lookup"><span data-stu-id="d4098-194">**[$psISE.Options.ShowIntellisenseInConsolePane](The-ISEOptions-Object.md#siicp)**</span></span>

-   <span data-ttu-id="d4098-195">**[$psISE.Options.ShowIntellisenseInScriptPane](The-ISEOptions-Object.md#siisp)**</span><span class="sxs-lookup"><span data-stu-id="d4098-195">**[$psISE.Options.ShowIntellisenseInScriptPane](The-ISEOptions-Object.md#siisp)**</span></span>

-   <span data-ttu-id="d4098-196">**[$psISE.Options.ShowLineNumbers](The-ISEOptions-Object.md#sln)**</span><span class="sxs-lookup"><span data-stu-id="d4098-196">**[$psISE.Options.ShowLineNumbers](The-ISEOptions-Object.md#sln)**</span></span>

-   <span data-ttu-id="d4098-197">**[$psISE.Options.ShowOutlining](The-ISEOptions-Object.md#so)**</span><span class="sxs-lookup"><span data-stu-id="d4098-197">**[$psISE.Options.ShowOutlining](The-ISEOptions-Object.md#so)**</span></span>

-   <span data-ttu-id="d4098-198">**[$psISE.Options.ShowToolBar](The-ISEOptions-Object.md#stb)**</span><span class="sxs-lookup"><span data-stu-id="d4098-198">**[$psISE.Options.ShowToolBar](The-ISEOptions-Object.md#stb)**</span></span>

-   <span data-ttu-id="d4098-199">**[$psISE.Options.ShowWarningBeforeSavingOnRun](The-ISEOptions-Object.md#swbsor)**</span><span class="sxs-lookup"><span data-stu-id="d4098-199">**[$psISE.Options.ShowWarningBeforeSavingOnRun](The-ISEOptions-Object.md#swbsor)**</span></span>

-   <span data-ttu-id="d4098-200">**[$psISE.Options.ShowWarningForDuplicateFiles](The-ISEOptions-Object.md#swfdf)**</span><span class="sxs-lookup"><span data-stu-id="d4098-200">**[$psISE.Options.ShowWarningForDuplicateFiles](The-ISEOptions-Object.md#swfdf)**</span></span>

-   <span data-ttu-id="d4098-201">**[$psISE.Options.TokenColors](The-ISEOptions-Object.md#tc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-201">**[$psISE.Options.TokenColors](The-ISEOptions-Object.md#tc)**</span></span>

-   <span data-ttu-id="d4098-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisense](The-ISEOptions-Object.md#uetsicpi)**</span><span class="sxs-lookup"><span data-stu-id="d4098-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisense](The-ISEOptions-Object.md#uetsicpi)**</span></span>

-   <span data-ttu-id="d4098-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisense](The-ISEOptions-Object.md#uetsispi)**</span><span class="sxs-lookup"><span data-stu-id="d4098-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisense](The-ISEOptions-Object.md#uetsispi)**</span></span>

-   <span data-ttu-id="d4098-204">**[$psISE.Options.UseLocalHelp](The-ISEOptions-Object.md#ulh)**</span><span class="sxs-lookup"><span data-stu-id="d4098-204">**[$psISE.Options.UseLocalHelp](The-ISEOptions-Object.md#ulh)**</span></span>

-   <span data-ttu-id="d4098-205">**[$psISE.Options.VerboseBackgroundColor](The-ISEOptions-Object.md#vbc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-205">**[$psISE.Options.VerboseBackgroundColor](The-ISEOptions-Object.md#vbc)**</span></span>

-   <span data-ttu-id="d4098-206">**[$psISE.Options.VerboseForegroundColor](The-ISEOptions-Object.md#vfc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-206">**[$psISE.Options.VerboseForegroundColor](The-ISEOptions-Object.md#vfc)**</span></span>

-   <span data-ttu-id="d4098-207">**[$psISE.Options.WarningBackgroundColor](The-ISEOptions-Object.md#wbc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-207">**[$psISE.Options.WarningBackgroundColor](The-ISEOptions-Object.md#wbc)**</span></span>

-   <span data-ttu-id="d4098-208">**[$psISE.Options.WarningForegroundColor](The-ISEOptions-Object.md#wfc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-208">**[$psISE.Options.WarningForegroundColor](The-ISEOptions-Object.md#wfc)**</span></span>

-   <span data-ttu-id="d4098-209">**[$psISE.Options.XmlTokenColors](The-ISEOptions-Object.md#xtc)**</span><span class="sxs-lookup"><span data-stu-id="d4098-209">**[$psISE.Options.XmlTokenColors](The-ISEOptions-Object.md#xtc)**</span></span>

-   <span data-ttu-id="d4098-210">**[$psISE.Options.Zoom](The-ISEOptions-Object.md#z)**</span><span class="sxs-lookup"><span data-stu-id="d4098-210">**[$psISE.Options.Zoom](The-ISEOptions-Object.md#z)**</span></span>

##  <span data-ttu-id="d4098-211"><a name="PowerShellTabs"></a> **[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="d4098-211"><a name="PowerShellTabs"></a> **[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span></span>
 <span data-ttu-id="d4098-212">**$psISE.PowerShellTabs** 개체는 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-212">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="d4098-213">로컬 컴퓨터 또는 연결된 원격 컴퓨터에서 사용 가능한 Windows PowerShell 실행 환경을 나타내는 현재 열려 있는 모든 PowerShell 탭의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-213">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="d4098-214">컬렉션의 각 멤버는 [PowerShellTab](The-PowerShellTab-Object.md) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="d4098-214">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4098-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4098-215">See Also</span></span>
- [<span data-ttu-id="d4098-216">Windows PowerShell ISE 스크립팅 개체 모델</span><span class="sxs-lookup"><span data-stu-id="d4098-216">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d4098-217">Windows PowerShell ISE 개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="d4098-217">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

