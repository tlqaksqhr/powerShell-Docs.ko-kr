---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "웹 기반 Windows PowerShell 콘솔 사용"
ms.openlocfilehash: 48ed1646c00f909c4e950f197f51a30205060ef0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
#  <a name="use-the-web-based-windows-powershell-console"></a><span data-ttu-id="6c17b-103">Use the Web-based Windows PowerShell Console</span><span class="sxs-lookup"><span data-stu-id="6c17b-103">Use the Web-based Windows PowerShell Console</span></span>

<span data-ttu-id="6c17b-104">업데이트됨: 2013년 6월 24일</span><span class="sxs-lookup"><span data-stu-id="6c17b-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="6c17b-105">적용 대상: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="6c17b-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="6c17b-106">Windows PowerShell® 웹 액세스를 사용하면 Windows PowerShell® 사용자가 SSL(Secure Sockets Layer) 보안 웹 사이트에 로그인하여 Windows PowerShell 세션, cmdlet 및 스크립트를 사용하여 원격 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-106">Windows PowerShell® Web Access lets Windows PowerShell® users sign in to a Secure Sockets Layer (SSL)-secured website to use Windows PowerShell sessions, cmdlets, and scripts to manage a remote computer.</span></span> <span data-ttu-id="6c17b-107">Windows PowerShell 콘솔은 웹 브라우저에서 실행되므로 이동 전화, 태블릿 컴퓨터, 공개 컴퓨팅 키오스크, 랩톱 컴퓨터 또는 공용 컴퓨터나 대여 컴퓨터 등의 다양한 클라이언트 장치에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-107">Because the Windows PowerShell console runs in a web browser, it can be opened from a variety of client devices, including cell phones, tablet computers, public computing kiosks, laptop computers, or shared or borrowed computers.</span></span> <span data-ttu-id="6c17b-108">웹 기반 Windows PowerShell 콘솔은 로그인 프로세스의 일부로 사용자가 지정한 원격 컴퓨터를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-108">The web-based Windows PowerShell console is targeted at a remote computer that is specified by users as part of the sign-in process.</span></span> <span data-ttu-id="6c17b-109">이 항목에서는 Windows PowerShell 웹 액세스 웹 기반 콘솔을 사용하여 로그인하고 시작하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-109">This topic describes how to sign in to and start using the Windows PowerShell Web Access web-based console.</span></span>

<span data-ttu-id="6c17b-110">그러나 Windows PowerShell 사용 방법이나 cmdlet 또는 스크립트 실행 방법에 대해서는 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-110">This topic does not describe how to use Windows PowerShell or run cmdlets or scripts.</span></span> <span data-ttu-id="6c17b-111">Windows PowerShell 사용 방법과 스크립트 관련 리소스에 대한 내용은 본 항목의 끝 부분에 있는 참고 항목 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c17b-111">For information about how to use Windows PowerShell, and scripting resources, see the See Also section at the end of this topic.</span></span>

<span data-ttu-id="6c17b-112">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="6c17b-112">In this topic:</span></span>

