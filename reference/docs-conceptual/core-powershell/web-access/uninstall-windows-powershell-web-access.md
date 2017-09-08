---
ms.date: 2017-08-23
keywords: powershell,cmdlet
title: "Windows PowerShell 웹 액세스 제거"
ms.openlocfilehash: 6b75eadb7264d7478fb3c9bc2b2ff355772ef4c2
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="63553-103">Windows PowerShell 웹 액세스 제거</span><span class="sxs-lookup"><span data-stu-id="63553-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="63553-104">업데이트됨: 2013년 6월 24일</span><span class="sxs-lookup"><span data-stu-id="63553-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="63553-105">적용 대상: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="63553-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="63553-106">이 항목의 단계에서는 Windows PowerShell 웹 액세스 웹 사이트 및 해당 응용 프로그램을 설치된 게이트웨이 서버에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="63553-107">사용자에게 알림</span><span class="sxs-lookup"><span data-stu-id="63553-107">Notify users</span></span>

<span data-ttu-id="63553-108">시작하기 전에 웹 기반 콘솔의 사용자에게 웹 사이트가 제거됨을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="63553-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>


<span data-ttu-id="63553-109">게이트웨이 서버에서 Windows PowerShell 웹 액세스를 제거하기 전에 `Uninstall-PswaWebApplication` cmdlet을 실행하여 웹 사이트와 Windows PowerShell 웹 액세스 웹 응용 프로그램을 제거하거나, IIS 관리자 절차 [IIS 관리자를 사용하여 Windows PowerShell 웹 액세스 웹 사이트와 웹 응용 프로그램을 삭제하려면]()을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-109">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the `Uninstall-PswaWebApplication` cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [to delete the windows powershell web access website and web applications by using iis manager]().</span></span>

<span data-ttu-id="63553-110">자동으로 설치된 IIS나 기타 기능은 Windows PowerShell 웹 액세스에서 실행되어야 하므로, Windows PowerShell 웹 액세스를 제거해도 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63553-110">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="63553-111">제거 프로세스에서는 Windows PowerShell 웹 액세스가 종속된 기능을 설치된 상태로 남겨 두기 때문에 필요한 경우 이러한 기능을 별도로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63553-111">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="63553-112">권장(빠른) 제거</span><span class="sxs-lookup"><span data-stu-id="63553-112">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="63553-113">이 섹션의 절차에서는 Windows PowerShell cmdlet을 사용하여</span><span class="sxs-lookup"><span data-stu-id="63553-113">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="63553-114">Windows PowerShell 웹 액세스 웹 응용 프로그램 및</span><span class="sxs-lookup"><span data-stu-id="63553-114">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="63553-115">Windows PowerShell 웹 액세스 기능을</span><span class="sxs-lookup"><span data-stu-id="63553-115">the Windows PowerShell Web Access feature</span></span>
 
<span data-ttu-id="63553-116">모두 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63553-116">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="63553-117">1단계: cmdlet을 사용하여 웹 응용 프로그램 삭제</span><span class="sxs-lookup"><span data-stu-id="63553-117">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="63553-118">다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="63553-118">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="63553-119">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-119">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="63553-120">Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-120">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="63553-121">`Uninstall-PswaWebApplication`을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="63553-121">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="63553-122">고유의 사용자 지정 웹 사이트 이름을 지정한 경우 `-WebsiteName` 매개 변수를 명령에 추가하고 웹 사이트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-122">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="63553-123">기본 응용 프로그램(**pswa**)이 아닌 사용자 지정 웹 응용 프로그램을 사용한 경우 `-WebApplicationName` 매개 변수를 명령에 추가하고 웹 응용 프로그램의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-123">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="63553-124">테스트 인증서를 사용하는 경우, 다음 예에서와 같이 cmdlet에 `DeleteTestCertificate` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-124">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="63553-125">2단계: cmdlet을 사용하여 Windows PowerShell 웹 액세스 제거</span><span class="sxs-lookup"><span data-stu-id="63553-125">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1.  <span data-ttu-id="63553-126">다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="63553-126">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="63553-127">세션이가 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-127">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="63553-128">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-128">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="63553-129">Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-129">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="63553-130">다음을 입력하고 **Enter** 키를 누릅니다. 여기서 *computer_name*은 Windows PowerShell 웹 액세스를 제거할 원격 서버를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="63553-130">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="63553-131">제거 작업에 필요한 경우 `-Restart` 매개 변수를 추가하여 대상 서버를 자동으로 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63553-131">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="63553-132">역할 및 기능을 오프라인 VHD에서 제거하려는 경우에는 `-ComputerName` 매개 변수와 `-VHD` 매개 변수를 모두 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-132">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="63553-133">`-ComputerName` 매개 변수에는 VHD를 탑재할 서버의 이름이 포함되며, `-VHD` 매개 변수에는 지정된 서버에서의 VHD 파일 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="63553-133">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="63553-134">제거가 완료되면 서버 관리자에서 **모든 서버** 페이지를 열고 기능을 제거한 서버를 선택한 후 선택한 서버 페이지에서 **역할 및 기능** 타일을 확인하여 Windows PowerShell 웹 액세스가 제거되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-134">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="63553-135">또한 선택한 서버(Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;)를 대상으로 `Get-WindowsFeature` cmdlet을 실행하여 서버에 설치된 역할 및 기능 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63553-135">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="63553-136">사용자 지정 제거</span><span class="sxs-lookup"><span data-stu-id="63553-136">Custom uninstallation</span></span>

