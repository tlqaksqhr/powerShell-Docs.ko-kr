---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능"
ms.openlocfilehash: 706830f618173879185f5b84570fdc7782434d59
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a><span data-ttu-id="e532c-103">Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능</span><span class="sxs-lookup"><span data-stu-id="e532c-103">Authorization Rules and Security Features of Windows PowerShell Web Access</span></span>

<span data-ttu-id="e532c-104">업데이트됨: 2013년 6월 24일</span><span class="sxs-lookup"><span data-stu-id="e532c-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="e532c-105">적용 대상: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e532c-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="e532c-106">Windows Server® 2012 R2 및 Windows Server® 2012의 Windows PowerShell® 웹 액세스에는 제한적인 보안 모델이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-106">Windows PowerShell® Web Access in Windows Server® 2012 R2 and Windows Server® 2012 has a restrictive security model.</span></span> <span data-ttu-id="e532c-107">사용자가 Windows PowerShell 웹 액세스 게이트웨이에 로그인하고 웹 기반 Windows PowerShell 콘솔을 사용할 수 있으려면 먼저 명시적으로 액세스 권한이 부여되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-107">Users must explicitly be granted access before they can sign in to the Windows PowerShell Web Access gateway and use the web-based Windows PowerShell console.</span></span>

-   [<span data-ttu-id="e532c-108">권한 부여 규칙 및 사이트 보안 구성</span><span class="sxs-lookup"><span data-stu-id="e532c-108">Configuring authorization rules and site security</span></span>](#BKMK_auth)

-   [<span data-ttu-id="e532c-109">세션 관리</span><span class="sxs-lookup"><span data-stu-id="e532c-109">Session management</span></span>](#BKMK_sesmgmt)


<span data-ttu-id="e532c-110">Windows PowerShell Web Access가 설치되고 게이트웨이가 구성되고 나면 사용자는 로그인 페이지를 브라우저에서 열 수 있지만 Windows PowerShell 웹 액세스 관리자가 사용자에게 액세스를 명시적으로 허용할 때까지는 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-110">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="e532c-111">Windows PowerShell 웹 액세스의 액세스 제어는 다음 표에 설명된 여러 Windows PowerShell cmdlet을 통해 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-111">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="e532c-112">권한 부여 규칙을 추가하거나 관리하는 작업에 해당하는 GUI는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-112">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="e532c-113">Windows PowerShell 웹 액세스 cmdlet에 대한 자세한 내용은 참조 항목 [Windows PowerShell 웹 액세스 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-113">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="e532c-114">관리자는 Windows PowerShell 웹 액세스에 대한 권한 부여 규칙을 정의하지 않을 수도 있고 원하는 수만큼(*n*개) 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-114">Administrators can define 0-*n* authentication rules for Windows PowerShell Web Access.</span></span> <span data-ttu-id="e532c-115">기본 보안은 허용적이지 않고 제한적이며, 0 인증 규칙은 사용자가 어디에도 액세스할 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-115">The default security is restrictive rather than permissive; zero authentication rules means no users have access to anything.</span></span>

<span data-ttu-id="e532c-116">Windows Server 2012 R2의 Add-PswaAuthorizationRule 및 Test-PswaAuthorizationRule에는 원격 컴퓨터 또는 활성 Windows PowerShell 웹 액세스 세션에서 Windows PowerShell 웹 액세스 권한 부여 규칙을 추가 및 테스트할 수 있게 해주는 Credential 매개 변수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-116">Add-PswaAuthorizationRule and Test-PswaAuthorizationRule in Windows Server 2012 R2 include a Credential parameter that allows you to add and test Windows PowerShell Web Access authorization rules from a remote computer, or from within an active Windows PowerShell Web Access session.</span></span> <span data-ttu-id="e532c-117">Credential 매개 변수가 있는 다른 Windows PowerShell cmdlet과 마찬가지로는 PSCredential 개체를 매개 변수 값으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-117">As with other Windows PowerShell cmdlets that have a Credential parameter, you can specify a PSCredential object as the value of the parameter.</span></span> <span data-ttu-id="e532c-118">원격 컴퓨터에 전달하려는 자격 증명이 포함된 PSCredential 개체를 만들려면 [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx) cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-118">To create a PSCredential object that contains credentials you want to pass to a remote computer, run the [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx) cmdlet.</span></span>

<span data-ttu-id="e532c-119">Windows PowerShell 웹 액세스 인증 규칙은 허용 목록 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-119">Windows PowerShell Web Access authentication rules are whitelist rules.</span></span> <span data-ttu-id="e532c-120">각 규칙은 사용자, 대상 컴퓨터 및 지정된 대상 컴퓨터의 특정 Windows PowerShell [세션 구성](https://technet.microsoft.com/library/dd819508.aspx)(끝점 또는 runspace라고도 함) 사이에 허용된 연결을 정의한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-120">Each rule is a definition of an allowed connection between users, target computers, and particular Windows PowerShell [session configurations](https://technet.microsoft.com/library/dd819508.aspx) (also referred to as endpoints or runspaces) on specified target computers.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e532c-121"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 보안 정보 </span></span><span class="sxs-lookup"><span data-stu-id="e532c-121"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e532c-122">사용자는 참인 규칙이 하나만 있어야 액세스 권한을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-122">A user needs only one rule to be true to get access.</span></span> <span data-ttu-id="e532c-123">웹 기반 콘솔에서 모든 언어에 액세스할 수 있는 권한이든, Windows PowerShell 원격 관리 cmdlet에만 액세스할 수 있는 권한이든, 사용자에게 한 컴퓨터에 대한 액세스 권한이 주어지면 사용자는 첫 번째 대상 컴퓨터에 연결된 다른 컴퓨터에도 로그온(또는 홉)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-123">If a user is given access to one computer with either full language access or access only to Windows PowerShell remote management cmdlets, from the web-based console, the user can log on (or hop) to other computers that are connected to the first target computer.</span></span> <span data-ttu-id="e532c-124">Windows PowerShell 웹 액세스를 가장 안전하게 구성하는 방법은 사용자가 일반적으로 원격 작업을 수행할 수 있는 제한된 세션 구성(끝점 또는 runspace라고도 함)만 액세스할 수 있도록 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-124">The most secure way to configure Windows PowerShell Web Access is to allow users access only to constrained session configurations (also called endpoints or runspaces) that allow them to accomplish specific tasks that they normally need to perform remotely.</span></span></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="e532c-125">이름</span><span class="sxs-lookup"><span data-stu-id="e532c-125">Name</span></span></p></th>
<th><p><span data-ttu-id="e532c-126">설명</span><span class="sxs-lookup"><span data-stu-id="e532c-126">Description</span></span></p></th>
<th><p><span data-ttu-id="e532c-127">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e532c-127">Parameters</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e532c-128"><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="e532c-128"><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="e532c-129">새로운 권한 부여 규칙을 Windows PowerShell 웹 액세스 권한 부여 규칙 집합에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-129">Adds a new authorization rule to the Windows PowerShell Web Access authorization rule set.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="e532c-130">ComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="e532c-130">ComputerGroupName</span></span></p></li>
<li><p><span data-ttu-id="e532c-131">ComputerName</span><span class="sxs-lookup"><span data-stu-id="e532c-131">ComputerName</span></span></p></li>
<li><p><span data-ttu-id="e532c-132">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="e532c-132">ConfigurationName</span></span></p></li>
<li><p><span data-ttu-id="e532c-133">RuleName</span><span class="sxs-lookup"><span data-stu-id="e532c-133">RuleName</span></span></p></li>
<li><p><span data-ttu-id="e532c-134">UserGroupName</span><span class="sxs-lookup"><span data-stu-id="e532c-134">UserGroupName</span></span></p></li>
<li><p><span data-ttu-id="e532c-135">UserName</span><span class="sxs-lookup"><span data-stu-id="e532c-135">UserName</span></span></p></li>
<li><p><span data-ttu-id="e532c-136">자격 증명(Windows Server 2012 R2 이상)</span><span class="sxs-lookup"><span data-stu-id="e532c-136">Credential (Windows Server 2012 R2 and later)</span></span></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e532c-137"><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="e532c-137"><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="e532c-138">지정된 권한 부여 규칙을 Windows PowerShell 웹 액세스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-138">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="e532c-139">Id</span><span class="sxs-lookup"><span data-stu-id="e532c-139">Id</span></span></p></li>
<li><p><span data-ttu-id="e532c-140">RuleName</span><span class="sxs-lookup"><span data-stu-id="e532c-140">RuleName</span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e532c-141"><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="e532c-141"><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="e532c-142">일련의 Windows PowerShell 웹 액세스 권한 부여 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-142">Returns a set of Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="e532c-143">이 cmdlet에 매개 변수를 지정하지 않고 실행하면 모든 규칙이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-143">When it is used without parameters, the cmdlet returns all rules.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="e532c-144">Id</span><span class="sxs-lookup"><span data-stu-id="e532c-144">Id</span></span></p></li>
<li><p><span data-ttu-id="e532c-145">RuleName</span><span class="sxs-lookup"><span data-stu-id="e532c-145">RuleName</span></span></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e532c-146"><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="e532c-146"><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="e532c-147">권한 부여 규칙을 평가하여 특정 사용자, 컴퓨터 또는 세션 구성에 대한 액세스 요청이 허용되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-147">Evaluates authorization rules to determine if a specific user, computer, or session configuration access request is authorized.</span></span> <span data-ttu-id="e532c-148">매개 변수를 추가하지 않으면 기본적으로 모든 권한 부여 규칙이 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-148">By default, if no parameters are added, the cmdlet evaluates all authorization rules.</span></span> <span data-ttu-id="e532c-149">관리자는 매개 변수를 추가하여 테스트할 권한 부여 규칙이나 그 하위 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-149">By adding parameters, administrators can specify an authorization rule or a subset of rules to test.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="e532c-150">ComputerName</span><span class="sxs-lookup"><span data-stu-id="e532c-150">ComputerName</span></span></p></li>
<li><p><span data-ttu-id="e532c-151">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="e532c-151">ConfigurationName</span></span></p></li>
<li><p><span data-ttu-id="e532c-152">RuleName</span><span class="sxs-lookup"><span data-stu-id="e532c-152">RuleName</span></span></p></li>
<li><p><span data-ttu-id="e532c-153">UserName</span><span class="sxs-lookup"><span data-stu-id="e532c-153">UserName</span></span></p></li>
<li><p><span data-ttu-id="e532c-154">자격 증명(Windows Server 2012 R2 이상)</span><span class="sxs-lookup"><span data-stu-id="e532c-154">Credential (Windows Server 2012 R2 and later)</span></span></p></li>
</ul></td>
</tr>
</tbody>
</table>

<span data-ttu-id="e532c-155">위의 cmdlet에서는 Windows PowerShell 웹 액세스 게이트웨이의 사용자에게 권한을 부여하는 데 사용되는 일련의 액세스 규칙이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-155">The preceding cmdlets create a set of access rules which are used to authorize a user on the Windows PowerShell Web Access gateway.</span></span> <span data-ttu-id="e532c-156">이러한 규칙은 대상 컴퓨터에 대한 ACL(액세스 제어 목록)과는 다른 것으로 웹 액세스에 대한 추가 보안 계층을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-156">The rules are different from the access control lists (ACLs) on the destination computer, and provide an additional layer of security for web access.</span></span> <span data-ttu-id="e532c-157">보안에 대한 자세한 내용은 다음 섹션에서 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-157">More details about security are described in the following section.</span></span>

<span data-ttu-id="e532c-158">사용자가 위의 보안 계층을 하나도 통과하지 못하면 브라우저 창에 일반적인 “액세스 거부” 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-158">If users cannot pass any of the preceding security layers, they receive a generic “access denied” message in their browser windows.</span></span> <span data-ttu-id="e532c-159">자세한 보안 정보가 게이트웨이 서버에서 기록되지만 최종 사용자에게는 통과한 보안 계층 개수 또는 로그인이나 인증에 실패한 계층에 대한 정보가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-159">Although security details are logged on the gateway server, end users are not shown information about how many security layers they passed, or at which layer the sign-in or authentication failure occurred.</span></span>

<span data-ttu-id="e532c-160">권한 부여 규칙을 구성하는 방법에 대한 자세한 내용은 이 항목의 [권한 부여 규칙 구성](#BKMK_configrules)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-160">For more information about configuring authorization rules, see [Configuring authorization rules](#BKMK_configrules) in this topic.</span></span>

<a href="" id="BKMK_sec"></a>
###

<span data-ttu-id="e532c-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">보안</span></a></span><span class="sxs-lookup"><span data-stu-id="e532c-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Security</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="e532c-162">Windows PowerShell 웹 액세스 보안 모델은 웹 기반 콘솔의 최종 사용자와 대상 컴퓨터 간의 4단계 계층으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-162">The Windows PowerShell Web Access security model has four layers between an end user of the web-based console, and a target computer.</span></span> <span data-ttu-id="e532c-163">Windows PowerShell 웹 액세스 관리자는 IIS 관리자 콘솔에서의 추가 구성을 통해 보안 계층을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-163">Windows PowerShell Web Access administrators can add security layers through additional configuration in the IIS Manager console.</span></span> <span data-ttu-id="e532c-164">IIS 관리자 콘솔에서 웹 사이트를 보호하는 방법에 대한 자세한 내용은 [웹 서버 보안 구성(IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-164">For more information about securing websites in the IIS Manager console, see [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx).</span></span> <span data-ttu-id="e532c-165">IIS 모범 사례 및 서비스 거부 공격 방지에 대한 자세한 내용은 [서비스 거부 공격 방지를 위한 모범 사례](https://technet.microsoft.com/library/cc750213.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-165">For more information about IIS best practices and preventing denial-of-service attacks, see [Best Practices for Preventing DoS/Denial of Service Attacks](https://technet.microsoft.com/library/cc750213.aspx).</span></span> <span data-ttu-id="e532c-166">관리자는 인증 소프트웨어 정품을 추가로 구매하여 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-166">An administrator can also buy and install additional, retail authentication software.</span></span>

<span data-ttu-id="e532c-167">다음 표에는 최종 사용자와 대상 컴퓨터 간의 4단계 보안 계층이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-167">The following table describes the four layers of security between end users and target computers.</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="e532c-168">순서</span><span class="sxs-lookup"><span data-stu-id="e532c-168">Order</span></span></p></th>
<th><p><span data-ttu-id="e532c-169">계층</span><span class="sxs-lookup"><span data-stu-id="e532c-169">Layer</span></span></p></th>
<th><p><span data-ttu-id="e532c-170">설명</span><span class="sxs-lookup"><span data-stu-id="e532c-170">Description</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e532c-171">1</span><span class="sxs-lookup"><span data-stu-id="e532c-171">1</span></span></p></td>
<td><p><span data-ttu-id="e532c-172">클라이언트 인증서 인증과 같은 웹 서버(IIS) 보안 기능</span><span class="sxs-lookup"><span data-stu-id="e532c-172">Web Server (IIS) security features, such as client certificate authentication</span></span></p></td>
<td><p><span data-ttu-id="e532c-173">Windows PowerShell 웹 액세스 사용자는 게이트웨이에서 자신의 계정을 인증하려면 항상 사용자 이름과 암호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-173">Windows PowerShell Web Access users must always provide a user name and password to authenticate their accounts on the gateway.</span></span> <span data-ttu-id="e532c-174">하지만 Windows PowerShell 웹 액세스 관리자는 클라이언트 인증서 인증을 선택적으로 켜거나 끌 수도 있습니다(<a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access(Windows PowerShell 웹 액세스 설치 및 사용)</a>의 10단계인 "IIS 관리자를 사용하여 기존 웹 사이트에 게이트웨이를 구성하려면" 참조).</span><span class="sxs-lookup"><span data-stu-id="e532c-174">However, Windows PowerShell Web Access administrators can also turn optional client certificate authentication on or off (see step 10 of “To use IIS Manager to configure the gateway in an existing website” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>).</span></span> <span data-ttu-id="e532c-175">선택적인 클라이언트 인증서 기능을 사용하려면 최종 사용자에게 사용자 이름과 암호 이외에 유효한 클라이언트 인증서가 있어야 하며, 이러한 기능은 웹 서버(IIS) 구성의 일부로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-175">The optional client certificate feature requires end users to have a valid client certificate, in addition to their user names and passwords, and is part of Web Server (IIS) configuration.</span></span> <span data-ttu-id="e532c-176">클라이언트 인증서 계층이 사용하도록 설정되면 Windows PowerShell 웹 액세스 로그인 페이지에서는 사용자의 로그인 자격 증명을 확인하기 전에 사용자에게 유효한 인증서를 제공하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-176">When the client certificate layer is enabled, the Windows PowerShell Web Access sign-in page prompts users to provide valid certificates before their sign-in credentials are evaluated.</span></span> <span data-ttu-id="e532c-177">클라이언트 인증서 인증에서는 클라이언트 인증서를 자동으로 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-177">Client certificate authentication automatically checks for the client certificate.</span></span></p>
<p><span data-ttu-id="e532c-178">유효한 인증서가 없으면 Windows PowerShell 웹 액세스에서 사용자에게 인증서를 제공하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-178">If a valid certificate is not found, Windows PowerShell Web Access informs users, so they can provide the certificate.</span></span> <span data-ttu-id="e532c-179">유효한 클라이언트 인증서가 검색되면 Windows PowerShell 웹 액세스에서 사용자가 해당하는 사용자 이름과 암호를 입력할 로그인 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-179">If a valid client certificate is found, Windows PowerShell Web Access opens the sign-in page for users to provide their user names and passwords.</span></span></p>
<p><span data-ttu-id="e532c-180">이는 웹 서버(IIS)에서 제공되는 추가 보안 설정의 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-180">This is one example of additional security settings that are offered by Web Server (IIS).</span></span> <span data-ttu-id="e532c-181">기타 IIS 보안 기능에 대한 자세한 내용은 <a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">웹 서버 보안 구성(IIS 7)</a>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-181">For more information about other IIS security features, see <a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">Configure Web Server Security (IIS 7)</a>.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e532c-182">2</span><span class="sxs-lookup"><span data-stu-id="e532c-182">2</span></span></p></td>
<td><p><span data-ttu-id="e532c-183">Windows PowerShell 웹 액세스 양식 기반 게이트웨이 인증</span><span class="sxs-lookup"><span data-stu-id="e532c-183">Windows PowerShell Web Access forms-based gateway authentication</span></span></p></td>
<td><p><span data-ttu-id="e532c-184">Windows PowerShell 웹 액세스 로그인 페이지에서는 자격 증명 세트(사용자 이름과 암호)를 요구하며, 대상 컴퓨터에 대해 다른 자격 증명을 제공할 수 있는 옵션을 사용자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-184">The Windows PowerShell Web Access sign-in page requires a set of credentials (user name and password) and offers users the option of providing different credentials for the target computer.</span></span> <span data-ttu-id="e532c-185">사용자가 대체 자격 증명을 제공하지 않으면 게이트웨이 연결에 사용되는 기본 사용자 이름과 암호가 대상 컴퓨터와 연결하는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-185">If the user does not provide alternate credentials, the primary user name and password that are used to connect to the gateway are also used to connect to the target computer.</span></span></p>
<p><span data-ttu-id="e532c-186">이렇게 요구된 자격 증명은 Windows PowerShell 웹 액세스 게이트웨이에서 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-186">The required credentials are authenticated on the Windows PowerShell Web Access gateway.</span></span> <span data-ttu-id="e532c-187">이러한 자격 증명은 로컬 Windows PowerShell 게이트웨이 서버나 Active Directory®의 유효한 사용자 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-187">These credentials must be valid user accounts on either the local Windows PowerShell Web Access gateway server, or in Active Directory®.</span></span></p>
<p><span data-ttu-id="e532c-188">사용자가 게이트웨이에서 인증되고 나면 Windows PowerShell 웹 액세스는 권한 부여 규칙을 점검하여 요청된 대상 컴퓨터에 대한 액세스 권한이 사용자에게 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-188">After a user is authenticated at the gateway, Windows PowerShell Web Access checks authorization rules to verify if the user has access to the requested target computer.</span></span> <span data-ttu-id="e532c-189">권한 부여에 성공하면 사용자의 자격 증명이 대상 컴퓨터에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-189">After successful authorization, the user’s credentials are passed along to the target computer.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e532c-190">3</span><span class="sxs-lookup"><span data-stu-id="e532c-190">3</span></span></p></td>
<td><p><span data-ttu-id="e532c-191">Windows PowerShell 웹 액세스 권한 부여 규칙</span><span class="sxs-lookup"><span data-stu-id="e532c-191">Windows PowerShell Web Access authorization rules</span></span></p></td>
<td><p><span data-ttu-id="e532c-192">사용자가 게이트웨이에서 인증되고 나면 Windows PowerShell 웹 액세스는 권한 부여 규칙을 점검하여 요청된 대상 컴퓨터에 대한 액세스 권한이 사용자에게 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-192">After a user is authenticated at the gateway, Windows PowerShell Web Access checks authorization rules to verify if the user has access to the requested target computer.</span></span> <span data-ttu-id="e532c-193">권한 부여에 성공하면 사용자의 자격 증명이 대상 컴퓨터에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-193">After successful authorization, the user’s credentials are passed along to the target computer.</span></span></p>
<p><span data-ttu-id="e532c-194">이러한 규칙은 사용자가 게이트웨이에서 인증된 이후에만 평가할 수 있으며, 그 전에 대상 컴퓨터에서 사용자를 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-194">These rules are evaluated only after a user has been authenticated by the gateway, and before a user can be authenticated on a target computer.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e532c-195">4</span><span class="sxs-lookup"><span data-stu-id="e532c-195">4</span></span></p></td>
<td><p><span data-ttu-id="e532c-196">대상 인증 및 권한 부여 규칙</span><span class="sxs-lookup"><span data-stu-id="e532c-196">Target authentication and authorization rules</span></span></p></td>
<td><p><span data-ttu-id="e532c-197">Windows PowerShell 웹 액세스의 보안을 위한 마지막 계층은 대상 컴퓨터의 자체 보안 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-197">The final layer of security for Windows PowerShell Web Access is the target computer’s own security configuration.</span></span> <span data-ttu-id="e532c-198">사용자는 대상 컴퓨터와 Windows PowerShell 웹 액세스 권한 부여 규칙에 적절한 액세스 권한이 구성되어 있어야 Windows PowerShell 웹 액세스를 통해 대상 컴퓨터를 관리할 수 있는 Windows PowerShell 웹 기반 콘솔을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-198">Users must have the appropriate access rights configured on the target computer, and also in the Windows PowerShell Web Access authorization rules, to run a Windows PowerShell web-based console that affects a target computer through Windows PowerShell Web Access.</span></span></p>
<p><span data-ttu-id="e532c-199">이 계층은 사용자가 <strong>Enter-PSSession</strong> 또는 <strong>New-PSSession</strong> cmdlet을 실행하여 Windows PowerShell 내에서 대상 컴퓨터에 대한 원격 Windows PowerShell 세션을 만들려고 하는 경우 연결 시도를 평가하는 동일한 보안 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-199">This layer offers the same security mechanisms that would evaluate connection attempts if users tried to create a remote Windows PowerShell session to a target computer from within Windows PowerShell by running the <strong>Enter-PSSession</strong> or <strong>New-PSSession</strong> cmdlets.</span></span></p>
<p><span data-ttu-id="e532c-200">기본적으로 Windows PowerShell 웹 액세스에서는 게이트웨이와 대상 컴퓨터를 모두 인증하는 데 기본 사용자 이름과 암호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-200">By default, Windows PowerShell Web Access uses the primary user name and password for authentication on both the gateway and the target computer.</span></span> <span data-ttu-id="e532c-201">하지만 <strong>옵션 연결 설정</strong> 섹션의 웹 기반 로그인 페이지에는 대상 컴퓨터에 다른 자격 증명을 제공하는 옵션이 있으므로, 필요에 따라 적절히 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-201">The web-based sign-in page, in a section titled <strong>Optional connection settings</strong>, offers users the option of providing different credentials for the target computer, if they are required.</span></span> <span data-ttu-id="e532c-202">사용자가 대체 자격 증명을 제공하지 않으면 게이트웨이 연결에 사용되는 기본 사용자 이름과 암호가 대상 컴퓨터와 연결하는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-202">If the user does not provide alternate credentials, the primary user name and password that are used to connect to the gateway are also used to connect to the target computer.</span></span></p>
<p><span data-ttu-id="e532c-203">권한 부여 규칙을 사용하면 사용자가 특정 세션 구성에 액세스할 수 있도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-203">Authorization rules can be used to allow users access to a particular session configuration.</span></span> <span data-ttu-id="e532c-204">Windows PowerShell 웹 액세스에 대한 제한된 runspace나 세션 구성을 만들어 특정 사용자가 Windows PowerShell 웹 액세스에 로그인할 때 특정 세션 구성에만 연결할 수 있도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-204">You can create restricted runspaces or session configurations for Windows PowerShell Web Access, and allow specific users to connect only to specific session configurations when they sign in to Windows PowerShell Web Access.</span></span> <span data-ttu-id="e532c-205">ACL(액세스 제어 목록)을 사용하면 특정 끝점에 액세스할 수 있는 사용자를 지정할 수 있으며, 이 섹션에 설명된 권한 부여 규칙을 통해 특정 사용자 집합의 끝점에 대한 액세스를 추가로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-205">You can use access control lists (ACLs) to determine which users have access to specific endpoints, and further restrict access to the endpoint for a specific set of users by using authorization rules described in this section.</span></span> <span data-ttu-id="e532c-206">제한된 runspace에 대한 자세한 내용은 MSDN의 <a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">제한된 Runspace</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-206">For more information about restricted runspaces, see <a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">Constrained Runspaces</a> on MSDN.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="e532c-207">

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">권한 부여 규칙 구성</span></a></span><span class="sxs-lookup"><span data-stu-id="e532c-207">

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configuring authorization rules</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="e532c-208">관리자는 Windows PowerShell 웹 액세스 사용자에 대해 자신의 Windows PowerShell 원격 관리 환경에서 이미 정의되어 있는 동일한 권한 부여 규칙을 사용하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-208">Administrators likely want the same authorization rule for Windows PowerShell Web Access users that is already defined in their environment for Windows PowerShell remote management.</span></span> <span data-ttu-id="e532c-209">이 섹션의 첫 번째 절차에서는 단일 세션 구성 내에서 한 컴퓨터를 관리하기 위해 로그인하는 한 명의 사용자에게 액세스를 허용하는 안전한 권한 부여 규칙을 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-209">The first procedure in this section describes how to add a secure authorization rule that grants access to one user, signing in to manage one computer, and within a single session configuration.</span></span> <span data-ttu-id="e532c-210">두 번째 절차에서는 더 이상 필요하지 않는 권한 부여 규칙을 제거하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-210">The second procedure describes how to remove an authorization rule that is no longer needed.</span></span>

<span data-ttu-id="e532c-211">특정 사용자가 Windows PowerShell 웹 액세스의 제한된 runspace 내에서만 작업할 수 있도록 사용자 지정 세션 구성을 사용하려는 경우, 사용자 지정 세션 구성을 만든 후에 이를 참조하는 권한 규칙을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-211">If you plan to use custom session configurations to allow specific users to work only within restricted runspaces in Windows PowerShell Web Access, create your custom session configurations before you add authorization rules that refer to them.</span></span> <span data-ttu-id="e532c-212">Windows PowerShell 웹 액세스 cmdlet을 사용하여 사용자 지정 세션 구성을 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-212">You cannot use the Windows PowerShell Web Access cmdlets to create custom session configurations.</span></span> <span data-ttu-id="e532c-213">사용자 지정 세션 구성을 만드는 방법에 대한 자세한 내용은 MSDN의 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-213">For more information about creating custom session configurations, see [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

<span data-ttu-id="e532c-214">Windows PowerShell 웹 액세스 cmdlet에서는 와일드카드 문자(\*)를 단독으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-214">Windows PowerShell Web Access cmdlets support one wildcard character, an asterisk ( \* ).</span></span> <span data-ttu-id="e532c-215">문자열에 포함된 와일드카드 문자는 지원되지 않으므로 속성(사용자, 컴퓨터 또는 세션 구성)당 하나의 와일드카드 문자를 단독으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-215">Wildcard characters within strings are not supported; use a single asterisk per property (users, computers, or session configurations).</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e532c-216"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="e532c-216"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e532c-217">권한 부여 규칙을 사용하여 사용자에게 액세스 권한을 허용하고 Windows PowerShell 웹 액세스 환경을 보호하는 여러 가지 방법에 대해서는 이 항목의 <a href="#BKMK_others">기타 권한 부여 규칙 시나리오 예</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-217">For more ways you can use authorization rules to grant access to users and help secure the Windows PowerShell Web Access environment, see <a href="#BKMK_others">Other authorization rule scenario examples</a> in this topic.</span></span></p></td>
</tr>
</tbody>
</table>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="e532c-218">제한적인 권한 부여 규칙을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e532c-218">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="e532c-219">다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-219">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="e532c-220">Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-220">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="e532c-221">Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-221">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="e532c-222"><span class="label">세션 구성을 사용하여 사용자 액세스를 제한하는 단계(옵션):</span> 규칙에 사용할 세션 구성이 이미 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-222"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="e532c-223">해당 구성을 아직 만들지 않은 경우 MSDN의 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)에서 세션 구성의 생성 지침을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-223">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="e532c-224">다음을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-224">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="e532c-225">Copy</span><span class="sxs-lookup"><span data-stu-id="e532c-225">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_1079478f-cd51-4d35-8022-4b532a9d57a4'); "클립보드로 복사")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="e532c-226">이 권한 부여 규칙을 통해 특정 사용자는 일반적으로 액세스 권한을 갖고 있는 네트워크상의 한 컴퓨터에만 액세스할 수 있으며, 일반적인 스크립팅 및 cmdlet 환경에 해당하는 특정 세션 구성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-226">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="e532c-227">다음 예에서는 <span class="code">Contoso</span> 도메인의 <span class="code">JSmith</span>라는 사용자에게 <span class="code">Contoso_214</span> 컴퓨터를 관리하고, <span class="code">NewAdminsOnly</span>라는 세션 구성을 사용할 수 있는 액세스 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-227">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="e532c-228">Copy</span><span class="sxs-lookup"><span data-stu-id="e532c-228">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4e760377-e401-4ef4-988f-7a0aec1b2a90'); "클립보드에 복사.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="e532c-229">**Get-PswaAuthorizationRule** cmdlet 또는 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;을 실행하여 규칙이 생성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-229">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="e532c-230">예를 들어 **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-230">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

#### <a name="to-remove-an-authorization-rule"></a><span data-ttu-id="e532c-231">권한 부여 규칙을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="e532c-231">To remove an authorization rule</span></span>

1.  <span data-ttu-id="e532c-232">Windows PowerShell 세션이 아직 열려 있지 않으면 이 섹션에 나와 있는 [제한적인 권한 부여 규칙을 추가하려면](#BKMK_arar)의 1단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-232">If a Windows PowerShell session is not already open, see step 1 of [To add a restrictive authorization rule](#BKMK_arar) in this section.</span></span>

2.  <span data-ttu-id="e532c-233">다음을 입력한 다음 **Enter** 키를 누릅니다(여기서 *rule ID*는 제거하려는 규칙의 고유한 ID 번호를 나타냄).</span><span class="sxs-lookup"><span data-stu-id="e532c-233">Type the following, and then press **Enter**, where *rule ID* represents the unique ID number of the rule that you want to remove.</span></span>

    [<span data-ttu-id="e532c-234">Copy</span><span class="sxs-lookup"><span data-stu-id="e532c-234">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0daef66d-0ecf-47fb-a8a0-d4dbceb8409d'); "클립보드에 복사.")

        Remove-PswaAuthorizationRule -ID <rule ID>

    <span data-ttu-id="e532c-235">또는 제거할 규칙의 ID 번호는 모르지만 이름을 알고 있다면 다음 예제에서 보여준 대로 해당 규칙의 이름을 가져와 규칙을 제거하는 <span class="code">Remove-PswaAuthorizationRule</span> cmdlet에 파이프로 연결합니다. Get-PswaAuthorizationRule -RuleName &lt;*rule name*&gt; | Remove-PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="e532c-235">Alternatively, if you do not know the ID number, but know the friendly name of the rule you want to remove, you can get the name of the rule, and pipe it to the <span class="code">Remove-PswaAuthorizationRule</span> cmdlet to remove the rule, as shown in the following example: Get-PswaAuthorizationRule -RuleName &lt;*rule name*&gt; | Remove-PswaAuthorizationRule.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="e532c-236"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="e532c-236"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="e532c-237">지정된 권한 부여 규칙을 삭제할지 확인하는 메시지는 표시되지 않으므로, <strong>Enter</strong> 키를 누르면 규칙이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-237">You are not prompted to confirm whether you want to delete the specified authorization rule; the rule is deleted when you press <strong>Enter</strong>.</span></span> <span data-ttu-id="e532c-238">따라서 <strong>Remove-PswaAuthorizationRule</strong> cmdlet을 실행하기 전에 권한 부여 규칙을 제거할 것인지 확실히 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-238">Be sure that you want to remove the authorization rule before running the <strong>Remove-PswaAuthorizationRule</strong> cmdlet.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="e532c-239">

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">기타 권한 부여 규칙 시나리오 예</span></a></span><span class="sxs-lookup"><span data-stu-id="e532c-239">

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Other authorization rule scenario examples</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="e532c-240">모든 Windows PowerShell 세션에서는 세션 구성을 사용하는데, 세션에 세션 구성이 지정되어 있지 않은 경우 Microsoft.PowerShell이라고 하는 기본 제공 Windows PowerShell 세션 구성이 Windows PowerShell에서 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-240">Every Windows PowerShell session uses a session configuration; if one is not specified for a session, Windows PowerShell uses the default, built-in Windows PowerShell session configuration, called Microsoft.PowerShell.</span></span> <span data-ttu-id="e532c-241">이 기본 세션 구성에는 컴퓨터에서 사용할 수 있는 모든 cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-241">The default session configuration includes all cmdlets that are available on a computer.</span></span> <span data-ttu-id="e532c-242">관리자는 제한된 runspace(최종 사용자가 제한된 범위의 cmdlet과 작업을 수행할 수 있음)가 사용된 세션 구성을 정의하여 모든 컴퓨터에 대한 액세스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-242">Administrators can restrict access to all computers by defining a session configuration with a restricted runspace (a limited range of cmdlets and tasks that their end users could perform).</span></span> <span data-ttu-id="e532c-243">한 컴퓨터에 대해 모든 언어에 액세스할 수 있거나 Windows PowerShell 원격 관리 cmdlet에만 액세스할 수 있도록 허용된 사용자는 첫 번째 컴퓨터에 연결된 다른 컴퓨터에도 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-243">A user who is granted access to one computer with either full language access or only the Windows PowerShell remote management cmdlets can connect to other computers that are connected to the first computer.</span></span> <span data-ttu-id="e532c-244">제한된 runspace를 정의하면 사용자가 허용된 자신의 Windows PowerShell runspace에서 다른 컴퓨터를 액세스할 수 없게 되어 Windows PowerShell 웹 액세스 환경의 보안을 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-244">Defining a restricted runspace can prevent users from accessing other computers from their allowed Windows PowerShell runspace, and improves the security of your Windows PowerShell Web Access environment.</span></span> <span data-ttu-id="e532c-245">그룹 정책을 사용하여 관리자가 Windows PowerShell 웹 액세스를 통해 액세스할 수 있도록 구성하려는 모든 컴퓨터에 세션 구성을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-245">The session configuration can be distributed (by using Group Policy) to all computers that administrators want to make accessible through Windows PowerShell Web Access.</span></span> <span data-ttu-id="e532c-246">세션 구성에 대한 자세한 내용은 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-246">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx).</span></span> <span data-ttu-id="e532c-247">아래 이 시나리오에 대한 몇 가지 예가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-247">The following are some examples of this scenario.</span></span>

-   <span data-ttu-id="e532c-248">관리자는 제한된 runspace가 사용되는 **PswaEndpoint**라는 끝점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-248">An administrator creates an endpoint, called **PswaEndpoint**, with a restricted runspace.</span></span> <span data-ttu-id="e532c-249">그런 다음 **\*,\*,PswaEndpoint**라는 규칙을 만들고 끝점을 다른 컴퓨터에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-249">Then, the administrator creates a rule, **\*,\*,PswaEndpoint**, and distributes the endpoint to other computers.</span></span> <span data-ttu-id="e532c-250">이 규칙을 통해 모든 사용자는 **PswaEndpoint**라는 끝점이 있는 모든 컴퓨터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-250">The rule allows all users to access all computers with the endpoint **PswaEndpoint**.</span></span> <span data-ttu-id="e532c-251">이 규칙이 규칙 집합에 유일하게 정의되어 있는 규칙이라면 이 끝점이 없는 컴퓨터에는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-251">If this is the only authorization rule defined in the rule set, computers without that endpoint would not be accessible.</span></span>

-   <span data-ttu-id="e532c-252">관리자는 제한된 runspace가 사용되는 **PswaEndpoint**라는 끝점을 만들었으며, 특정 사용자만 액세스할 수 있도록 제한하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-252">The administrator created an endpoint with a restricted runspace called **PswaEndpoint**,and wants to restrict access to specific users.</span></span> <span data-ttu-id="e532c-253">관리자는 **Level1Support**라는 사용자 그룹을 만들고 **Level1Support,\*,PswaEndpoint** 규칙을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-253">The administrator creates a group of users called **Level1Support**, and defines the following rule: **Level1Support,\*,PswaEndpoint**.</span></span> <span data-ttu-id="e532c-254">이 규칙에서는 **Level1Support** 그룹의 모든 사용자가 **PswaEndpoint** 구성이 사용된 모든 컴퓨터에 액세스할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-254">The rule grants any users in the group **Level1Support** access to all computers with the **PswaEndpoint** configuration.</span></span> <span data-ttu-id="e532c-255">이와 마찬가지로, 특정 컴퓨터 집합에만 액세스하도록 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-255">Similarly, access can be restricted to a specific set of computers.</span></span>

-   <span data-ttu-id="e532c-256">일부 관리자는 특정 사용자에게 다른 사용자보다 많은 액세스 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-256">Some administrators provide certain users more access than others.</span></span> <span data-ttu-id="e532c-257">예를 들어 관리자는 **Admins**과 **BasicSupport**라는 두 개의 사용자 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-257">For example, an administrator creates two user groups, **Admins** and **BasicSupport**.</span></span> <span data-ttu-id="e532c-258">또한 관리자는 제한된 runspace가 사용되는 **PswaEndpoint**라는 끝점을 만들고, **Admins,\*,\*** 및 **BasicSupport,\*,PswaEndpoint**라는 두 개의 규칙을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-258">The administrator also creates an endpoint with a restricted runspace called **PswaEndpoint**, and defines the following two rules: **Admins,\*,\*** and **BasicSupport,\*,PswaEndpoint**.</span></span> <span data-ttu-id="e532c-259">첫 번째 규칙에서는 **Admin** 그룹의 모든 사용자에게 모든 컴퓨터에 대한 액세스 권한을 제공하지만, 두 번째 규칙에서는 **BasicSupport** 그룹의 모든 사용자에게 **PswaEndpoint**가 포함된 컴퓨터에만 액세스할 수 있는 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-259">The first rule provides all users in the **Admin** group access to all computers, and the second rule provides all users in the **BasicSupport** group access only to those computers with **PswaEndpoint**.</span></span>

-   <span data-ttu-id="e532c-260">관리자는 개인 테스트 환경을 구축했으며, 권한을 부여받은 모든 네트워크 사용자가 일반적으로 액세스하던 네트워크상의 모든 컴퓨터와, 일반적으로 액세스하던 모든 세션 구성에 액세스할 수 있도록 허용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-260">An administrator has set up a private test environment, and wants to allow all authorized network users access to all computers on the network to which they typically have access, with access to all session configurations to which they typically have access.</span></span> <span data-ttu-id="e532c-261">이 권한 부여 규칙은 개인 테스트 환경에서 사용되므로 관리자는 보안성이 없는 권한 부여 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-261">Because this is a private test environment, the administrator creates an authorization rule that is not secure.</span></span> <span data-ttu-id="e532c-262">관리자는 <span class="code">Add-PswaAuthorizationRule \* \* \*</span> cmdlet을 실행합니다(여기서 와일드카드 문자 **\***는 각각 모든 사용자, 모든 컴퓨터 및 모든 구성을 나타냄).</span><span class="sxs-lookup"><span data-stu-id="e532c-262">The administrator runs the cmdlet <span class="code">Add-PswaAuthorizationRule \* \* \*</span>, which uses the wildcard character **\*** to represent all users, all computers, and all configurations.</span></span> <span data-ttu-id="e532c-263">이 규칙은 <span class="code">Add-PswaAuthorizationRule -UserName \* -ComputerName \* -ConfigurationName \*</span>과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-263">This rule is the equivalent of the following: <span class="code">Add-PswaAuthorizationRule -UserName \* -ComputerName \* -ConfigurationName \*</span>.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="e532c-264"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 보안 정보 </span></span><span class="sxs-lookup"><span data-stu-id="e532c-264"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="e532c-265">이 규칙은 보안 환경에서는 사용하지 않는 것이 좋으며, Windows PowerShell 웹 액세스 권한 부여 규칙에서 제공되는 보안 계층을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-265">This rule is not recommended in a secure environment, and bypasses the authorization rule layer of security provided by Windows PowerShell Web Access.</span></span></p></td>
    </tr>
    </tbody>
    </table>

-   <span data-ttu-id="e532c-266">관리자는 사용자가 작업 그룹과 도메인을 모두 포함하는 환경에서 대상 컴퓨터에 연결할 수 있도록 해야 합니다. 여기서 작업 그룹 컴퓨터는 도메인의 대상 컴퓨터에 연결하는 데 사용되기도 하며, 도메인 컴퓨터는 작업 그룹의 대상 컴퓨터에 연결하는 데 사용되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-266">An administrator must allow users to connect to target computers in an environment that includes both workgroups and domains, where workgroup computers are occasionally used to connect to target computers in domains, and computers in domains are occasionally used to connect to target computers in workgroups.</span></span> <span data-ttu-id="e532c-267">관리자에게는 작업 그룹의 게이트웨이 서버인 *PswaServer*가 있고, 대상 컴퓨터 *srv1.contoso.com* 은 도메인에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-267">The administrator has a gateway server, *PswaServer*, in a workgroup; and target computer *srv1.contoso.com* is in a domain.</span></span> <span data-ttu-id="e532c-268">사용자 *Chris*는 작업 그룹 게이트웨이 서버와 대상 컴퓨터에서 모두 인증된 로컬 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-268">User *Chris* is an authorized local user on both the workgroup gateway server and the target computer.</span></span> <span data-ttu-id="e532c-269">작업 그룹 서버에서 Chris의 사용자 이름은 *chrisLocal*;이며, 대상 컴퓨터에서는 *contoso\\chris*입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-269">His user name on the workgroup server is *chrisLocal*; and his user name on the target computer is *contoso\\chris*.</span></span> <span data-ttu-id="e532c-270">관리자는 다음 규칙을 추가하여 Chris에게 srv1.contoso.com에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-270">To authorize access to srv1.contoso.com for Chris, the administrator adds the following rule.</span></span>

    [<span data-ttu-id="e532c-271">Copy</span><span class="sxs-lookup"><span data-stu-id="e532c-271">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_8d183d3d-1c19-44b8-9297-530b0efc7c79'); "클립보드에 복사.")

        Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell

    <span data-ttu-id="e532c-272">위 규칙의 예에서는 게이트웨이 서버에서 Chris를 인증한 다음 *srv1*에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-272">The preceding rule example authenticates Chris on the gateway server, and then authorizes his access to *srv1*.</span></span> <span data-ttu-id="e532c-273">로그인 페이지에서 Chris는 **옵션 연결 설정** 영역(*contoso\\chris*)에서 두 번째 자격 증명 집합을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-273">On the sign-in page, Chris must provide a second set of credentials in the **Optional connection settings** area (*contoso\\chris*).</span></span> <span data-ttu-id="e532c-274">게이트웨이 서버는 추가 자격 증명 집합을 사용하여 대상 컴퓨터인 *srv1.contoso.com*에서 사용자를 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-274">The gateway server uses the additional set of credentials to authenticate him on the target computer, *srv1.contoso.com*.</span></span>

    <span data-ttu-id="e532c-275">위 시나리오에서는 다음 작업에 성공하고 한 가지 이상의 권한 부여 규칙에 따라 허용된 후에만 Windows PowerShell 웹 액세스를 대상 컴퓨터에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-275">In the preceding scenario, Windows PowerShell Web Access establishes a successful connection to the target computer only after the following have been successful, and allowed by at least one authorization rule.</span></span>

    1.  <span data-ttu-id="e532c-276">*server_name*\\*user_name* 형식의 사용자 이름을 권한 부여 규칙에 추가하여 작업 그룹 게이트웨이 서버에서 인증</span><span class="sxs-lookup"><span data-stu-id="e532c-276">Authentication on the workgroup gateway server by adding a user name in the format *server_name*\\*user_name* to the authorization rule</span></span>

    2.  <span data-ttu-id="e532c-277">**옵션 연결 설정** 영역의 로그인 페이지에서 제공된 대체 자격 증명을 사용하여 대상 컴퓨터에서 인증</span><span class="sxs-lookup"><span data-stu-id="e532c-277">Authentication on the target computer by using alternate credentials provided on the sign-in page, in the **Optional connection settings** area</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="e532c-278"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></span><span class="sxs-lookup"><span data-stu-id="e532c-278"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="e532c-279">게이트웨이 및 대상 컴퓨터가 다른 작업 그룹이나 도메인에 있을 경우, 두 개의 작업 그룹 컴퓨터나 두 개의 도메인 또는 작업 그룹과 도메인 간에 트러스트 관계가 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-279">If gateway and target computers are in different workgroups or domains, a trust relationship must be established between the two workgroup computers, the two domains, or between the workgroup and the domain.</span></span> <span data-ttu-id="e532c-280">이 관계는 Windows PowerShell 웹 액세스 권한 부여 규칙 cmdlet을 사용하여 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-280">This relationship cannot be configured by using Windows PowerShell Web Access authorization rule cmdlets.</span></span> <span data-ttu-id="e532c-281">권한 규칙이 컴퓨터 간의 트러스트 관계를 정의하지는 않습니다. 즉 권한 규칙은 특정 대상 컴퓨터와 세션 구성에 연결하는 사용자만 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-281">Authorization rules do not define a trust relationship between computers; they can only authorize users to connect to specific target computers and session configurations.</span></span> <span data-ttu-id="e532c-282">서로 다른 도메인 간에 트러스트 관계를 구성하는 방법에 대한 자세한 내용은 <a href="https://technet.microsoft.com/library/cc794775.aspx">도메인 및 포리스트 트러스트 만들기</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-282">For more information about how to configure a trust relationship between different domains, see <a href="https://technet.microsoft.com/library/cc794775.aspx">Creating Domain and Forest Trusts</a>.</span></span> <span data-ttu-id="e532c-283">신뢰할 수 있는 호스트 목록에 작업 그룹 컴퓨터를 추가하는 방법에 대한 자세한 내용은 <a href="https://technet.microsoft.com/library/dd759202.aspx">서버 관리자를 통한 원격 관리</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-283">For more information about how to add workgroup computers to a trusted hosts list, see <a href="https://technet.microsoft.com/library/dd759202.aspx">Remote Management with Server Manager</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="e532c-284"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">여러 사이트에 단일 권한 부여 규칙 집합 사용</span></a></span><span class="sxs-lookup"><span data-stu-id="e532c-284"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using a single set of authorization rules for multiple sites</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="e532c-285">권한 부여 규칙은 XML 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-285">Authorization rules are stored in an XML file.</span></span> <span data-ttu-id="e532c-286">이 XML 파일의 기본 경로 이름은 %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-286">By default, the path name of the XML file is %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml.</span></span>

<span data-ttu-id="e532c-287">권한 부여 규칙 XML 파일은 %windir%\\Web\\PowershellWebAccess\\data에 있는 **powwa.config** 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-287">The path to the authorization rules XML file is stored in the **powwa.config** file, which is found in %windir%\\Web\\PowershellWebAccess\\data.</span></span> <span data-ttu-id="e532c-288">관리자는 기본 설정이나 요구 사항에 맞춰 이 **powwa.config**에 포함된 기본 경로를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-288">The administrator has the flexibility to change the reference to the default path in **powwa.config** to suit preferences or requirements.</span></span> <span data-ttu-id="e532c-289">관리자가 파일 위치를 변경할 수 있으므로 여러 Windows PowerShell 웹 액세스 게이트웨이에서 동일한 권한 부여 규칙을 사용해야 할 경우 그러한 구성이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-289">Allowing the administrator to change the location of the file lets multiple Windows PowerShell Web Access gateways use the same authorization rules, if such a configuration is desired.</span></span>

<a href="" id="BKMK_sesmgmt"></a>

<span data-ttu-id="e532c-290"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">세션 관리</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="e532c-290"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Session management</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="e532c-291">기본적으로 Windows PowerShell 웹 액세스에서는 사용자가 한 번에 세 세션까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-291">By default, Windows PowerShell Web Access limits a user to three sessions at one time.</span></span> <span data-ttu-id="e532c-292">하지만 IIS 관리자를 사용하여 사용자당 여러 세션을 지원하도록 웹 응용 프로그램의 **web.config** 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-292">You can edit the web application’s **web.config** file in IIS Manager to support a different number of sessions per user.</span></span> <span data-ttu-id="e532c-293">**web.config** 파일의 경로는 $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-293">The path to the **web.config** file is $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config.</span></span>

<span data-ttu-id="e532c-294">기본적으로 웹 서버(IIS)는 설정이 편집될 경우 응용 프로그램 풀을 다시 시작하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-294">By default, Web Server (IIS) is configured to restart the application pool if any settings are edited.</span></span> <span data-ttu-id="e532c-295">예를 들어 **web.config** 파일이 변경되면 응용 프로그램 풀이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-295">For example, the application pool is restarted if changes are made to the **web.config** file.</span></span> <span data-ttu-id="e532c-296">Windows PowerShell 웹 액세스에서는 메모리 내 세션 상태가 사용되므로, 응용 프로그램 풀이 다시 시작되면 Windows PowerShell 웹 액세스 세션에 로그인한 사용자는 해당 세션을 잃어버리게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-296">Because Windows PowerShell Web Access uses in-memory session states, users signed in to Windows PowerShell Web Access sessions lose their sessions when the application pool is restarted.</span></span>

###

<span data-ttu-id="e532c-297"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">로그인 페이지의 기본 매개 변수 설정</span></a></span><span class="sxs-lookup"><span data-stu-id="e532c-297"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Setting default parameters on the sign-in page</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="e532c-298">Windows PowerShell 웹 액세스 게이트웨이가 Windows Server 2012 R2에서 실행되는 경우 Windows PowerShell 웹 액세스 로그인 페이지에 표시되는 설정에 대한 기본값을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-298">If your Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, you can configure default values for the settings that are displayed on the Windows PowerShell Web Access sign-in page.</span></span> <span data-ttu-id="e532c-299">이전 단락에 설명된 **web.config** 파일에서 값을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-299">You can configure values in the **web.config** file that is described in the preceding paragraph.</span></span> <span data-ttu-id="e532c-300">로그인 페이지 설정에 대한 기본값은 web.config 파일의 **appSettings** 섹션에 있습니다. 다음은 **appSettings** 섹션의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-300">Default values for the sign-in page settings are found in the **appSettings** section of the web.config file; the following is an example of the **appSettings** section.</span></span> <span data-ttu-id="e532c-301">이러한 설정에 유효한 값은 대부분 Windows PowerShell에서 [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet의 해당 매개 변수에 대한 값과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-301">Valid values for many of these settings are the same as those for the corresponding parameters of the [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet in Windows PowerShell.</span></span> <span data-ttu-id="e532c-302">예를 들어 다음 코드 블록에 표시된 <span class="code">defaultApplicationName</span> 키는 대상 컴퓨터의 **$PSSessionApplicationName** 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-302">For example, the <span class="code">defaultApplicationName</span> key, as shown in the following code block, is the value of the **$PSSessionApplicationName** preference variable on the target computer.</span></span>

[<span data-ttu-id="e532c-303">Copy</span><span class="sxs-lookup"><span data-stu-id="e532c-303">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_6ccfd0a1-485a-4ac5-9636-89ebab501bef'); "클립보드에 복사.")

    <appSettings>
            <add key="maxSessionsAllowedPerUser" value="3"/>
            <add key="defaultPortNumber" value="5985"/>
            <add key="defaultSSLPortNumber" value="5986"/>
            <add key="defaultApplicationName" value="WSMAN"/>
            <add key="defaultUseSslSelection" value="0"/>
            <add key="defaultAuthenticationType" value="0"/>
            <add key="defaultAllowRedirection" value="0"/>
            <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
    </appSettings>

###

<span data-ttu-id="e532c-304"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">시간 제한 및 계획되지 않은 연결 끊김</span></a></span><span class="sxs-lookup"><span data-stu-id="e532c-304"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Time-outs and unplanned disconnections</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="e532c-305">Windows PowerShell 웹 액세스 세션의 시간이 초과됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-305">Windows PowerShell Web Access sessions time out.</span></span> <span data-ttu-id="e532c-306">Windows Server 2012에서 실행되는 Windows PowerShell 웹 액세스에서는 15분 동안 세션 활동이 없을 경우 로그인한 사용자에게 시간 초과 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-306">In Windows PowerShell Web Access running on Windows Server 2012, A time-out message is displayed to signed-in users after 15 minutes of session inactivity.</span></span> <span data-ttu-id="e532c-307">이 메시지가 표시된 후 5분 이내에 사용자가 응답하지 않으면 세션이 종료되고 사용자는 로그아웃됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-307">If the user does not respond within five minutes after the time-out message is displayed, the session is ended, and the user is signed out.</span></span> <span data-ttu-id="e532c-308">IIS 관리자에서 웹 사이트 설정 중 세션의 시간 초과 기간을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-308">You can change time-out periods for sessions in the website settings in IIS Manager.</span></span>

<span data-ttu-id="e532c-309">Windows Server 2012 R2에서 실행되는 Windows PowerShell 웹 액세스에서는 기본적으로 20분 동안 활동이 없을 경우 세션이 시간 초과됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-309">In Windows PowerShell Web Access running on Windows Server 2012 R2, sessions time out, by default, after 20 minutes of inactivity.</span></span> <span data-ttu-id="e532c-310">사용자가 직접 세션을 닫았기 때문이 아니라 네트워크 오류나 기타 계획되지 않은 종료 또는 실패로 인해 웹 기반 콘솔의 세션에서 연결이 끊어진 경우 클라이언트 쪽의 시간 제한 기간이 경과할 때까지 Windows PowerShell 웹 액세스 세션이 대상 컴퓨터에 연결된 상태로 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-310">If users are disconnected from sessions in the web-based console because of network errors or other unplanned shutdowns or failures, and not because they have closed the sessions themselves, the Windows PowerShell Web Access sessions continue to run, connected to target computers, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="e532c-311">기본값인 20분 또는 게이트웨이 관리자가 지정한 시간 제한 기간 중 더 짧은 시간 후에 세션 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-311">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

<span data-ttu-id="e532c-312">게이트웨이 서버가 Windows Server 2012 R2를 실행하는 경우 Windows PowerShell 웹 액세스를 통해 사용자가 나중에 저장된 세션에 다시 연결할 수 있지만 네트워크 오류, 계획되지 않은 종료 또는 기타 실패로 인해 세션 연결이 끊어진 경우에는 게이트웨이 관리자가 지정한 시간 제한 기간이 경과할 때까지 사용자가 저장된 세션을 보거나 다시 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-312">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but when network errors, unplanned shutdowns, or other failures disconnect sessions, users cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

<span data-ttu-id="e532c-313"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">참고 항목</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="e532c-313"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="e532c-314">[Windows PowerShell 웹 액세스 설치 및 사용](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Windows PowerShell 웹 액세스 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)</span><span class="sxs-lookup"><span data-stu-id="e532c-314">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx)</span></span>

<span data-ttu-id="e532c-315"><span>표시:</span> 상속됨 보호됨</span><span class="sxs-lookup"><span data-stu-id="e532c-315"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="e532c-316"><span class="stdr-votetitle">이 페이지가 도움이 되었나요?</span></span><span class="sxs-lookup"><span data-stu-id="e532c-316"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="e532c-317">예 아니요</span><span class="sxs-lookup"><span data-stu-id="e532c-317">Yes No</span></span>

<span data-ttu-id="e532c-318">추가 피드백</span><span class="sxs-lookup"><span data-stu-id="e532c-318">Additional feedback?</span></span>

<span data-ttu-id="e532c-319"><span class="stdr-count"><span class="stdr-charcnt">1500</span>자 남음</span> 제출 건너뛰기</span><span class="sxs-lookup"><span data-stu-id="e532c-319"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="e532c-320"><span class="stdr-thankyou">감사합니다.</span></span><span class="sxs-lookup"><span data-stu-id="e532c-320"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="e532c-321"><span class="stdr-appreciate">피드백에 감사드립니다.</span></span><span class="sxs-lookup"><span data-stu-id="e532c-321"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="e532c-322">프로필 관리</span><span class="sxs-lookup"><span data-stu-id="e532c-322">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="e532c-323"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 사이트 피드백</a> 사이트 피드백</span><span class="sxs-lookup"><span data-stu-id="e532c-323"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="e532c-324"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="e532c-324"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="e532c-325">사용 환경에 대한 의견을 제공해주세요...</span><span class="sxs-lookup"><span data-stu-id="e532c-325">Tell us about your experience...</span></span>

<span data-ttu-id="e532c-326">페이지가 빨리 로드되었나요?</span><span class="sxs-lookup"><span data-stu-id="e532c-326">Did the page load quickly?</span></span>

<span data-ttu-id="e532c-327"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="e532c-327"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="e532c-328">페이지 디자인이 마음에 드세요?</span><span class="sxs-lookup"><span data-stu-id="e532c-328">Do you like the page design?</span></span>

<span data-ttu-id="e532c-329"><span> 예<span> </span></span> <span> 아니요<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="e532c-329"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="e532c-330">기타 의견</span><span class="sxs-lookup"><span data-stu-id="e532c-330">Tell us more</span></span>

-   [<span data-ttu-id="e532c-331">Flash 뉴스레터</span><span class="sxs-lookup"><span data-stu-id="e532c-331">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="e532c-332">연락처</span><span class="sxs-lookup"><span data-stu-id="e532c-332">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="e532c-333">개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="e532c-333">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="e532c-334">사용 조건</span><span class="sxs-lookup"><span data-stu-id="e532c-334">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="e532c-335">상표</span><span class="sxs-lookup"><span data-stu-id="e532c-335">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="e532c-336">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="e532c-336">© 2016 Microsoft</span></span>

<span data-ttu-id="e532c-337">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="e532c-337">© 2016 Microsoft</span></span>

<span data-ttu-id="e532c-338">본 웹 사이트에서 연결되거나 참조된 타사 스크립트 및 코드의 경우 Microsoft가 아닌 해당 코드를 소유한 측에서 사용자에게 라이선스를 허여합니다.</span><span class="sxs-lookup"><span data-stu-id="e532c-338">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="e532c-339">ASP.NET Ajax CDN 사용 약관 - http://www.asp.net/ajaxlibrary/CDN.ashx를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e532c-339">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