-   [<span data-ttu-id="6c17b-113">지원되는 브라우저 및 클라이언트 장치</span><span class="sxs-lookup"><span data-stu-id="6c17b-113">Supported browsers and client devices</span></span>](#BKMK_browser)

-   [<span data-ttu-id="6c17b-114">Windows PowerShell 웹 액세스 로그인</span><span class="sxs-lookup"><span data-stu-id="6c17b-114">Signing in to Windows PowerShell Web Access</span></span>](#BKMK_sign)

-   [<span data-ttu-id="6c17b-115">로그아웃 및 시간 초과</span><span class="sxs-lookup"><span data-stu-id="6c17b-115">Signing out and timing out</span></span>](#BKMK_timeout)

-   [<span data-ttu-id="6c17b-116">웹 기반 Windows PowerShell 콘솔의 차이점</span><span class="sxs-lookup"><span data-stu-id="6c17b-116">Differences in the web-based Windows PowerShell console</span></span>](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

<span data-ttu-id="6c17b-117">Windows PowerShell 웹 액세스에서는 다음과 같은 인터넷 브라우저를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-117">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="6c17b-118">모바일 브라우저는 공식적으로는 지원되지 않지만 대부분 웹 기반 Windows PowerShell 콘솔을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-118">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="6c17b-119">쿠키를 적용하고 JavaScript 및 HTTPS 웹 사이트를 실행하는 다른 브라우저도 사용할 수 있지만 공식 테스트를 거치지는 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-119">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="6c17b-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">지원되는 데스크톱 컴퓨터 브라우저</span></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="6c17b-121">Microsoft Windows® 8.0, 9.0, 10.0 및 11.0용 Windows® Internet Explorer®</span><span class="sxs-lookup"><span data-stu-id="6c17b-121">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="6c17b-122">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="6c17b-122">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="6c17b-123">Windows용 Google Chrome™ 17.0.963.56m</span><span class="sxs-lookup"><span data-stu-id="6c17b-123">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="6c17b-124">Windows용 Apple Safari® 5.1.2</span><span class="sxs-lookup"><span data-stu-id="6c17b-124">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="6c17b-125">Mac OS®용 Apple Safari 5.1.2</span><span class="sxs-lookup"><span data-stu-id="6c17b-125">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="6c17b-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">최소한의 테스트를 거친 모바일 장치 또는 브라우저</span></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="6c17b-127">Windows Phone 7 및 7.5</span><span class="sxs-lookup"><span data-stu-id="6c17b-127">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="6c17b-128">Google Android WebKit 3.1 Browser Android 2.2.1(커널 2.6)</span><span class="sxs-lookup"><span data-stu-id="6c17b-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="6c17b-129">iPhone 운영 체제 5.0.1용 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="6c17b-129">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="6c17b-130">iPad 2 운영 체제 5.0.1용 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="6c17b-130">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="6c17b-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">브라우저 요구 사항</span></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="6c17b-132">Windows PowerShell 웹 액세스 웹 기반 콘솔을 사용하려면 브라우저에서 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-132">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="6c17b-133">Windows PowerShell 웹 액세스 게이트웨이 웹 사이트의 쿠키를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-133">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="6c17b-134">HTTPS 페이지를 열고 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-134">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="6c17b-135">JavaScript가 사용되는 웹 사이트를 열고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-135">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_sign"></a>

<span data-ttu-id="6c17b-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Windows PowerShell 웹 액세스 로그인</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing in to Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="6c17b-137">Windows PowerShell 웹 액세스 관리자는 조직의 Windows PowerShell 웹 액세스 게이트웨이 웹 사이트 주소에 해당하는 URL을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-137">Your Windows PowerShell Web Access administrator should provide you with a URL that is the address of your organization’s Windows PowerShell Web Access gateway website.</span></span> <span data-ttu-id="6c17b-138">기본적으로 이 웹 사이트의 주소는 https://&lt;server_name&gt;/pswa입니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-138">By default, this website address is https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="6c17b-139">Windows PowerShell 웹 액세스에 로그인하기 전에 관리하려는 원격 컴퓨터의 이름이나 IP 주소를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-139">Before you sign in to Windows PowerShell Web Access, be sure that you have the name or IP address of the remote computer that you want to manage.</span></span> <span data-ttu-id="6c17b-140">사용자는 원격 컴퓨터에 대한 권한이 있어야 하고 원격 컴퓨터는 원격 관리를 허용하도록 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-140">You must be an authorized user on the remote computer, and it must be configured to allow remote management.</span></span> <span data-ttu-id="6c17b-141">원격 관리를 허용하도록 컴퓨터를 구성하는 방법에 대한 자세한 내용은 [Enable and Use Remote Commands in Windows PowerShell(Windows PowerShell에서 원격 명령 설정 및 사용)](https://technet.microsoft.com/magazine/ff700227.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c17b-141">For more information about configuring your computer to allow remote management, see [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span></span> <span data-ttu-id="6c17b-142">원격 관리를 허용하도록 컴퓨터를 구성하는 가장 간단한 방법은 관리자 권한(**관리자 권한으로 실행**)을 사용하여 열린 Windows PowerShell 세션에서 컴퓨터의 **Enable-PSRemoting -force** cmdlet을 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-142">The simplest method of configuring your computer to allow remote management is to run the **Enable-PSRemoting -force** cmdlet on the computer, in a Windows PowerShell session that has been opened with elevated user rights (**Run as Administrator**).</span></span>

### <a name="to-sign-in-to-windows-powershell-web-access"></a><span data-ttu-id="6c17b-143">Windows PowerShell 웹 액세스에 로그인하려면</span><span class="sxs-lookup"><span data-stu-id="6c17b-143">To sign in to Windows PowerShell Web Access</span></span>

1.  <span data-ttu-id="6c17b-144">인터넷 브라우저 창이나 탭에서 Windows PowerShell 웹 액세스 웹 사이트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-144">Open the Windows PowerShell Web Access website in an Internet browser window or tab.</span></span>

2.  <span data-ttu-id="6c17b-145">Windows PowerShell 웹 액세스 로그인 페이지에서 네트워크 사용자 이름과 암호 및 관리하려는 컴퓨터의 이름을 제공합니다(사용자는 해당 컴퓨터에 대한 권한이 있는 사용자임).</span><span class="sxs-lookup"><span data-stu-id="6c17b-145">On the Windows PowerShell Web Access sign-in page, provide your network user name, password, and the name of the computer that you want to manage (and on which you are an authorized user).</span></span> <span data-ttu-id="6c17b-146">Windows PowerShell 웹 액세스 관리자가 사용자에게 컴퓨터 이름 대신 사용자 지정 사이트나 프록시 서버의 URI를 사용하도록 지침을 내린 경우 **연결 유형** 필드에서 **연결 URI**를 선택한 다음 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-146">If the Windows PowerShell Web Access administrator has instructed you to use a URI to a custom site or proxy server instead of a computer name, select **Connection URI** in the **Connection type** field, and then provide the URI.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="6c17b-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="6c17b-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p><span data-ttu-id="6c17b-148">대상 컴퓨터가 작업 그룹에 있는 경우 &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt; 등의 구문을 이용하여 사용자 이름을 입력하고 컴퓨터에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-148">If the destination computer is in a workgroup, use the following syntax to provide your user name and sign in to the computer:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    <li><p><span data-ttu-id="6c17b-149">대상 컴퓨터가 게이트웨이 서버인 경우 <strong>컴퓨터 이름</strong> 필드에 <strong>localhost</strong>를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-149">If the destination computer is the gateway server, you can specify <strong>localhost</strong> in the <strong>Computer name</strong> field.</span></span></p></li>
    <li><p><span data-ttu-id="6c17b-150">대상 컴퓨터가 게이트웨이 서버이며 게이트웨이 서버가 작업 그룹에 있는 경우 <strong>컴퓨터 이름</strong> 필드에 <strong>localhost</strong>를 지정할 수 있지만 <strong>사용자 이름</strong> 필드에는 localhost\&lt;<em>user_name</em>&gt;을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-150">If the destination computer is the gateway server, and the gateway server is in a workgroup, you can use <strong>localhost</strong> in the <strong>Computer name</strong> field, but do not use localhost\&lt;<em>user_name</em>&gt; in the <strong>User name</strong> field.</span></span> <span data-ttu-id="6c17b-151">&lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-151">You must use &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  <span data-ttu-id="6c17b-152">**옵션 연결 설정** 섹션은 관리하려는 원격 컴퓨터의 권한 부여 요구 사항과 관련된 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-152">The **Optional Connection Settings** section relates to the authorization requirements of the remote computer that you want to manage.</span></span> <span data-ttu-id="6c17b-153">옵션 연결 설정에 해당하는 매개 변수에 대한 자세한 내용은 [Enter-PSSession cmdlet 도움말](https://technet.microsoft.com/library/dd315384.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c17b-153">For more information about the parameters that are equivalent to optional connection settings, see the [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx).</span></span>

    <span data-ttu-id="6c17b-154">대개 Windows PowerShell 웹 액세스 게이트웨이를 통한 전달에 사용하는 자격 증명은 관리하려는 원격 컴퓨터에서 인식되는 자격 증명과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-154">Typically, the credentials you use to pass through the Windows PowerShell Web Access gateway are the same that are recognized by the remote computer that you want to manage.</span></span> <span data-ttu-id="6c17b-155">하지만 2단계에서 지정된 원격 컴퓨터를 관리하는 데 다른 자격 증명을 사용하려면 **옵션 연결 설정** 섹션을 확장하여 대체 자격 증명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-155">However, if you want to use different credentials to manage the remote computer that you specified in step 2, expand the **Optional Connection Settings** section, and provide the alternate credentials.</span></span> <span data-ttu-id="6c17b-156">그렇지 않을 경우 6단계로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-156">Otherwise, skip to step 6.</span></span>

4.  <span data-ttu-id="6c17b-157">Windows PowerShell 웹 액세스 관리자가 Windows PowerShell 웹 액세스 사용자를 위해 사용자 지정 세션 구성을 만든 경우 **구성 이름** 필드에 세션 구성의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-157">If the Windows PowerShell Web Access administrator has created a custom session configuration for Windows PowerShell Web Access users, type the name of the session configuration name in the **Configuration name** field.</span></span> <span data-ttu-id="6c17b-158">세션 구성에 대한 자세한 내용은 Microsoft 웹 사이트에서 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c17b-158">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) on the Microsoft website.</span></span>

5.  <span data-ttu-id="6c17b-159">달리 Windows PowerShell 웹 액세스 관리자의 지침이 없는 한, **기본값**으로 설정된 **인증 유형**을 그대로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-159">Keep the **Authentication type** set to **Default** unless you have been instructed to do otherwise by the Windows PowerShell Web Access administrator.</span></span>

6.  <span data-ttu-id="6c17b-160">**로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-160">Click **Sign in**.</span></span>

<a href="" id="BKMK_timeout"></a>

<span data-ttu-id="6c17b-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">로그아웃 및 시간 초과</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing out and timing out</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="6c17b-162">다음 중 하나를 수행하여 웹 기반 Windows PowerShell 세션에서 로그아웃합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-162">Any of the following signs you out of a web-based Windows PowerShell session.</span></span>

-   <span data-ttu-id="6c17b-163">콘솔의 오른쪽 상단 모서리에 있는 **로그아웃**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-163">Clicking **Sign out** in the lower right corner of the console.</span></span> <span data-ttu-id="6c17b-164">(Windows Server 2012만 해당)</span><span class="sxs-lookup"><span data-stu-id="6c17b-164">(Windows Server 2012 only)</span></span>

-   <span data-ttu-id="6c17b-165">콘솔의 오른쪽 아래에 있는 **저장** 또는 **끝내기**를 클릭합니다(Windows Server 2012 R2만 해당).</span><span class="sxs-lookup"><span data-stu-id="6c17b-165">Clicking **Save** or **Exit** in the lower right corner of the console (Windows Server 2012 R2 only).</span></span> <span data-ttu-id="6c17b-166">**저장**을 클릭하면 Windows PowerShell 웹 액세스 세션이 저장되고 닫힙니다. 나중에 세션에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-166">Clicking **Save** saves and closes your Windows PowerShell Web Access session; you can reconnect to the session later.</span></span> <span data-ttu-id="6c17b-167">Windows PowerShell 웹 액세스에 다시 로그인하면 Windows PowerShell 웹 액세스에서 저장된 세션 목록을 표시합니다. 저장된 세션을 선택하고 다시 연결하거나 새 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-167">When you sign in to Windows PowerShell Web Access again, Windows PowerShell Web Access displays a list of your saved sessions; you can either select and reconnect to a saved session, or start a new session.</span></span> <span data-ttu-id="6c17b-168">사용자에게 허용되는 최대 열린 세션 수(저장 및 활성)는 게이트웨이 관리자가 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-168">The maximum number of open sessions that users are allowed, both saved and active, is configured by the gateway administrator.</span></span>

    <span data-ttu-id="6c17b-169">**끝내기**를 클릭하면 저장하지 않고 Windows PowerShell 웹 액세스 세션에서 로그아웃됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-169">Clicking **Exit** signs you out of the Windows PowerShell Web Access session without saving it.</span></span>

-   <span data-ttu-id="6c17b-170">동일한 브라우저 세션이나 동일한 브라우저 세션의 새 탭에서 다른 원격 컴퓨터를 관리하기 위해 로그인을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-170">Attempting to sign in to manage a different remote computer in the same browser session, or in a new tab of the same browser session.</span></span> <span data-ttu-id="6c17b-171">게이트웨이 서버가 Windows Server 2012 R2를 실행하는 경우에는 적용되지 않습니다. Windows Server 2012 R2에서 실행되는 Windows PowerShell 웹 액세스는 동일한 브라우저 세션의 새 탭에서 여러 사용자 세션을 허용하지 않습니다. 동일한 컴퓨터에서 둘 이상의 활성 세션을 사용하는 방법에 대한 자세한 내용은 이 항목의 [웹 기반 콘솔의 제한 사항](#BKMK_limits) 섹션에 있는 "동시에 여러 대상 컴퓨터에 연결"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c17b-171">(This does not apply if the gateway server is running Windows Server 2012 R2; Windows PowerShell Web Access running on Windows Server 2012 R2 does allow multiple user sessions in new tabs in the same browser session.) For more information about how to use more than one active session on the same computer, see “Connecting to multiple target computers simultaneously” in the [Limitations of the web-based console](#BKMK_limits) section of this topic.</span></span>

-   <span data-ttu-id="6c17b-172">세션 비활성 시간 제한은 20분입니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-172">20 minutes of inactivity in the session.</span></span> <span data-ttu-id="6c17b-173">게이트웨이 관리자는 비활성 시간 제한값을 사용자 지정할 수 있습니다. 자세한 내용은 [세션 관리](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c17b-173">The gateway administrator can customize the inactivity time-out period; for more information, see [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span></span>

    -   <span data-ttu-id="6c17b-174">직접 세션을 닫았기 때문이 아니라 네트워크 오류나 기타 계획되지 않은 종료 또는 오류로 인해 웹 기반 콘솔에서 세션 연결이 끊어진 경우 클라이언트 쪽의 시간 제한 기간이 경과할 때까지 Windows PowerShell 웹 액세스 세션이 대상 컴퓨터에 연결된 상태로 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-174">If you are disconnected from a session in the web-based console because of a network error or other unplanned shutdown or failure, and not because you have closed the session yourself, the Windows PowerShell Web Access session continues to run, connected to the target computer, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="6c17b-175">기본적으로,이 시간 제한 기간은 20분이며 게이트웨이 관리자가 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-175">By default, this time-out period is 20 minutes, and is configured by the gateway administrator.</span></span> <span data-ttu-id="6c17b-176">기본값인 20분 또는 게이트웨이 관리자가 지정한 시간 제한 기간 중 더 짧은 시간 후에 세션 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-176">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

        <span data-ttu-id="6c17b-177">게이트웨이 서버가 Windows Server 2012 R2를 실행하는 경우 Windows PowerShell 웹 액세스를 통해 사용자가 나중에 저장된 세션에 다시 연결할 수 있지만 게이트웨이 관리자가 지정한 시간 제한 기간이 경과할 때까지 저장된 세션을 보거나 다시 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-177">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but you cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

-   <span data-ttu-id="6c17b-178">브라우저 창이나 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-178">Closing the browser window or tab.</span></span>

-   <span data-ttu-id="6c17b-179">브라우저가 실행 중인 클라이언트 장치를 끄거나 네트워크와의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-179">Turning off the client device on which the browser is running, or disconnecting it from the network.</span></span>

-   <span data-ttu-id="6c17b-180">웹 콘솔에서 **끝내기** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-180">Running the **Exit** command in the web console.</span></span> <span data-ttu-id="6c17b-181">연결하려는 세션의 구성이 [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) 모드를 지원하도록 구성되어 있거나 제한된 runspace에 있는 경우에는 이 명령이 작동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-181">This command does not work if the session configuration to which you are connected to is configured to support [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) mode, or is in a restricted runspace.</span></span>

<span data-ttu-id="6c17b-182">다시 로그인하려면 Windows PowerShell 웹 액세스 웹 페이지를 다시 열고 이 항목의 [Windows PowerShell 웹 액세스에 로그인하려면](#BKMK_signin)에 설명된 단계를 수행하여 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-182">If you want to sign in again, open the Windows PowerShell Web Access web page again, and sign in by following the steps in [To sign in to Windows PowerShell Web Access](#BKMK_signin) in this topic.</span></span>

<a href="" id="BKMK_web"></a>

<span data-ttu-id="6c17b-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">웹 기반 Windows PowerShell 콘솔의 차이점</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differences in the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="6c17b-184">Windows PowerShell 웹 액세스에 로그인하고 나면 웹 기반 Windows PowerShell 콘솔이 브라우저 창이나 탭으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-184">After signing in to Windows PowerShell Web Access, a web-based Windows PowerShell console opens in your browser window or tab.</span></span> <span data-ttu-id="6c17b-185">이 콘솔은 로그인 과정에서 지정된 원격 컴퓨터와 연결되므로 원격 컴퓨터에서 사용 가능한 Windows PowerShell cmdlet 또는 스크립트만 콘솔에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-185">Because the console is connected to the remote computer that you specified during the sign-in process, only those Windows PowerShell cmdlets or scripts that are available on the remote computer can be used in the console.</span></span> <span data-ttu-id="6c17b-186">이 섹션에서는 Windows PowerShell 웹 액세스 콘솔의 제한 사항 및 Windows PowerShell 웹 액세스 콘솔과 설치된 **PowerShell.exe** 콘솔 간의 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-186">This section describes other limitations of Windows PowerShell Web Access consoles, and differences between Windows PowerShell Web Access consoles and the installed **PowerShell.exe** console.</span></span>

###

<span data-ttu-id="6c17b-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">PowerShell.exe를 사용하여 얻는 기능상의 차이점</span></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Functional disparity with PowerShell.exe</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="6c17b-188">대부분의 Windows PowerShell 호스트 기능은 Windows PowerShell 웹 액세스 웹 기반 콘솔에서도 사용할 수 있지만, 일부 기능은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-188">The majority of Windows PowerShell host functionality is available in the Windows PowerShell Web Access web-based console, but there are some features that are not available.</span></span>

-   <span data-ttu-id="6c17b-189"><span class="label">중첩된 진행률 표시.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-189"><span class="label">Nested progress displays.</span></span></span>  <span data-ttu-id="6c17b-190">Windows PowerShell 웹 액세스에서도 cmdlet의 진행 상황을 보고하는 진행률 GUI가 표시되지만, 최상위 수준의 진행률 정보만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-190">Windows PowerShell Web Access displays a progress GUI for cmdlets that report progress, but only top-level progress information is displayed.</span></span>

-   <span data-ttu-id="6c17b-191"><span class="label">입력 색 수정.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-191"><span class="label">Input color modification.</span></span></span>  <span data-ttu-id="6c17b-192">입력 색(전경/배경 둘 다)을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-192">The input color (both foreground and background) cannot be changed.</span></span> <span data-ttu-id="6c17b-193">출력, 경고, 자세한 정보 및 오류 메시지의 스타일은 모두 스크립트를 실행하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-193">The style of output, warning, verbose, and error messages can all be changed by running a script.</span></span>

-   <span data-ttu-id="6c17b-194"><span class="label">PSHostRawUserInterface.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-194"><span class="label">PSHostRawUserInterface.</span></span></span>  <span data-ttu-id="6c17b-195">Windows PowerShell 웹 액세스는 Windows PowerShell 원격 관리를 통해 구현되며 원격 runspace가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-195">Windows PowerShell Web Access is implemented over Windows PowerShell remote management, and uses a remote runspace.</span></span> <span data-ttu-id="6c17b-196">그러나 Windows PowerShell 웹 액세스는 이 인터페이스에서 일부 메서드(예: Windows 콘솔에 작성하는 모든 명령)를 구현하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-196">Windows PowerShell Web Access does not implement some methods in this interface; for example, any command that writes to the Windows console.</span></span> <span data-ttu-id="6c17b-197">**PowerTab** 등의 명령은 Windows PowerShell에서 작동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-197">Commands such as **PowerTab** do not work in Windows PowerShell Web Access.</span></span>

-   <span data-ttu-id="6c17b-198"><span class="label">기능 키.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-198"><span class="label">Function keys.</span></span></span>  <span data-ttu-id="6c17b-199">일부 기능 키는 대부분의 경우 브라우저에서 명령이 예약되어 있으므로 Windows PowerShell 웹 액세스에서는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-199">Windows PowerShell Web Access does not support some function keys, in many cases because the commands are reserved by the browser.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="6c17b-200">지원되지 않는 기능 키</span><span class="sxs-lookup"><span data-stu-id="6c17b-200">Unsupported Function Key</span></span></p></th>
<th><p><span data-ttu-id="6c17b-201">작업</span><span class="sxs-lookup"><span data-stu-id="6c17b-201">Action</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-202">Ctrl+C</span><span class="sxs-lookup"><span data-stu-id="6c17b-202">Ctrl+C</span></span></p></td>
<td><p><span data-ttu-id="6c17b-203">Windows PowerShell 웹 액세스에서 <strong>Ctrl+C</strong>는 브라우저에서 내용을 복사하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-203">In Windows PowerShell Web Access, <strong>Ctrl+C</strong> is used by the browser to copy content.</span></span> <span data-ttu-id="6c17b-204">이 콘솔에서는 <strong>취소</strong> 단추를 사용할 수 있으며, <strong>Ctrl+Q</strong>를 사용해 명령을 취소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-204">The console offers a <strong>Cancel</strong> button, and users can also use <strong>Ctrl+Q</strong> to cancel commands.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-205">Alt-space, e, l</span><span class="sxs-lookup"><span data-stu-id="6c17b-205">Alt-space, e, l</span></span></p></td>
<td><p><span data-ttu-id="6c17b-206">화면 버퍼를 통해 스크롤</span><span class="sxs-lookup"><span data-stu-id="6c17b-206">Scroll through the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-207">Alt+Space, e, f</span><span class="sxs-lookup"><span data-stu-id="6c17b-207">Alt+Space, e, f</span></span></p></td>
<td><p><span data-ttu-id="6c17b-208">화면 버퍼에서 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="6c17b-208">Search for text in the screen buffer</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-209">Alt+Space, e, k</span><span class="sxs-lookup"><span data-stu-id="6c17b-209">Alt+Space, e, k</span></span></p></td>
<td><p><span data-ttu-id="6c17b-210">화면 버퍼에서 복사할 텍스트 선택</span><span class="sxs-lookup"><span data-stu-id="6c17b-210">Select text to be copied from the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-211">Alt+Space, e, p</span><span class="sxs-lookup"><span data-stu-id="6c17b-211">Alt+Space, e, p</span></span></p></td>
<td><p><span data-ttu-id="6c17b-212">Windows PowerShell 콘솔에 클립보드 내용 붙여넣기</span><span class="sxs-lookup"><span data-stu-id="6c17b-212">Paste clipboard contents into the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-213">Alt+Space, c</span><span class="sxs-lookup"><span data-stu-id="6c17b-213">Alt+Space, c</span></span></p></td>
<td><p><span data-ttu-id="6c17b-214">Windows PowerShell 콘솔 닫기</span><span class="sxs-lookup"><span data-stu-id="6c17b-214">Close the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-215">Ctrl+Break</span><span class="sxs-lookup"><span data-stu-id="6c17b-215">Ctrl+Break</span></span></p></td>
<td><p><span data-ttu-id="6c17b-216">강제로 Windows PowerShell 창 닫기</span><span class="sxs-lookup"><span data-stu-id="6c17b-216">Force the Windows PowerShell window to close</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-217">Ctrl+Home</span><span class="sxs-lookup"><span data-stu-id="6c17b-217">Ctrl+Home</span></span></p></td>
<td><p><span data-ttu-id="6c17b-218">현재 명령줄의 처음부터 삭제</span><span class="sxs-lookup"><span data-stu-id="6c17b-218">Deletes from the beginning of the current command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-219">Ctrl+End</span><span class="sxs-lookup"><span data-stu-id="6c17b-219">Ctrl+End</span></span></p></td>
<td><p><span data-ttu-id="6c17b-220">명령줄의 끝까지 삭제</span><span class="sxs-lookup"><span data-stu-id="6c17b-220">Deletes to end of the command line</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-221">F1</span><span class="sxs-lookup"><span data-stu-id="6c17b-221">F1</span></span></p></td>
<td><p><span data-ttu-id="6c17b-222">명령줄에서 커서 위치의 한 문자를 오른쪽으로 이동</span><span class="sxs-lookup"><span data-stu-id="6c17b-222">Move cursor one character to the right on your command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-223">F2</span><span class="sxs-lookup"><span data-stu-id="6c17b-223">F2</span></span></p></td>
<td><p><span data-ttu-id="6c17b-224">마지막으로 실행한 명령을 입력된 문자로 복사하여 새로운 명령 만들기</span><span class="sxs-lookup"><span data-stu-id="6c17b-224">Creates a new command by copying your last command up to the character that you type</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-225">F3</span><span class="sxs-lookup"><span data-stu-id="6c17b-225">F3</span></span></p></td>
<td><p><span data-ttu-id="6c17b-226">마지막 명령줄의 내용으로 명령줄 완성</span><span class="sxs-lookup"><span data-stu-id="6c17b-226">Complete the command line with content from your last command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-227">F4</span><span class="sxs-lookup"><span data-stu-id="6c17b-227">F4</span></span></p></td>
<td><p><span data-ttu-id="6c17b-228">커서 위치의 문자 삭제</span><span class="sxs-lookup"><span data-stu-id="6c17b-228">Deletes characters from cursor position</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-229">F5</span><span class="sxs-lookup"><span data-stu-id="6c17b-229">F5</span></span></p></td>
<td><p><span data-ttu-id="6c17b-230">명령 기록을 역방향으로 검사</span><span class="sxs-lookup"><span data-stu-id="6c17b-230">Scan backward through your command history.</span></span> <span data-ttu-id="6c17b-231">Windows PowerShell 웹 액세스에서 명령 기록의 명령에 액세스하려면 웹 기반 콘솔에서 <strong>기록</strong> 스크롤 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-231">To access commands in the command history in Windows PowerShell Web Access, click the <strong>History</strong> scroll buttons in the web-based console.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-232">F7</span><span class="sxs-lookup"><span data-stu-id="6c17b-232">F7</span></span></p></td>
<td><p><span data-ttu-id="6c17b-233">명령 기록에서 대화형으로 명령 선택</span><span class="sxs-lookup"><span data-stu-id="6c17b-233">Interactively select a command from your command history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-234">F8</span><span class="sxs-lookup"><span data-stu-id="6c17b-234">F8</span></span></p></td>
<td><p><span data-ttu-id="6c17b-235">기록을 스캔하여 현재 텍스트와 일치하는 명령 표시</span><span class="sxs-lookup"><span data-stu-id="6c17b-235">Scan history displaying commands that match current text</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-236">F9</span><span class="sxs-lookup"><span data-stu-id="6c17b-236">F9</span></span></p></td>
<td><p><span data-ttu-id="6c17b-237">히스토리의 명령 중 특정 번호가 매겨진 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-237">Run a specific numbered command from history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-238">Page Up</span><span class="sxs-lookup"><span data-stu-id="6c17b-238">Page Up</span></span></p></td>
<td><p><span data-ttu-id="6c17b-239">기록의 첫 번째 명령 실행</span><span class="sxs-lookup"><span data-stu-id="6c17b-239">Run the first command in the history</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c17b-240">Page Down</span><span class="sxs-lookup"><span data-stu-id="6c17b-240">Page Down</span></span></p></td>
<td><p><span data-ttu-id="6c17b-241">히스토리의 마지막 명령 실행</span><span class="sxs-lookup"><span data-stu-id="6c17b-241">Run the last command in the history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c17b-242">Alt+F7</span><span class="sxs-lookup"><span data-stu-id="6c17b-242">Alt+F7</span></span></p></td>
<td><p><span data-ttu-id="6c17b-243">명령 기록 목록 지우기</span><span class="sxs-lookup"><span data-stu-id="6c17b-243">Clear the command history list</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="6c17b-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">웹 기반 콘솔의 제한 사항</span></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations of the web-based console</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="6c17b-245"><span class="label">더블 홉.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-245"><span class="label">Double-hop.</span></span></span>   <span data-ttu-id="6c17b-246">Windows PowerShell 웹 액세스를 사용하여 새로운 세션을 만들거나 새로운 세션에서 작업하려고 할 때 더블 홉(즉, 첫 번째 연결로 두 번째 컴퓨터에 연결) 제한 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-246">You can encounter the double-hop (or connecting to a second computer from the first connection) limitation if you try to create or work on a new session by using Windows PowerShell Web Access.</span></span> <span data-ttu-id="6c17b-247">Windows PowerShell 웹 액세스에서는 원격 runspace를 사용하는데, 현재 **PowerShell.exe**는 원격 runspace에서 두 번째 컴퓨터에 대한 원격 연결을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-247">Windows PowerShell Web Access uses a remote runspace, and currently, **PowerShell.exe** does not support establishing a remote connection to a second computer from a remote runspace.</span></span> <span data-ttu-id="6c17b-248">**Enter-PSSession** cmdlet을 사용하여 기존 연결을 통해 두 번째 원격 컴퓨터에 연결하려고 하면 "네트워크 리소스를 가져올 수 없습니다."와 같은 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-248">If you attempt to connect to a second remote computer from an existing connection by using the **Enter-PSSession** cmdlet, for example, you can get various errors, such as “Cannot get network resources.”</span></span>

    <span data-ttu-id="6c17b-249">이러한 더블 홉 오류를 방지하려면 관리자가 조직의 네트워크 환경에 CredSSP 인증을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-249">To avoid double-hop errors, your administrator should configure CredSSP authentication in your organization’s network environment.</span></span> <span data-ttu-id="6c17b-250">CredSSP 인증 구성에 대한 자세한 내용은 Microsoft 웹 사이트의 [두 번째 홉 원격 제어를 위한 CredSSP](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c17b-250">For more information about configuring CredSSP authentication, see [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) on the Microsoft website.</span></span> <span data-ttu-id="6c17b-251">두 번째 원격 컴퓨터를 관리하려는 경우 명시적 자격 증명을 제공할 수도 있지만, 암시적 자격 증명으로는 두 번째 홉이 허용되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-251">You can also provide explicit credentials when you want to manage a second remote computer; implicit credentials are unlikely to allow the second hop.</span></span>

-   <span data-ttu-id="6c17b-252">Windows PowerShell 웹 액세스에는 원격 Windows PowerShell 세션과 동일한 제약이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-252">Windows PowerShell Web Access uses and has the same limitations as a remote Windows PowerShell session.</span></span> <span data-ttu-id="6c17b-253">콘솔 기반 편집기나 텍스트 기반 메뉴 프로그램 같은 Windows 콘솔 API를 직접 호출하는 명령은 표준 입력, 출력 및 오류 파이프를 읽거나 쓸 수 없으므로 작동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-253">Commands that directly call Windows console APIs, such as those for console-based editors or text-based menu programs, do not work because the commands do not read or write to standard input, output, and error pipes.</span></span> <span data-ttu-id="6c17b-254">따라서 **notepad.exe** 등의 실행 파일을 시작하는 명령이나 <span class="code">OpenGridView</span> 또는 <span class="code">ogv</span> 같이 GUI를 표시하는 명령은 작동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-254">Therefore, commands that launch an executable file, such as **notepad.exe**, or display a GUI, such as <span class="code">OpenGridView</span> or <span class="code">ogv</span>, do not work.</span></span> <span data-ttu-id="6c17b-255">이러한 동작은 사용자의 작업 환경에 반영되므로 Windows PowerShell 웹 액세스가 사용자의 명령에 응답하지 않는 것처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-255">Your experience is affected by this behavior; to you, it appears that Windows PowerShell Web Access is not responding to your command.</span></span>

-   <span data-ttu-id="6c17b-256">제한된 runspace가 지원되거나 **NoLanguage** 모드 상태인 세션 구성에서는 탭 완성이 작동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-256">Tab completion does not work in a session configuration with a restricted runspace or one that is in **NoLanguage** mode.</span></span> <span data-ttu-id="6c17b-257">관리자가 탭 완성이 지원되도록 세션을 구성할 수 있지만 그럴 경우 다음과 같은 정보가 권한이 없는 사용자에게 노출될 수 있으므로 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-257">Although administrators can configure a session to support tab completion, it is discouraged for security reasons, because it can expose the following information to unauthorized users.</span></span>

    -   <span data-ttu-id="6c17b-258">내부 파일 시스템 경로</span><span class="sxs-lookup"><span data-stu-id="6c17b-258">Internal file system paths</span></span>

    -   <span data-ttu-id="6c17b-259">내부 컴퓨터의 공유 폴더</span><span class="sxs-lookup"><span data-stu-id="6c17b-259">Shared folders on internal computers</span></span>

    -   <span data-ttu-id="6c17b-260">runspace의 변수</span><span class="sxs-lookup"><span data-stu-id="6c17b-260">Variables in the runspace</span></span>

    -   <span data-ttu-id="6c17b-261">로드된 유형 또는 .NET Framework 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="6c17b-261">Loaded types or.NET Framework namespaces</span></span>

    -   <span data-ttu-id="6c17b-262">환경 변수</span><span class="sxs-lookup"><span data-stu-id="6c17b-262">Environment variables</span></span>

-   <span data-ttu-id="6c17b-263">Windows PowerShell 웹 액세스에서 **NoLanguage** 세션 구성이나 제한된 runspace에 로그인한 사용자는 **끝내기** 명령을 실행하여 세션을 종료할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-263">Users who are signed in to a **NoLanguage** session configuration or a restricted runspace in Windows PowerShell Web Access cannot run the **Exit** command to end the session.</span></span> <span data-ttu-id="6c17b-264">로그아웃하려면 콘솔 페이지에서 **로그아웃**을 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-264">To sign out, users should click **Sign Out** on the console page.</span></span>

-   <span data-ttu-id="6c17b-265"><span class="label">동시에 여러 대상 컴퓨터에 연결.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-265"><span class="label">Connecting to multiple target computers simultaneously.</span></span></span>   <span data-ttu-id="6c17b-266">게이트웨이 서버가 Windows Server 2012를 실행하는 경우 Windows PowerShell 웹 액세스에서는 브라우저 세션당 하나의 원격 컴퓨터만 연결할 수 있으며, 사용자가 한 번 로그인한 다음 별도의 브라우저 탭을 사용하여 여러 원격 컴퓨터에 연결하는 것은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-266">If the gateway server is running Windows Server 2012, Windows PowerShell Web Access allows only one remote computer connection per browser session; it does not allow users to sign in once, and connect to multiple remote computers by using separate browser tabs.</span></span> <span data-ttu-id="6c17b-267">새 탭이나 새 브라우저 창을 열면 Windows PowerShell 웹 액세스에서 현재 세션을 끊고 새 세션을 시작하라는 메시지가 표시되므로 새로운(또는 동일한) 원격 컴퓨터에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-267">When you open a new tab or new browser window, Windows PowerShell Web Access prompts you to disconnect your current session and start a new session, so that you can connect to the new (or the same) remote computer.</span></span> <span data-ttu-id="6c17b-268">하지만 서로 다른 원격 컴퓨터에 두 개 이상의 별도 세션을 원하는 경우 Internet Explorer를 통해 새 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-268">If two or more separate sessions to different remote computers are desired, however, a feature in Internet Explorer lets you create a new session.</span></span> <span data-ttu-id="6c17b-269">Internet Explorer에서 새 브라우저 세션을 시작하려면 **ALT** 키를 눌러 **파일** 메뉴를 열고 **새 세션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-269">To start a new browser session in Internet Explorer, press **ALT**, open the **File** menu, and then select **New Session**.</span></span> <span data-ttu-id="6c17b-270">그런 다음 Windows PowerShell 웹 액세스 웹 사이트를 새 세션에서 열고 다른 원격 컴퓨터로 로그인하여 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-270">Then, open the Windows PowerShell Web Access website in the new session, and sign in to access another remote computer.</span></span>

    <span data-ttu-id="6c17b-271">Windows PowerShell 웹 액세스 게이트웨이가 Windows Server 2012 R2에서 실행되는 경우 사용자는 다른 브라우저 탭에서 원격 컴퓨터에 대한 연결을 여러 개 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-271">When the Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, users can open multiple connections to remote computers in different browser tabs.</span></span> <span data-ttu-id="6c17b-272">웹 기반 Windows PowerShell 콘솔을 사용하여 원격 컴퓨터에 대한 연결을 두 개 이상 열려는 경우 Windows PowerShell 웹 액세스 게이트웨이 관리자에게 문의하여 이 기능이 게이트웨이 서버에서 지원되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-272">If you want to open more than one connection to a remote computer by using the web-based Windows PowerShell console, check with your Windows PowerShell Web Access gateway administrator to see if this feature is supported by the gateway server.</span></span>

-   <span data-ttu-id="6c17b-273"><span class="label">영구 Windows PowerShell 세션(다시 연결).</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-273"><span class="label">Persistent Windows PowerShell sessions (Reconnection).</span></span></span>   <span data-ttu-id="6c17b-274">Windows PowerShell 웹 액세스 게이트웨이의 시간이 초과된 후에는 게이트웨이와 대상 컴퓨터 간의 원격 연결이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-274">After you time out of the Windows PowerShell Web Access gateway, the remote connection between the gateway and the target computer is closed.</span></span> <span data-ttu-id="6c17b-275">이로 인해 현재 처리되고 있는 cmdlet 또는 스크립트가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-275">This stops any cmdlets or scripts that are currently in process.</span></span> <span data-ttu-id="6c17b-276">따라서 시간이 오래 걸리는 작업을 수행할 때는 작업을 시작하고, 컴퓨터와의 연결을 끊은 다음, 나중에 다시 연결하고, 작업을 지속할 수 있는 Windows PowerShell **-Job** 인프라를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-276">You are encouraged to use the Windows PowerShell **-Job** infrastructure when you are performing long-running tasks, so that you can start jobs, disconnect from the computer, reconnect later, and have jobs persist.</span></span> <span data-ttu-id="6c17b-277">또한 **-Job** cmdlet을 사용하면 Windows PowerShell 웹 액세스를 사용하여 작업을 시작한 다음 Windows PowerShell 웹 액세스 또는 다른 호스트(예: Windows PowerShell® ISE(통합 스크립팅 환경))를 실행하여 로그아웃하고 나중에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-277">Another benefit of using **-Job** cmdlets is that you can start them by using Windows PowerShell Web Access, sign out, and then reconnect later, either by running Windows PowerShell Web Access or another host (such as Windows PowerShell® Integrated Scripting Environment (ISE)).</span></span>

-   <span data-ttu-id="6c17b-278"><span class="label">콘솔 크기 조정.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-278"><span class="label">Console resizing.</span></span></span>   <span data-ttu-id="6c17b-279">**PowerShell.exe** 콘솔 창의 크기는 다음과 같은 세 가지 방법으로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-279">The **PowerShell.exe** console window can be resized in the following three ways.</span></span>

    -   <span data-ttu-id="6c17b-280">마우스를 사용하여 콘솔 창을 끌어 크기 조정</span><span class="sxs-lookup"><span data-stu-id="6c17b-280">Drag and adjust the console window size with a mouse</span></span>

    -   <span data-ttu-id="6c17b-281">콘솔 속성 GUI를 사용하여 높이 및 폭 속성 변경</span><span class="sxs-lookup"><span data-stu-id="6c17b-281">Change the height and width properties by using a GUI for console properties</span></span>

    -   <span data-ttu-id="6c17b-282">cmdlet을 사용하여 콘솔 창의 높이와 폭 변경</span><span class="sxs-lookup"><span data-stu-id="6c17b-282">Changing the height and width of console windows with a cmdlet</span></span>

        <span data-ttu-id="6c17b-283">Windows PowerShell 웹 액세스의 콘솔 창은 다음의 cmdlet을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-283">The console window for Windows PowerShell Web Access can be configured by using the cmdlets as follows.</span></span> <span data-ttu-id="6c17b-284">다음 예에서는 Windows PowerShell 웹 액세스 콘솔의 폭을 **20**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-284">In the following example, a user changes the width of Windows PowerShell Web Access console to **20**.</span></span>

        [<span data-ttu-id="6c17b-285">Copy</span><span class="sxs-lookup"><span data-stu-id="6c17b-285">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "클립보드에 복사.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        <span data-ttu-id="6c17b-286">이와 비슷한 방법으로 콘솔 높이를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-286">You can change the height of the console in a similar manner.</span></span>

        <span data-ttu-id="6c17b-287">콘솔 표시를 사용자 지정할 수 있는 추가적인 예가 [Windows PowerShell 팀 블로그](http://blogs.msdn.com/b/powershell/)에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-287">Additional examples for customizing the console view are available in the [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).</span></span>

<span data-ttu-id="6c17b-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">참고 항목</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="6c17b-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="6c17b-289">[Windows PowerShell Cmdlet 참조](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Microsoft TechNet의 Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet 스크립트 센터 리포지토리](http://gallery.technet.microsoft.com/scriptcenter)
[스크립트 센터 - 스크립팅 이용자 여러분!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell 팀 블로그](http://blogs.msdn.com/b/powershell/)</span><span class="sxs-lookup"><span data-stu-id="6c17b-289">[Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell on Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/)</span></span>

<span data-ttu-id="6c17b-290"><span>표시:</span> 상속됨 보호됨</span><span class="sxs-lookup"><span data-stu-id="6c17b-290"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="6c17b-291"><span class="stdr-votetitle">이 페이지가 도움이 되었나요?</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-291"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="6c17b-292">예 아니요</span><span class="sxs-lookup"><span data-stu-id="6c17b-292">Yes No</span></span>

<span data-ttu-id="6c17b-293">추가 피드백</span><span class="sxs-lookup"><span data-stu-id="6c17b-293">Additional feedback?</span></span>

<span data-ttu-id="6c17b-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span>자 남음</span> 제출 건너뛰기</span><span class="sxs-lookup"><span data-stu-id="6c17b-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="6c17b-295"><span class="stdr-thankyou">감사합니다.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-295"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="6c17b-296"><span class="stdr-appreciate">피드백에 감사드립니다.</span></span><span class="sxs-lookup"><span data-stu-id="6c17b-296"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="6c17b-297">프로필 관리</span><span class="sxs-lookup"><span data-stu-id="6c17b-297">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="6c17b-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 사이트 피드백</a> 사이트 피드백</span><span class="sxs-lookup"><span data-stu-id="6c17b-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="6c17b-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="6c17b-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="6c17b-300">사용 환경에 대한 의견을 제공해주세요...</span><span class="sxs-lookup"><span data-stu-id="6c17b-300">Tell us about your experience...</span></span>

<span data-ttu-id="6c17b-301">페이지가 빨리 로드되었나요?</span><span class="sxs-lookup"><span data-stu-id="6c17b-301">Did the page load quickly?</span></span>

<span data-ttu-id="6c17b-302"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="6c17b-302"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="6c17b-303">페이지 디자인이 마음에 드세요?</span><span class="sxs-lookup"><span data-stu-id="6c17b-303">Do you like the page design?</span></span>

<span data-ttu-id="6c17b-304"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="6c17b-304"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="6c17b-305">기타 의견</span><span class="sxs-lookup"><span data-stu-id="6c17b-305">Tell us more</span></span>

-   [<span data-ttu-id="6c17b-306">Flash 뉴스레터</span><span class="sxs-lookup"><span data-stu-id="6c17b-306">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="6c17b-307">연락처</span><span class="sxs-lookup"><span data-stu-id="6c17b-307">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="6c17b-308">개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="6c17b-308">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="6c17b-309">사용 조건</span><span class="sxs-lookup"><span data-stu-id="6c17b-309">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="6c17b-310">상표</span><span class="sxs-lookup"><span data-stu-id="6c17b-310">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="6c17b-311">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="6c17b-311">© 2016 Microsoft</span></span>

<span data-ttu-id="6c17b-312">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="6c17b-312">© 2016 Microsoft</span></span>

<span data-ttu-id="6c17b-313">본 웹 사이트에서 연결되거나 참조된 타사 스크립트 및 코드의 경우 Microsoft가 아닌 해당 코드를 소유한 측에서 사용자에게 라이선스를 허여합니다.</span><span class="sxs-lookup"><span data-stu-id="6c17b-313">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="6c17b-314">ASP.NET Ajax CDN 사용 약관 - http://www.asp.net/ajaxlibrary/CDN.ashx를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c17b-314">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

