---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 웹 액세스 설치 및 사용"
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
#  <a name="install-and-use-windows-powershell-web-access"></a><span data-ttu-id="318a4-103">Install and Use Windows PowerShell Web Access(Windows PowerShell 웹 액세스 설치 및 사용)</span><span class="sxs-lookup"><span data-stu-id="318a4-103">Install and Use Windows PowerShell Web Access</span></span>

<span data-ttu-id="318a4-104">업데이트됨: 2013년 11월 5일</span><span class="sxs-lookup"><span data-stu-id="318a4-104">Updated: November 5, 2013</span></span>

<span data-ttu-id="318a4-105">적용 대상: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="318a4-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="318a4-106">Windows PowerShell® 웹 액세스는 Windows Server® 2012에 처음 도입되었고 Windows PowerShell 게이트웨이로 사용되며 원격 컴퓨터를 대상으로 하는 웹 기반 Windows PowerShell 콘솔을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-106">Windows PowerShell® Web Access, first introduced in Windows Server® 2012, acts as a Windows PowerShell gateway, providing a web-based Windows PowerShell console that is targeted at a remote computer.</span></span> <span data-ttu-id="318a4-107">이 기능을 사용하면 IT 전문가가 클라이언트 장치에 Windows PowerShell, 원격 관리 소프트웨어 또는 브라우저 플러그 인을 설치하지 않고도 웹 브라우저의 Windows PowerShell 콘솔에서 Windows PowerShell 명령과 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-107">It enables IT Pros to run Windows PowerShell commands and scripts from a Windows PowerShell console in a web browser, with no Windows PowerShell, remote management software, or browser plug-in installation necessary on the client device.</span></span> <span data-ttu-id="318a4-108">웹 기반 Windows PowerShell 콘솔을 실행하려면 올바르게 구성된 Windows PowerShell 웹 액세스 게이트웨이와 JavaScript®를 지원하고 쿠키를 적용하는 클라이언트 장치 브라우저만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-108">All that is required to run the web-based Windows PowerShell console is a properly-configured Windows PowerShell Web Access gateway, and a client device browser that supports JavaScript® and accepts cookies.</span></span>

<span data-ttu-id="318a4-109">클라이언트 장치에는 랩톱, 정지 상태의 개인 컴퓨터, 대여된 컴퓨터, 태블릿 컴퓨터, 웹 키오스크, Windows 기반 운영 체제를 실행 중인 컴퓨터 및 이동 전화 브라우저 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-109">Examples of client devices include laptops, non-work personal computers, borrowed computers, tablet computers, web kiosks, computers that are not running a Windows-based operating system, and cell phone browsers.</span></span> <span data-ttu-id="318a4-110">IT 전문가는 인터넷 연결과 웹 브라우저에 대한 권한을 지닌 장치에서 원격 Windows 기반 서버의 주요 관리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-110">IT Pros can perform critical management tasks on remote Windows-based servers from devices that have access to an Internet connection and a web browser.</span></span>

<span data-ttu-id="318a4-111">사용자는 게이트웨이를 설치 및 구성하고 나서 웹 브라우저를 사용하여 Windows PowerShell 콘솔에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-111">After successful gateway setup and configuration, users can access a Windows PowerShell console by using a web browser.</span></span> <span data-ttu-id="318a4-112">사용자가 안전한 Windows PowerShell 웹 액세스 웹 사이트를 열면 인증을 거친 후 웹 기반 Windows PowerShell 콘솔을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-112">When users open the secured Windows PowerShell Web Access website, they can run a web-based Windows PowerShell console after successful authentication.</span></span>

<span data-ttu-id="318a4-113">Windows PowerShell 웹 액세스 설치 및 구성은 다음의 세 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-113">Windows PowerShell Web Access setup and configuration is a three-step process:</span></span>

1.  <span data-ttu-id="318a4-114">Windows PowerShell 웹 액세스 설치</span><span class="sxs-lookup"><span data-stu-id="318a4-114">Installing Windows PowerShell Web Access</span></span>

2.  <span data-ttu-id="318a4-115">게이트웨이 구성</span><span class="sxs-lookup"><span data-stu-id="318a4-115">Configuring the gateway</span></span>

3.  <span data-ttu-id="318a4-116">사용자가 웹 기반 Windows PowerShell 콘솔에 액세스하도록 허용하는 권한 부여 규칙 구성</span><span class="sxs-lookup"><span data-stu-id="318a4-116">Configuring authorization rules that allow users access to the web-based Windows PowerShell console</span></span>

<span data-ttu-id="318a4-117">Windows PowerShell 웹 액세스를 설치 및 구성하기 전에 Windows PowerShell 웹 액세스를 설치, 보호 및 제거하는 방법에 대한 지침이 포함된 이 전체 가이드를 읽는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-117">Before you install and configure Windows PowerShell Web Access, we recommend that you read this entire guide, which includes instructions about how to install, secure, and uninstall Windows PowerShell Web Access.</span></span> <span data-ttu-id="318a4-118">[웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) 항목에서는 사용자가 웹 기반 콘솔에 로그인하는 방법을 설명하고 웹 기반 Windows PowerShell 콘솔과 **powershell.exe** 콘솔 간의 제한 사항과 차이점을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-118">The [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) topic describes how users sign in to the web-based console, and covers limitations and differences between the web-based Windows PowerShell console and the **powershell.exe** console.</span></span> <span data-ttu-id="318a4-119">웹 기반 콘솔의 최종 사용자라면 [웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)을 읽어야 하지만, 이 가이드의 나머지 부분은 읽을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-119">End users of the web-based console should read [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), but do not need to read the rest of this guide.</span></span>

<span data-ttu-id="318a4-120">이 항목에서는 심층 웹 서버(IIS) 작업 지침을 제공하지 않으며, 이 항목에 설명된 Windows PowerShell 웹 액세스 게이트웨이를 구성하는 데 필요한 단계만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-120">This topic does not provide in-depth Web Server (IIS) operations guidance; only those steps required to configure the Windows PowerShell Web Access gateway are described in this topic.</span></span> <span data-ttu-id="318a4-121">IIS에서의 웹 사이트 구성 및 보안에 대한 자세한 내용은 참고 항목 섹션의 IIS 설명서 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-121">For more information about configuring and securing websites in IIS, see the IIS documentation resources in the See Also section.</span></span>

<span data-ttu-id="318a4-122">다음 그림에는 Windows PowerShell 웹 액세스 작동 방식이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-122">The following diagram shows how Windows PowerShell Web Access works.</span></span>

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

<span data-ttu-id="318a4-123">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="318a4-123">In this topic:</span></span>