<span data-ttu-id="63553-137">이 섹션의 절차를 따라서 서버 관리자의 역할 및 기능 제거 마법사 및 IIS 관리자 콘솔을 사용하여 Windows PowerShell 웹 액세스 웹 응용 프로그램 및 Windows PowerShell 웹 액세스 기능을 모두 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63553-137">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="63553-138">1단계: IIS 관리자를 사용하여 웹 응용 프로그램 삭제</span><span class="sxs-lookup"><span data-stu-id="63553-138">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="63553-139">다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="63553-139">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="63553-140">콘솔이 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-140">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="63553-141">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-141">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="63553-142">서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-142">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="63553-143">Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-143">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="63553-144">**응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-144">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="63553-145">IIS 관리자의 트리 창에서 Windows PowerShell 웹 액세스 웹 응용 프로그램이 실행 중인 웹 사이트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-145">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="63553-146">**작업** 창의 **웹 사이트 관리**에서 **중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-146">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="63553-147">트리 창에서 Windows PowerShell 웹 액세스 웹 응용 프로그램이 실행 중인 웹 사이트의 웹 응용 프로그램을 마우스 오른쪽 단추로 클릭한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-147">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="63553-148">트리 창에서 **응용 프로그램 풀**을 선택하고 Windows PowerShell 웹 액세스 응용 프로그램 폴더를 선택한 후 **작업** 창에서 **중지**를 선택하고 내용 창에서 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-148">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="63553-149">IIS 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="63553-149">Close IIS Manager.</span></span>

> <span data-ttu-id="63553-150">![경고](images/SecurityNote.jpeg)**참고**:</span><span class="sxs-lookup"><span data-stu-id="63553-150">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="63553-151">인증서는 제거 과정에서 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63553-151">The certificate is not deleted during uninstallation.</span></span> 
>
> <span data-ttu-id="63553-152">자체 서명된 인증서를 만들었거나 테스트 인증서를 사용한 경우에 이 인증서를 제거하려면 IIS 관리자에서 해당 인증서를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-152">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span> 

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="63553-153">2단계: 역할 및 기능 제거 마법사를 사용하여 Windows PowerShell 웹 액세스 제거</span><span class="sxs-lookup"><span data-stu-id="63553-153">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="63553-154">서버 관리자가 이미 열려 있으면 다음 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-154">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="63553-155">서버 관리자가 아직 열려 있지 않으면 다음 중 하나를 수행하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="63553-155">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="63553-156">Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-156">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="63553-157">Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-157">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="63553-158">**관리** 메뉴에서 **역할 및 기능 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-158">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="63553-159">**대상 서버 선택** 페이지에서 기능을 제거할 서버나 오프라인 VHD를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-159">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="63553-160">오프라인 VHD를 선택하려면 먼저 VHD가 탑재될 서버를 선택한 다음 VHD 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-160">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="63553-161">대상 서버를 선택하고 나면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-161">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="63553-162">다시 **다음** 을 클릭하여 **기능 제거** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-162">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="63553-163">**Windows PowerShell 웹 액세스**확인란의 선택을 취소하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-163">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="63553-164">**제거 선택 확인** 페이지에서 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63553-164">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="63553-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63553-165">See Also</span></span>

- [<span data-ttu-id="63553-166">Windows PowerShell 웹 액세스 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="63553-166">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="63553-167">IIS 관리자 7.0 도움말</span><span class="sxs-lookup"><span data-stu-id="63553-167">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)
