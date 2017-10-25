---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "명령에 대한 정보 가져오기"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="c61ed-103">명령에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="c61ed-103">Getting Information About Commands</span></span>
<span data-ttu-id="c61ed-104">Windows PowerShell **Get-Command** cmdlet은 현재 세션에서 사용할 수 있는 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="c61ed-105">Windows PowerShell 프롬프트에 **Get-Command**를 입력할 경우 다음과 비슷한 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="c61ed-106">이 출력은 내부 명령을 표 형식으로 요약하는 Cmd.exe의 도움말 출력과 흡사합니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="c61ed-107">위에 표시된 **Get-Command** 명령 출력의 발췌 부분에서 표시되는 모든 명령의 CommandType은 Cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="c61ed-108">cmdlet은 Windows PowerShell의 고유한 명령 유형으로, Cmd.exe의 **dir** 및 **cd** 명령과 거의 일치하고 UNIX 셸(예: BASH)에 기본 제공되는 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="c61ed-109">**Get-Command** 명령의 출력에서는 모든 정의를 줄임표(...)로 끝내서 PowerShell에서 사용 가능한 공간에 내용을 모두 표시할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="c61ed-110">Windows PowerShell에서는 출력을 표시할 때 출력 형식을 텍스트로 지정한 다음 데이터가 창에 맞도록 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="c61ed-111">이에 대해서는 나중에 포맷터 섹션에서 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="c61ed-112">**Get-Command** cmdlet에는 각 cmdlet의 구문을 가져오는 **Syntax** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="c61ed-113">Get-Help cmdlet의 구문을 가져오려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="c61ed-114">**Get-Command Get-Help -Syntax**</span><span class="sxs-lookup"><span data-stu-id="c61ed-114">**Get-Command Get-Help -Syntax**</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="c61ed-115">사용 가능한 명령 유형 표시</span><span class="sxs-lookup"><span data-stu-id="c61ed-115">Displaying Available Command Types</span></span>
<span data-ttu-id="c61ed-116">**Get-Command** 명령은 Windows PowerShell에서 사용할 수 있는 명령을 모두 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="c61ed-117">대신 **Get-Command** 명령은 현재 세션에 있는 cmdlet만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="c61ed-118">Windows PowerShell에서는 실제로 다양한 유형의 명령을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="c61ed-119">별칭, 함수, 스크립트 등은 Windows PowerShell 사용자 가이드에서 자세히 설명하지 않지만 Windows PowerShell 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="c61ed-120">실행할 수 있거나 등록된 파일 형식 처리기가 있는 외부 파일도 명령으로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="c61ed-121">세션의 모든 명령을 가져오려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="c61ed-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="c61ed-122">이 목록에는 검색 경로에 있는 외부 파일이 포함되므로 수천 개의 항목이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="c61ed-123">찾을 명령의 수를 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="c61ed-124">다른 형식의 네이티브 명령을 가져오려면 **Get-Command** cmdlet의 **CommandType** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c61ed-125">별표(\*)는 Windows PowerShell 명령 인수에서 와일드카드 일치에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="c61ed-126">\*는 "하나 이상의 문자 일치"를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="c61ed-127">문자 "a"로 시작하는 모든 명령을 찾으려면 **Get-Command a\&#42;**를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="c61ed-128">Cmd.exe의 와일드카드 일치와 달리 Windows PowerShell의 와일드카드는 점(.)도 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c61ed-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="c61ed-129">명령에 할당된 애칭인 명령 별칭을 가져오려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="c61ed-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="c61ed-130">현재 세션의 함수를 가져오려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="c61ed-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="c61ed-131">Windows PowerShell의 검색 경로에 스크립트를 표시하려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="c61ed-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```

