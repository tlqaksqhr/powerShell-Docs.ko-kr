---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "친숙한 명령 이름 사용"
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 5e72e721bdb9d48684092344a0169907e7e25d40
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="5ee07-103">친숙한 명령 이름 사용</span><span class="sxs-lookup"><span data-stu-id="5ee07-103">Using Familiar Command Names</span></span>
<span data-ttu-id="5ee07-104">Windows PowerShell에서는 *별칭*이라고 하는 메커니즘을 사용하여 대체 이름으로 명령을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-104">Using a mechanism called *aliasing*, Windows PowerShell allows users to refer to commands by alternate names.</span></span> <span data-ttu-id="5ee07-105">별칭은 다른 셸을 사용해 본 경험이 있는 사용자가 이미 알고 있는 일반적인 명령 이름을 다시 사용하여 Windows PowerShell에서 유사한 작업을 수행할 수 있도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-105">Aliasing allows users with experience in other shells to reuse common command names that they already know to perform similar operations in Windows PowerShell.</span></span> <span data-ttu-id="5ee07-106">따라서 이 설명서에서 Windows PowerShell 별칭을 자세히 설명하지 않지만 Windows PowerShell 시작부터 이러한 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-106">Although we will not discuss Windows PowerShell aliases in detail, you can still use them as you get started with Windows PowerShell.</span></span>

<span data-ttu-id="5ee07-107">별칭은 사용자가 입력하는 명령 이름을 다른 명령과 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-107">Aliasing associates a command name that you type with another command.</span></span> <span data-ttu-id="5ee07-108">예를 들어 Windows PowerShell에는 출력 창을 지우는 **Clear-Host**라는 내부 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-108">For example, Windows PowerShell has an internal function named **Clear-Host** that clears the output window.</span></span> <span data-ttu-id="5ee07-109">명령 프롬프트에서 **cls** 또는 **clear** 명령을 입력하면 Windows PowerShell은 이러한 명령을 **Clear-Host** 함수의 별칭으로 해석하고 **Clear-Host** 함수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-109">If you type either the **cls** or **clear** command at a command prompt, Windows PowerShell interprets that this is an alias for the **Clear-Host** function and runs the **Clear-Host** function.</span></span>

<span data-ttu-id="5ee07-110">이 기능은 사용자가 Windows PowerShell을 익히는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-110">This feature helps users to learn Windows PowerShell.</span></span> <span data-ttu-id="5ee07-111">첫째, 대부분의 Cmd.exe 및 UNIX 사용자는 많은 명령의 이름을 이미 알고 있기 때문에, Windows PowerShell에서 이러한 명령이 동일한 결과를 나타내지는 않더라도 그 형태가 유사하여 따로 이름을 외우지 않아도 Windows PowerShell 명령을 사용하여 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-111">First, most Cmd.exe and UNIX users have a large repertoire of commands that users already know by name, and although the Windows PowerShell equivalents may not produce identical results, they are close enough in form that users can use them to do work without having to first memorize the Windows PowerShell names.</span></span> <span data-ttu-id="5ee07-112">둘째, 다른 셸에 이미 익숙한 사용자가 새 셸을 익히는 데 있어서 가장 어려운 점은 손에 익은 습관 때문에 발생하는 실수입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-112">Second, the major source of frustration in learning a new shell when the user is already familiar with another shell, is the errors that are caused by "finger memory".</span></span> <span data-ttu-id="5ee07-113">예를 들어 Cmd.exe를 몇 년 동안 사용한 사용자의 경우 화면에 표시된 출력 내용을 모두 지우고자 할 때 반사적으로 **cls** 명령을 입력한 다음 Enter 키를 누를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-113">If you have used Cmd.exe for years, when you have a screen full of output and want to clean it up, you would reflexively type the **cls** command and press the ENTER key.</span></span> <span data-ttu-id="5ee07-114">Windows PowerShell에 **Clear-Host** 함수에 대한 별칭이 없다면 "**'cls' is not recognized as a cmdlet, function, operable program, or script file.**"이라는 오류 메시지만 표시되고,</span><span class="sxs-lookup"><span data-stu-id="5ee07-114">Without the alias to the **Clear-Host** function in Windows PowerShell, you would simply get the error message "**'cls' is not recognized as a cmdlet, function, operable program, or script file.**"</span></span> <span data-ttu-id="5ee07-115">출력 내용을 어떻게 지울 수 있는지에 대한 어떠한 정보도 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-115">and be left with no idea of what to do to clear the output.</span></span>