-   [<span data-ttu-id="318a4-124">Windows PowerShell 웹 액세스 실행에 필요한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="318a4-124">Requirements for running Windows PowerShell Web Access</span></span>](#BKMK_reqs)

-   [<span data-ttu-id="318a4-125">브라우저 및 클라이언트 장치 지원</span><span class="sxs-lookup"><span data-stu-id="318a4-125">Browser and client device support</span></span>](#BKMK_browser)

-   [<span data-ttu-id="318a4-126">권장(빠른) 배포</span><span class="sxs-lookup"><span data-stu-id="318a4-126">Recommended (quick) deployment</span></span>](#BKMK_recm)

-   [<span data-ttu-id="318a4-127">사용자 지정 배포</span><span class="sxs-lookup"><span data-stu-id="318a4-127">Custom deployment</span></span>](#BKMK_custom)

-   [<span data-ttu-id="318a4-128">정품 인증서 구성</span><span class="sxs-lookup"><span data-stu-id="318a4-128">Configure a genuine certificate</span></span>](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<span data-ttu-id="318a4-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Windows PowerShell 웹 액세스 실행에 필요한 요구 사항</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="318a4-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requirements for running Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-130">Windows PowerShell 웹 액세스에는 웹 서버(IIS), .NET Framework 4.5, 그리고 게이트웨이를 실행할 서버에서 실행되는 Windows PowerShell 3.0 또는 Windows PowerShell 4.0이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-130">Windows PowerShell Web Access requires Web Server (IIS), .NET Framework 4.5, and Windows PowerShell 3.0 or Windows PowerShell 4.0 to be running on the server on which you want to run the gateway.</span></span> <span data-ttu-id="318a4-131">서버 관리자의 역할 및 기능 추가 마법사 또는 서버 관리자용 Windows PowerShell 배포 cmdlet을 사용하여 Windows Server 2012 R2 또는 Windows Server 2012가 실행되고 있는 서버에 Windows PowerShell 웹 액세스를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-131">You can install Windows PowerShell Web Access on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either the Add Roles and Features Wizard in Server Manager, or Windows PowerShell deployment cmdlets for Server Manager.</span></span> <span data-ttu-id="318a4-132">서버 관리자 또는 서버 관리자의 배포 cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하면 필수 역할 및 기능이 설치 과정의 일부분으로 자동 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-132">When you install Windows PowerShell Web Access by using Server Manager or its deployment cmdlets, required roles and features are automatically added as part of the installation process.</span></span>

<span data-ttu-id="318a4-133">Windows PowerShell 웹 액세스를 통해 원격 사용자는 웹 브라우저의 Windows PowerShell을 사용하여 조직 내 컴퓨터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-133">Windows PowerShell Web Access allows remote users to access computers in your organization by using Windows PowerShell in a web browser.</span></span> <span data-ttu-id="318a4-134">Windows PowerShell 웹 액세스가 편리하고 강력한 관리 도구이기는 하지만 웹 기반 액세스로 인해 보안 위험에 노출될 수 있으므로 가급적 안전하게 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-134">Although Windows PowerShell Web Access is a convenient and powerful management tool, the web-based access poses security risks, and should be configured as securely as possible.</span></span> <span data-ttu-id="318a4-135">따라서 Windows PowerShell 웹 액세스 게이트웨이를 구성하는 관리자는 사용 가능한 보안 계층, 즉 Windows PowerShell 웹 액세스에 포함된 cmdlet 기반의 권한 부여 규칙과 웹 서버(IIS) 및 타사 응용 프로그램에서 제공되는 보안 계층을 모두 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-135">We recommend that administrators who configure the Windows PowerShell Web Access gateway use available security layers, both the cmdlet-based authorization rules included with Windows PowerShell Web Access, and security layers that are available in Web Server (IIS) and third-party applications.</span></span> <span data-ttu-id="318a4-136">이 설명서에는 테스트 환경용으로만 권장되는 보안되지 않은 예와, 안전한 배포용으로 권장되는 예가 모두 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-136">This documentation includes both unsecure examples that are only recommended for test environments, as well as examples that are recommended for secure deployments.</span></span>

<a href="" id="BKMK_browser"></a>

<span data-ttu-id="318a4-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">브라우저 및 클라이언트 장치 지원</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="318a4-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser and client device support</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-138">Windows PowerShell 웹 액세스에서는 다음과 같은 인터넷 브라우저를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-138">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="318a4-139">모바일 브라우저는 공식적으로는 지원되지 않지만 대부분 웹 기반 Windows PowerShell 콘솔을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-139">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="318a4-140">쿠키를 적용하고 JavaScript 및 HTTPS 웹 사이트를 실행하는 다른 브라우저도 사용할 수 있지만 공식 테스트를 거치지는 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-140">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="318a4-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">지원되는 데스크톱 컴퓨터 브라우저</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="318a4-142">Microsoft Windows® 8.0, 9.0, 10.0 및 11.0용 Windows® Internet Explorer®</span><span class="sxs-lookup"><span data-stu-id="318a4-142">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="318a4-143">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="318a4-143">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="318a4-144">Windows용 Google Chrome™ 17.0.963.56m</span><span class="sxs-lookup"><span data-stu-id="318a4-144">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="318a4-145">Windows용 Apple Safari® 5.1.2</span><span class="sxs-lookup"><span data-stu-id="318a4-145">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="318a4-146">Mac OS®용 Apple Safari 5.1.2</span><span class="sxs-lookup"><span data-stu-id="318a4-146">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="318a4-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">최소한의 테스트를 거친 모바일 장치 또는 브라우저</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="318a4-148">Windows Phone 7 및 7.5</span><span class="sxs-lookup"><span data-stu-id="318a4-148">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="318a4-149">Google Android WebKit 3.1 Browser Android 2.2.1(커널 2.6)</span><span class="sxs-lookup"><span data-stu-id="318a4-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="318a4-150">iPhone 운영 체제 5.0.1용 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="318a4-150">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="318a4-151">iPad 2 운영 체제 5.0.1용 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="318a4-151">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="318a4-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">브라우저 요구 사항</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-153">Windows PowerShell 웹 액세스 웹 기반 콘솔을 사용하려면 브라우저에서 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-153">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="318a4-154">Windows PowerShell 웹 액세스 게이트웨이 웹 사이트의 쿠키를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-154">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="318a4-155">HTTPS 페이지를 열고 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-155">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="318a4-156">JavaScript가 사용되는 웹 사이트를 열고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-156">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_recm"></a>

<span data-ttu-id="318a4-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">권장(빠른) 배포</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="318a4-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-158">Windows PowerShell cmdlet을 사용하거나 서버 관리자 내에서 열린 역할 및 기능 추가 마법사를 사용하여 Windows Server 2012 R2 또는 Windows Server 2012를 실행하는 서버에서 Windows PowerShell 웹 액세스 게이트웨이를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-158">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either Windows PowerShell cmdlets, or by using the Add Roles and Features Wizard that is opened from within Server Manager.</span></span> <span data-ttu-id="318a4-159">빠른 설치 및 구성을 위해 이 섹션에 설명된 대로 Windows PowerShell cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-159">For quick installation and configuration, use Windows PowerShell cmdlets, as described in this section.</span></span>

-   [<span data-ttu-id="318a4-160">1단계: Windows PowerShell 웹 액세스 설치</span><span class="sxs-lookup"><span data-stu-id="318a4-160">Step 1: Install Windows PowerShell Web Access</span></span>](#BKMK_step1)

-   [<span data-ttu-id="318a4-161">2단계: 게이트웨이 구성</span><span class="sxs-lookup"><span data-stu-id="318a4-161">Step 2: Configure the gateway</span></span>](#BKMK_step2)

-   [<span data-ttu-id="318a4-162">3단계: 제한적인 권한 부여 규칙 구성</span><span class="sxs-lookup"><span data-stu-id="318a4-162">Step 3: Configure a restrictive authorization rule</span></span>](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<span data-ttu-id="318a4-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">1단계: Windows PowerShell 웹 액세스 설치</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="318a4-164">Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-164">To install Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="318a4-165">다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-165">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="318a4-166">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-166">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="318a4-167">Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-167">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="318a4-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="318a4-169">Windows PowerShell 3.0 및 4.0에서는 서버 관리자 cmdlet 모듈의 일부인 cmdlet을 실행하기 전에 해당 모듈을 Windows PowerShell 세션으로 가져올 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-169">In Windows PowerShell 3.0 and 4.0, there is no need to import the Server Manager cmdlet module into the Windows PowerShell session before running cmdlets that are part of the module.</span></span> <span data-ttu-id="318a4-170">모듈의 일부인 cmdlet을 처음으로 실행하면 모듈을 자동으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-170">A module is automatically imported the first time you run a cmdlet that is part of the module.</span></span> <span data-ttu-id="318a4-171">또한 Windows PowerShell cmdlet은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-171">Also, Windows PowerShell cmdlets are not case-sensitive.</span></span></p></td>
    </tr>
    </tbody>
    </table>

2.  <span data-ttu-id="318a4-172">다음을 입력하고 **Enter** 키를 누릅니다. 여기서 *computer_name*은 Windows PowerShell 웹 액세스를 설치할 원격 컴퓨터를 나타냅니다(해당되는 경우).</span><span class="sxs-lookup"><span data-stu-id="318a4-172">Type the following, and then press **Enter**, where *computer_name* represents a remote computer on which you want to install Windows PowerShell Web Access, if applicable.</span></span> <span data-ttu-id="318a4-173">필요에 따라 <span class="code">Restart</span> 매개 변수를 사용하여 대상 서버를 자동으로 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-173">The <span class="code">Restart</span> parameter automatically restarts destination servers if required.</span></span>

    [<span data-ttu-id="318a4-174">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-174">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "클립보드에 복사.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="318a4-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="318a4-176">Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하면 웹 서버(IIS) 관리 도구가 기본적으로 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-176">Installing Windows PowerShell Web Access by using Windows PowerShell cmdlets does not add Web Server (IIS) management tools by default.</span></span> <span data-ttu-id="318a4-177">관리 도구를 Windows PowerShell 웹 액세스 게이트웨이와 동일한 서버에 설치하려면 이 단계에서와 같이 설치 명령에 <span class="code">IncludeManagementTools</span> 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-177">If you want to install the management tools on the same server as the Windows PowerShell Web Access gateway, add the <span class="code">IncludeManagementTools</span> parameter to the installation command (as provided in this step).</span></span> <span data-ttu-id="318a4-178">원격 컴퓨터에서 Windows PowerShell 웹 액세스 웹 사이트를 관리하려면 게이트웨이를 관리하려는 컴퓨터에서 <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Windows 8.1용 원격 서버 관리 도구</a> 또는 <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Windows 8용 원격 서버 관리 도구</a>를 설치하여 IIS 관리자 스냅인을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-178">If you are managing the Windows PowerShell Web Access website from a remote computer, install the IIS Manager snap-in by installing <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remote Server Administration Tools for Windows 8.1</a> or <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remote Server Administration Tools for Windows 8</a> on the computer from which you want to manage the gateway.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="318a4-179">역할 및 기능을 오프라인 VHD에 설치하려면 <span class="code">ComputerName</span> 매개 변수와 <span class="code">VHD</span> 매개 변수를 모두 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-179">To install roles and features on an offline VHD, you must add both the <span class="code">ComputerName</span> parameter and the <span class="code">VHD</span> parameter.</span></span> <span data-ttu-id="318a4-180"><span class="code">ComputerName</span> 매개 변수에는 VHD를 탑재할 서버의 이름이 포함되며, <span class="code">VHD</span> 매개 변수에는 지정된 서버에서의 VHD 파일 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-180">The <span class="code">ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="318a4-181">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-181">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "클립보드에 복사.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  <span data-ttu-id="318a4-182">설치가 완료되면 관리자 권한으로 열린 Windows PowerShell 콘솔에서 대상 서버에 대한 **Get-WindowsFeature** cmdlet을 실행하여 Windows PowerShell 웹 액세스가 대상 서버에 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-182">When installation is complete, verify that Windows PowerShell Web Access was installed on destination servers by running the **Get-WindowsFeature** cmdlet on a destination server, in a Windows PowerShell console that has been opened with elevated user rights.</span></span> <span data-ttu-id="318a4-183">서버 관리자 콘솔에서도 **모든 서버** 페이지에서 대상 서버를 선택한 다음 해당 서버의 **역할 및 기능** 타일을 살펴보면 Windows PowerShell 웹 액세스가 설치되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-183">You can also verify that Windows PowerShell Web Access was installed in the Server Manager console, by selecting a destination server on the **All Servers** page, and then viewing the **Roles and Features** tile for the selected server.</span></span> <span data-ttu-id="318a4-184">Windows PowerShell 웹 액세스의 추가 정보 파일을 살펴볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-184">You can also view the readme file for Windows PowerShell Web Access.</span></span>

4.  <span data-ttu-id="318a4-185">Windows PowerShell 웹 액세스가 설치되고 나면 게이트웨이에 필요한 기본 설치 지침이 포함된 추가 정보 파일을 검토하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-185">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="318a4-186">이러한 설치 지침은 다음 섹션인 [2단계: 게이트웨이 구성](#BKMK_step2)에도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-186">These setup instructions are also in the following section, [Step 2: Configure the gateway](#BKMK_step2).</span></span> <span data-ttu-id="318a4-187">추가 정보 파일의 경로는 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>입니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-187">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

<a href="" id="BKMK_step2"></a>
###

<span data-ttu-id="318a4-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">2단계: 게이트웨이 구성</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-189">**Install-PswaWebApplication** cmdlet을 사용하면 Windows PowerShell 웹 액세스를 가장 빨리 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-189">The **Install-PswaWebApplication** cmdlet is a quick way to get Windows PowerShell Web Access configured.</span></span> <span data-ttu-id="318a4-190"><span class="code">UseTestCertificate</span> 매개 변수를 <span class="code">Install-PswaWebApplication</span> cmdlet에 추가하여 자체 서명된 테스트용 SSL 인증서를 설치할 수 있지만 안전하지 않으므로, 안전한 프로덕션 환경을 위해서는 항상 CA(인증 기관)에서 서명된 올바른 SSL 인증서를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-190">Although you can add the <span class="code">UseTestCertificate</span> parameter to the <span class="code">Install-PswaWebApplication</span> cmdlet to install a self-signed SSL certificate for test purposes, this is not secure; for a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="318a4-191">관리자는 IIS 관리자 콘솔을 사용하여 자신이 선택한 서명된 인증서로 테스트 인증서를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-191">Administrators can replace the test certificate with a signed certificate of their choice by using the IIS Manager console.</span></span>

<span data-ttu-id="318a4-192"><span class="code">Install-PswaWebApplication</span> cmdlet을 실행하거나 IIS 관리자에서 GUI 기반의 구성 단계를 수행하여 Windows PowerShell 웹 액세스 웹 응용 프로그램 구성을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-192">You can complete Windows PowerShell Web Access web application configuration either by running the <span class="code">Install-PswaWebApplication</span> cmdlet or by performing GUI-based configuration steps in IIS Manager.</span></span> <span data-ttu-id="318a4-193">기본적으로 이 cmdlet은 IIS 관리자에 표시된 바와 같이 **기본 웹 사이트** 컨테이너에 웹 응용 프로그램인 **pswa**(및 해당 응용 프로그램 풀인 **pswa_pool**)를 설치합니다. 필요에 따라 웹 응용 프로그램의 기본 사이트 컨테이너를 변경하는 명령을 이 cmdlet에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-193">By default, the cmdlet installs the web application, **pswa** (and an application pool for it, **pswa_pool**), in the **Default Web Site** container, as shown in IIS Manager; if desired, you can instruct the cmdlet to change the default site container of the web application.</span></span> <span data-ttu-id="318a4-194">IIS 관리자는 웹 응용 프로그램에서 사용 가능한 구성 옵션(예: SSL(Secure Sockets Layer) 인증서의 포트 번호 변경)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-194">IIS Manager offers configuration options that are available for web applications, such as changing the port number or the Secure Sockets Layer (SSL) certificate.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="318a4-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 보안 정보 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="318a4-196">관리자는 반드시 CA에서 서명된 유효한 인증서를 사용하도록 게이트웨이를 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-196">We strongly recommend that administrators configure the gateway to use a valid certificate that has been signed by a CA.</span></span></p></td>
</tr>
</tbody>
</table>

-   [<span data-ttu-id="318a4-197">Install-PswaWebApplication을 사용하여 테스트 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-197">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>](#BKMK_testcert)

-   [<span data-ttu-id="318a4-198">Install-PswaWebApplication 및 IIS 관리자를 사용하여 정품 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-198">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>](#BKMK_gencert)

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a><span data-ttu-id="318a4-199">Install-PswaWebApplication을 사용하여 테스트 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-199">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>

1.  <span data-ttu-id="318a4-200">다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-200">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="318a4-201">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-201">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="318a4-202">Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-202">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="318a4-203">다음을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-203">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="318a4-204">**Install-PswaWebApplication -UseTestCertificate**</span><span class="sxs-lookup"><span data-stu-id="318a4-204">**Install-PswaWebApplication -UseTestCertificate**</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="318a4-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 보안 정보 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="318a4-206"><span class="code">UseTestCertificate</span> 매개 변수는 개인 테스트 환경에서만 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-206">The <span class="code">UseTestCertificate</span> parameter should only be used in a private test environment.</span></span> <span data-ttu-id="318a4-207">안전한 프로덕션 환경을 위해 CA에서 서명된 유효한 인증서를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-207">For a secure production environment, we recommend using a valid certificate that has been signed by a CA.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="318a4-208">이 cmdlet을 실행하면 Windows PowerShell 웹 액세스 웹 응용 프로그램이 IIS 기본 웹 사이트 컨테이너에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-208">Running the cmdlet installs the Windows PowerShell Web Access web application within the IIS Default Web Site container.</span></span> <span data-ttu-id="318a4-209">이 cmdlet은 기본 웹 사이트인 https://&lt;server_name&gt;/pswa에서 Windows PowerShell 웹 액세스를 실행하는 데 필요한 인프라를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-209">The cmdlet creates the infrastructure required to run Windows PowerShell Web Access on the default website, https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="318a4-210">웹 응용 프로그램을 다른 웹 사이트에 설치하려면 <span class="code">WebSiteName</span> 매개 변수를 추가하여 웹 사이트 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-210">To install the web application in a different website, provide the website name by adding the <span class="code">WebSiteName</span> parameter.</span></span> <span data-ttu-id="318a4-211">웹 응용 프로그램의 이름을 변경하려면(기본 이름: <span class="code">pswa</span>) <span class="code">WebApplicationName</span> 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-211">To change the name of the web application (the default is <span class="code">pswa</span>), add the <span class="code">WebApplicationName</span> parameter.</span></span>

    <span data-ttu-id="318a4-212">이 cmdlet을 실행하면 다음과 같은 설정이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-212">The following settings are configured by running the cmdlet.</span></span> <span data-ttu-id="318a4-213">필요에 따라 IIS 관리자 콘솔에서 이러한 설정을 수동으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-213">You can change these manually in the IIS Manager console, if desired.</span></span>

    -   <span data-ttu-id="318a4-214">Path: /pswa</span><span class="sxs-lookup"><span data-stu-id="318a4-214">Path: /pswa</span></span>

    -   <span data-ttu-id="318a4-215">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="318a4-215">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="318a4-216">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="318a4-216">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="318a4-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="318a4-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

    <span data-ttu-id="318a4-218"><span class="label">예:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span><span class="sxs-lookup"><span data-stu-id="318a4-218"><span class="label">Example:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span></span>

    <span data-ttu-id="318a4-219">이 예에서 결과로 표시되는 Windows PowerShell 웹 액세스의 웹 사이트는 https://&lt;*server_name*&gt;/myWebApp입니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-219">In this example, the resulting website for Windows PowerShell Web Access is https://&lt; *server_name*&gt;/myWebApp.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="318a4-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="318a4-221">권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-221">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="318a4-222">자세한 내용은 <a href="#BKMK_step3">3단계: 제한적인 권한 부여 규칙 구성</a> 및 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능</a>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-222">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a><span data-ttu-id="318a4-223">Install-PswaWebApplication 및 IIS 관리자를 사용하여 정품 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-223">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>

1.  <span data-ttu-id="318a4-224">다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-224">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="318a4-225">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-225">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="318a4-226">Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-226">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="318a4-227">다음을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-227">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="318a4-228">**Install-PswaWebApplication**</span><span class="sxs-lookup"><span data-stu-id="318a4-228">**Install-PswaWebApplication**</span></span>

    <span data-ttu-id="318a4-229">이 cmdlet을 실행하면 다음과 같은 게이트웨이 설정이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-229">The following gateway settings are configured by running the cmdlet.</span></span> <span data-ttu-id="318a4-230">필요에 따라 IIS 관리자 콘솔에서 이러한 설정을 수동으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-230">You can change these manually in the IIS Manager console, if desired.</span></span> <span data-ttu-id="318a4-231"><span class="code">Install-PswaWebApplication</span> cmdlet의 <span class="code">WebsiteName</span> 및 <span class="code">WebApplicationName</span> 매개 변수에 대한 값을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-231">You can also specify values for the <span class="code">WebsiteName</span> and <span class="code">WebApplicationName</span> parameters of the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span>

    -   <span data-ttu-id="318a4-232">Path: /pswa</span><span class="sxs-lookup"><span data-stu-id="318a4-232">Path: /pswa</span></span>

    -   <span data-ttu-id="318a4-233">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="318a4-233">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="318a4-234">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="318a4-234">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="318a4-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="318a4-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

3.  <span data-ttu-id="318a4-236">다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-236">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="318a4-237">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-237">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="318a4-238">서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-238">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="318a4-239">Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-239">On the Windows **Start** screen, click **Server Manager**.</span></span>

4.  <span data-ttu-id="318a4-240">IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-240">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="318a4-241">**사이트** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-241">Expand the **Sites** folder.</span></span>

5.  <span data-ttu-id="318a4-242">Windows PowerShell 웹 액세스 웹 응용 프로그램이 설치된 웹 사이트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-242">Select the website in which you have installed the Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="318a4-243">**작업** 창에서 **바인딩**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-243">In the **Actions** pane, click **Bindings**.</span></span>

6.  <span data-ttu-id="318a4-244">**사이트 바인딩** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-244">In the **Site Binding** dialog box, click **Add**.</span></span>

7.  <span data-ttu-id="318a4-245">**사이트 바인딩 추가** 대화 상자의 **유형** 필드에서 **https**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-245">In the **Add Site Binding** dialog box, in the **Type** field, select **https**.</span></span>

8.  <span data-ttu-id="318a4-246">**SSL 인증서** 필드의 드롭다운 메뉴에서 서명된 인증서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-246">In the **SSL certificate** field, select your signed certificate from the drop-down menu.</span></span> <span data-ttu-id="318a4-247">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-247">Click **OK**.</span></span> <span data-ttu-id="318a4-248">인증서를 얻는 방법에 대한 자세한 내용은 이 항목의 [IIS 관리자로 SSL 인증서를 구성하려면](#BKMK_cert)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-248">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

    <span data-ttu-id="318a4-249">이제 Windows PowerShell 웹 액세스 웹 응용 프로그램이 서명된 SSL 인증서를 사용하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-249">The Windows PowerShell Web Access web application is now configured to use your signed SSL certificate.</span></span> <span data-ttu-id="318a4-250">브라우저 창에서 https://&lt;server_name&gt;/pswa를 열어 Windows PowerShell 웹 액세스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-250">You can access Windows PowerShell Web Access by opening https://&lt;server_name&gt;/pswa in a browser window.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="318a4-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="318a4-252">권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-252">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="318a4-253">자세한 내용은 <a href="#BKMK_step3">3단계: 제한적인 권한 부여 규칙 구성</a> 및 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능</a>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-253">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="318a4-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">3단계: 제한적인 권한 부여 규칙 구성</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-255">Windows PowerShell Web Access가 설치되고 게이트웨이가 구성되고 나면 사용자는 로그인 페이지를 브라우저에서 열 수 있지만 Windows PowerShell 웹 액세스 관리자가 사용자에게 액세스를 명시적으로 허용할 때까지는 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-255">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="318a4-256">Windows PowerShell 웹 액세스의 액세스 제어는 다음 표에 설명된 여러 Windows PowerShell cmdlet을 통해 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-256">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="318a4-257">권한 부여 규칙을 추가하거나 관리하는 작업에 해당하는 GUI는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-257">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="318a4-258">Windows PowerShell 웹 액세스 cmdlet에 대한 자세한 내용은 참조 항목 [Windows PowerShell 웹 액세스 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-258">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="318a4-259">Windows PowerShell 웹 액세스 권한 부여 규칙 및 보안에 대한 자세한 내용은 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-259">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="318a4-260">제한적인 권한 부여 규칙을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-260">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="318a4-261">다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-261">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="318a4-262">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-262">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="318a4-263">Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-263">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="318a4-264"><span class="label">세션 구성을 사용하여 사용자 액세스를 제한하는 단계(옵션):</span> 규칙에 사용할 세션 구성이 이미 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-264"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="318a4-265">해당 구성을 아직 만들지 않은 경우 MSDN의 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)에서 세션 구성의 생성 지침을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-265">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="318a4-266">다음을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-266">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="318a4-267">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-267">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "클립보드에 복사.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="318a4-268">이 권한 부여 규칙을 통해 특정 사용자는 일반적으로 액세스 권한을 갖고 있는 네트워크상의 한 컴퓨터에만 액세스할 수 있으며, 일반적인 스크립팅 및 cmdlet 환경에 해당하는 특정 세션 구성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-268">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="318a4-269">다음 예에서는 <span class="code">Contoso</span> 도메인의 <span class="code">JSmith</span>라는 사용자에게 <span class="code">Contoso_214</span> 컴퓨터를 관리하고, <span class="code">NewAdminsOnly</span>라는 세션 구성을 사용할 수 있는 액세스 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-269">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="318a4-270">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-270">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "클립보드에 복사.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="318a4-271">**Get-PswaAuthorizationRule** cmdlet 또는 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;을 실행하여 규칙이 생성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-271">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="318a4-272">예를 들어 **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-272">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="318a4-273">권한 부여 규칙을 구성하고 나면 권한이 부여된 사용자가 웹 기반 콘솔에 로그인하고 Windows PowerShell 웹 액세스를 사용할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-273">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_custom"></a>

<span data-ttu-id="318a4-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">사용자 지정 배포</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="318a4-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-275">서버 관리자의 역할 및 기능 추가 마법사를 사용하여 Windows Server 2012 R2 또는 Windows Server 2012를 실행하는 서버에서 Windows PowerShell 웹 액세스 게이트웨이를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-275">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using the Add Roles and Features Wizard in Server Manager.</span></span> <span data-ttu-id="318a4-276">Windows PowerShell 웹 액세스가 설치되면 IIS 관리자에서 게이트웨이 구성을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-276">After Windows PowerShell Web Access is installed, you can customize the configuration of the gateway in IIS Manager.</span></span>

<a href="" id="BKMK_custom1"></a>
###

<span data-ttu-id="318a4-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">1단계: Windows PowerShell 웹 액세스 설치</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a><span data-ttu-id="318a4-278">역할 및 기능 추가 마법사를 사용하여 Windows PowerShell 웹 액세스를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-278">To install Windows PowerShell Web Access by using the Add Roles and Features Wizard</span></span>

1.  <span data-ttu-id="318a4-279">서버 관리자가 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-279">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="318a4-280">서버 관리자가 아직 열려 있지 않으면 다음 중 하나를 수행하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-280">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="318a4-281">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-281">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="318a4-282">Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-282">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="318a4-283">**관리** 메뉴에서 **역할 및 기능 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-283">On the **Manage** menu, click **Add Roles and Features**.</span></span>

3.  <span data-ttu-id="318a4-284">**설치 유형 선택** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-284">On the **Select installation type** page, select **Role-based or feature-based installation**.</span></span> <span data-ttu-id="318a4-285">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-285">Click **Next**.</span></span>

4.  <span data-ttu-id="318a4-286">**대상 서버 선택** 페이지에서 서버 풀의 서버를 선택하거나 오프라인 VHD를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-286">On the **Select destination server** page, select a server from the server pool, or select an offline VHD.</span></span> <span data-ttu-id="318a4-287">오프라인 VHD를 대상 서버로 선택하려면 먼저 VHD가 탑재될 서버를 선택한 다음 VHD 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-287">To select an offline VHD as your destination server, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="318a4-288">서버를 서버 풀에 추가하는 방법에 대한 자세한 내용은 서버 관리자 도움말을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-288">For information about how to add servers to your server pool, see the Server Manager Help.</span></span> <span data-ttu-id="318a4-289">대상 서버를 선택하고 나면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-289">After you have selected the destination server, click **Next**.</span></span>

5.  <span data-ttu-id="318a4-290">마법사의 **기능 선택** 페이지에서 **Windows PowerShell**을 확장한 다음 **Windows PowerShell 웹 액세스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-290">On the **Select features** page of the wizard, expand **Windows PowerShell**, and then select **Windows PowerShell Web Access**.</span></span>

6.  <span data-ttu-id="318a4-291">.NET Framework 4.5와 웹 서버(IIS)의 역할 서비스 등 필수 기능을 추가하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-291">Note that you are prompted to add required features, such as .NET Framework 4.5, and role services of Web Server (IIS).</span></span> <span data-ttu-id="318a4-292">필수 기능을 추가하고 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-292">Add required features and continue.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="318a4-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="318a4-294">역할 및 기능 추가 마법사를 사용하여 Windows PowerShell 웹 액세스를 설치하는 경우 IIS 관리자 스냅인을 포함한 웹 서버(IIS)도 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-294">Installing Windows PowerShell Web Access by using the Add Roles and Features Wizard also installs Web Server (IIS), including the IIS Manager snap-in.</span></span> <span data-ttu-id="318a4-295">스냅인과 기타 IIS 관리 도구는 역할 및 기능 추가 마법사를 사용하면 기본적으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-295">The snap-in and other IIS management tools are installed by default if you use Add Roles and Features Wizard.</span></span> <span data-ttu-id="318a4-296">하지만 다음 절차에 설명된 대로 Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하는 경우에는 관리 도구가 기본적으로 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-296">If you install Windows PowerShell Web Access by using Windows PowerShell cmdlets as described in the following procedure, management tools are not added by default.</span></span></p></td>
    </tr>
    </tbody>
    </table>

7.  <span data-ttu-id="318a4-297">**설치 선택 확인** 페이지에서는 Windows PowerShell 웹 액세스의 기능 파일을 4단계에서 선택한 대상 서버에 저장하지 않을 경우 **대체 원본 경로 지정**을 클릭하고 기능 파일에 대한 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-297">On the **Confirm installation selections** page, if the feature files for Windows PowerShell Web Access are not stored on the destination server that you selected in step 4, click **Specify an alternate source path**, and provide the path to the feature files.</span></span> <span data-ttu-id="318a4-298">그렇지 않으면 **설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-298">Otherwise, click **Install**.</span></span>

8.  <span data-ttu-id="318a4-299">**설치**를 클릭하고 나면 설치 진행률, 결과 및 메시지(경고, 오류 또는 Windows PowerShell 웹 액세스에 필요한 설치 후 구성 단계 등)가 **설치 진행률** 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-299">After you click **Install**, the **Installation progress** page displays installation progress, results, and messages such as warnings, failures, or post-installation configuration steps that are required for Windows PowerShell Web Access.</span></span> <span data-ttu-id="318a4-300">Windows PowerShell 웹 액세스가 설치되고 나면 게이트웨이에 필요한 기본 설치 지침이 포함된 추가 정보 파일을 검토하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-300">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="318a4-301">이러한 지침은 이 항목에도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-301">These instructions are also included in this topic.</span></span> <span data-ttu-id="318a4-302">추가 정보 파일의 경로는 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>입니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-302">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

###

<span data-ttu-id="318a4-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">2단계: 게이트웨이 구성</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-304">이 섹션의 지침에는 Windows PowerShell 웹 액세스 웹 응용 프로그램을 웹 사이트의 루트 디렉터리가 아닌 하위 디렉터리에 설치하는 방법이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-304">Instructions in this section are for installing the Windows PowerShell Web Access web application in a subdirectory—and not in the root directory—of your website.</span></span> <span data-ttu-id="318a4-305">이 절차는 <span class="code">Install-PswaWebApplication</span> cmdlet에서 수행된 작업에 해당하는 GUI 기반 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-305">This procedure is the GUI-based equivalent of the actions performed by the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span> <span data-ttu-id="318a4-306">이 섹션에는 IIS 관리자를 사용하여 Windows PowerShell 웹 액세스 게이트웨이를 루트 웹 사이트로 구성하는 방법도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-306">This section also includes instructions for how to use IIS Manager to configure the Windows PowerShell Web Access gateway as a root website.</span></span>

-   [<span data-ttu-id="318a4-307">IIS 관리자를 사용하여 기존 웹 사이트에 게이트웨이를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-307">To use IIS Manager to configure the gateway in an existing website</span></span>](#BKMK_configman)

-   [<span data-ttu-id="318a4-308">IIS 관리자를 사용하여 테스트 인증서를 사용하는 루트 웹 사이트로 게이트웨이를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-308">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>](#BKMK_configroot)

-   

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a><span data-ttu-id="318a4-309">IIS 관리자를 사용하여 기존 웹 사이트에 게이트웨이를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-309">To use IIS Manager to configure the gateway in an existing website</span></span>

1.  <span data-ttu-id="318a4-310">다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-310">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="318a4-311">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-311">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="318a4-312">서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-312">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="318a4-313">Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-313">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="318a4-314">**응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-314">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="318a4-315">Windows PowerShell 웹 액세스의 새로운 응용 프로그램 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-315">Create a new application pool for Windows PowerShell Web Access.</span></span> <span data-ttu-id="318a4-316">IIS 관리자 트리 창에서 게이트웨이 서버의 노드를 확장한 다음 **응용 프로그램 풀**을 선택하고 **작업** 창에서 **응용 프로그램 풀 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-316">Expand the node of the gateway server in the IIS Manager tree pane, select **Application Pools**, and click **Add Application Pool** in the **Actions** pane.</span></span>

3.  <span data-ttu-id="318a4-317">이름이 **pswa_pool**인 새로운 응용 프로그램 풀을 추가하거나 다른 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-317">Add a new application pool with the name **pswa_pool**, or provide another name.</span></span> <span data-ttu-id="318a4-318">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-318">Click **OK**.</span></span>

4.  <span data-ttu-id="318a4-319">IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-319">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="318a4-320">**사이트** 폴더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-320">Select the **Sites** folder.</span></span>

5.  <span data-ttu-id="318a4-321">Windows PowerShell 웹 액세스 웹 사이트를 추가할 웹 사이트(예: **기본 웹 사이트**)를 마우스 오른쪽 단추로 클릭한 다음 **응용 프로그램 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-321">Right-click the website (for example, **Default Web Site**) to which you would like to add the Windows PowerShell Web Access website, and then click **Add Application**.</span></span>

6.  <span data-ttu-id="318a4-322">**별칭** 필드에 pswa를 입력하거나 다른 별칭을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-322">In the **Alias** field, type pswa, or provide another alias.</span></span> <span data-ttu-id="318a4-323">이 별칭은 가상 디렉터리 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-323">The alias becomes the virtual directory name.</span></span> <span data-ttu-id="318a4-324">예를 들어 다음 URL, 즉 https://&lt;server_name&gt;/pswa의 **pswa**는 이 단계에서 지정된 별칭을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-324">For example, **pswa** in the following URL represents the alias specified in this step: https://&lt;server_name&gt;/pswa.</span></span>

7.  <span data-ttu-id="318a4-325">**응용 프로그램 풀** 필드에서는 3단계에서 만든 응용 프로그램 풀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-325">In the **Application pool** field, select the application pool that you created in step 3.</span></span>

8.  <span data-ttu-id="318a4-326">**실제 경로** 필드에서 응용 프로그램의 위치를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-326">In the **Physical path** field, browse for the location of the application.</span></span> <span data-ttu-id="318a4-327">기본 위치인 %windir%/Web/PowerShellWebAccess/wwwroot를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-327">You can use the default location, %windir%/Web/PowerShellWebAccess/wwwroot.</span></span> <span data-ttu-id="318a4-328">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-328">Click **OK**.</span></span>

9.  <span data-ttu-id="318a4-329">이 항목에서 [IIS 관리자로 SSL 인증서를 구성하려면](#BKMK_cert) 절차의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-329">Follow the steps in the procedure [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic.</span></span>

10. <span data-ttu-id="318a4-330"><span class="label">선택적 보안 단계:</span> 트리 창에서 웹 사이트를 선택한 상태에서 내용 창의 **SSL 설정**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-330"><span class="label">Optional security step:</span> With the website selected in the tree pane, double-click **SSL Settings** in the content pane.</span></span> <span data-ttu-id="318a4-331">**SSL 필요**를 선택한 다음 **작업** 창에서 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-331">Select **Require SSL**, and then in the **Actions** pane, click **Apply**.</span></span> <span data-ttu-id="318a4-332">필요에 따라 **SSL 설정** 창에서 Windows PowerShell 웹 액세스 웹 사이트에 연결하는 사용자에게는 클라이언트 인증서가 있어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-332">Optionally, in the **SSL Settings** pane, you can require that users connecting to the Windows PowerShell Web Access website have client certificates.</span></span> <span data-ttu-id="318a4-333">클라이언트 인증서를 통해 클라이언트 장치 사용자의 신분을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-333">Client certificates help to verify the identity of a client device user.</span></span> <span data-ttu-id="318a4-334">클라이언트 인증서를 요구하여 Windows PowerShell 웹 액세스의 보안을 강화하는 방법에 대한 자세한 내용은 이 가이드의 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-334">For more information about how requiring client certificates can increase the security of Windows PowerShell Web Access, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in this guide.</span></span>

11. <span data-ttu-id="318a4-335">클라이언트 장치에서 브라우저 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-335">Open a browser session on a client device.</span></span> <span data-ttu-id="318a4-336">지원되는 브라우저와 장치에 대한 자세한 내용은 이 항목의 [브라우저 및 클라이언트 장치 지원](#BKMK_browser)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-336">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this topic.</span></span>

12. <span data-ttu-id="318a4-337">새로운 Windows PowerShell 웹 액세스 웹 사이트인 https://&lt;*gateway_server_name*&gt;/pswa를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-337">Open the new Windows PowerShell Web Access website, https://&lt; *gateway_server_name*&gt;/pswa.</span></span>

    <span data-ttu-id="318a4-338">브라우저에 Windows PowerShell 웹 액세스 콘솔 로그인 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-338">The browser should display the Windows PowerShell Web Access console sign-in page.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="318a4-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="318a4-340">권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-340">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

13. <span data-ttu-id="318a4-341">관리자 권한(관리자 권한으로 실행)을 사용하여 열린 Windows PowerShell 세션에서 다음 스크립트(여기서 *application_pool_name*은 3단계에서 만든 응용 프로그램 풀의 이름을 나타냄)를 실행하여 권한 부여 파일에 대한 액세스 권한을 응용 프로그램 풀에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-341">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 3, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="318a4-342">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-342">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "클립보드에 복사.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="318a4-343">권한 부여 파일에 대한 기존 액세스 권한을 확인하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-343">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="318a4-344">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-344">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "클립보드에 복사.")

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a><span data-ttu-id="318a4-345">IIS 관리자를 사용하여 테스트 인증서를 사용하는 루트 웹 사이트로 게이트웨이를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-345">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>

1.  <span data-ttu-id="318a4-346">다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-346">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="318a4-347">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-347">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="318a4-348">서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-348">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="318a4-349">Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-349">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="318a4-350">**응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-350">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="318a4-351">IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-351">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="318a4-352">**사이트** 폴더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-352">Select the **Sites** folder.</span></span>

3.  <span data-ttu-id="318a4-353">**작업** 창에서 **웹 사이트 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-353">In the **Actions** pane, click **Add Website**.</span></span>

4.  <span data-ttu-id="318a4-354">**Windows PowerShell 웹 액세스**와 같은 웹 사이트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-354">Type a name for the website, such as **Windows PowerShell Web Access**.</span></span>

5.  <span data-ttu-id="318a4-355">새 웹 사이트의 응용 프로그램 풀이 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-355">An application pool is automatically created for the new website.</span></span> <span data-ttu-id="318a4-356">다른 응용 프로그램 풀을 사용하려면 **선택**을 클릭하여 새 웹 사이트와 연결될 응용 프로그램 풀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-356">To use a different application pool, click **Select** to select an application pool to associate with the new website.</span></span> <span data-ttu-id="318a4-357">**응용 프로그램 풀 선택** 대화 상자에서 다른 응용 프로그램 풀을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-357">Select the alternate application pool in the **Select Application Pool** dialog box, and then click **OK**.</span></span>

6.  <span data-ttu-id="318a4-358">**실제 경로** 텍스트 상자에서 %*windir*%/Web/PowerShellWebAccess/wwwroot로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-358">In the **Physical path** text box, navigate to %*windir*%/Web/PowerShellWebAccess/wwwroot.</span></span>

7.  <span data-ttu-id="318a4-359">**바인딩** 영역의 **유형** 필드에서 **https**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-359">In the **Type** field of the **Binding** area, select **https**.</span></span>

8.  <span data-ttu-id="318a4-360">다른 사이트나 응용 프로그램에서 사용하고 있지 않은 웹 사이트에 포트 번호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-360">Assign a port number to the website that is not already in use by another site or application.</span></span> <span data-ttu-id="318a4-361">열린 포트를 찾으려면 명령 프롬프트 창에서 **netstat** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-361">To locate open ports, you can run the **netstat** command in a Command Prompt window.</span></span> <span data-ttu-id="318a4-362">기본 포트 번호는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-362">The default port number is 443.</span></span>

    <span data-ttu-id="318a4-363">다른 웹 사이트에서 443을 이미 사용하고 있거나 이 포트 번호를 변경해야 할 다른 보안상의 이유가 있는 경우, 기본 포트 번호를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-363">Change the default port if another website is already using 443, or if you have other security reasons for changing the port number.</span></span> <span data-ttu-id="318a4-364">선택한 포트를 게이트웨이 서버에서 실행 중인 다른 웹 사이트에서 사용하고 있을 경우 **웹 사이트 추가** 대화 상자에서 **확인**을 클릭하면 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-364">If another website that is running on your gateway server is using your selected port, a warning is displayed when you click **OK** in the **Add Website** dialog box.</span></span> <span data-ttu-id="318a4-365">Windows PowerShell 웹 액세스를 실행하려면 미사용 포트를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-365">You must use an unused port to run Windows PowerShell Web Access.</span></span>

9.  <span data-ttu-id="318a4-366">조직에 필요한 경우에는 선택적으로 **www.contoso.com** 같이 조직과 사용자가 쉽게 알아볼 수 있는 호스트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-366">Optionally, if needed for your organization, specify a host name that makes sense to your organization and users, such as **www.contoso.com**.</span></span> <span data-ttu-id="318a4-367">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-367">Click **OK**.</span></span>

10. <span data-ttu-id="318a4-368">보다 안전한 프로덕션 환경을 위해 반드시 CA에서 서명된 유효한 인증서를 제공하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-368">For a more secure production environment, we strongly recommend providing a valid certificate that has been signed by a CA.</span></span> <span data-ttu-id="318a4-369">사용자는 HTTPS 웹 사이트를 통해서만 Windows PowerShell 웹 액세스에 연결할 수 있으므로, SSL 인증서를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-369">You must provide an SSL certificate, because users can only connect to Windows PowerShell Web Access through an HTTPS website.</span></span> <span data-ttu-id="318a4-370">인증서를 얻는 방법에 대한 자세한 내용은 이 항목의 [IIS 관리자로 SSL 인증서를 구성하려면](#BKMK_cert)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-370">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

11. <span data-ttu-id="318a4-371">**확인**을 클릭하여 **웹 사이트 추가** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-371">Click **OK** to close the **Add Website** dialog box.</span></span>

12. <span data-ttu-id="318a4-372">관리자 권한(관리자 권한으로 실행)을 사용하여 열린 Windows PowerShell 세션에서 다음 스크립트(여기서 *application_pool_name*은 4단계에서 만든 응용 프로그램 풀의 이름을 나타냄)를 실행하여 권한 부여 파일에 대한 액세스 권한을 응용 프로그램 풀에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-372">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 4, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="318a4-373">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-373">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "클립보드에 복사.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="318a4-374">권한 부여 파일에 대한 기존 액세스 권한을 확인하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-374">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="318a4-375">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-375">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "클립보드에 복사.")

        c:\windows\system32\icacls.exe $authorizationFile

13. <span data-ttu-id="318a4-376">IIS 관리자 트리 창에서 새 웹 사이트가 선택된 상태에서 **작업** 창의 **시작**을 클릭하여 웹 사이트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-376">With the new website selected in the IIS Manager tree pane, click **Start** in the **Actions** pane to start the website.</span></span>

14. <span data-ttu-id="318a4-377">클라이언트 장치에서 브라우저 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-377">Open a browser session on a client device.</span></span> <span data-ttu-id="318a4-378">지원되는 브라우저와 장치에 대한 자세한 내용은 이 문서의 [브라우저 및 클라이언트 장치 지원](#BKMK_browser)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-378">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this document.</span></span>

15. <span data-ttu-id="318a4-379">새로운 Windows PowerShell 웹 액세스 웹 사이트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-379">Open the new Windows PowerShell Web Access website.</span></span>

    <span data-ttu-id="318a4-380">루트 웹 사이트가 Windows PowerShell 웹 액세스 폴더를 가리키므로, https://&lt;*gateway_server_name*&gt;을 열면 Windows PowerShell 웹 액세스 로그인 페이지가 브라우저에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-380">Because the root website points to the Windows PowerShell Web Access folder, the browser should display the Windows PowerShell Web Access sign-in page when you open https://&lt; *gateway_server_name*&gt;.</span></span> <span data-ttu-id="318a4-381">URL에는 **/pswa**를 추가하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-381">You should not need to add **/pswa** to the URL.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="318a4-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="318a4-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="318a4-383">권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-383">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="318a4-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">3단계: 제한적인 권한 부여 규칙 구성</span></a></span><span class="sxs-lookup"><span data-stu-id="318a4-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-385">Windows PowerShell Web Access가 설치되고 게이트웨이가 구성되고 나면 사용자는 로그인 페이지를 브라우저에서 열 수 있지만 Windows PowerShell 웹 액세스 관리자가 사용자에게 액세스를 명시적으로 허용할 때까지는 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-385">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="318a4-386">Windows PowerShell 웹 액세스의 액세스 제어는 다음 표에 설명된 여러 Windows PowerShell cmdlet을 통해 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-386">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="318a4-387">권한 부여 규칙을 추가하거나 관리하는 작업에 해당하는 GUI는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-387">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="318a4-388">Windows PowerShell 웹 액세스 cmdlet에 대한 자세한 내용은 참조 항목 [Windows PowerShell 웹 액세스 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-388">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="318a4-389">Windows PowerShell 웹 액세스 권한 부여 규칙 및 보안에 대한 자세한 내용은 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-389">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="318a4-390">제한적인 권한 부여 규칙을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-390">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="318a4-391">다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-391">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="318a4-392">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-392">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="318a4-393">Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-393">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="318a4-394"><span class="label">세션 구성을 사용하여 사용자 액세스를 제한하는 단계(옵션):</span> 규칙에 사용할 세션 구성이 이미 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-394"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="318a4-395">해당 구성을 아직 만들지 않은 경우 MSDN의 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)에서 세션 구성의 생성 지침을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-395">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="318a4-396">다음을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-396">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="318a4-397">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-397">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "클립보드에 복사.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="318a4-398">이 권한 부여 규칙을 통해 특정 사용자는 일반적으로 액세스 권한을 갖고 있는 네트워크상의 한 컴퓨터에만 액세스할 수 있으며, 일반적인 스크립팅 및 cmdlet 환경에 해당하는 특정 세션 구성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-398">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="318a4-399">다음 예에서는 <span class="code">Contoso</span> 도메인의 <span class="code">JSmith</span>라는 사용자에게 <span class="code">Contoso_214</span> 컴퓨터를 관리하고, <span class="code">NewAdminsOnly</span>라는 세션 구성을 사용할 수 있는 액세스 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-399">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="318a4-400">Copy</span><span class="sxs-lookup"><span data-stu-id="318a4-400">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "클립보드에 복사.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="318a4-401">**Get-PswaAuthorizationRule** cmdlet 또는 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;을 실행하여 규칙이 생성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-401">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="318a4-402">예를 들어 **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-402">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="318a4-403">권한 부여 규칙을 구성하고 나면 권한이 부여된 사용자가 웹 기반 콘솔에 로그인하고 Windows PowerShell 웹 액세스를 사용할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-403">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_configcert"></a>

<span data-ttu-id="318a4-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">정품 인증서 구성</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="318a4-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configure a genuine certificate</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-405">안전한 프로덕션 환경을 위해 항상 CA(인증 기관)에서 서명된 유효한 SSL 인증서를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-405">For a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="318a4-406">이 섹션의 절차에서는 CA에서 유효한 SSL 인증서를 얻고 적용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-406">The procedure in this section describes how to obtain and apply a valid SSL certificate from a CA.</span></span>

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a><span data-ttu-id="318a4-407">IIS 관리자로 SSL 인증서를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="318a4-407">To configure an SSL certificate in IIS Manager</span></span>

1.  <span data-ttu-id="318a4-408">IIS 관리자 트리 창에서 Windows PowerShell 웹 액세스가 설치되어 있는 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-408">In the IIS Manager tree pane, select the server on which Windows PowerShell Web Access is installed.</span></span>

2.  <span data-ttu-id="318a4-409">내용 창에서 **서버 인증서**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-409">In the content pane, double click **Server Certificates**.</span></span>

3.  <span data-ttu-id="318a4-410">**작업** 창에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-410">In the **Actions** pane, do one of the following.</span></span> <span data-ttu-id="318a4-411">IIS에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [IIS 7에서 서버 인증서 구성](https://technet.microsoft.com/library/cc732230.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-411">For more information about configuring server certificates in IIS, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span></span>

    -   <span data-ttu-id="318a4-412">네트워크 위치에서 기존의 유효한 인증서를 가져오려면 **가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-412">Click **Import** to import an existing, valid certificate from a location on your network.</span></span>

    -   <span data-ttu-id="318a4-413">CA에서 VeriSign™, Thawte 또는 GeoTrust® 등의 인증서를 요청하려면 **인증서 요청 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-413">Click **Create Certificate Request** to request a certificate from a CA such as VeriSign™, Thawte, or GeoTrust®.</span></span> <span data-ttu-id="318a4-414">인증서의 일반 이름은 요청의 호스트 헤더와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-414">The certificate's common name must match the host header in the request.</span></span> <span data-ttu-id="318a4-415">예를 들어 클라이언트 브라우저에서 http://www.contoso.com/을 요청하면 일반 이름도 http://www.contoso.com/이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-415">For example, if the client browser requests http://www.contoso.com/, then the common name must also be http://www.contoso.com/.</span></span> <span data-ttu-id="318a4-416">이 방법이 Windows PowerShell 웹 액세스 게이트웨이에 인증서를 제공하는 가장 안전한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-416">This is the most secure and recommended option for providing the Windows PowerShell Web Access gateway with a certificate.</span></span>

    -   <span data-ttu-id="318a4-417">곧바로 사용할 수 있는 인증서를 만든 다음 나중에 필요할 때 CA에서 서명을 받아 사용하려면 **자체 서명된 인증서 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-417">Click **Create a Self-Signed Certificate** to create a certificate that you can use immediately, and have signed later by a CA if desired.</span></span> <span data-ttu-id="318a4-418">**Windows PowerShell 웹 액세스**와 같이 자체 서명된 인증서에 알기 쉬운 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-418">Specify a friendly name for the self-signed certificate, such as **Windows PowerShell Web Access**.</span></span> <span data-ttu-id="318a4-419">이 방법은 안전하지 않으므로 개인 테스트 환경용으로만 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-419">This option is not considered secure, and is recommended only for a private test environment.</span></span>

4.  <span data-ttu-id="318a4-420">인증서를 만들거나 구한 다음, IIS 관리자 트리 창에서 인증서가 적용될 웹 사이트(예: **기본 웹 사이트**)를 IIS 관리자 트리 창에서 선택한 다음 **작업** 창에서 **바인딩**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-420">After creating or obtaining a certificate, select the website to which the certificate is applied (for example, **Default Web Site**) in the IIS Manager tree pane, and then click **Bindings** in the **Actions** pane.</span></span>

5.  <span data-ttu-id="318a4-421">해당 사이트의 바인딩이 표시되지 않은 경우, **사이트 바인딩 추가** 대화 상자에서 사이트의 **https** 바인딩을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-421">In the **Add Site Binding** dialog box, add an **https** binding for the site, if one is not already displayed.</span></span> <span data-ttu-id="318a4-422">자체 서명된 인증서를 사용하지 않을 경우에는 이 절차의 3단계에서 설명된 호스트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-422">If you are not using a self-signed certificate, specify the host name from step 3 of this procedure.</span></span> <span data-ttu-id="318a4-423">자체 서명된 인증서를 사용할 경우에는 이 단계가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-423">If you are using a self-signed certificate, this step is not required.</span></span>

6.  <span data-ttu-id="318a4-424">이 절차의 3단계에서 얻거나 만든 인증서를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-424">Select the certificate that you obtained or created in step 3 of this procedure, and then click **OK**.</span></span>

<a href="" id="BKMK_using"></a>

<span data-ttu-id="318a4-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">웹 기반 Windows PowerShell 콘솔 사용</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="318a4-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-426">이 항목에 설명된 대로 Windows PowerShell 웹 액세스가 설치되고 게이트웨이 구성이 완료된 다음에는 Windows PowerShell 웹 기반 콘솔을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-426">After Windows PowerShell Web Access is installed and the gateway configuration is finished as described in this topic, the Windows PowerShell web-based console is ready to use.</span></span> <span data-ttu-id="318a4-427">웹 기반 콘솔에서 시작하는 방법에 대한 자세한 내용은 [웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-427">For more information about getting started in the web-based console, see [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span></span>

<span data-ttu-id="318a4-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">참고 항목</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="318a4-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="318a4-429">[IIS(인터넷 정보 서비스) 7.0 설명서](https://technet.microsoft.com/library/cc753433.aspx)
[IIS 관리자 7.0 도움말](https://technet.microsoft.com/library/cc732664.aspx)
[웹 서버 보안 구성(IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec 배포 리소스](https://technet.microsoft.com/network/bb531150)</span><span class="sxs-lookup"><span data-stu-id="318a4-429">[Internet Information Services (IIS) 7.0 Documentation](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)</span></span>

<span data-ttu-id="318a4-430"><span>표시:</span> 상속됨 보호됨</span><span class="sxs-lookup"><span data-stu-id="318a4-430"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="318a4-431"><span class="stdr-votetitle">이 페이지가 도움이 되었나요?</span></span><span class="sxs-lookup"><span data-stu-id="318a4-431"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="318a4-432">예 아니요</span><span class="sxs-lookup"><span data-stu-id="318a4-432">Yes No</span></span>

<span data-ttu-id="318a4-433">추가 피드백</span><span class="sxs-lookup"><span data-stu-id="318a4-433">Additional feedback?</span></span>

<span data-ttu-id="318a4-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span>자 남음</span> 제출 건너뛰기</span><span class="sxs-lookup"><span data-stu-id="318a4-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="318a4-435"><span class="stdr-thankyou">감사합니다.</span></span><span class="sxs-lookup"><span data-stu-id="318a4-435"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="318a4-436"><span class="stdr-appreciate">피드백에 감사드립니다.</span></span><span class="sxs-lookup"><span data-stu-id="318a4-436"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="318a4-437">프로필 관리</span><span class="sxs-lookup"><span data-stu-id="318a4-437">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="318a4-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 사이트 피드백</a> 사이트 피드백</span><span class="sxs-lookup"><span data-stu-id="318a4-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="318a4-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="318a4-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="318a4-440">사용 환경에 대한 의견을 제공해주세요...</span><span class="sxs-lookup"><span data-stu-id="318a4-440">Tell us about your experience...</span></span>

<span data-ttu-id="318a4-441">페이지가 빨리 로드되었나요?</span><span class="sxs-lookup"><span data-stu-id="318a4-441">Did the page load quickly?</span></span>

<span data-ttu-id="318a4-442"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="318a4-442"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="318a4-443">페이지 디자인이 마음에 드세요?</span><span class="sxs-lookup"><span data-stu-id="318a4-443">Do you like the page design?</span></span>

<span data-ttu-id="318a4-444"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="318a4-444"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="318a4-445">기타 의견</span><span class="sxs-lookup"><span data-stu-id="318a4-445">Tell us more</span></span>

-   [<span data-ttu-id="318a4-446">Flash 뉴스레터</span><span class="sxs-lookup"><span data-stu-id="318a4-446">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="318a4-447">연락처</span><span class="sxs-lookup"><span data-stu-id="318a4-447">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="318a4-448">개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="318a4-448">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="318a4-449">사용 조건</span><span class="sxs-lookup"><span data-stu-id="318a4-449">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="318a4-450">상표</span><span class="sxs-lookup"><span data-stu-id="318a4-450">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="318a4-451">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="318a4-451">© 2016 Microsoft</span></span>

<span data-ttu-id="318a4-452">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="318a4-452">© 2016 Microsoft</span></span>

<span data-ttu-id="318a4-453">본 웹 사이트에서 연결되거나 참조된 타사 스크립트 및 코드의 경우 Microsoft가 아닌 해당 코드를 소유한 측에서 사용자에게 라이선스를 허여합니다.</span><span class="sxs-lookup"><span data-stu-id="318a4-453">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="318a4-454">ASP.NET Ajax CDN 사용 약관 - http://www.asp.net/ajaxlibrary/CDN.ashx를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="318a4-454">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

