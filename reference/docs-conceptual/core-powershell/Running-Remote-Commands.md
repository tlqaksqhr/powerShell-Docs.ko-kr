---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "원격 명령 실행"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: c3bf002e7a3daa5afc8219dd846145808eef3c9b
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="f3a9e-103">원격 명령 실행</span><span class="sxs-lookup"><span data-stu-id="f3a9e-103">Running Remote Commands</span></span>
<span data-ttu-id="f3a9e-104">단일 Windows PowerShell 명령으로 한 대 이상의 컴퓨터에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="f3a9e-105">Windows PowerShell에서는 WMI, RPC, WS-Management 등과 같은 다양한 기술을 사용하여 원격 컴퓨팅을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="f3a9e-106">구성 없이 원격 작업</span><span class="sxs-lookup"><span data-stu-id="f3a9e-106">Remoting Without Configuration</span></span>
<span data-ttu-id="f3a9e-107">많은 Windows PowerShell cmdlet에서는 데이터를 수집하고 하나 이상의 원격 컴퓨터에서 설정을 변경할 수 있는 ComputerName 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="f3a9e-108">이러한 cmdlet은 다양한 통신 기술을 사용하고 대부분은 특별한 구성 없이도 Windows PowerShell에서 지원하는 모든 Windows 운영 체제에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="f3a9e-109">이러한 cmdlet은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-109">These cmdlets include:</span></span>