<span data-ttu-id="5ee07-116">다음은 Windows PowerShell에서 사용할 수 있는 일반적인 Cmd.exe 및 UNIX 명령에 대한 간단한 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-116">The following is a brief listing of the common Cmd.exe and UNIX commands that you can use inside Windows PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="5ee07-117">cat</span><span class="sxs-lookup"><span data-stu-id="5ee07-117">cat</span></span>|<span data-ttu-id="5ee07-118">dir</span><span class="sxs-lookup"><span data-stu-id="5ee07-118">dir</span></span>|<span data-ttu-id="5ee07-119">탑재</span><span class="sxs-lookup"><span data-stu-id="5ee07-119">mount</span></span>|<span data-ttu-id="5ee07-120">rm</span><span class="sxs-lookup"><span data-stu-id="5ee07-120">rm</span></span>|
|<span data-ttu-id="5ee07-121">cd</span><span class="sxs-lookup"><span data-stu-id="5ee07-121">cd</span></span>|<span data-ttu-id="5ee07-122">echo</span><span class="sxs-lookup"><span data-stu-id="5ee07-122">echo</span></span>|<span data-ttu-id="5ee07-123">move</span><span class="sxs-lookup"><span data-stu-id="5ee07-123">move</span></span>|<span data-ttu-id="5ee07-124">rmdir</span><span class="sxs-lookup"><span data-stu-id="5ee07-124">rmdir</span></span>|
|<span data-ttu-id="5ee07-125">chdir</span><span class="sxs-lookup"><span data-stu-id="5ee07-125">chdir</span></span>|<span data-ttu-id="5ee07-126">erase</span><span class="sxs-lookup"><span data-stu-id="5ee07-126">erase</span></span>|<span data-ttu-id="5ee07-127">popd</span><span class="sxs-lookup"><span data-stu-id="5ee07-127">popd</span></span>|<span data-ttu-id="5ee07-128">sleep</span><span class="sxs-lookup"><span data-stu-id="5ee07-128">sleep</span></span>|
|<span data-ttu-id="5ee07-129">clear</span><span class="sxs-lookup"><span data-stu-id="5ee07-129">clear</span></span>|<span data-ttu-id="5ee07-130">h</span><span class="sxs-lookup"><span data-stu-id="5ee07-130">h</span></span>|<span data-ttu-id="5ee07-131">ps</span><span class="sxs-lookup"><span data-stu-id="5ee07-131">ps</span></span>|<span data-ttu-id="5ee07-132">sort</span><span class="sxs-lookup"><span data-stu-id="5ee07-132">sort</span></span>|
|<span data-ttu-id="5ee07-133">cls</span><span class="sxs-lookup"><span data-stu-id="5ee07-133">cls</span></span>|<span data-ttu-id="5ee07-134">history</span><span class="sxs-lookup"><span data-stu-id="5ee07-134">history</span></span>|<span data-ttu-id="5ee07-135">pushd</span><span class="sxs-lookup"><span data-stu-id="5ee07-135">pushd</span></span>|<span data-ttu-id="5ee07-136">tee</span><span class="sxs-lookup"><span data-stu-id="5ee07-136">tee</span></span>|
|<span data-ttu-id="5ee07-137">copy</span><span class="sxs-lookup"><span data-stu-id="5ee07-137">copy</span></span>|<span data-ttu-id="5ee07-138">kill</span><span class="sxs-lookup"><span data-stu-id="5ee07-138">kill</span></span>|<span data-ttu-id="5ee07-139">pwd</span><span class="sxs-lookup"><span data-stu-id="5ee07-139">pwd</span></span>|<span data-ttu-id="5ee07-140">형식</span><span class="sxs-lookup"><span data-stu-id="5ee07-140">type</span></span>|
|<span data-ttu-id="5ee07-141">del</span><span class="sxs-lookup"><span data-stu-id="5ee07-141">del</span></span>|<span data-ttu-id="5ee07-142">lp</span><span class="sxs-lookup"><span data-stu-id="5ee07-142">lp</span></span>|<span data-ttu-id="5ee07-143">r</span><span class="sxs-lookup"><span data-stu-id="5ee07-143">r</span></span>|<span data-ttu-id="5ee07-144">write</span><span class="sxs-lookup"><span data-stu-id="5ee07-144">write</span></span>|
|<span data-ttu-id="5ee07-145">diff</span><span class="sxs-lookup"><span data-stu-id="5ee07-145">diff</span></span>|<span data-ttu-id="5ee07-146">ls</span><span class="sxs-lookup"><span data-stu-id="5ee07-146">ls</span></span>|<span data-ttu-id="5ee07-147">ren</span><span class="sxs-lookup"><span data-stu-id="5ee07-147">ren</span></span>||

