---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "변수를 사용하여 개체 저장"
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="1b223-103">변수를 사용하여 개체 저장</span><span class="sxs-lookup"><span data-stu-id="1b223-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="1b223-104">PowerShell에서는 개체에 대한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-104">PowerShell works with objects.</span></span> <span data-ttu-id="1b223-105">PowerShell에서는 이름이 기본적으로 지정되는 개체인 변수를 만들어 출력을 나중에 사용하기 위해 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="1b223-106">다른 셸에서 변수에 대한 작업을 수행하는 데 익숙한 경우 PowerShell 변수는 텍스트가 아닌 개체라는 사실에 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="1b223-107">변수 이름은 항상 $ 문자로 시작되며 모든 영숫자 문자와 밑줄을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="1b223-108">변수 만들기</span><span class="sxs-lookup"><span data-stu-id="1b223-108">Creating a Variable</span></span>
<span data-ttu-id="1b223-109">변수를 만들려면 다음과 같이 유효한 변수 이름을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="1b223-110">이 경우 **$loc**에 지정된 값이 없기 때문에 아무 결과도 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="1b223-111">동일한 단계에서 변수를 만드는 작업과 변수에 값을 할당하는 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="1b223-112">PowerShell은 변수가 없으면 변수를 만들기만 하고, 변수가 있으면 기존 변수에 지정된 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="1b223-113">**$loc** 변수에 현재 위치를 저장하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="1b223-114">이 명령을 입력하면 출력이 $loc에 보내지기 때문에 아무 결과도 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="1b223-115">PowerShell에서 출력이 표시된다면 이는 달리 리디렉션되지 않은 데이터가 항상 화면에 표시되기 때문에 발생하는 의도하지 않은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="1b223-116">다음과 같이 $loc를 입력하면 현재 위치가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="1b223-117">**Get-Member**를 사용하여 변수의 내용에 대한 정보를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="1b223-118">다음과 같이 $loc를 Get-Member에 파이프하면 Get-Location을 입력한 것과 마찬가지로 변수에 **PathInfo** 개체가 포함되어 있는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="1b223-119">변수 조작</span><span class="sxs-lookup"><span data-stu-id="1b223-119">Manipulating Variables</span></span>
<span data-ttu-id="1b223-120">PowerShell에는 변수를 조작할 수 있는 여러 명령이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="1b223-121">다음과 같이 입력하면 이러한 명령의 전체 목록을 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="1b223-122">현재 PowerShell 세션에서 사용자가 직접 만든 변수 외에도 여러 시스템 정의 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="1b223-123">**Remove-Variable** cmdlet을 사용하여 PowerShell에서 제어하지 않는 모든 변수를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="1b223-124">다음 명령을 입력하면 모든 변수를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="1b223-125">이 경우 다음과 같은 확인 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="1b223-126">**Get-Variable** cmdlet을 실행하면 나머지 PowerShell 변수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="1b223-127">또한 변수 PowerShell 드라이브도 있으므로 다음과 같이 입력하면 모든 PowerShell 변수를 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="1b223-128">Cmd.exe 변수 사용</span><span class="sxs-lookup"><span data-stu-id="1b223-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="1b223-129">PowerShell은 Cmd.exe가 아니지만, 명령 셸 환경에서 실행되며 Windows 환경에서 사용할 수 있는 것과 동일한 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="1b223-130">이러한 변수는 **env**:라는 드라이브를 통해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="1b223-131">다음과 같이 입력하면 이러한 변수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="1b223-132">표준 변수 cmdlet은 원래 **env:** 변수와 함께 사용하도록 설계되지 않았지만 **env:** 접두사를 지정하여 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="1b223-133">예를 들어 운영 체제 루트 디렉터리를 보려면 다음과 같이 입력하여 PowerShell에서 명령 셸 **%SystemRoot%** 변수를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="1b223-134">또한 PowerShell에서 환경 변수를 만들고 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="1b223-135">Windows PowerShell에서 액세스하는 환경 변수는 다른 Windows 환경 변수에 대한 일반적인 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="1b223-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>

