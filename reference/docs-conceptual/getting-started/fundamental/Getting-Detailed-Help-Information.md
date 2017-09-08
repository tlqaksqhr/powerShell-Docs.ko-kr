---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "자세한 도움말 정보 보기"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: c786ce089073abccdf186dc1d9e8ee383f83655d
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="78a3d-103">자세한 도움말 정보 보기</span><span class="sxs-lookup"><span data-stu-id="78a3d-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="78a3d-104">Windows PowerShell에는 Windows PowerShell 개념과 Windows PowerShell 언어를 설명하는 자세한 도움말 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="78a3d-105">각 cmdlet 및 공급자에 대한 도움말 항목과 많은 함수 및 스크립트에 대한 도움말 항목도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="78a3d-106">명령 프롬프트에서 이러한 도움말 항목을 표시하거나 Microsoft TechNet 라이브러리에서 이러한 항목의 가장 최근에 업데이트된 버전을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="78a3d-107">Windows PowerShell 통합 스크립팅 환경 등 Windows PowerShell을 호스트하는 대부분의 프로그램은 상황에 맞는 도움말, 컴파일된 도움말 파일(.chm) 등의 추가 도움말 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="78a3d-108">Cmdlet에 대한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="78a3d-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="78a3d-109">Windows PowerShell cmdlet에 대한 도움말을 보려면 [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="78a3d-110">예를 들어 [Get-Childitem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet에 대한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="78a3d-111">또는</span><span class="sxs-lookup"><span data-stu-id="78a3d-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="78a3d-112">Get-Help cmdlet에 대한 도움말을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="78a3d-113">예:</span><span class="sxs-lookup"><span data-stu-id="78a3d-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="78a3d-114">세션에 있는 모든 cmdlet 도움말 항목의 목록을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="78a3d-115">각 도움말 항목을 한 번에 한 페이지씩 표시하려면 **help** 함수 또는 해당 별칭 **man**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="78a3d-116">예를 들어 Get-ChildItem cmdlet에 대한 도움말을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="78a3d-117">또는</span><span class="sxs-lookup"><span data-stu-id="78a3d-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="78a3d-118">해당 매개 변수 및 사용 예제에 대한 설명을 포함하여 cmdlet, 함수 또는 스크립트에 대한 자세한 정보를 표시하려면 Get-Help cmdlet의 *Detailed* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="78a3d-119">예를 들어 Get-ChildItem cmdlet에 대한 자세한 정보를 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="78a3d-120">도움말 항목의 모든 내용을 표시하려면 Get-Help cmdlet의 *Full* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="78a3d-121">예를 들어 Get-ChildItem cmdlet에 대한 도움말 항목의 모든 내용을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="78a3d-122">cmdlet의 매개 변수에 대한 자세한 도움말을 보려면 Get-Help cmdlet의 *Parameter* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="78a3d-123">예를 들어 Get-ChildItem cmdlet의 모든 매개 변수에 대한 자세한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="78a3d-124">도움말 항목의 예제만 표시하려면 Get-Help의 *Example* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="78a3d-125">예를 들어 Get-ChildItem cmdlet에 대한 도움말 항목의 예제만 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="78a3d-126">작성하는 cmdlet의 도움말 항목을 작성하는 방법에 대한 자세한 내용은 MSDN 라이브러리에서 [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415)(Cmdlet 도움말 작성 방법) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78a3d-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="78a3d-127">개념 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="78a3d-127">Getting Conceptual Help</span></span>
<span data-ttu-id="78a3d-128">Get-Help cmdlet은 Windows PowerShell 언어에 대한 항목을 포함하여 Windows PowerShell의 개념 항목에 대한 정보도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="78a3d-129">개념 도움말 항목은 "about_" 접두사로 시작합니다(예: about_line_editing).</span><span class="sxs-lookup"><span data-stu-id="78a3d-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="78a3d-130">개념 항목의 이름은 영어가 아닌 Windows PowerShell 버전에서도 영어로 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="78a3d-131">개념 항목 목록을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="78a3d-132">특정 도움말 항목을 표시하려면 다음과 같이 항목 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="78a3d-133">*Detailed*, *Parameter* 및 *Examples*와 같은 Get-Help의 매개 변수는 개념 도움말 항목의 표시에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="78a3d-134">공급자에 대한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="78a3d-134">Getting Help About Providers</span></span>
<span data-ttu-id="78a3d-135">Get-Help cmdlet은 Windows PowerShell 공급자에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="78a3d-136">공급자에 대한 도움말을 보려면 "Get-Help"를 입력한 다음 공급자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="78a3d-137">예를 들어 레지스트리 공급자에 대한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="78a3d-138">세션에 있는 모든 공급자 도움말 항목의 목록을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="78a3d-139">*Detailed*, *Parameter* 및 *Examples*와 같은 Get-Help의 매개 변수는 공급자 도움말 항목의 표시에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="78a3d-140">스크립트 및 함수에 대한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="78a3d-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="78a3d-141">Windows PowerShell의 많은 스크립트 및 함수에는 도움말 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="78a3d-142">Get-Help cmdlet을 사용하여 스크립트 및 함수에 대한 도움말 항목을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="78a3d-143">함수에 대한 도움말을 표시하려면 "get-help"를 입력한 다음 함수 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="78a3d-144">예를 들어 Disable-PSRemoting 함수에 대한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="78a3d-145">스크립트에 대한 도움말을 표시하려면 스크립트 파일의 정규화된 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="78a3d-146">스크립트가 Path 환경 변수에 표시된 경로에 있으면 명령에서 경로를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="78a3d-147">예를 들어 C:\\PS-Test 디렉터리에 "TestScript.ps1"이라는 스크립트가 있는 경우 이 스크립트의 도움말 항목을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="78a3d-148">*Detailed*, *Full*, *Examples* 및 *Parameter*와 같이 cmdlet 도움말을 표시하도록 설계된 매개 변수는 스크립트 도움말 및 함수 도움말에서도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="78a3d-149">그러나 "get-help \*"를 입력하여 모든 도움말을 표시할 때는 함수 및 스크립트에 대한 도움말이 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="78a3d-150">함수 및 스크립트에 대한 도움말 항목을 작성하는 방법에 대한 자세한 내용은 [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) 및 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78a3d-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="78a3d-151">온라인 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="78a3d-151">Getting Help Online</span></span>
<span data-ttu-id="78a3d-152">인터넷에 연결된 경우에는 온라인에서 도움말 항목을 보는 것이 가장 좋은 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="78a3d-153">온라인 항목은 업데이트하기 쉽기 때문에 최신 내용이 제공될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="78a3d-154">온라인 도움말을 보려면 Get-Help cmdlet의 *Online* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="78a3d-155">Get-Help cmdlet의 *Online* 매개 변수는 cmdlet 도움말, 함수 도움말 및 스크립트 도움말에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="78a3d-156">개념(About) 항목이나 공급자 도움말 항목에서는 *Online* 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="78a3d-157">또한 이 기능은 선택 항목이기 때문에 일부 cmdlet, 함수 또는 스크립트 도움말 항목에서는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="78a3d-158">그러나 공급자 도움말 및 개념(About) 도움말 항목을 포함하여 Windows PowerShell과 함께 제공되는 모든 도움말 항목은 Microsoft TechNet 라이브러리의 [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) 섹션에서 온라인으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="78a3d-159">Get-Help cmdlet의 *Online* 매개 변수를 사용하려면 다음 명령 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="78a3d-160">예를 들어 Get-ChildItem cmdlet에 대한 온라인 버전의 도움말 항목을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="78a3d-161">온라인 버전의 도움말 항목이 있는 경우 기본 브라우저에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="78a3d-162">도움말 항목에 대해 온라인 도움말이 지원되는 경우 도움말 항목의 인터넷 주소(URL)도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="78a3d-163">인터넷 주소는 도움말 항목의 관련 링크 섹션에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="78a3d-164">예를 들어 Add-Computer cmdlet의 온라인 버전에 대한 URL을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="78a3d-165">항목의 관련 링크 섹션에 있는 첫 번째 줄은 아래와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="78a3d-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="78a3d-166">도움말 항목의 온라인 지원을 제공하는 방법에 대한 자세한 내용은 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)와 MSDN 라이브러리의 [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415)(Cmdlet 도움말 작성 방법)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78a3d-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="78a3d-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78a3d-167">See Also</span></span>
- [<span data-ttu-id="78a3d-168">about_Functions [m2]</span><span class="sxs-lookup"><span data-stu-id="78a3d-168">about_Functions [m2]</span></span>](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [<span data-ttu-id="78a3d-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="78a3d-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="78a3d-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="78a3d-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [<span data-ttu-id="78a3d-171">Get-Help [m2]</span><span class="sxs-lookup"><span data-stu-id="78a3d-171">Get-Help [m2]</span></span>](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)

