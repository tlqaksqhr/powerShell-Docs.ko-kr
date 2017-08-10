---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 웹 액세스 제거"
ms.openlocfilehash: 7231d5eadceda8e3b28d9a81c2b5dcbe43680ff2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="69fb7-103">Windows PowerShell 웹 액세스 제거</span><span class="sxs-lookup"><span data-stu-id="69fb7-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="69fb7-104">업데이트됨: 2013년 6월 24일</span><span class="sxs-lookup"><span data-stu-id="69fb7-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="69fb7-105">적용 대상: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="69fb7-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="69fb7-106">Windows Server 2012 R2 또는 Windows Server 2012를 실행하는 게이트웨이 서버에서 Windows PowerShell 웹 액세스 웹 사이트 및 응용 프로그램을 삭제하려면 이 항목의 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-106">Follow steps in this topic to delete the Windows PowerShell Web Access website and application from the gateway server that is running either Windows Server 2012 R2 or Windows Server 2012.</span></span> <span data-ttu-id="69fb7-107">시작하기 전에 웹 기반 콘솔의 사용자에게 웹 사이트가 제거됨을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-107">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

<span data-ttu-id="69fb7-108">게이트웨이 서버에서 Windows PowerShell 웹 액세스를 제거하기 전에 <span class="code">Uninstall-PswaWebApplication</span> cmdlet을 실행하여 웹 사이트와 Windows PowerShell 웹 액세스 웹 응용 프로그램을 제거하거나, IIS 관리자 절차 [IIS 관리자를 사용하여 Windows PowerShell 웹 액세스 웹 사이트와 웹 응용 프로그램을 삭제하려면](#BKMK_delsite)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-108">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the <span class="code">Uninstall-PswaWebApplication</span> cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [To delete the Windows PowerShell Web Access website and web applications by using IIS Manager](#BKMK_delsite).</span></span>

<span data-ttu-id="69fb7-109">자동으로 설치된 IIS나 기타 기능은 Windows PowerShell 웹 액세스에서 실행되어야 하므로, Windows PowerShell 웹 액세스를 제거해도 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="69fb7-110">제거 프로세스에서는 Windows PowerShell 웹 액세스가 종속된 기능을 설치된 상태로 남겨 두기 때문에 필요한 경우 이러한 기능을 별도로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

<span data-ttu-id="69fb7-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">권장(빠른) 제거</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="69fb7-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69fb7-112">이 섹션의 절차를 따라서 Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스 웹 응용 프로그램 및 Windows PowerShell 웹 액세스 기능을 모두 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-112">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using Windows PowerShell cmdlets.</span></span>

###

<span data-ttu-id="69fb7-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">1단계: 웹 응용 프로그램 삭제</span></a></span><span class="sxs-lookup"><span data-stu-id="69fb7-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69fb7-114">고유의 사용자 지정 웹 사이트 이름을 지정한 경우 <span class="code">WebsiteName</span> 매개 변수를 명령에 추가하고 웹 사이트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-114">If you have specified your own, custom website name, add the <span class="code">WebsiteName</span> parameter to your command, and specify the website name.</span></span> <span data-ttu-id="69fb7-115">기본 응용 프로그램(**pswa**)이 아닌 사용자 지정 웹 응용 프로그램을 사용한 경우 <span class="code">WebApplicationName</span> 매개 변수를 명령에 추가하고 웹 응용 프로그램의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-115">If you have used a custom web application (not the default application, **pswa**, add the <span class="code">WebApplicationName</span> parameter to your command, and specify the name of the web application.</span></span>

#### <a name="to-delete-the-website-and-web-applications-by-using-the-uninstall-pswawebapplication-cmdlet"></a><span data-ttu-id="69fb7-116">Uninstall-PswaWebApplication cmdlet을 사용하여 웹 사이트와 웹 응용 프로그램을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="69fb7-116">To delete the website and web applications by using the Uninstall-PswaWebApplication cmdlet</span></span>

1.  <span data-ttu-id="69fb7-117">다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="69fb7-118">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="69fb7-119">Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="69fb7-120">**Uninstall-PswaWebApplication**을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-120">Type **Uninstall-PswaWebApplication**, and then press **Enter**.</span></span>

3.  <span data-ttu-id="69fb7-121">테스트 인증서를 사용하는 경우, 다음 예에서와 같이 cmdlet에 <span class="code">DeleteTestCertificate</span> 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-121">If you are using a test certificate, add the <span class="code">DeleteTestCertificate</span> parameter to the cmdlet, as shown in the following example.</span></span>

    [<span data-ttu-id="69fb7-122">Copy</span><span class="sxs-lookup"><span data-stu-id="69fb7-122">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "클립보드에 복사.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<span data-ttu-id="69fb7-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">2단계: Windows PowerShell 웹 액세스 제거</span></a></span><span class="sxs-lookup"><span data-stu-id="69fb7-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="69fb7-124">Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="69fb7-124">To uninstall Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="69fb7-125">다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="69fb7-126">세션이가 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="69fb7-127">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="69fb7-128">Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="69fb7-129">다음을 입력하고 **Enter** 키를 누릅니다. 여기서 *computer_name*은 Windows PowerShell 웹 액세스를 제거할 원격 서버를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="69fb7-130">제거 작업에 필요한 경우 <span class="code">-Restart</span> 매개 변수를 추가하여 대상 서버를 자동으로 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-130">The <span class="code">-Restart</span> parameter automatically restarts destination servers if required by the removal.</span></span>

    [<span data-ttu-id="69fb7-131">Copy</span><span class="sxs-lookup"><span data-stu-id="69fb7-131">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "클립보드에 복사.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="69fb7-132">역할 및 기능을 오프라인 VHD에서 제거하려는 경우에는 <span class="code">-ComputerName</span> 매개 변수와 <span class="code">-VHD</span> 매개 변수를 모두 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-132">To remove roles and features from an offline VHD, you must add both the <span class="code">-ComputerName</span> parameter and the <span class="code">-VHD</span> parameter.</span></span> <span data-ttu-id="69fb7-133"><span class="code">-ComputerName</span> 매개 변수에는 VHD를 탑재할 서버의 이름이 포함되며, <span class="code">-VHD</span> 매개 변수에는 지정된 서버에서의 VHD 파일 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-133">The <span class="code">-ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">-VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="69fb7-134">Copy</span><span class="sxs-lookup"><span data-stu-id="69fb7-134">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "클립보드에 복사.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

3.  <span data-ttu-id="69fb7-135">제거가 완료되면 서버 관리자에서 **모든 서버** 페이지를 열고 기능을 제거한 서버를 선택한 후 선택한 서버 페이지에서 **역할 및 기능** 타일을 확인하여 Windows PowerShell 웹 액세스가 제거되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-135">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span> <span data-ttu-id="69fb7-136">선택한 서버를 대상으로 <span class="code">Get-WindowsFeature</span> cmdlet(Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;)을 실행하여 서버에 설치된 역할 및 기능 목록을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-136">You can also run the <span class="code">Get-WindowsFeature</span> cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

<span data-ttu-id="69fb7-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">사용자 지정 제거</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="69fb7-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69fb7-138">이 섹션의 절차를 따라서 서버 관리자의 역할 및 기능 제거 마법사 및 IIS 관리자 콘솔을 사용하여 Windows PowerShell 웹 액세스 웹 응용 프로그램 및 Windows PowerShell 웹 액세스 기능을 모두 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-138">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

###

<span data-ttu-id="69fb7-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">1단계: 웹 응용 프로그램 삭제</span></a></span><span class="sxs-lookup"><span data-stu-id="69fb7-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-delete-the-windows-powershell-web-access-website-and-web-applications-by-using-iis-manager"></a><span data-ttu-id="69fb7-140">IIS 관리자를 사용하여 Windows PowerShell 웹 액세스의 웹 사이트와 웹 응용 프로그램을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="69fb7-140">To delete the Windows PowerShell Web Access website and web applications by using IIS Manager</span></span>

1.  <span data-ttu-id="69fb7-141">다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-141">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="69fb7-142">콘솔이 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-142">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="69fb7-143">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-143">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="69fb7-144">서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-144">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="69fb7-145">Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-145">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="69fb7-146">**응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-146">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="69fb7-147">IIS 관리자의 트리 창에서 Windows PowerShell 웹 액세스 웹 응용 프로그램이 실행 중인 웹 사이트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-147">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

3.  <span data-ttu-id="69fb7-148">**작업** 창의 **웹 사이트 관리**에서 **중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-148">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

4.  <span data-ttu-id="69fb7-149">트리 창에서 Windows PowerShell 웹 액세스 웹 응용 프로그램이 실행 중인 웹 사이트의 웹 응용 프로그램을 마우스 오른쪽 단추로 클릭한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-149">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

5.  <span data-ttu-id="69fb7-150">트리 창에서 **응용 프로그램 풀**을 선택하고 Windows PowerShell 웹 액세스 응용 프로그램 폴더를 선택한 후 **작업** 창에서 **중지**를 선택하고 내용 창에서 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-150">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

6.  <span data-ttu-id="69fb7-151">IIS 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-151">Close IIS Manager.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="69fb7-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="69fb7-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="69fb7-153">인증서는 제거 과정에서 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-153">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="69fb7-154">자체 서명된 인증서를 만들었거나 테스트 인증서를 사용한 경우에 이 인증서를 제거하려면 IIS 관리자에서 해당 인증서를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-154">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="69fb7-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">2단계: Windows PowerShell 웹 액세스 제거</span></a></span><span class="sxs-lookup"><span data-stu-id="69fb7-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="69fb7-156">역할 및 기능 제거 마법사를 사용하여 Windows PowerShell 웹 액세스를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="69fb7-156">To uninstall Windows PowerShell Web Access by using the Remove Roles and Features Wizard</span></span>

1.  <span data-ttu-id="69fb7-157">서버 관리자가 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-157">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="69fb7-158">서버 관리자가 아직 열려 있지 않으면 다음 중 하나를 수행하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-158">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="69fb7-159">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-159">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="69fb7-160">Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-160">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="69fb7-161">**관리** 메뉴에서 **역할 및 기능 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-161">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

3.  <span data-ttu-id="69fb7-162">**대상 서버 선택** 페이지에서 기능을 제거할 서버나 오프라인 VHD를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-162">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="69fb7-163">오프라인 VHD를 선택하려면 먼저 VHD가 탑재될 서버를 선택한 다음 VHD 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-163">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="69fb7-164">대상 서버를 선택하고 나면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-164">After you have selected the destination server, click **Next**.</span></span>

4.  <span data-ttu-id="69fb7-165">다시 **다음** 을 클릭하여 **기능 제거** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-165">Click **Next** again to skip to the **Remove features** page.</span></span>

5.  <span data-ttu-id="69fb7-166">**Windows PowerShell 웹 액세스**확인란의 선택을 취소하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-166">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

6.  <span data-ttu-id="69fb7-167">**제거 선택 확인** 페이지에서 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-167">On the **Confirm removal selections** page, click **Remove**.</span></span>

<span data-ttu-id="69fb7-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">참고 항목</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="69fb7-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69fb7-169">[Windows PowerShell 웹 액세스 설치 및 사용](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS 관리자 7.0 도움말](https://technet.microsoft.com/library/cc732664.aspx)</span><span class="sxs-lookup"><span data-stu-id="69fb7-169">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)</span></span>

<span data-ttu-id="69fb7-170"><span>표시:</span> 상속됨 보호됨</span><span class="sxs-lookup"><span data-stu-id="69fb7-170"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="69fb7-171"><span class="stdr-votetitle">이 페이지가 도움이 되었나요?</span></span><span class="sxs-lookup"><span data-stu-id="69fb7-171"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="69fb7-172">예 아니요</span><span class="sxs-lookup"><span data-stu-id="69fb7-172">Yes No</span></span>

<span data-ttu-id="69fb7-173">추가 피드백</span><span class="sxs-lookup"><span data-stu-id="69fb7-173">Additional feedback?</span></span>

<span data-ttu-id="69fb7-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span>자 남음</span> 제출 건너뛰기</span><span class="sxs-lookup"><span data-stu-id="69fb7-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="69fb7-175"><span class="stdr-thankyou">감사합니다.</span></span><span class="sxs-lookup"><span data-stu-id="69fb7-175"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="69fb7-176"><span class="stdr-appreciate">피드백에 감사드립니다.</span></span><span class="sxs-lookup"><span data-stu-id="69fb7-176"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="69fb7-177">프로필 관리</span><span class="sxs-lookup"><span data-stu-id="69fb7-177">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="69fb7-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 사이트 피드백</a> 사이트 피드백</span><span class="sxs-lookup"><span data-stu-id="69fb7-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="69fb7-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="69fb7-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="69fb7-180">사용 환경에 대한 의견을 제공해주세요...</span><span class="sxs-lookup"><span data-stu-id="69fb7-180">Tell us about your experience...</span></span>

<span data-ttu-id="69fb7-181">페이지가 빨리 로드되었나요?</span><span class="sxs-lookup"><span data-stu-id="69fb7-181">Did the page load quickly?</span></span>

<span data-ttu-id="69fb7-182"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="69fb7-182"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="69fb7-183">페이지 디자인이 마음에 드세요?</span><span class="sxs-lookup"><span data-stu-id="69fb7-183">Do you like the page design?</span></span>

<span data-ttu-id="69fb7-184"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="69fb7-184"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="69fb7-185">기타 의견</span><span class="sxs-lookup"><span data-stu-id="69fb7-185">Tell us more</span></span>

-   [<span data-ttu-id="69fb7-186">Flash 뉴스레터</span><span class="sxs-lookup"><span data-stu-id="69fb7-186">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="69fb7-187">연락처</span><span class="sxs-lookup"><span data-stu-id="69fb7-187">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="69fb7-188">개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="69fb7-188">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="69fb7-189">사용 조건</span><span class="sxs-lookup"><span data-stu-id="69fb7-189">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="69fb7-190">상표</span><span class="sxs-lookup"><span data-stu-id="69fb7-190">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="69fb7-191">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="69fb7-191">© 2016 Microsoft</span></span>

<span data-ttu-id="69fb7-192">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="69fb7-192">© 2016 Microsoft</span></span>

<span data-ttu-id="69fb7-193">본 웹 사이트에서 연결되거나 참조된 타사 스크립트 및 코드의 경우 Microsoft가 아닌 해당 코드를 소유한 측에서 사용자에게 라이선스를 허여합니다.</span><span class="sxs-lookup"><span data-stu-id="69fb7-193">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="69fb7-194">ASP.NET Ajax CDN 사용 약관 - http://www.asp.net/ajaxlibrary/CDN.ashx를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69fb7-194">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