<span data-ttu-id="5ee07-148">사용자 자신이 이러한 명령 중 하나를 반사적으로 사용하고 있음을 알아채고 기본 Windows PowerShell 명령의 실제 이름을 확인하려면 다음과 같이 **Get-Alias** 명령을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-148">If you find yourself using one of these commands reflexively and want to learn the real name of the native Windows PowerShell command, you can use the **Get-Alias** command:</span></span>

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

<span data-ttu-id="5ee07-149">일반적으로 이 Windows PowerShell 사용자 가이드에서는 읽기 쉽도록 예제에 별칭을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-149">To make examples more readable, the Windows PowerShell User's Guide generally avoids using aliases.</span></span> <span data-ttu-id="5ee07-150">그러나 별칭을 많이 알고 있으면 다른 곳에서 가져온 임의의 Windows PowerShell 코드 조각을 사용하여 작업하는 경우나 사용자 고유의 별칭을 정의하려는 경우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-150">However, knowing more about aliases this early can still be useful if you are working with arbitrary snippets of Windows PowerShell code from another source or want to define your own aliases.</span></span> <span data-ttu-id="5ee07-151">이 섹션의 나머지 부분에서는 표준 별칭과 사용자 고유의 별칭을 정의하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-151">The rest of this section will discuss standard aliases and how to define your own aliases.</span></span>

### <a name="interpreting-standard-aliases"></a><span data-ttu-id="5ee07-152">표준 별칭 해석</span><span class="sxs-lookup"><span data-stu-id="5ee07-152">Interpreting Standard Aliases</span></span>
<span data-ttu-id="5ee07-153">위에서 설명한 별칭은 다른 인터페이스와의 이름 호환성을 위해 개발된 반면 Windows PowerShell에 기본 제공된 별칭은 주로 명령 이름을 간략하게 표현하기 위해 개발되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-153">Unlike the aliases described above, which were designed for name-compatibility with other interfaces, the aliases built into Windows PowerShell are generally designed for brevity.</span></span> <span data-ttu-id="5ee07-154">이러한 약식 이름은 빨리 입력할 수는 있지만 참조 대상을 모르면 해석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-154">These shorter names can be typed quickly, but are impossible to read if you do not know what they refer to.</span></span>

<span data-ttu-id="5ee07-155">Windows PowerShell에서는 일반적인 동사와 명사에 대한 약식 이름을 기반으로 하는 일련의 표준 별칭을 제공하여 명확하면서도 간결한 별칭을 만들기 때문에</span><span class="sxs-lookup"><span data-stu-id="5ee07-155">Windows PowerShell tries to compromise between clarity and brevity by providing a set of standard aliases that are based on shorthand names for common verbs and nouns.</span></span> <span data-ttu-id="5ee07-156">약식 이름만 알면 해석할 수 있는 일반적인 cmdlet에 대한 핵심 별칭 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-156">This allows a core set of aliases for common cmdlets that are readable when you know the shorthand names.</span></span> <span data-ttu-id="5ee07-157">예를 들어 표준 별칭에서 동사 **Get**은 **g**로, 동사 **Set**은 **s**로, 명사 **Item**은 **i**로, 명사 **Location**은 **l**로, 명사 Command는 **cm**으로 축약됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-157">For example, in standard aliases the verb **Get** is abbreviated to **g**, the verb **Set** is abbreviated to **s**, the noun **Item** is abbreviated to **i**, the noun **Location** is abbreviated to **l**, and the noun Command is abbreviated to **cm**.</span></span>

