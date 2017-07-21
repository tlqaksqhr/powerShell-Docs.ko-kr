---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEOptions 개체"
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 56bdd5999b46b6e29e762c2d9a2060cebe3a1299
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="7e83d-103">ISEOptions 개체</span><span class="sxs-lookup"><span data-stu-id="7e83d-103">The ISEOptions Object</span></span>
  <span data-ttu-id="7e83d-104">**ISEOptions** 개체는 Windows PowerShell ISE에 대한 다양한 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="7e83d-105">**Microsoft.PowerShell.Host.ISE.ISEOptions** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="7e83d-106">**ISEOptions** 개체는 다음 메서드 및 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-106">The **ISEOptions** object provides the following methods and properties.</span></span>

 <span data-ttu-id="7e83d-107">**메서드**</span><span class="sxs-lookup"><span data-stu-id="7e83d-107">**Methods**</span></span>

-   [<span data-ttu-id="7e83d-108">RestoreDefaultConsoleTokenColors()</span><span class="sxs-lookup"><span data-stu-id="7e83d-108">RestoreDefaultConsoleTokenColors()</span></span>](#rdctc)

-   [<span data-ttu-id="7e83d-109">RestoreDefaults()</span><span class="sxs-lookup"><span data-stu-id="7e83d-109">RestoreDefaults()</span></span>](#rd)

-   [<span data-ttu-id="7e83d-110">RestoreDefaultTokenColors()</span><span class="sxs-lookup"><span data-stu-id="7e83d-110">RestoreDefaultTokenColors()</span></span>](#rdtc)

-   [<span data-ttu-id="7e83d-111">RestoreDefaultXmlTokenColors()</span><span class="sxs-lookup"><span data-stu-id="7e83d-111">RestoreDefaultXmlTokenColors()</span></span>](#rdxtc)

 <span data-ttu-id="7e83d-112">**속성**</span><span class="sxs-lookup"><span data-stu-id="7e83d-112">**Properties**</span></span>

-   [<span data-ttu-id="7e83d-113">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="7e83d-113">AutoSaveMinuteInterval</span></span>](#asmi)

-   [<span data-ttu-id="7e83d-114">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-114">CommandPaneBackgroundColor</span></span>](#cpbc)

-   [<span data-ttu-id="7e83d-115">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="7e83d-115">CommandPaneUp</span></span>](#cpu)

-   [<span data-ttu-id="7e83d-116">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-116">ConsolePaneBackgroundColor</span></span>](#conpbc)

-   [<span data-ttu-id="7e83d-117">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-117">ConsolePaneForegroundColor</span></span>](#conpfc)

-   [<span data-ttu-id="7e83d-118">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-118">ConsolePaneTextBackgroundColor</span></span>](#conptbc)

-   [<span data-ttu-id="7e83d-119">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="7e83d-119">ConsoleTokenColors</span></span>](#contc)

-   [<span data-ttu-id="7e83d-120">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-120">DebugBackgroundColor</span></span>](#dbc)

-   [<span data-ttu-id="7e83d-121">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-121">DebugForegroundColor</span></span>](#dfc)

-   [<span data-ttu-id="7e83d-122">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="7e83d-122">DefaultOptions</span></span>](#do)

-   [<span data-ttu-id="7e83d-123">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-123">ErrorBackgroundColor</span></span>](#ebc)

-   [<span data-ttu-id="7e83d-124">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-124">ErrorForegroundColor</span></span>](#efc)

-   [<span data-ttu-id="7e83d-125">FontName</span><span class="sxs-lookup"><span data-stu-id="7e83d-125">FontName</span></span>](#fn)

-   [<span data-ttu-id="7e83d-126">FontSize</span><span class="sxs-lookup"><span data-stu-id="7e83d-126">FontSize</span></span>](#fs)

-   [<span data-ttu-id="7e83d-127">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="7e83d-127">IntellisenseTimeoutInSeconds</span></span>](#itis)

-   [<span data-ttu-id="7e83d-128">MruCount</span><span class="sxs-lookup"><span data-stu-id="7e83d-128">MruCount</span></span>](#mc)

-   [<span data-ttu-id="7e83d-129">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-129">OutputPaneBackgroundColor</span></span>](#opbc)

-   [<span data-ttu-id="7e83d-130">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-130">OutputPaneTextForegroundColor</span></span>](#optfc)

-   [<span data-ttu-id="7e83d-131">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-131">OutputPaneTextBackgroundColor</span></span>](#optbc)

-   [<span data-ttu-id="7e83d-132">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-132">ScriptPaneBackgroundColor</span></span>](#spbc)

-   [<span data-ttu-id="7e83d-133">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-133">ScriptPaneForegroundColor</span></span>](#spfc)

-   [<span data-ttu-id="7e83d-134">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="7e83d-134">SelectedScriptPaneState</span></span>](#ssps)

-   [<span data-ttu-id="7e83d-135">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="7e83d-135">ShowDefaultSnippets</span></span>](#sds)

-   [<span data-ttu-id="7e83d-136">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="7e83d-136">ShowIntellisenseInConsolePane</span></span>](#siicp)

-   [<span data-ttu-id="7e83d-137">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="7e83d-137">ShowIntellisenseInScriptPane</span></span>](#siisp)

-   [<span data-ttu-id="7e83d-138">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="7e83d-138">ShowLineNumbers</span></span>](#sln)

-   [<span data-ttu-id="7e83d-139">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="7e83d-139">ShowOutlining</span></span>](#so)

-   [<span data-ttu-id="7e83d-140">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="7e83d-140">ShowToolBar</span></span>](#stb)

-   [<span data-ttu-id="7e83d-141">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="7e83d-141">ShowWarningBeforeSavingOnRun</span></span>](#swbsor)

-   [<span data-ttu-id="7e83d-142">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="7e83d-142">ShowWarningForDuplicateFiles</span></span>](#swfdf)

-   [<span data-ttu-id="7e83d-143">TokenColors</span><span class="sxs-lookup"><span data-stu-id="7e83d-143">TokenColors</span></span>](#tc)

-   [<span data-ttu-id="7e83d-144">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="7e83d-144">UseEnterToSelectInConsolePaneIntellisense</span></span>](#uetsicpi)

-   [<span data-ttu-id="7e83d-145">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="7e83d-145">UseEnterToSelectInScriptPaneIntellisense</span></span>](#uetsispi)

-   [<span data-ttu-id="7e83d-146">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="7e83d-146">UseLocalHelp</span></span>](#ulh)

-   [<span data-ttu-id="7e83d-147">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-147">VerboseBackgroundColor</span></span>](#vbc)

-   [<span data-ttu-id="7e83d-148">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-148">VerboseForegroundColor</span></span>](#vfc)

-   [<span data-ttu-id="7e83d-149">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-149">WarningBackgroundColor</span></span>](#wbc)

-   [<span data-ttu-id="7e83d-150">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-150">WarningForegroundColor</span></span>](#wfc)

-   [<span data-ttu-id="7e83d-151">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="7e83d-151">XmlTokenColors</span></span>](#xtc)

-   [<span data-ttu-id="7e83d-152">확대/축소</span><span class="sxs-lookup"><span data-stu-id="7e83d-152">Zoom</span></span>](#z)

## <a name="methods"></a><span data-ttu-id="7e83d-153">메서드</span><span class="sxs-lookup"><span data-stu-id="7e83d-153">Methods</span></span>

###  <span data-ttu-id="7e83d-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="7e83d-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="7e83d-155">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-156">콘솔 창에서 토큰 색의 기본값을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-156">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <span data-ttu-id="7e83d-157"><a name="rd"></a> RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="7e83d-157"><a name="rd"></a> RestoreDefaults\(\)</span></span>
  <span data-ttu-id="7e83d-158">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-159">콘솔 창에 있는 모든 옵션 설정의 기본값을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-159">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="7e83d-160">또한 메시지가 다시 표시되지 않도록 하기 위해 표준 확인란을 제공하는 다양한 경고 메시지의 동작을 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-160">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <span data-ttu-id="7e83d-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="7e83d-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="7e83d-162">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-163">스크립트 창에서 토큰 색의 기본값을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-163">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <span data-ttu-id="7e83d-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="7e83d-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="7e83d-165">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-165">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-166">Windows PowerShell ISE에 표시되는 XML 요소에 대한 토큰 색의 기본값을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-166">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="7e83d-167">[XmlTokenColors](#xtc)도 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e83d-167">Also see [XmlTokenColors](#xtc).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="7e83d-168">속성</span><span class="sxs-lookup"><span data-stu-id="7e83d-168">Properties</span></span>

###  <span data-ttu-id="7e83d-169"><a name="asmi"></a> AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="7e83d-169"><a name="asmi"></a> AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="7e83d-170">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-170">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-171">Windows PowerShell ISE의 파일 자동 저장 작업 간격(분 단위 수)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-171">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="7e83d-172">기본값은 2분입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-172">The default value is 2 minutes.</span></span> <span data-ttu-id="7e83d-173">이 값은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-173">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <span data-ttu-id="7e83d-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="7e83d-175">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-175">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="7e83d-176">이후 버전에 대해서는 [ConsolePaneBackgroundColor](#conpbc)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e83d-176">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="7e83d-177">명령 창에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-177">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="7e83d-178">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-178">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <span data-ttu-id="7e83d-179"><a name="cpu"></a> CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="7e83d-179"><a name="cpu"></a> CommandPaneUp</span></span>
  <span data-ttu-id="7e83d-180">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-180">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="7e83d-181">명령 창이 출력 창 위에 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-181">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <span data-ttu-id="7e83d-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="7e83d-183">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-183">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-184">콘솔 창에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-184">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="7e83d-185">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-185">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <span data-ttu-id="7e83d-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="7e83d-187">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-188">콘솔 창에 있는 텍스트의 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-188">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <span data-ttu-id="7e83d-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="7e83d-190">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-190">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-191">콘솔 창에 있는 텍스트의 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-191">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="7e83d-192"><a name="contc"></a> ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="7e83d-192"><a name="contc"></a> ConsoleTokenColors</span></span>
  <span data-ttu-id="7e83d-193">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-193">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-194">Windows PowerShell ISE 콘솔 창에서 IntelliSense 토큰의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-194">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="7e83d-195">이 속성은 토큰 형식과 콘솔 창에 대한 색의 이름/값 쌍을 포함하는 사전 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-195">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="7e83d-196">스크립트 창에서 IntelliSense 토큰의 색을 변경하려면 [TokenColors](#tc)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-196">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tc).</span></span> <span data-ttu-id="7e83d-197">색을 기본값으로 다시 설정하려면 [RestoreDefaultConsoleTokenColors()](#rdctc)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-197">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors()](#rdctc).</span></span> <span data-ttu-id="7e83d-198">다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="7e83d-198">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="7e83d-199"><a name="dbc"></a> DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-199"><a name="dbc"></a> DebugBackgroundColor</span></span>
  <span data-ttu-id="7e83d-200">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-200">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-201">콘솔 창에 표시되는 디버그 텍스트의 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-201">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="7e83d-202">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-202">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="7e83d-203"><a name="dfc"></a> DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-203"><a name="dfc"></a> DebugForegroundColor</span></span>
  <span data-ttu-id="7e83d-204">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-204">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-205">콘솔 창에 표시되는 디버그 텍스트의 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-205">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="7e83d-206">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-206">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <span data-ttu-id="7e83d-207"><a name="do"></a> DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="7e83d-207"><a name="do"></a> DefaultOptions</span></span>
  <span data-ttu-id="7e83d-208">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-208">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-209">Reset 메서드를 사용할 때 사용할 기본값을 지정하는 속성의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-209">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3

```

###  <span data-ttu-id="7e83d-210"><a name="ebc"></a> ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-210"><a name="ebc"></a> ErrorBackgroundColor</span></span>
  <span data-ttu-id="7e83d-211">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-211">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-212">콘솔 창에 나타나는 오류 텍스트에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-212">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="7e83d-213">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-213">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <span data-ttu-id="7e83d-214"><a name="efc"></a> ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-214"><a name="efc"></a> ErrorForegroundColor</span></span>
  <span data-ttu-id="7e83d-215">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-215">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-216">콘솔 창에 나타나는 오류 텍스트의 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-216">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="7e83d-217">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-217">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <span data-ttu-id="7e83d-218"><a name="fn"></a> FontName</span><span class="sxs-lookup"><span data-stu-id="7e83d-218"><a name="fn"></a> FontName</span></span>
  <span data-ttu-id="7e83d-219">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-219">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-220">현재 스크립트 창과 콘솔 창 모두에서 사용 중인 글꼴 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-220">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <span data-ttu-id="7e83d-221"><a name="fs"></a> FontSize</span><span class="sxs-lookup"><span data-stu-id="7e83d-221"><a name="fs"></a> FontSize</span></span>
  <span data-ttu-id="7e83d-222">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-222">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-223">글꼴 크기를 정수로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-223">Specifies the font size as an integer.</span></span> <span data-ttu-id="7e83d-224">스크립트 창, 명령 창 및 출력 창에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-224">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="7e83d-225">값의 유효한 범위는 8-32입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-225">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <span data-ttu-id="7e83d-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="7e83d-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="7e83d-227">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-227">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-228">IntelliSense에서 현재 입력한 텍스트를 확인하는 데 사용하는 시간(초)의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-228">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="7e83d-229">이 시간(초)이 지나면 IntelliSense에서는 제한 시간이 끝나서 계속 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-229">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="7e83d-230">기본값은 3초입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-230">The default value is 3 seconds.</span></span> <span data-ttu-id="7e83d-231">이 값은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-231">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <span data-ttu-id="7e83d-232"><a name="mc"></a> MruCount</span><span class="sxs-lookup"><span data-stu-id="7e83d-232"><a name="mc"></a> MruCount</span></span>
  <span data-ttu-id="7e83d-233">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-233">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-234">Windows PowerShell ISE에서 추적하는 최근에 열린 파일의 수를 지정하고 **파일 열기** 메뉴의 맨 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-234">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="7e83d-235">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-235">The default value is 10.</span></span> <span data-ttu-id="7e83d-236">이 값은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-236">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <span data-ttu-id="7e83d-237"><a name="opbc"></a> OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-237"><a name="opbc"></a> OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="7e83d-238">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-238">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="7e83d-239">이후 버전에 대해서는 [ConsolePaneBackgroundColor](#conpbc)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e83d-239">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="7e83d-240">출력 창 자체에 대한 배경색을 가져오거나 설정하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-240">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="7e83d-241">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-241">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <span data-ttu-id="7e83d-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="7e83d-243">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-243">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="7e83d-244">이후 버전에 대해서는 [ConsolePaneForegroundColor](#conpfc)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e83d-244">For later versions, see [ConsolePaneForegroundColor](#conpfc).</span></span>

 <span data-ttu-id="7e83d-245">Windows PowerShell ISE 2.0의 출력 창에 있는 텍스트의 전경색을 변경하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-245">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <span data-ttu-id="7e83d-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="7e83d-247">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-247">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="7e83d-248">이후 버전에 대해서는 [ConsolePaneTextBackgroundColor](#conptbc)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e83d-248">For later versions, see [ConsolePaneTextBackgroundColor](#conptbc).</span></span>

 <span data-ttu-id="7e83d-249">출력 창에 있는 텍스트의 배경색을 변경하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-249">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="7e83d-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="7e83d-251">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-251">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-252">파일에 대한 배경색을 가져오거나 설정하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-252">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="7e83d-253">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-253">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <span data-ttu-id="7e83d-254"><a name="spfc"></a> ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-254"><a name="spfc"></a> ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="7e83d-255">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-255">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-256">스크립트 창에서 스크립트가 아닌 파일에 대한 전경색을 가져오거나 설정하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-256">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="7e83d-257">스크립트 파일에 대한 전경색을 설정하려면 [TokenColors](The-ISEOptions-Object.md#tc) 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-257">To set the foreground color for script files, use the [TokenColors](The-ISEOptions-Object.md#tc) property.</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <span data-ttu-id="7e83d-258"><a name="ssps"></a> SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="7e83d-258"><a name="ssps"></a> SelectedScriptPaneState</span></span>
  <span data-ttu-id="7e83d-259">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-259">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-260">디스플레이에서의 스크립트 창 위치를 가져오거나 설정하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-260">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="7e83d-261">이 문자열은 "최대화", "맨 위" 또는 "오른쪽"일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-261">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <span data-ttu-id="7e83d-262"><a name="sds"></a> ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="7e83d-262"><a name="sds"></a> ShowDefaultSnippets</span></span>
  <span data-ttu-id="7e83d-263">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-264">코드 조각의 **CTRL+J** 목록에 Windows PowerShell에 포함된 시작 세트가 포함되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-264">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="7e83d-265">**$false**로 설정하면 사용자가 정의한 코드 조각만 **CTRL+J** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-265">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="7e83d-266">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-266">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <span data-ttu-id="7e83d-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="7e83d-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="7e83d-268">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-268">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-269">IntelliSense가 콘솔 창에서 구문, 매개 변수 및 값 제안을 제공하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-269">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="7e83d-270">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-270">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <span data-ttu-id="7e83d-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="7e83d-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="7e83d-272">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-272">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-273">IntelliSense가 스크립트 창에서 구문, 매개 변수 및 값 제안을 제공하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-273">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="7e83d-274">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-274">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <span data-ttu-id="7e83d-275"><a name="sln"></a> ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="7e83d-275"><a name="sln"></a> ShowLineNumbers</span></span>
  <span data-ttu-id="7e83d-276">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-276">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-277">스크립트 창의 왼쪽 여백에 줄 번호가 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-277">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="7e83d-278">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-278">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <span data-ttu-id="7e83d-279"><a name="so"></a> ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="7e83d-279"><a name="so"></a> ShowOutlining</span></span>
  <span data-ttu-id="7e83d-280">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-280">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-281">스크립트 창에서 왼쪽 여백에 있는 코드 섹션 옆에 확장 및 축소가 가능한 대괄호가 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-281">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="7e83d-282">표시된다면 텍스트 블록의 옆에 있는 빼기(\(-\)) 아이콘을 클릭하여 텍스트 블록을 축소하거나 더하기(\(+\)) 아이콘을 클릭하여 텍스트 블록을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-282">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="7e83d-283">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-283">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <span data-ttu-id="7e83d-284"><a name="stb"></a> ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="7e83d-284"><a name="stb"></a> ShowToolBar</span></span>
  <span data-ttu-id="7e83d-285">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-286">Windows PowerShell ISE 창의 맨 위에 ISE 도구 모음이 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-286">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="7e83d-287">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-287">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <span data-ttu-id="7e83d-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="7e83d-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="7e83d-289">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-289">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-290">스크립트를 실행하기 전에 자동으로 저장할 때 경고 메시지가 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-290">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="7e83d-291">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-291">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <span data-ttu-id="7e83d-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="7e83d-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="7e83d-293">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-293">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-294">다른 PowerShell 탭에 동일한 파일이 열리면 경고 메시지가 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-294">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="7e83d-295">**$true**로 설정된 경우, 여러 탭에서 같은 파일을 열려고 하면 "이 파일의 복사본이 다른 Windows PowerShell 탭에서 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-295">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab.</span></span> <span data-ttu-id="7e83d-296">이 파일의 변경 내용은 열려 있는 모든 복사본에 적용됩니다."라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-296">Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="7e83d-297">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-297">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <span data-ttu-id="7e83d-298"><a name="tc"></a> TokenColors</span><span class="sxs-lookup"><span data-stu-id="7e83d-298"><a name="tc"></a> TokenColors</span></span>
  <span data-ttu-id="7e83d-299">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-299">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-300">Windows PowerShell ISE 스크립트 창에서 IntelliSense 토큰의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-300">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="7e83d-301">이 속성은 토큰 형식과 스크립트 창에 대한 색의 이름/값 쌍을 포함하는 사전 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-301">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="7e83d-302">콘솔 창에서 IntelliSense 토큰의 색을 변경하려면 [ConsoleTokenColors](#contc)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-302">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#contc).</span></span> <span data-ttu-id="7e83d-303">색을 기본값으로 다시 설정하려면 [RestoreDefaultTokenColors()](#rdtc)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-303">To reset the colors to the default values, see [RestoreDefaultTokenColors()](#rdtc).</span></span> <span data-ttu-id="7e83d-304">다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="7e83d-304">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="7e83d-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="7e83d-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="7e83d-306">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-306">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-307">콘솔 창에서 IntelliSense 제공 옵션을 선택하기 위해 Enter 키를 사용할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-307">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="7e83d-308">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-308">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <span data-ttu-id="7e83d-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="7e83d-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="7e83d-310">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-310">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-311">스크립트 창에서 IntelliSense 제공 옵션을 선택하기 위해 Enter 키를 사용할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-311">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="7e83d-312">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-312">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <span data-ttu-id="7e83d-313"><a name="ulh"></a> UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="7e83d-313"><a name="ulh"></a> UseLocalHelp</span></span>
  <span data-ttu-id="7e83d-314">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-314">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-315">커서가 키워드 있는 상태에서 F1 키를 누를 때 로컬로 설치된 도움말이나 온라인 TechNet 라이브러리 도움말이 나타나는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-315">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="7e83d-316">**$true**로 설정된 경우, 팝업 창에 로컬로 설치된 도움말 콘텐츠가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-316">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="7e83d-317">`Update-Help` 명령을 실행하여 도움말 파일을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-317">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="7e83d-318">**$false**로 설정된 경우, 브라우저로 TechNet 라이브러리에 있는 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-318">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <span data-ttu-id="7e83d-319"><a name="vbc"></a> VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-319"><a name="vbc"></a> VerboseBackgroundColor</span></span>
  <span data-ttu-id="7e83d-320">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-320">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-321">콘솔 창에 나타나는 자세한 정보 텍스트에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-321">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="7e83d-322">**System.Windows.Media.Color** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-322">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="7e83d-323"><a name="vfc"></a> VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-323"><a name="vfc"></a> VerboseForegroundColor</span></span>
  <span data-ttu-id="7e83d-324">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-324">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-325">콘솔 창에 나타나는 자세한 정보 텍스트에 대한 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-325">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="7e83d-326">**System.Windows.Media.Color** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-326">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <span data-ttu-id="7e83d-327"><a name="wbc"></a> WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-327"><a name="wbc"></a> WarningBackgroundColor</span></span>
  <span data-ttu-id="7e83d-328">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-328">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-329">콘솔 창에 나타나는 경고 텍스트에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-329">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="7e83d-330">**System.Windows.Media.Color** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-330">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="7e83d-331"><a name="wfc"></a> WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7e83d-331"><a name="wfc"></a> WarningForegroundColor</span></span>
  <span data-ttu-id="7e83d-332">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-332">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e83d-333">출력 창에 나타나는 경고 텍스트의 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-333">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="7e83d-334">**System.Windows.Media.Color** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-334">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <span data-ttu-id="7e83d-335"><a name="xtc"></a> XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="7e83d-335"><a name="xtc"></a> XmlTokenColors</span></span>
  <span data-ttu-id="7e83d-336">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-336">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-337">Windows PowerShell ISE에 표시되는 토큰 형식과 XML 콘텐츠에 대한 색의 이름/값 쌍을 포함하는 사전 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-337">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="7e83d-338">다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="7e83d-338">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="7e83d-339">[RestoreDefaultXmlTokenColors()](#rdxtc)도 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e83d-339">Also see [RestoreDefaultXmlTokenColors()](#rdxtc).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <span data-ttu-id="7e83d-340"><a name="z"></a> 확대/축소</span><span class="sxs-lookup"><span data-stu-id="7e83d-340"><a name="z"></a> Zoom</span></span>
  <span data-ttu-id="7e83d-341">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-341">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="7e83d-342">콘솔 창과 스크립트 창 모두에서 텍스트의 상대 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-342">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="7e83d-343">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-343">The default value is 100.</span></span> <span data-ttu-id="7e83d-344">값이 작을수록 Windows PowerShell ISE의 텍스트가 작게 표시되고, 큰 숫자일수록 텍스트가 더 크게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-344">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="7e83d-345">값은 20에서 400 사이의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="7e83d-345">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="7e83d-346">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e83d-346">See Also</span></span>
- [<span data-ttu-id="7e83d-347">Windows PowerShell ISE 스크립팅 개체 모델</span><span class="sxs-lookup"><span data-stu-id="7e83d-347">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7e83d-348">Windows PowerShell ISE 개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="7e83d-348">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

