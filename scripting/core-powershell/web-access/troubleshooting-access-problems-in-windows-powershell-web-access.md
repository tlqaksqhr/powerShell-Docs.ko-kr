---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 웹 액세스의 액세스 문제 해결"
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
#  <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="05cb7-103">Windows PowerShell 웹 액세스의 액세스 문제 해결</span><span class="sxs-lookup"><span data-stu-id="05cb7-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="05cb7-104">업데이트됨: 2013년 6월 24일</span><span class="sxs-lookup"><span data-stu-id="05cb7-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="05cb7-105">적용 대상: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="05cb7-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

<span data-ttu-id="05cb7-106">다음 표에는 Windows PowerShell 웹 액세스를 사용하여 원격 컴퓨터에 연결할 때 발생할 수 있는 몇 가지 일반적인 문제와 이러한 문제에 대한 해결 방안이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-106">The following table identifies some common problems that users might experience when they are attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="05cb7-107">문제</span><span class="sxs-lookup"><span data-stu-id="05cb7-107">Problem</span></span></p></th>
<th><p><span data-ttu-id="05cb7-108">가능한 원인 및 해결 방안</span><span class="sxs-lookup"><span data-stu-id="05cb7-108">Possible cause and solution</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="05cb7-109">로그인 오류</span><span class="sxs-lookup"><span data-stu-id="05cb7-109">Sign-in failure</span></span></p></td>
<td><p><span data-ttu-id="05cb7-110">다음과 같은 이유로 인해 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-110">Failure could occur because of any of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="05cb7-111">원격 컴퓨터에 특정 세션 구성이나 컴퓨터에 대한 사용자 액세스를 허용하는 권한 부여 규칙이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-111">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span> <span data-ttu-id="05cb7-112">Windows PowerShell 웹 액세스 보안이 제한적이므로 권한 부여 규칙을 사용하여 명시적으로 사용자에게 원격 컴퓨터에 대한 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-112">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span> <span data-ttu-id="05cb7-113">권한 부여 규칙을 만드는 방법에 대한 자세한 내용은 이 가이드의 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능</a>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05cb7-113">For more information about creating authorization rules, see <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> in this guide.</span></span></p></li>
<li><p><span data-ttu-id="05cb7-114">사용자에게는 대상 컴퓨터에 대해 허가받은 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-114">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="05cb7-115">이 권한은 ACL(액세스 제어 목록)에서 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-115">This is determined by access control lists (ACLs).</span></span> <span data-ttu-id="05cb7-116">자세한 내용은 <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">웹 기반 Windows PowerShell 콘솔 사용</a>의 "Windows PowerShell 웹 액세스에 로그인" 또는 <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell 팀 블로그</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05cb7-116">For more information, see “Signing in to Windows PowerShell Web Access” in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Use the Web-based Windows PowerShell Console</a>, or the <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>.</span></span></p>
<ul>
<li><p><span data-ttu-id="05cb7-117">Windows PowerShell 원격 관리 기능이 대상 컴퓨터에서 사용되지 않는 상태일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-117">Windows PowerShell remote management might not be enabled on the destination computer.</span></span> <span data-ttu-id="05cb7-118">사용자가 연결하려는 컴퓨터에서 이 기능이 사용되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-118">Verify that it is enabled on the computer to which the user is trying to connect.</span></span> <span data-ttu-id="05cb7-119">자세한 내용은 Windows PowerShell 정보 도움말 항목에 있는 <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a>의 " 컴퓨터를 원격으로 사용할 수 있도록 구성하는 방법"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05cb7-119">For more information, see “How to Configure Your Computer for Remoting” in <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> in the Windows PowerShell About Help Topics.</span></span></p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="05cb7-120">사용자가 Internet Explorer 창에서 Windows PowerShell 웹 액세스에 로그인하려고 하면 <strong>내부 서버 오류</strong> 페이지가 표시되거나 Internet Explorer의 응답이 중지되는 경우.</span><span class="sxs-lookup"><span data-stu-id="05cb7-120">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an <strong>Internal Server Error</strong> page, or Internet Explorer stops responding.</span></span> <span data-ttu-id="05cb7-121">이 문제는 Internet Explorer에서만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-121">This issue is specific to Internet Explorer.</span></span></p></td>
<td><p><span data-ttu-id="05cb7-122">이 문제는 사용자가 한자를 포함한 도메인 이름으로 로그인한 경우 또는 게이트웨이 서버 이름의 일부로 한자가 두 개 이상 포함된 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span> <span data-ttu-id="05cb7-123">이 문제를 해결하려면 사용자가 <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">Internet Explorer 10을 설치 및 실행</a>한 후 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-123">To work around this issue, the user should <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">install and run Internet Explorer 10</a>, and then perform the following steps.</span></span></p>
<ol>
<li><p><span data-ttu-id="05cb7-124">Internet Explorer <strong>문서 모드</strong> 설정을 <strong>IE10 표준</strong>으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-124">Change the Internet Explorer <strong>Document Mode</strong> setting to <strong>IE10 standards</strong>.</span></span></p>
<ol>
<li><p><span data-ttu-id="05cb7-125"><strong>F12</strong> 키를 눌러 개발자 도구 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-125">Press <strong>F12</strong> to open the Developer Tools console.</span></span></p></li>
<li><p><span data-ttu-id="05cb7-126">Internet Explorer 10에서 <strong>브라우저 모드</strong>를 클릭한 후 <strong>Internet Explorer 10</strong>을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-126">In Internet Explorer 10, click <strong>Browser Mode</strong>, and then select <strong>Internet Explorer 10</strong>.</span></span></p></li>
<li><p><span data-ttu-id="05cb7-127"><strong>문서 모드</strong>를 클릭한 후 <strong>IE10 표준</strong>을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-127">Click <strong>Document Mode</strong>, and then click <strong>IE10 standards</strong>.</span></span></p></li>
<li><p><span data-ttu-id="05cb7-128"><strong>F12</strong> 키를 다시 눌러 개발자 도구 콘솔을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-128">Press <strong>F12</strong> again to close the Developer Tools console.</span></span></p></li>
</ol></li>
<li><p><span data-ttu-id="05cb7-129">자동 프록시 구성을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-129">Disable automatic proxy configuration.</span></span></p>
<ol>
<li><p><span data-ttu-id="05cb7-130">Internet Explorer 10에서 <strong>도구</strong>를 클릭한 후 <strong>인터넷 옵션</strong>을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-130">In Internet Explorer 10, click <strong>Tools</strong>, and then click <strong>Internet Options</strong>.</span></span></p></li>
<li><p><span data-ttu-id="05cb7-131"><strong>인터넷 옵션</strong> 대화 상자의 <strong>연결</strong> 탭에서 <strong>LAN 설정</strong>을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-131">In the <strong>Internet Options</strong> dialog box, on the <strong>Connections</strong> tab, click <strong>LAN settings</strong>.</span></span></p></li>
<li><p><span data-ttu-id="05cb7-132"><strong>자동으로 설정 검색</strong> 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-132">Clear the <strong>Automatically detect settings</strong> check box.</span></span> <span data-ttu-id="05cb7-133"><strong>확인</strong>을 클릭한 후 다시 <strong>확인</strong>을 클릭하여 <strong>인터넷 옵션</strong> 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-133">Click <strong>OK</strong>, and then click <strong>OK</strong> again to close the <strong>Internet Options</strong> dialog box.</span></span></p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="05cb7-134">원격 작업 그룹 컴퓨터에 연결할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="05cb7-134">Cannot connect to a remote workgroup computer</span></span></p></td>
<td><p><span data-ttu-id="05cb7-135">대상 컴퓨터가 작업 그룹의 구성원인 경우에는 &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt; 등의 구문을 이용하여 사용자 이름을 입력하고 컴퓨터에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-135">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="05cb7-136">웹 서버(IIS) 역할이 설치되어 있는데도 웹 서버(IIS) 관리 도구를 찾을 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="05cb7-136">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span></p></td>
<td><p><span data-ttu-id="05cb7-137"><span class="code">Install-WindowsFeature</span> cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치한 경우 <span class="code">IncludeManagementTools</span> 매개 변수를 cmdlet에 추가하지 않으면 관리 도구가 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-137">If you installed Windows PowerShell Web Access by using the <span class="code">Install-WindowsFeature</span> cmdlet, management tools are not installed unless the <span class="code">IncludeManagementTools</span> parameter is added to the cmdlet.</span></span> <span data-ttu-id="05cb7-138">이에 해당하는 예는 <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Windows PowerShell 웹 액세스 설치 및 사용</a>의 "Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하려면"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05cb7-138">For an example, see “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>.</span></span> <span data-ttu-id="05cb7-139">IIS 관리자 콘솔 및 기타 IIS 관리 도구가 필요한 경우 게이트웨이 서버를 대상으로 하는 역할 및 기능 추가 마법사 세션에서 해당 도구를 선택하여 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-139">You can add the IIS Manager console and other IIS management tools that you need by selecting the tools in an Add Roles and Features Wizard session that is targeted at the gateway server.</span></span> <span data-ttu-id="05cb7-140">역할 및 기능 추가 마법사는 서버 관리자 내에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-140">The Add Roles and Features Wizard is opened from within Server Manager.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="05cb7-141">Windows PowerShell 웹 액세스 웹 사이트에 액세스할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="05cb7-141">The Windows PowerShell Web Access website is not accessible</span></span></p></td>
<td><p><span data-ttu-id="05cb7-142">Internet Explorer에서 보안 강화 구성(IE ESC)이 사용되는 경우 신뢰할 수 있는 사이트 목록에 Windows PowerShell 웹 액세스 웹 사이트를 추가하거나 IE ESC를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-142">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites, or disable IE ESC.</span></span> <span data-ttu-id="05cb7-143">IE ESC는 서버 관리자의 <strong>로컬 서버</strong> 페이지에 있는 <strong>속성</strong> 타일에서 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-143">You can disable IE ESC in the <strong>Properties</strong> tile on the <strong>Local Server</strong> page in Server Manager.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="05cb7-144">게이트웨이 서버가 대상 컴퓨터이고 작업 그룹에 있을 때 연결하려고 하면 다음 오류 메시지가 표시됩니다. <strong>권한 부여 오류가 발생했습니다. 대상 컴퓨터에 연결할 권한이 있는지 확인하세요.</strong></span><span class="sxs-lookup"><span data-stu-id="05cb7-144">The following error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup: <strong>An authorization failure occurred. Verify that you are authorized to connect to the destination computer.</strong></span></span></p></td>
<td><p><span data-ttu-id="05cb7-145">또한 게이트웨이 서버가 대상 서버이며 작업 그룹에 속해 있는 경우 사용자 이름, 컴퓨터 이름 및 사용자 그룹 이름을 다음 표와 같이 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-145">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name as shown in the following table.</span></span> <span data-ttu-id="05cb7-146">컴퓨터 이름을 나타내는 데에는 점(.)을 단독으로 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-146">Do not use a dot (.) by itself to represent the computer name.</span></span></p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="05cb7-147">시나리오</span><span class="sxs-lookup"><span data-stu-id="05cb7-147">Scenario</span></span></p></th>
<th><p><span data-ttu-id="05cb7-148">UserName 매개 변수</span><span class="sxs-lookup"><span data-stu-id="05cb7-148">UserName Parameter</span></span></p></th>
<th><p><span data-ttu-id="05cb7-149">UserGroup 매개 변수</span><span class="sxs-lookup"><span data-stu-id="05cb7-149">UserGroup Parameter</span></span></p></th>
<th><p><span data-ttu-id="05cb7-150">ComputerName 매개 변수</span><span class="sxs-lookup"><span data-stu-id="05cb7-150">ComputerName Parameter</span></span></p></th>
<th><p><span data-ttu-id="05cb7-151">ComputerGroup 매개 변수</span><span class="sxs-lookup"><span data-stu-id="05cb7-151">ComputerGroup Parameter</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="05cb7-152">도메인의 게이트웨이 서버</span><span class="sxs-lookup"><span data-stu-id="05cb7-152">Gateway server is in a domain</span></span></p></td>
<td><p><span data-ttu-id="05cb7-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em> 또는 .\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="05cb7-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> 또는 .\<em>user_group</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em>, or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="05cb7-155">정규화된 게이트웨이 서버의 이름 또는 Localhost</span><span class="sxs-lookup"><span data-stu-id="05cb7-155">Fully qualified name of gateway server, or Localhost</span></span></p></td>
<td><p><span data-ttu-id="05cb7-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> 또는 .\<em>computer_group</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em>, or .\<em>computer_group</em></span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="05cb7-157">작업 그룹의 게이트웨이 서버</span><span class="sxs-lookup"><span data-stu-id="05cb7-157">Gateway server is in a workgroup</span></span></p></td>
<td><p><span data-ttu-id="05cb7-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em> 또는 .\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="05cb7-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> 또는 .\<em>user_group</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="05cb7-160">서버 이름</span><span class="sxs-lookup"><span data-stu-id="05cb7-160">Server name</span></span></p></td>
<td><p><span data-ttu-id="05cb7-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> 또는 .\<em>computer_group</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> or .\<em>computer_group</em></span></span></p></td>
</tr>
</tbody>
</table>
</div>
<p><span data-ttu-id="05cb7-162">다음 중 하나로 형식화된 자격 증명을 사용하여 게이트웨이 서버에 대상 컴퓨터로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-162">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="05cb7-163"><em>Server_name</em>\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-163"><em>Server_name</em>\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="05cb7-164">Localhost\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-164">Localhost\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="05cb7-165">.\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="05cb7-165">.\<em>user_name</em></span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="05cb7-166">SID(보안 식별자)는 구문 <em>user_name</em>/<em>computer_name</em>  대신 권한 부여 규칙에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-166">A security identifier (SID) is displayed in an authorization rule instead of the syntax <em>user_name</em>/<em>computer_name</em> </span></span></p></td>
<td><p><span data-ttu-id="05cb7-167">규칙이 더 이상 유효하지 않거나, Active Directory 도메인 서비스를 쿼리하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-167">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="05cb7-168">권한 부여 규칙은 게이트웨이 서버가 이전에는 작업 그룹에 있었지만 나중에 도메인에 가입한 시나리오에서는 항상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-168">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="05cb7-169">권한 부여 규칙에 지정된 대상 컴퓨터에는 도메인의 IPv6 주소로 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-169">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span></p></td>
<td><p><span data-ttu-id="05cb7-170">권한 부여 규칙은 도메인 이름 형식의 IPv6 주소를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-170">Authorization rules do not support an IPv6 address in form of a domain name.</span></span> <span data-ttu-id="05cb7-171">IPv6 주소를 사용하여 대상 컴퓨터를 지정하려면 권한 부여 규칙의 원래 IPv6 주소(콜론 포함)를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="05cb7-171">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="05cb7-172">도메인과 숫자(콜론 포함)가 모두 포함된 IPv6 주소는 Windows PowerShell 웹 액세스 로그인 페이지에서 대상 컴퓨터 이름으로 사용할 수는 있지만 권한 부여 규칙에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-172">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> <span data-ttu-id="05cb7-173">IPv6 주소에 대한 자세한 내용은 <a href="https://technet.microsoft.com/library/cc781672.aspx">IPv6 작동 방법</a>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05cb7-173">For more information about IPv6 addresses, see <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="05cb7-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">참고 항목</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="05cb7-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="05cb7-175">[Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span><span class="sxs-lookup"><span data-stu-id="05cb7-175">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span></span>

<span data-ttu-id="05cb7-176"><span>표시:</span> 상속됨 보호됨</span><span class="sxs-lookup"><span data-stu-id="05cb7-176"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="05cb7-177"><span class="stdr-votetitle">이 페이지가 도움이 되었나요?</span></span><span class="sxs-lookup"><span data-stu-id="05cb7-177"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="05cb7-178">예 아니요</span><span class="sxs-lookup"><span data-stu-id="05cb7-178">Yes No</span></span>

<span data-ttu-id="05cb7-179">추가 피드백</span><span class="sxs-lookup"><span data-stu-id="05cb7-179">Additional feedback?</span></span>

<span data-ttu-id="05cb7-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span>자 남음</span> 제출 건너뛰기</span><span class="sxs-lookup"><span data-stu-id="05cb7-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="05cb7-181"><span class="stdr-thankyou">감사합니다.</span></span><span class="sxs-lookup"><span data-stu-id="05cb7-181"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="05cb7-182"><span class="stdr-appreciate">피드백에 감사드립니다.</span></span><span class="sxs-lookup"><span data-stu-id="05cb7-182"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="05cb7-183">프로필 관리</span><span class="sxs-lookup"><span data-stu-id="05cb7-183">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="05cb7-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 사이트 피드백</a> 사이트 피드백</span><span class="sxs-lookup"><span data-stu-id="05cb7-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="05cb7-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="05cb7-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="05cb7-186">사용 환경에 대한 의견을 제공해주세요...</span><span class="sxs-lookup"><span data-stu-id="05cb7-186">Tell us about your experience...</span></span>

<span data-ttu-id="05cb7-187">페이지가 빨리 로드되었나요?</span><span class="sxs-lookup"><span data-stu-id="05cb7-187">Did the page load quickly?</span></span>

<span data-ttu-id="05cb7-188"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="05cb7-188"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="05cb7-189">페이지 디자인이 마음에 드세요?</span><span class="sxs-lookup"><span data-stu-id="05cb7-189">Do you like the page design?</span></span>

<span data-ttu-id="05cb7-190"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="05cb7-190"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="05cb7-191">기타 의견</span><span class="sxs-lookup"><span data-stu-id="05cb7-191">Tell us more</span></span>

-   [<span data-ttu-id="05cb7-192">Flash 뉴스레터</span><span class="sxs-lookup"><span data-stu-id="05cb7-192">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="05cb7-193">연락처</span><span class="sxs-lookup"><span data-stu-id="05cb7-193">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="05cb7-194">개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="05cb7-194">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="05cb7-195">사용 조건</span><span class="sxs-lookup"><span data-stu-id="05cb7-195">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="05cb7-196">상표</span><span class="sxs-lookup"><span data-stu-id="05cb7-196">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="05cb7-197">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="05cb7-197">© 2016 Microsoft</span></span>

<span data-ttu-id="05cb7-198">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="05cb7-198">© 2016 Microsoft</span></span>

<span data-ttu-id="05cb7-199">본 웹 사이트에서 연결되거나 참조된 타사 스크립트 및 코드의 경우 Microsoft가 아닌 해당 코드를 소유한 측에서 사용자에게 라이선스를 허여합니다.</span><span class="sxs-lookup"><span data-stu-id="05cb7-199">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="05cb7-200">ASP.NET Ajax CDN 사용 약관 - http://www.asp.net/ajaxlibrary/CDN.ashx를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05cb7-200">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