<span data-ttu-id="5ee07-158">다음은 이러한 방식으로 별칭을 만드는 방법을 보여 주는 간단한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-158">Here is a brief example to illustrate how this works.</span></span> <span data-ttu-id="5ee07-159">Get-Item의 표준 별칭은 Get을 나타내는 **g**와 Item을 나타내는 **i**를 결합한 **gi**입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-159">The standard alias for Get-Item comes from combining **g** for Get and **i** for Item: **gi**.</span></span> <span data-ttu-id="5ee07-160">Set-Item의 표준 별칭은 Set을 나타내는 **s**와 Item을 나타내는 **i**를 결합한 **si**입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-160">The standard alias for Set-Item comes from combining **s** for Set and **i** for Item: **si**.</span></span> <span data-ttu-id="5ee07-161">Get-Location의 표준 별칭은 Get을 나타내는 **g**와 Location을 나타내는 **l**을 결합한 **gl**입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-161">The standard alias for Get-Location comes from combining **g** for Get and **l** for Location, **gl**.</span></span> <span data-ttu-id="5ee07-162">Set-Location의 표준 별칭은 Set을 나타내는 **s**와 Location을 나타내는 **l**을 결합한 **sl**입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-162">The standard alias for Set-Location comes from combining **s** for Set and **l** for Location, **sl**.</span></span> <span data-ttu-id="5ee07-163">Get-Command의 표준 별칭은 Get을 나타내는 **g**와 Command를 나타내는 **cm**을 결합한 **gcm**입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-163">The standard alias for Get-Command comes from combining **g** for Get and **cm** for Command, **gcm**.</span></span> <span data-ttu-id="5ee07-164">Set-Command cmdlet은 실제로 없지만 있다고 가정할 경우 표준 별칭은 Set을 나타내는 **s**와 Command를 나타내는 **cm**을 결합한 **scm**입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-164">There is no Set-Command cmdlet, but if there were, we would be able to guess that the standard alias comes from **s** for Set and **cm** for Command: **scm**.</span></span> <span data-ttu-id="5ee07-165">또한 Windows PowerShell 별칭에 익숙한 사용자는 **scm**을 보면 이 별칭이 Set-Command를 나타낸다는 것을 짐작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-165">Furthermore, people familiar with Windows PowerShell aliasing who encounter **scm** would be able to guess that the alias refers to Set-Command.</span></span>

### <a name="creating-new-aliases"></a><span data-ttu-id="5ee07-166">새 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="5ee07-166">Creating New Aliases</span></span>
<span data-ttu-id="5ee07-167">Set-Alias cmdlet을 사용하여 사용자 고유의 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-167">You can create your own aliases using the Set-Alias cmdlet.</span></span> <span data-ttu-id="5ee07-168">예를 들어 다음 문은 표준 별칭 해석에서 설명한 표준 cmdlet 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-168">For example, the following statements create the standard cmdlet aliases discussed in Interpreting Standard Aliases:</span></span>

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="5ee07-169">내부적으로 Windows PowerShell은 시작할 때 이와 같은 명령을 사용하지만 이러한 별칭은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-169">Internally, Windows PowerShell uses commands like these during startup, but these aliases are not changeable.</span></span> <span data-ttu-id="5ee07-170">실제로 이러한 명령 중 하나를 실행하려고 하면 다음과 같이 별칭을 수정할 수 없다는 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5ee07-170">If you attempt to actually execute one of these commands, you will get an error explaining that the alias cannot be modified.</span></span> <span data-ttu-id="5ee07-171">예:</span><span class="sxs-lookup"><span data-stu-id="5ee07-171">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
