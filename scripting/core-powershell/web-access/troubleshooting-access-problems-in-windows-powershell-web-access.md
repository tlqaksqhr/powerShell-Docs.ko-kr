---
title:  Windows PowerShell 웹 액세스의 액세스 문제 해결
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
---

#  Windows PowerShell 웹 액세스의 액세스 문제 해결

업데이트됨: 2013년 6월 24일

적용 대상: Windows Server 2012 R2, Windows Server 2012

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

다음 표에는 Windows PowerShell 웹 액세스를 사용하여 원격 컴퓨터에 연결할 때 발생할 수 있는 몇 가지 일반적인 문제와 이러한 문제에 대한 해결 방안이 포함되어 있습니다.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>문제</p></th>
<th><p>가능한 원인 및 해결 방안</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>로그인 오류</p></td>
<td><p>다음과 같은 이유로 인해 오류가 발생할 수 있습니다.</p>
<ul>
<li><p>원격 컴퓨터에 특정 세션 구성이나 컴퓨터에 대한 사용자 액세스를 허용하는 권한 부여 규칙이 없습니다. Windows PowerShell 웹 액세스 보안이 제한적이므로 권한 부여 규칙을 사용하여 명시적으로 사용자에게 원격 컴퓨터에 대한 액세스를 허용해야 합니다. 권한 부여 규칙을 만드는 방법에 대한 자세한 내용은 이 가이드의 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능</a>을 참조하세요.</p></li>
<li><p>사용자에게는 대상 컴퓨터에 대해 허가받은 권한이 없습니다. 이 권한은 ACL(액세스 제어 목록)에서 결정됩니다. 자세한 내용은 <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">웹 기반 Windows PowerShell 콘솔 사용</a>의 "Windows PowerShell 웹 액세스에 로그인" 또는 <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell 팀 블로그</a>를 참조하세요.</p>
<ul>
<li><p>Windows PowerShell 원격 관리 기능이 대상 컴퓨터에서 사용되지 않는 상태일 수 있습니다. 사용자가 연결하려는 컴퓨터에서 이 기능이 사용되는지 확인합니다. 자세한 내용은 Windows PowerShell 정보 도움말 항목에 있는 <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a>의 " 컴퓨터를 원격으로 사용할 수 있도록 구성하는 방법"을 참조하세요.</p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p>사용자가 Internet Explorer 창에서 Windows PowerShell 웹 액세스에 로그인하려고 하면 <strong>내부 서버 오류</strong> 페이지가 표시되거나 Internet Explorer의 응답이 중지되는 경우. 이 문제는 Internet Explorer에서만 발생합니다.</p></td>
<td><p>이 문제는 사용자가 한자를 포함한 도메인 이름으로 로그인한 경우 또는 게이트웨이 서버 이름의 일부로 한자가 두 개 이상 포함된 경우에 발생할 수 있습니다. 이 문제를 해결하려면 사용자가 <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">Internet Explorer 10을 설치 및 실행</a>한 후 다음 단계를 수행해야 합니다.</p>
<ol>
<li><p>Internet Explorer <strong>문서 모드</strong> 설정을 <strong>IE10 표준</strong>으로 변경합니다.</p>
<ol>
<li><p><strong>F12</strong> 키를 눌러 개발자 도구 콘솔을 엽니다.</p></li>
<li><p>Internet Explorer 10에서 <strong>브라우저 모드</strong>를 클릭한 후 <strong>Internet Explorer 10</strong>을 선택합니다.</p></li>
<li><p><strong>문서 모드</strong>를 클릭한 후 <strong>IE10 표준</strong>을 클릭합니다.</p></li>
<li><p><strong>F12</strong> 키를 다시 눌러 개발자 도구 콘솔을 선택합니다.</p></li>
</ol></li>
<li><p>자동 프록시 구성을 사용하지 않도록 설정합니다.</p>
<ol>
<li><p>Internet Explorer 10에서 <strong>도구</strong>를 클릭한 후 <strong>인터넷 옵션</strong>을 클릭합니다.</p></li>
<li><p><strong>인터넷 옵션</strong> 대화 상자의 <strong>연결</strong> 탭에서 <strong>LAN 설정</strong>을 클릭합니다.</p></li>
<li><p><strong>자동으로 설정 검색</strong> 확인란을 선택 취소합니다. <strong>확인</strong>을 클릭한 후 다시 <strong>확인</strong>을 클릭하여 <strong>인터넷 옵션</strong> 대화 상자를 닫습니다.</p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>원격 작업 그룹 컴퓨터에 연결할 수 없는 경우</p></td>
<td><p>대상 컴퓨터가 작업 그룹의 구성원인 경우에는 다음 구문을 이용하여 사용자 이름을 입력하고 컴퓨터에 로그인합니다. &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>웹 서버(IIS) 역할이 설치되어 있는데도 웹 서버(IIS) 관리 도구를 찾을 수 없는 경우</p></td>
<td><p><span class="code">Install-WindowsFeature</span> cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치한 경우 <span class="code">IncludeManagementTools</span> 매개 변수를 cmdlet에 추가하지 않으면 관리 도구가 설치되지 않습니다. 이에 해당하는 예는 <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Windows PowerShell 웹 액세스 설치 및 사용</a>의 "Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하려면"을 참조하세요. IIS 관리자 콘솔 및 기타 IIS 관리 도구가 필요한 경우 게이트웨이 서버를 대상으로 하는 역할 및 기능 추가 마법사 세션에서 해당 도구를 선택하여 추가할 수 있습니다. 역할 및 기능 추가 마법사는 서버 관리자 내에서 열립니다.</p></td>
</tr>
<tr class="odd">
<td><p>Windows PowerShell 웹 액세스 웹 사이트에 액세스할 수 없는 경우</p></td>
<td><p>Internet Explorer에서 보안 강화 구성(IE ESC)이 사용되는 경우 신뢰할 수 있는 사이트 목록에 Windows PowerShell 웹 액세스 웹 사이트를 추가하거나 IE ESC를 사용하지 않도록 설정합니다. IE ESC는 서버 관리자의 <strong>로컬 서버</strong> 페이지에 있는 <strong>속성</strong> 타일에서 사용하지 않도록 설정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>게이트웨이 서버가 대상 컴퓨터이고 작업 그룹에 있을 때 연결하려고 하면 다음 오류 메시지가 표시됩니다. <strong>권한 부여 오류가 발생했습니다. 대상 컴퓨터에 연결할 권한이 있는지 검증하세요.</strong></p></td>
<td><p>또한 게이트웨이 서버가 대상 서버이며 작업 그룹에 속해 있는 경우 사용자 이름, 컴퓨터 이름 및 사용자 그룹 이름을 다음 표와 같이 지정합니다. 컴퓨터 이름을 나타내는 데에는 점(.)을 단독으로 사용하면 안 됩니다.</p>
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
<th><p>시나리오</p></th>
<th><p>UserName 매개 변수</p></th>
<th><p>UserGroup 매개 변수</p></th>
<th><p>ComputerName 매개 변수</p></th>
<th><p>ComputerGroup 매개 변수</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>도메인의 게이트웨이 서버</p></td>
<td><p><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em> 또는 .\<em>user_name</em></p></td>
<td><p><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> 또는 .\<em>user_group</em></p></td>
<td><p>정규화된 게이트웨이 서버의 이름 또는 Localhost</p></td>
<td><p><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> 또는 .\<em>computer_group</em></p></td>
</tr>
<tr class="even">
<td><p>작업 그룹의 게이트웨이 서버</p></td>
<td><p><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em> 또는 .\<em>user_name</em></p></td>
<td><p><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> 또는 .\<em>user_group</em></p></td>
<td><p>서버 이름</p></td>
<td><p><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> 또는 .\<em>computer_group</em></p></td>
</tr>
</tbody>
</table>
</div>
<p>다음 중 하나로 형식화된 자격 증명을 사용하여 게이트웨이 서버에 대상 컴퓨터로 로그인합니다.</p>
<ul>
<li><p><em>Server_name</em>\<em>user_name</em></p></li>
<li><p>Localhost\<em>user_name</em></p></li>
<li><p>.\<em>user_name</em></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>SID(보안 식별자)는 구문 <em>user_name</em>/<em>computer_name 대신 권한 부여 규칙에 표시됩니다.</em> </p></td>
<td><p>규칙이 더 이상 유효하지 않거나, Active Directory 도메인 서비스를 쿼리하지 못했습니다. 권한 부여 규칙은 게이트웨이 서버가 이전에는 작업 그룹에 있었지만 나중에 도메인에 가입한 시나리오에서는 항상 유효하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p>권한 부여 규칙에 지정된 대상 컴퓨터에는 도메인의 IPv6 주소로 로그인할 수 없습니다.</p></td>
<td><p>권한 부여 규칙은 도메인 이름 형식의 IPv6 주소를 지원하지 않습니다. IPv6 주소를 사용하여 대상 컴퓨터를 지정하려면 권한 부여 규칙의 원래 IPv6 주소(콜론 포함)를 사용하십시오. 도메인과 숫자(콜론 포함)가 모두 포함된 IPv6 주소는 Windows PowerShell 웹 액세스 로그인 페이지에서 대상 컴퓨터 이름으로 사용할 수는 있지만 권한 부여 규칙에서는 사용할 수 없습니다. IPv6 주소에 대한 자세한 내용은 <a href="https://technet.microsoft.com/library/cc781672.aspx">IPv6 작동 방법</a>을 참조하세요.</p></td>
</tr>
</tbody>
</table>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">참고 항목</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about\_Remote\_Requirements](https://technet.microsoft.com/library/dd315349.aspx)

