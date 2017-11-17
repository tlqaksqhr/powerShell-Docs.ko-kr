---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "이전 버전의 Windows에서 Windows PowerShell 시작"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="54794-103">이전 버전의 Windows에서 Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="54794-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="54794-104">이 섹션에서는 Windows® 7, Windows Server® 2008 R2 및 Windows Server® 2008에서 Windows PowerShell 및 Windows PowerShell ISE(통합 스크립팅 환경)을 시작하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="54794-105">또한 Windows Server® 2008 R2 및 Windows Server® 2008의 Windows PowerShell 2.0에서 Windows PowerShell ISE에 대한 선택적 기능을 사용하도록 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="54794-106">지원되는 시스템에 Windows PowerShell 4.0을 설치하려면 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)을 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="54794-107">자세한 내용은 [Windows PowerShell 설치](Installing-Windows-PowerShell.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54794-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="54794-108">지원되는 시스템에 Windows PowerShell 3.0을 설치하려면 [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290)을 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="54794-109">자세한 내용은 [Windows PowerShell 설치](Installing-Windows-PowerShell.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54794-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="54794-110">이전 버전의 Windows에서 Windows PowerShell을 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="54794-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="54794-111">다음 방법 중 하나를 사용하여 Windows PowerShell 3.0 또는 Windows PowerShell 4.0의 설치된 버전을 시작합니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="54794-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="54794-112">시작 메뉴</span><span class="sxs-lookup"><span data-stu-id="54794-112">From the Start Menu</span></span>

- <span data-ttu-id="54794-113">**시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

- <span data-ttu-id="54794-114">**시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="54794-115">명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="54794-115">At the Command Prompt</span></span>

- <span data-ttu-id="54794-116">Cmd.exe, Windows PowerShell 또는 Windows PowerShell ISE에서 Windows PowerShell을 시작하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="54794-117">PowerShell.exe 프로그램의 매개 변수를 사용하여 세션을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54794-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="54794-118">자세한 내용은 [PowerShell.exe 명령줄 도움말](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54794-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="54794-119">관리자 권한("관리자 권한으로 실행")</span><span class="sxs-lookup"><span data-stu-id="54794-119">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="54794-120">**시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="54794-121">이전 릴리스의 Windows에서 Windows PowerShell ISE를 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="54794-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="54794-122">다음 방법 중 하나를 사용하여 Windows PowerShell ISE를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="54794-123">시작 메뉴</span><span class="sxs-lookup"><span data-stu-id="54794-123">From the Start Menu</span></span>

- <span data-ttu-id="54794-124">**시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

- <span data-ttu-id="54794-125">**시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell ISE**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="54794-126">명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="54794-126">At the Command Prompt</span></span>

- <span data-ttu-id="54794-127">Cmd.exe, Windows PowerShell 또는 Windows PowerShell ISE에서 Windows PowerShell을 시작하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="54794-128">또는</span><span class="sxs-lookup"><span data-stu-id="54794-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="54794-129">관리자 권한("관리자 권한으로 실행")</span><span class="sxs-lookup"><span data-stu-id="54794-129">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="54794-130">**시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="54794-131">이전 릴리스의 Windows에서 Windows PowerShell ISE를 사용하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="54794-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="54794-132">Windows PowerShell 4.0 및 Windows PowerShell 3.0의 경우 모든 버전의 Windows에서 Windows PowerShell ISE가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="54794-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="54794-133">아직 사용되지 않는 경우 Windows Management Framework 4.0 또는 Windows Management Framework 3.0에서 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="54794-134">Windows PowerShell 2.0의 경우 Windows 7에서는 Windows PowerShell ISE가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="54794-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="54794-135">그러나 Windows Server 2008 R2 및 Windows Server 2008에서는 선택적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="54794-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="54794-136">Windows Server 2008 R2 또는 Windows Server 2008의 Windows PowerShell 2.0에서 Windows PowerShell ISE를 사용하도록 설정하려면 다음 절차를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="54794-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="54794-137">Windows PowerShell ISE(통합 스크립팅 환경)를 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="54794-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="54794-138">서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-138">Start Server Manager.</span></span>

2. <span data-ttu-id="54794-139">**기능**을 클릭한 다음 **기능 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-139">Click **Features** and then click **Add Features**.</span></span>

3. <span data-ttu-id="54794-140">기능 선택에서 Windows PowerShell ISE(통합 스크립팅 환경)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54794-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

