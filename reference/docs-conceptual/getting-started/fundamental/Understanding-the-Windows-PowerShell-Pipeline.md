---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 파이프라인 이해
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="26c67-103">Windows PowerShell 파이프라인 이해</span><span class="sxs-lookup"><span data-stu-id="26c67-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="26c67-104">파이프는 사실상 Windows PowerShell의 모든 영역에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="26c67-105">화면에 텍스트가 표시되어 있는 경우에도 Windows PowerShell은 명령 사이에 있는 텍스트를 파이프하는 대신</span><span class="sxs-lookup"><span data-stu-id="26c67-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="26c67-106">개체를 파이프합니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="26c67-107">파이프라인에 사용되는 표기법과 다른 셸에 사용되는 표기법이 유사하기 때문에 처음에는 Windows PowerShell에 새로 도입된 기능을 쉽게 확인하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="26c67-108">예를 들어 **Out-Host** cmdlet을 사용하여 다른 명령의 출력을 페이지 단위로 표시하면 다음과 같이 일반 텍스트가 페이지 단위로 나뉘어져 화면에 표시된 것처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="26c67-109">Out-Host -Paging 명령은 긴 출력을 천천히 표시하려는 경우에 유용한 파이프라인 요소로,</span><span class="sxs-lookup"><span data-stu-id="26c67-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="26c67-110">특히 CPU를 많이 사용하는 작업에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="26c67-111">Out-Host cmdlet이 전체 페이지를 표시할 준비가 되면 프로세스가 이 cmdlet에 전달되므로 파이프라인에서 이 cmdlet 앞에 있는 cmdlet은 다음 페이지를 출력할 수 있을 때까지 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="26c67-112">Windows 작업 관리자에서 Windows PowerShell이 사용하는 CPU와 메모리를 모니터링하면 이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="26c67-113">다음 명령을 실행합니다. **Get-ChildItem C:\\Windows -Recurse**.</span><span class="sxs-lookup"><span data-stu-id="26c67-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="26c67-114">CPU 및 메모리 사용량을 다음 명령과 비교합니다. **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span><span class="sxs-lookup"><span data-stu-id="26c67-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="26c67-115">화면에 텍스트가 표시되지만 이것은 개체를 콘솔 창에 텍스트로 표시해야 하기 때문이며</span><span class="sxs-lookup"><span data-stu-id="26c67-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="26c67-116">Windows PowerShell에서 실제로 진행되고 있는 작업을 보여 주기 위한 것일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="26c67-117">Get-Location cmdlet을 예로 들어 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="26c67-118">현재 위치가 C 드라이브의 루트일 때 **Get-Location**을 입력하면 다음과 같은 내용이 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="26c67-119">Windows PowerShell에서 파이프라인으로 결합한 **Get-Location | Out-Host**와 같은 명령을 실행하면 일련의 문자가 화면에 표시되는 순서대로 **Get-Location**에서 **Out-Host**로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="26c67-120">즉, 머리글 정보를 무시할 경우 **Out-Host**에 '**C'** 문자, '**:'** 문자 및 '**\\'** 문자가 차례로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="26c67-121">**Out-Host** cmdlet으로는 **Get-Location** cmdlet이 출력하는 문자에 연결된 의미를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="26c67-122">Windows PowerShell은 텍스트 대신 개체를 사용하여 파이프라인에 있는 명령과 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="26c67-123">사용자의 관점에서 볼 때 개체는 관련 정보를 하나의 단위로 쉽게 조작할 수 있는 형식으로 패키징하고 필요한 특정 항목을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="26c67-124">**Get-Location** 명령은 현재 경로가 포함된 텍스트를 반환하지 않고</span><span class="sxs-lookup"><span data-stu-id="26c67-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="26c67-125">현재 경로와 함께 몇 가지 다른 정보가 포함된 **PathInfo** 개체라는 정보 패키지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="26c67-126">그러면 **Out-Host** cmdlet이 이 **PathInfo** 개체를 화면에 보내고 Windows PowerShell은 형식 지정 규칙에 따라 표시할 정보와 이러한 정보의 표시 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="26c67-127">사실 **Get-Location** cmdlet이 출력하는 머리글 정보는 화면에 표시할 데이터의 형식을 지정하는 프로세스의 일부로 해당 프로세스의 끝에만 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="26c67-128">화면에는 출력 개체에 대한 전체 정보 대신 요약 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="26c67-129">Windows PowerShell 명령이 출력하는 정보가 콘솔 창에 표시되는 정보보다 많을 경우 콘솔 창에 표시되지 않는 요소를 검색하거나</span><span class="sxs-lookup"><span data-stu-id="26c67-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="26c67-130">추가 데이터를 표시할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="26c67-130">How do you view the extra data?</span></span> <span data-ttu-id="26c67-131">특정 Windows PowerShell이 일반적으로 사용하는 것과 다른 형식으로 데이터를 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="26c67-132">이 장의 나머지 부분에서는 특정 Windows PowerShell 개체의 구조를 검색하는 방법과 이러한 정보를 파일이나 프린터와 같은 다른 출력 위치로 보내는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="26c67-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>