<span>표시:</span> 상속됨 보호됨

<span class="stdr-votetitle">이 페이지가 도움이 되었나요?</span>
예 아니요

추가 피드백

<span class="stdr-count"><span class="stdr-charcnt">1500</span>자 남음</span> 제출 건너뛰기

<span class="stdr-thankyou">감사합니다.</span> <span class="stdr-appreciate">피드백에 감사드립니다.</span>

[프로필 관리](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 사이트 피드백</a> 사이트 피드백

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

사용 환경에 대한 의견을 제공해주세요...

페이지가 빨리 로드되었나요?

<span> 예<span> </span></span><span> 아니요<span> </span></span>

페이지 디자인이 마음에 드세요?

<span> 예<span> </span></span><span> 아니요<span> </span></span>

기타 의견

-   [Flash 뉴스레터](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [연락처](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [개인 정보 취급 방침](https://privacy.microsoft.com/privacystatement)
-   |
-   [사용 조건](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [상표](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

© 2016 Microsoft

© 2016 Microsoft

본 웹 사이트에서 연결되거나 참조된 타사 스크립트 및 코드의 경우 Microsoft가 아닌 해당 코드를 소유한 측에서 사용자에게 라이선스를 허여합니다. ASP.NET Ajax CDN 사용 약관 - http://www.asp.net/ajaxlibrary/CDN.ashx를 참조하세요.
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />



<!--HONumber=May16_HO2-->