- [<span data-ttu-id="f3a9e-110">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="f3a9e-110">Restart-Computer</span></span>](https://technet.microsoft.com/en-us/library/dd315301.aspx)

- [<span data-ttu-id="f3a9e-111">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="f3a9e-111">Test-Connection</span></span>](https://technet.microsoft.com/en-us/library/dd315259.aspx)

- [<span data-ttu-id="f3a9e-112">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="f3a9e-112">Clear-EventLog</span></span>](https://technet.microsoft.com/en-us/library/dd347552.aspx)

- [<span data-ttu-id="f3a9e-113">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="f3a9e-113">Get-EventLog</span></span>](https://technet.microsoft.com/en-us/library/dd315250.aspx)

- [<span data-ttu-id="f3a9e-114">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="f3a9e-114">Get-HotFix</span></span>](https://technet.microsoft.com/en-us/library/e1ef636f-5170-4675-b564-199d9ef6f101)

 -   [<span data-ttu-id="f3a9e-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="f3a9e-115">Get-Process</span></span>](https://technet.microsoft.com/en-us/library/dd347630.aspx)

- [<span data-ttu-id="f3a9e-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="f3a9e-116">Get-Service</span></span>](https://technet.microsoft.com/en-us/library/dd347591.aspx)

- [<span data-ttu-id="f3a9e-117">Set-Service</span><span class="sxs-lookup"><span data-stu-id="f3a9e-117">Set-Service</span></span>](https://technet.microsoft.com/en-us/library/dd315324.aspx)

- [<span data-ttu-id="f3a9e-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="f3a9e-118">Get-WinEvent</span></span>](https://technet.microsoft.com/en-us/library/dd315358.aspx)

- [<span data-ttu-id="f3a9e-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="f3a9e-119">Get-WmiObject</span></span>](https://technet.microsoft.com/en-us/library/dd315295.aspx)

<span data-ttu-id="f3a9e-120">일반적으로 특별한 구성 없이 원격 작업을 지원하는 cmdlet에는 ComputerName 매개 변수는 있지만 Session 매개 변수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="f3a9e-121">세션에서 이러한 cmdlet을 찾으려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="f3a9e-122">Windows PowerShell 원격 작업</span><span class="sxs-lookup"><span data-stu-id="f3a9e-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="f3a9e-123">WS-Management 프로토콜을 사용하는 Windows PowerShell 원격 작업을 이용하면 한 대 이상의 원격 컴퓨터에서 Windows PowerShell 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="f3a9e-124">또한 여러 컴퓨터에서 영구 연결을 설정하고, 1:1 대화형 세션을 시작하고, 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="f3a9e-125">Windows PowerShell 원격 작업을 사용하려면 원격 관리를 위해 원격 컴퓨터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="f3a9e-126">자세한 내용과 지침은 [원격 요구 사항 정보](https://technet.microsoft.com/en-us/library/dd315349.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="f3a9e-127">Windows PowerShell 원격 작업을 구성한 후 다양한 원격 전략을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="f3a9e-128">이 문서의 나머지 부분에서 일부 원격 전략을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="f3a9e-129">자세한 내용은 [원격 정보](https://technet.microsoft.com/en-us/library/dd347744.aspx) 및 [원격 FAQ 정보](https://technet.microsoft.com/en-us/library/dd347744.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="f3a9e-130">대화형 세션 시작</span><span class="sxs-lookup"><span data-stu-id="f3a9e-130">Start an Interactive Session</span></span>
<span data-ttu-id="f3a9e-131">단일 원격 컴퓨터와 대화형 세션을 시작하려면 [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) cmdlet.</span></span> <span data-ttu-id="f3a9e-132">예를 들어 Server01 원격 컴퓨터와 대화형 세션을 시작하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="f3a9e-133">명령 프롬프트가 변경되어 연결된 컴퓨터의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="f3a9e-134">이제부터 프롬프트에 입력하는 명령이 원격 컴퓨터에서 실행되고 그 결과가 로컬 컴퓨터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="f3a9e-135">대화형 세션을 종료하려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="f3a9e-136">Enter-PSSession 및 Exit-PSSession cmdlet에 대한 자세한 내용은 [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) 및 [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) and [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="f3a9e-137">원격 명령 실행</span><span class="sxs-lookup"><span data-stu-id="f3a9e-137">Run a Remote Command</span></span>
<span data-ttu-id="f3a9e-138">한 대 이상의 원격 컴퓨터에서 명령을 실행하려면 [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-138">To run any command on one or many remote computers, use the [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx) cmdlet.</span></span>
<span data-ttu-id="f3a9e-139">예를 들어 Server01 및 Server02 원격 컴퓨터에서 [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) 명령을 실행하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-139">For example, to run a [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="f3a9e-140">출력은 사용자의 컴퓨터에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="f3a9e-141">Invoke-Command cmdlet에 대한 자세한 내용은 [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="f3a9e-142">스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="f3a9e-142">Run a Script</span></span>
<span data-ttu-id="f3a9e-143">한 대 이상의 원격 컴퓨터에서 스크립트를 실행하려면 Invoke-Command cmdlet의 FilePath 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="f3a9e-144">스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="f3a9e-145">결과는 로컬 컴퓨터에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="f3a9e-146">예를 들어 다음 명령은 Server01 및 Server02 원격 컴퓨터에서 DiskCollect.ps1 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="f3a9e-147">Invoke-Command cmdlet에 대한 자세한 내용은 [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="f3a9e-148">영구 연결 설정</span><span class="sxs-lookup"><span data-stu-id="f3a9e-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="f3a9e-149">데이터를 공유하는 일련의 관련 명령을 실행하려면 원격 컴퓨터에서 세션을 만든 다음 Invoke-Command cmdlet을 사용하여 해당 세션에서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="f3a9e-150">원격 세션을 만들려면 New-PSSession cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="f3a9e-151">예를 들어 다음 명령은 Server01 컴퓨터에서 원격 세션을 만들고 Server02 컴퓨터에서 다른 원격 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="f3a9e-152">이 명령은 세션 개체를 $s 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="f3a9e-153">세션을 설정했으므로 이제 해당 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="f3a9e-154">세션이 영구 세션이므로 명령을 실행하여 데이터를 수집하고 후속 명령에서 해당 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="f3a9e-155">예를 들어 다음 명령은 $s 변수의 세션에서 Get-Hotfix 명령을 실행하고 결과를 $h 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="f3a9e-156">$h 변수는 $s의 각 세션에서 생성되지만 로컬 세션에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="f3a9e-157">이제 다음과 같이 후속 명령의 $h 변수에서 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="f3a9e-158">결과는 로컬 컴퓨터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="f3a9e-159">고급 원격 작업</span><span class="sxs-lookup"><span data-stu-id="f3a9e-159">Advanced Remoting</span></span>
<span data-ttu-id="f3a9e-160">Windows PowerShell 원격 관리가 여기에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="f3a9e-161">Windows PowerShell과 함께 설치되는 cmdlet을 사용하여 로컬 끝점과 원격 끝점 모두에서 원격 세션을 설정하여 구성하고, 사용자 지정되고 제한된 세션을 만들고, 사용자가 원격 세션에서 암시적으로 실행되는 명령을 원격 세션에서 가져오도록 허용하고, 원격 세션의 보안을 구성하는 등과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="f3a9e-162">원격 구성을 쉽게 설정할 수 있도록 Windows PowerShell에는 WSMan 공급자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="f3a9e-163">공급자가 만드는 WSMAN: 드라이브를 사용하여 로컬 컴퓨터와 원격 컴퓨터에서 구성 설정 계층을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="f3a9e-164">WSMan 공급자에 대한 자세한 내용을 보려면 [WSMan 공급자](https://technet.microsoft.com/en-us/library/dd819476.aspx) 및 [WS-Management Cmdlet 정보](https://technet.microsoft.com/en-us/library/dd819481.aspx)를 참조하거나 Windows PowerShell 콘솔에서 "Get-Help wsman"을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="f3a9e-165">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-165">For more information, see:</span></span>
- [<span data-ttu-id="f3a9e-166">원격 FAQ 정보</span><span class="sxs-lookup"><span data-stu-id="f3a9e-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="f3a9e-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f3a9e-167">Register-PSSessionConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dd819496.aspx)
- <span data-ttu-id="f3a9e-168">[Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx).</span><span class="sxs-lookup"><span data-stu-id="f3a9e-168">[Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx).</span></span> 

<span data-ttu-id="f3a9e-169">원격 오류에 대한 도움이 필요한 경우 [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a9e-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3a9e-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3a9e-170">See Also</span></span>
- [<span data-ttu-id="f3a9e-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f3a9e-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="f3a9e-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="f3a9e-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="f3a9e-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="f3a9e-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="f3a9e-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="f3a9e-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="f3a9e-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="f3a9e-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="f3a9e-176">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f3a9e-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="f3a9e-177">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f3a9e-177">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
- [<span data-ttu-id="f3a9e-178">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="f3a9e-178">Import-PSSession</span></span>](https://technet.microsoft.com/en-us/library/048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
- [<span data-ttu-id="f3a9e-179">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f3a9e-179">New-PSSession</span></span>](https://technet.microsoft.com/en-us/library/59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
- [<span data-ttu-id="f3a9e-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f3a9e-180">Register-PSSessionConfiguration</span></span>](https://technet.microsoft.com/en-us/library/af68867a-d201-4b19-a1de-594015ed8a25)
- [<span data-ttu-id="f3a9e-181">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="f3a9e-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

