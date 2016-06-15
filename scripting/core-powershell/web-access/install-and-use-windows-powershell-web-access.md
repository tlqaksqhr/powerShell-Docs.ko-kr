---
title:  Windows PowerShell 웹 액세스 설치 및 사용
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
---

#  Install and Use Windows PowerShell Web Access(Windows PowerShell 웹 액세스 설치 및 사용)

업데이트됨: 2013년 11월 5일

적용 대상: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell® 웹 액세스는 Windows Server® 2012에 처음 도입되었고 Windows PowerShell 게이트웨이로 사용되며 원격 컴퓨터를 대상으로 하는 웹 기반 Windows PowerShell 콘솔을 제공합니다. 이 기능을 사용하면 IT 전문가가 클라이언트 장치에 Windows PowerShell, 원격 관리 소프트웨어 또는 브라우저 플러그 인을 설치하지 않고도 웹 브라우저의 Windows PowerShell 콘솔에서 Windows PowerShell 명령과 스크립트를 실행할 수 있습니다. 웹 기반 Windows PowerShell 콘솔을 실행하려면 올바르게 구성된 Windows PowerShell 웹 액세스 게이트웨이와 JavaScript®를 지원하고 쿠키를 적용하는 클라이언트 장치 브라우저만 있으면 됩니다.

클라이언트 장치에는 랩톱, 정지 상태의 개인 컴퓨터, 대여된 컴퓨터, 태블릿 컴퓨터, 웹 키오스크, Windows 기반 운영 체제를 실행 중인 컴퓨터 및 이동 전화 브라우저 등이 포함됩니다. IT 전문가는 인터넷 연결과 웹 브라우저에 대한 권한을 지닌 장치에서 원격 Windows 기반 서버의 주요 관리 작업을 수행할 수 있습니다.

사용자는 게이트웨이를 설치 및 구성하고 나서 웹 브라우저를 사용하여 Windows PowerShell 콘솔에 액세스할 수 있습니다. 사용자가 안전한 Windows PowerShell 웹 액세스 웹 사이트를 열면 인증을 거친 후 웹 기반 Windows PowerShell 콘솔을 실행할 수 있습니다.

Windows PowerShell 웹 액세스 설치 및 구성은 다음의 세 단계로 구성됩니다.

1.  Windows PowerShell 웹 액세스 설치

2.  게이트웨이 구성

3.  사용자가 웹 기반 Windows PowerShell 콘솔에 액세스하도록 허용하는 권한 부여 규칙 구성

Windows PowerShell 웹 액세스를 설치 및 구성하기 전에 Windows PowerShell 웹 액세스를 설치, 보호 및 제거하는 방법에 대한 지침이 포함된 이 전체 가이드를 읽는 것이 좋습니다. [웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) 항목에서는 사용자가 웹 기반 콘솔에 로그인하는 방법을 설명하고 웹 기반 Windows PowerShell 콘솔과 **powershell.exe** 콘솔 간의 제한 사항과 차이점을 다룹니다. 웹 기반 콘솔의 최종 사용자라면 [웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)을 읽어야 하지만, 이 가이드의 나머지 부분은 읽을 필요가 없습니다.

이 항목에서는 심층 웹 서버(IIS) 작업 지침을 제공하지 않으며, 이 항목에 설명된 Windows PowerShell 웹 액세스 게이트웨이를 구성하는 데 필요한 단계만 제공합니다. IIS에서의 웹 사이트 구성 및 보안에 대한 자세한 내용은 참고 항목 섹션의 IIS 설명서 리소스를 참조하세요.

다음 그림에는 Windows PowerShell 웹 액세스 작동 방식이 나와 있습니다.

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

이 항목의 내용:

-   [Windows PowerShell 웹 액세스 실행에 필요한 요구 사항](#BKMK_reqs)

-   [브라우저 및 클라이언트 장치 지원](#BKMK_browser)

-   [권장(빠른) 배포](#BKMK_recm)

-   [사용자 지정 배포](#BKMK_custom)

-   [정품 인증서 구성](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Windows PowerShell 웹 액세스 실행에 필요한 요구 사항</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Windows PowerShell 웹 액세스에는 웹 서버(IIS), .NET Framework 4.5, 그리고 게이트웨이를 실행할 서버에서 실행되는 Windows PowerShell 3.0 또는 Windows PowerShell 4.0이 필요합니다. 서버 관리자의 역할 및 기능 추가 마법사 또는 서버 관리자용 Windows PowerShell 배포 cmdlet을 사용하여 Windows Server 2012 R2 또는 Windows Server 2012가 실행되고 있는 서버에 Windows PowerShell 웹 액세스를 설치할 수 있습니다. 서버 관리자 또는 서버 관리자의 배포 cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하면 필수 역할 및 기능이 설치 과정의 일부분으로 자동 추가됩니다.

Windows PowerShell 웹 액세스를 통해 원격 사용자는 웹 브라우저의 Windows PowerShell을 사용하여 조직 내 컴퓨터에 액세스할 수 있습니다. Windows PowerShell 웹 액세스가 편리하고 강력한 관리 도구이기는 하지만 웹 기반 액세스로 인해 보안 위험에 노출될 수 있으므로 가급적 안전하게 구성해야 합니다. 따라서 Windows PowerShell 웹 액세스 게이트웨이를 구성하는 관리자는 사용 가능한 보안 계층, 즉 Windows PowerShell 웹 액세스에 포함된 cmdlet 기반의 권한 부여 규칙과 웹 서버(IIS) 및 타사 응용 프로그램에서 제공되는 보안 계층을 모두 사용하는 것이 좋습니다. 이 설명서에는 테스트 환경용으로만 권장되는 보안되지 않은 예와, 안전한 배포용으로 권장되는 예가 모두 포함되어 있습니다.

<a href="" id="BKMK_browser"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">브라우저 및 클라이언트 장치 지원</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Windows PowerShell 웹 액세스에서는 다음과 같은 인터넷 브라우저를 지원합니다. 모바일 브라우저는 공식적으로는 지원되지 않지만 대부분 웹 기반 Windows PowerShell 콘솔을 실행할 수 있습니다. 쿠키를 적용하고 JavaScript 및 HTTPS 웹 사이트를 실행하는 다른 브라우저도 사용할 수 있지만 공식 테스트를 거치지는 않았습니다.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">지원되는 데스크톱 컴퓨터 브라우저</span></a>

------------------------------------------------------------------------

-   Microsoft Windows® 8.0, 9.0, 10.0 및 11.0용 Windows® Internet Explorer®

-   Mozilla Firefox® 10.0.2

-   Windows용 Google Chrome™ 17.0.963.56m

-   Windows용 Apple Safari® 5.1.2

-   Mac OS®용 Apple Safari 5.1.2

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">최소한의 테스트를 거친 모바일 장치 또는 브라우저</span></a>

------------------------------------------------------------------------

-   Windows Phone 7 및 7.5

-   Google Android WebKit 3.1 Browser Android 2.2.1(커널 2.6)

-   iPhone 운영 체제 5.0.1용 Apple Safari

-   iPad 2 운영 체제 5.0.1용 Apple Safari

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">브라우저 요구 사항</span></a>

------------------------------------------------------------------------

Windows PowerShell 웹 액세스 웹 기반 콘솔을 사용하려면 브라우저에서 다음을 수행해야 합니다.

-   Windows PowerShell 웹 액세스 게이트웨이 웹 사이트의 쿠키를 허용합니다.

-   HTTPS 페이지를 열고 읽을 수 있습니다.

-   JavaScript가 사용되는 웹 사이트를 열고 실행합니다.

<a href="" id="BKMK_recm"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">권장(빠른) 배포</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Windows PowerShell cmdlet을 사용하거나 서버 관리자 내에서 열린 역할 및 기능 추가 마법사를 사용하여 Windows Server 2012 R2 또는 Windows Server 2012를 실행하는 서버에서 Windows PowerShell 웹 액세스 게이트웨이를 설치할 수 있습니다. 빠른 설치 및 구성을 위해 이 섹션에 설명된 대로 Windows PowerShell cmdlet을 사용합니다.

-   [1단계: Windows PowerShell 웹 액세스 설치](#BKMK_step1)

-   [2단계: 게이트웨이 구성](#BKMK_step2)

-   [3단계: 제한적인 권한 부여 규칙 구성](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">1단계: Windows PowerShell 웹 액세스 설치</span></a>

------------------------------------------------------------------------

#### Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하려면

1.  다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

    -   Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Windows PowerShell 3.0 및 4.0에서는 서버 관리자 cmdlet 모듈의 일부인 cmdlet을 실행하기 전에 해당 모듈을 Windows PowerShell 세션으로 가져올 필요가 없습니다. 모듈의 일부인 cmdlet을 처음으로 실행하면 모듈을 자동으로 가져옵니다. 또한 Windows PowerShell cmdlet은 대/소문자를 구분하지 않습니다.</p></td>
    </tr>
    </tbody>
    </table>

2.  다음을 입력하고 **Enter** 키를 누릅니다. 여기서 *computer\_name*은 Windows PowerShell 웹 액세스를 설치할 원격 컴퓨터를 나타냅니다(해당되는 경우). 필요에 따라 <span class="code">Restart</span> 매개 변수를 사용하여 대상 서버를 자동으로 다시 시작합니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "클립보드에 복사.")

        Install-WindowsFeature –Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하면 웹 서버(IIS) 관리 도구가 기본적으로 추가되지 않습니다. 관리 도구를 Windows PowerShell 웹 액세스 게이트웨이와 동일한 서버에 설치하려면 이 단계에서와 같이 설치 명령에 <span class="code">IncludeManagementTools</span> 매개 변수를 추가합니다. 원격 컴퓨터에서 Windows PowerShell 웹 액세스 웹 사이트를 관리하려면 게이트웨이를 관리하려는 컴퓨터에서 <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Windows 8.1용 원격 서버 관리 도구</a> 또는 <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Windows 8용 원격 서버 관리 도구</a>를 설치하여 IIS 관리자 스냅인을 설치합니다.</p></td>
    </tr>
    </tbody>
    </table>

    역할 및 기능을 오프라인 VHD에 설치하려면 <span class="code">ComputerName</span> 매개 변수와 <span class="code">VHD</span> 매개 변수를 모두 추가해야 합니다. <span class="code">ComputerName</span> 매개 변수에는 VHD를 탑재할 서버의 이름이 포함되며, <span class="code">VHD</span> 매개 변수에는 지정된 서버에서의 VHD 파일 경로가 포함됩니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "클립보드에 복사.")

        Install-WindowsFeature –Name WindowsPowerShellWebAccess –VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  설치가 완료되면 관리자 권한으로 열린 Windows PowerShell 콘솔에서 대상 서버에 대한 **Get-WindowsFeature** cmdlet을 실행하여 Windows PowerShell 웹 액세스가 대상 서버에 설치되었는지 확인합니다. 서버 관리자 콘솔에서도 **모든 서버** 페이지에서 대상 서버를 선택한 다음 해당 서버의 **역할 및 기능** 타일을 살펴보면 Windows PowerShell 웹 액세스가 설치되었는지 확인할 수 있습니다. Windows PowerShell 웹 액세스의 추가 정보 파일을 살펴볼 수도 있습니다.

4.  Windows PowerShell 웹 액세스가 설치되고 나면 게이트웨이에 필요한 기본 설치 지침이 포함된 추가 정보 파일을 검토하라는 메시지가 표시됩니다. 이러한 설치 지침은 다음 섹션인 [2단계: 게이트웨이 구성](#BKMK_step2)에도 포함되어 있습니다. 추가 정보 파일의 경로는 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>입니다.

<a href="" id="BKMK_step2"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">2단계: 게이트웨이 구성</span></a>

------------------------------------------------------------------------

**Install-PswaWebApplication** cmdlet을 사용하면 Windows PowerShell 웹 액세스를 가장 빨리 구성할 수 있습니다. <span class="code">UseTestCertificate</span> 매개 변수를 <span class="code">Install-PswaWebApplication</span> cmdlet에 추가하여 자체 서명된 테스트용 SSL 인증서를 설치할 수 있지만 안전하지 않으므로, 안전한 프로덕션 환경을 위해서는 항상 CA(인증 기관)에서 서명된 올바른 SSL 인증서를 사용해야 합니다. 관리자는 IIS 관리자 콘솔을 사용하여 자신이 선택한 서명된 인증서로 테스트 인증서를 바꿀 수 있습니다.

<span class="code">Install-PswaWebApplication</span> cmdlet을 실행하거나 IIS 관리자에서 GUI 기반의 구성 단계를 수행하여 Windows PowerShell 웹 액세스 웹 응용 프로그램 구성을 완료할 수 있습니다. 기본적으로 이 cmdlet은 IIS 관리자에 표시된 바와 같이 **기본 웹 사이트** 컨테이너에 웹 응용 프로그램인 **pswa**(및 해당 응용 프로그램 풀인 **pswa\_pool**)를 설치합니다. 필요에 따라 웹 응용 프로그램의 기본 사이트 컨테이너를 변경하는 명령을 이 cmdlet에 추가할 수 있습니다. IIS 관리자는 웹 응용 프로그램에서 사용 가능한 구성 옵션(예: SSL(Secure Sockets Layer) 인증서의 포트 번호 변경)을 제공합니다.

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 보안 정보 </span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>관리자는 반드시 CA에서 서명된 유효한 인증서를 사용하도록 게이트웨이를 구성하는 것이 좋습니다.</p></td>
</tr>
</tbody>
</table>

-   [Install-PswaWebApplication을 사용하여 테스트 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면](#BKMK_testcert)

-   [Install-PswaWebApplication 및 IIS 관리자를 사용하여 정품 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면](#BKMK_gencert)

#### Install-PswaWebApplication을 사용하여 테스트 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면

1.  다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.

    -   Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.

2.  다음을 입력하고 **Enter** 키를 누릅니다.

    **Install-PswaWebApplication -UseTestCertificate**

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 보안 정보 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span class="code">UseTestCertificate</span> 매개 변수는 개인 테스트 환경에서만 사용되어야 합니다. 안전한 프로덕션 환경을 위해 CA에서 서명된 유효한 인증서를 사용하는 것이 좋습니다.</p></td>
    </tr>
    </tbody>
    </table>

    이 cmdlet을 실행하면 Windows PowerShell 웹 액세스 웹 응용 프로그램이 IIS 기본 웹 사이트 컨테이너에 설치됩니다. 이 cmdlet은 기본 웹 사이트인 https://&lt;server\_name&gt;/pswa에서 Windows PowerShell 웹 액세스를 실행하는 데 필요한 인프라를 만듭니다. 웹 응용 프로그램을 다른 웹 사이트에 설치하려면 <span class="code">WebSiteName</span> 매개 변수를 추가하여 웹 사이트 이름을 입력합니다. 웹 응용 프로그램의 이름을 변경하려면(기본 이름: <span class="code">pswa</span>) <span class="code">WebApplicationName</span> 매개 변수를 추가합니다.

    이 cmdlet을 실행하면 다음과 같은 설정이 구성됩니다. 필요에 따라 IIS 관리자 콘솔에서 이러한 설정을 수동으로 변경할 수 있습니다.

    -   Path: /pswa

    -   ApplicationPool: pswa\_pool

    -   EnabledProtocols: http

    -   PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

    <span class="label">예:</span><span class="code">Install-PswaWebApplication –webApplicationName myWebApp –useTestCertificate</span>

    이 예에서 결과로 표시되는 Windows PowerShell 웹 액세스의 웹 사이트는 https://&lt;*server\_name*&gt;/myWebApp입니다.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다. 자세한 내용은 <a href="#BKMK_step3">3단계: 제한적인 권한 부여 규칙 구성</a> 및 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능</a>을 참조하세요.</p></td>
    </tr>
    </tbody>
    </table>

#### Install-PswaWebApplication 및 IIS 관리자를 사용하여 정품 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면

1.  다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.

    -   Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.

2.  다음을 입력하고 **Enter** 키를 누릅니다.

    **Install-PswaWebApplication**

    이 cmdlet을 실행하면 다음과 같은 게이트웨이 설정이 구성됩니다. 필요에 따라 IIS 관리자 콘솔에서 이러한 설정을 수동으로 변경할 수 있습니다. <span class="code">Install-PswaWebApplication</span> cmdlet의 <span class="code">WebsiteName</span> 및 <span class="code">WebApplicationName</span> 매개 변수에 대한 값을 지정할 수도 있습니다.

    -   Path: /pswa

    -   ApplicationPool: pswa\_pool

    -   EnabledProtocols: http

    -   PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3.  다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.

    -   Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다. 서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.

    -   Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.

4.  IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다. **사이트** 폴더를 확장합니다.

5.  Windows PowerShell 웹 액세스 웹 응용 프로그램이 설치된 웹 사이트를 선택합니다. **작업** 창에서 **바인딩**을 클릭합니다.

6.  **사이트 바인딩** 대화 상자에서 **추가**를 클릭합니다.

7.  **사이트 바인딩 추가** 대화 상자의 **유형** 필드에서 **https**를 선택합니다.

8.  **SSL 인증서** 필드의 드롭다운 메뉴에서 서명된 인증서를 선택합니다. **확인**을 클릭합니다. 인증서를 얻는 방법에 대한 자세한 내용은 이 항목의 [IIS 관리자로 SSL 인증서를 구성하려면](#BKMK_cert)을 참조하세요.

    이제 Windows PowerShell 웹 액세스 웹 응용 프로그램이 서명된 SSL 인증서를 사용하도록 구성됩니다. 브라우저 창에서 https://&lt;server\_name&gt;/pswa를 열어 Windows PowerShell 웹 액세스에 액세스할 수 있습니다.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다. 자세한 내용은 <a href="#BKMK_step3">3단계: 제한적인 권한 부여 규칙 구성</a> 및 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능</a>을 참조하세요.</p></td>
    </tr>
    </tbody>
    </table>

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">3단계: 제한적인 권한 부여 규칙 구성</span></a>

------------------------------------------------------------------------

Windows PowerShell Web Access가 설치되고 게이트웨이가 구성되고 나면 사용자는 로그인 페이지를 브라우저에서 열 수 있지만 Windows PowerShell 웹 액세스 관리자가 사용자에게 액세스를 명시적으로 허용할 때까지는 로그인할 수 없습니다. Windows PowerShell 웹 액세스의 액세스 제어는 다음 표에 설명된 여러 Windows PowerShell cmdlet을 통해 관리할 수 있습니다. 권한 부여 규칙을 추가하거나 관리하는 작업에 해당하는 GUI는 없습니다. Windows PowerShell 웹 액세스 cmdlet에 대한 자세한 내용은 참조 항목 [Windows PowerShell 웹 액세스 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)을 참조하세요.

Windows PowerShell 웹 액세스 권한 부여 규칙 및 보안에 대한 자세한 내용은 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)을 참조하세요.

#### 제한적인 권한 부여 규칙을 추가하려면

1.  다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

    -   Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

2.  <span class="label">세션 구성을 사용하여 사용자 액세스를 제한하는 단계(옵션):</span> 규칙에 사용할 세션 구성이 이미 있는지 확인합니다. 해당 구성을 아직 만들지 않은 경우 MSDN의 [about\_Session\_Configuration\_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)에서 세션 구성의 생성 지침을 사용하세요.

3.  다음을 입력하고 **Enter** 키를 누릅니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "클립보드에 복사.")

        Add-PswaAuthorizationRule –UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    이 권한 부여 규칙을 통해 특정 사용자는 일반적으로 액세스 권한을 갖고 있는 네트워크상의 한 컴퓨터에만 액세스할 수 있으며, 일반적인 스크립팅 및 cmdlet 환경에 해당하는 특정 세션 구성에 액세스할 수 있습니다. 다음 예에서는 <span class="code">Contoso</span> 도메인의 <span class="code">JSmith</span>라는 사용자에게 <span class="code">Contoso\_214</span> 컴퓨터를 관리하고, <span class="code">NewAdminsOnly</span>라는 세션 구성을 사용할 수 있는 액세스 권한이 부여됩니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "클립보드에 복사.")

        Add-PswaAuthorizationRule –UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  **Get-PswaAuthorizationRule** cmdlet 또는 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer\_name&gt;을 실행하여 규칙이 생성되었는지 확인합니다. 예를 들어 **Test-PswaAuthorizationRule ?UserName Contoso\\JSmith ?ComputerName Contoso\_214**를 실행합니다.

권한 부여 규칙을 구성하고 나면 권한이 부여된 사용자가 웹 기반 콘솔에 로그인하고 Windows PowerShell 웹 액세스를 사용할 준비가 됩니다.

<a href="" id="BKMK_custom"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">사용자 지정 배포</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

서버 관리자의 역할 및 기능 추가 마법사를 사용하여 Windows Server 2012 R2 또는 Windows Server 2012를 실행하는 서버에서 Windows PowerShell 웹 액세스 게이트웨이를 설치할 수 있습니다. Windows PowerShell 웹 액세스가 설치되면 IIS 관리자에서 게이트웨이 구성을 사용자 지정할 수 있습니다.

<a href="" id="BKMK_custom1"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">1단계: Windows PowerShell 웹 액세스 설치</span></a>

------------------------------------------------------------------------

#### 역할 및 기능 추가 마법사를 사용하여 Windows PowerShell 웹 액세스를 설치하려면

1.  서버 관리자가 이미 열려 있으면 다음 단계로 이동합니다. 서버 관리자가 아직 열려 있지 않으면 다음 중 하나를 수행하여 엽니다.

    -   Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.

    -   Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.

2.  **관리** 메뉴에서 **역할 및 기능 추가**를 클릭합니다.

3.  **설치 유형 선택** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다. **다음**을 클릭합니다.

4.  **대상 서버 선택** 페이지에서 서버 풀의 서버를 선택하거나 오프라인 VHD를 선택합니다. 오프라인 VHD를 대상 서버로 선택하려면 먼저 VHD가 탑재될 서버를 선택한 다음 VHD 파일을 선택합니다. 서버를 서버 풀에 추가하는 방법에 대한 자세한 내용은 서버 관리자 도움말을 참조하세요. 대상 서버를 선택하고 나면 **다음**을 클릭합니다.

5.  마법사의 **기능 선택** 페이지에서 **Windows PowerShell**을 확장한 다음 **Windows PowerShell 웹 액세스**를 선택합니다.

6.  .NET Framework 4.5와 웹 서버(IIS)의 역할 서비스 등 필수 기능을 추가하라는 메시지가 표시됩니다. 필수 기능을 추가하고 계속합니다.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>역할 및 기능 추가 마법사를 사용하여 Windows PowerShell 웹 액세스를 설치하는 경우 IIS 관리자 스냅인을 포함한 웹 서버(IIS)도 설치합니다. 스냅인과 기타 IIS 관리 도구는 역할 및 기능 추가 마법사를 사용하면 기본적으로 설치됩니다. 하지만 다음 절차에 설명된 대로 Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하는 경우에는 관리 도구가 기본적으로 추가되지 않습니다.</p></td>
    </tr>
    </tbody>
    </table>

7.  **설치 선택 확인** 페이지에서는 Windows PowerShell 웹 액세스의 기능 파일을 4단계에서 선택한 대상 서버에 저장하지 않을 경우 **대체 원본 경로 지정**을 클릭하고 기능 파일에 대한 경로를 제공합니다. 그렇지 않으면 **설치**를 클릭합니다.

8.  **설치**를 클릭하고 나면 설치 진행률, 결과 및 메시지(경고, 오류 또는 Windows PowerShell 웹 액세스에 필요한 설치 후 구성 단계 등)가 **설치 진행률** 페이지에 표시됩니다. Windows PowerShell 웹 액세스가 설치되고 나면 게이트웨이에 필요한 기본 설치 지침이 포함된 추가 정보 파일을 검토하라는 메시지가 표시됩니다. 이러한 지침은 이 항목에도 포함되어 있습니다. 추가 정보 파일의 경로는 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>입니다.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">2단계: 게이트웨이 구성</span></a>

------------------------------------------------------------------------

이 섹션의 지침에는 Windows PowerShell 웹 액세스 웹 응용 프로그램을 웹 사이트의 루트 디렉터리가 아닌 하위 디렉터리에 설치하는 방법이 포함되어 있습니다. 이 절차는 <span class="code">Install-PswaWebApplication</span> cmdlet에서 수행된 작업에 해당하는 GUI 기반 작업입니다. 이 섹션에는 IIS 관리자를 사용하여 Windows PowerShell 웹 액세스 게이트웨이를 루트 웹 사이트로 구성하는 방법도 포함되어 있습니다.

-   [IIS 관리자를 사용하여 기존 웹 사이트에 게이트웨이를 구성하려면](#BKMK_configman)

-   [IIS 관리자를 사용하여 테스트 인증서를 사용하는 루트 웹 사이트로 게이트웨이를 구성하려면](#BKMK_configroot)

-   

#### IIS 관리자를 사용하여 기존 웹 사이트에 게이트웨이를 구성하려면

1.  다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.

    -   Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다. 서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.

    -   Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다. **응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.

2.  Windows PowerShell 웹 액세스의 새로운 응용 프로그램 풀을 만듭니다. IIS 관리자 트리 창에서 게이트웨이 서버의 노드를 확장한 다음 **응용 프로그램 풀**을 선택하고 **작업** 창에서 **응용 프로그램 풀 추가**를 클릭합니다.

3.  이름이 **pswa\_pool**인 새로운 응용 프로그램 풀을 추가하거나 다른 이름을 입력합니다. **확인**을 클릭합니다.

4.  IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다. **사이트** 폴더를 선택합니다.

5.  Windows PowerShell 웹 액세스 웹 사이트를 추가할 웹 사이트(예: **기본 웹 사이트**)를 마우스 오른쪽 단추로 클릭한 다음 **응용 프로그램 추가**를 클릭합니다.

6.  **별칭** 필드에 pswa를 입력하거나 다른 별칭을 제공합니다. 이 별칭은 가상 디렉터리 이름이 됩니다. 예를 들어 다음 URL, 즉 https://&lt;server\_name&gt;/pswa의 **pswa**는 이 단계에서 지정된 별칭을 나타냅니다.

7.  **응용 프로그램 풀** 필드에서는 3단계에서 만든 응용 프로그램 풀을 선택합니다.

8.  **실제 경로** 필드에서 응용 프로그램의 위치를 검색합니다. 기본 위치인 %windir%/Web/PowerShellWebAccess/wwwroot를 사용할 수 있습니다. **확인**을 클릭합니다.

9.  이 항목의 [IIS 관리자로 SSL 인증서를 구성하려면](#BKMK_cert) 절차의 단계를 따릅니다.

10. <span class="label">선택적 보안 단계:</span> 트리 창에서 웹 사이트를 선택한 상태에서 내용 창의 **SSL 설정**을 두 번 클릭합니다. **SSL 필요**를 선택한 다음 **작업** 창에서 **적용**을 클릭합니다. 필요에 따라 **SSL 설정** 창에서 Windows PowerShell 웹 액세스 웹 사이트에 연결하는 사용자에게는 클라이언트 인증서가 있어야 할 수 있습니다. 클라이언트 인증서를 통해 클라이언트 장치 사용자의 신분을 확인할 수 있습니다. 클라이언트 인증서를 요구하여 Windows PowerShell 웹 액세스의 보안을 강화하는 방법에 대한 자세한 내용은 이 가이드의 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)을 참조하세요.

11. 클라이언트 장치에서 브라우저 세션을 엽니다. 지원되는 브라우저와 장치에 대한 자세한 내용은 이 항목의 [브라우저 및 클라이언트 장치 지원](#BKMK_browser)을 참조하세요.

12. 새로운 Windows PowerShell 웹 액세스 웹 사이트인 https://&lt;*gateway\_server\_name*&gt;/pswa를 엽니다.

    브라우저에 Windows PowerShell 웹 액세스 콘솔 로그인 페이지가 표시됩니다.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다.</p></td>
    </tr>
    </tbody>
    </table>

13. 관리자 권한으로 실행 옵션을 사용하여 연 Windows PowerShell 세션에서 다음 스크립트(여기서 *application\_pool\_name*은 3단계에서 만든 응용 프로그램 풀의 이름을 나타냄)를 실행하여 권한 부여 파일에 대한 액세스 권한을 응용 프로그램 풀에 제공합니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "클립보드에 복사.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    권한 부여 파일에 대한 기존 액세스 권한을 확인하려면 다음 명령을 실행합니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "클립보드에 복사.")

        c:\windows\system32\icacls.exe $authorizationFile

#### IIS 관리자를 사용하여 테스트 인증서를 사용하는 루트 웹 사이트로 게이트웨이를 구성하려면

1.  다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.

    -   Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다. 서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.

    -   Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다. **응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.

2.  IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다. **사이트** 폴더를 선택합니다.

3.  **작업** 창에서 **웹 사이트 추가**를 클릭합니다.

4.  **Windows PowerShell 웹 액세스**와 같은 웹 사이트의 이름을 입력합니다.

5.  새 웹 사이트의 응용 프로그램 풀이 자동으로 만들어집니다. 다른 응용 프로그램 풀을 사용하려면 **선택**을 클릭하여 새 웹 사이트와 연결될 응용 프로그램 풀을 선택합니다. **응용 프로그램 풀 선택** 대화 상자에서 다른 응용 프로그램 풀을 선택한 다음 **확인**을 클릭합니다.

6.  **실제 경로** 텍스트 상자에서 %*windir*%/Web/PowerShellWebAccess/wwwroot로 이동합니다.

7.  **바인딩** 영역의 **유형** 필드에서 **https**를 선택합니다.

8.  다른 사이트나 응용 프로그램에서 사용하고 있지 않은 웹 사이트에 포트 번호를 할당합니다. 열린 포트를 찾으려면 명령 프롬프트 창에서 **netstat** 명령을 실행합니다. 기본 포트 번호는 443입니다.

    다른 웹 사이트에서 443을 이미 사용하고 있거나 이 포트 번호를 변경해야 할 다른 보안상의 이유가 있는 경우, 기본 포트 번호를 변경합니다. 선택한 포트를 게이트웨이 서버에서 실행 중인 다른 웹 사이트에서 사용하고 있을 경우 **웹 사이트 추가** 대화 상자에서 **확인**을 클릭하면 경고가 표시됩니다. Windows PowerShell 웹 액세스를 실행하려면 미사용 포트를 사용해야 합니다.

9.  조직에 필요한 경우에는 선택적으로 **www.contoso.com** 같이 조직과 사용자가 쉽게 알아볼 수 있는 호스트 이름을 지정합니다. **확인**을 클릭합니다.

10. 보다 안전한 프로덕션 환경을 위해 반드시 CA에서 서명된 유효한 인증서를 제공하는 것이 좋습니다. 사용자는 HTTPS 웹 사이트를 통해서만 Windows PowerShell 웹 액세스에 연결할 수 있으므로, SSL 인증서를 제공해야 합니다. 인증서를 얻는 방법에 대한 자세한 내용은 이 항목의 [IIS 관리자로 SSL 인증서를 구성하려면](#BKMK_cert)을 참조하세요.

11. **확인**을 클릭하여 **웹 사이트 추가** 대화 상자를 닫습니다.

12. 관리자 권한(관리자 권한으로 실행)을 사용하여 열린 Windows PowerShell 세션에서 다음 스크립트(여기서 *application\_pool\_name*은 4단계에서 만든 응용 프로그램 풀의 이름을 나타냄)를 실행하여 권한 부여 파일에 대한 액세스 권한을 응용 프로그램 풀에 제공합니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "클립보드에 복사.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    권한 부여 파일에 대한 기존 액세스 권한을 확인하려면 다음 명령을 실행합니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "클립보드에 복사.")

        c:\windows\system32\icacls.exe $authorizationFile

13. IIS 관리자 트리 창에서 새 웹 사이트가 선택된 상태에서 **작업** 창의 **시작**을 클릭하여 웹 사이트를 시작합니다.

14. 클라이언트 장치에서 브라우저 세션을 엽니다. 지원되는 브라우저와 장치에 대한 자세한 내용은 이 문서의 [브라우저 및 클라이언트 장치 지원](#BKMK_browser)을 참조하세요.

15. 새로운 Windows PowerShell 웹 액세스 웹 사이트를 엽니다.

    루트 웹 사이트가 Windows PowerShell 웹 액세스 폴더를 가리키므로, https://&lt;*gateway\_server\_name*&gt;을 열면 Windows PowerShell 웹 액세스 로그인 페이지가 브라우저에 표시됩니다. URL에는 **/pswa**를 추가하지 않아도 됩니다.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">참고 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">3단계: 제한적인 권한 부여 규칙 구성</span></a>

------------------------------------------------------------------------

Windows PowerShell Web Access가 설치되고 게이트웨이가 구성되고 나면 사용자는 로그인 페이지를 브라우저에서 열 수 있지만 Windows PowerShell 웹 액세스 관리자가 사용자에게 액세스를 명시적으로 허용할 때까지는 로그인할 수 없습니다. Windows PowerShell 웹 액세스의 액세스 제어는 다음 표에 설명된 여러 Windows PowerShell cmdlet을 통해 관리할 수 있습니다. 권한 부여 규칙을 추가하거나 관리하는 작업에 해당하는 GUI는 없습니다. Windows PowerShell 웹 액세스 cmdlet에 대한 자세한 내용은 참조 항목 [Windows PowerShell 웹 액세스 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)을 참조하세요.

Windows PowerShell 웹 액세스 권한 부여 규칙 및 보안에 대한 자세한 내용은 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)을 참조하세요.

#### 제한적인 권한 부여 규칙을 추가하려면

1.  다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

    -   Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

2.  <span class="label">세션 구성을 사용하여 사용자 액세스를 제한하는 단계(옵션):</span> 규칙에 사용할 세션 구성이 이미 있는지 확인합니다. 해당 구성을 아직 만들지 않은 경우 MSDN의 [about\_Session\_Configuration\_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)에서 세션 구성의 생성 지침을 사용하세요.

3.  다음을 입력하고 **Enter** 키를 누릅니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "클립보드에 복사.")

        Add-PswaAuthorizationRule –UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    이 권한 부여 규칙을 통해 특정 사용자는 일반적으로 액세스 권한을 갖고 있는 네트워크상의 한 컴퓨터에만 액세스할 수 있으며, 일반적인 스크립팅 및 cmdlet 환경에 해당하는 특정 세션 구성에 액세스할 수 있습니다. 다음 예에서는 <span class="code">Contoso</span> 도메인의 <span class="code">JSmith</span>라는 사용자에게 <span class="code">Contoso\_214</span> 컴퓨터를 관리하고, <span class="code">NewAdminsOnly</span>라는 세션 구성을 사용할 수 있는 액세스 권한이 부여됩니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "클립보드에 복사.")

        Add-PswaAuthorizationRule –UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  **Get-PswaAuthorizationRule** cmdlet 또는 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer\_name&gt;을 실행하여 규칙이 생성되었는지 확인합니다. 예를 들어 **Test-PswaAuthorizationRule ?UserName Contoso\\JSmith ?ComputerName Contoso\_214**를 실행합니다.

권한 부여 규칙을 구성하고 나면 권한이 부여된 사용자가 웹 기반 콘솔에 로그인하고 Windows PowerShell 웹 액세스를 사용할 준비가 됩니다.

<a href="" id="BKMK_configcert"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">정품 인증서 구성</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

안전한 프로덕션 환경을 위해 항상 CA(인증 기관)에서 서명된 유효한 SSL 인증서를 사용하세요. 이 섹션의 절차에서는 CA에서 유효한 SSL 인증서를 얻고 적용하는 방법을 설명합니다.

### IIS 관리자로 SSL 인증서를 구성하려면

1.  IIS 관리자 트리 창에서 Windows PowerShell 웹 액세스가 설치되어 있는 서버를 선택합니다.

2.  내용 창에서 **서버 인증서**를 두 번 클릭합니다.

3.  **작업** 창에서 다음 중 하나를 수행합니다. IIS에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [IIS 7에서 서버 인증서 구성](https://technet.microsoft.com/library/cc732230.aspx)을 참조하세요.

    -   네트워크 위치에서 기존의 유효한 인증서를 가져오려면 **가져오기**를 클릭합니다.

    -   CA에서 VeriSign™, Thawte 또는 GeoTrust® 등의 인증서를 요청하려면 **인증서 요청 만들기**를 클릭합니다. 인증서의 일반 이름은 요청의 호스트 헤더와 일치해야 합니다. 예를 들어 클라이언트 브라우저에서 http://www.contoso.com/을 요청하면 일반 이름도 http://www.contoso.com/이어야 합니다. 이 방법이 Windows PowerShell 웹 액세스 게이트웨이에 인증서를 제공하는 가장 안전한 방법입니다.

    -   곧바로 사용할 수 있는 인증서를 만든 다음 나중에 필요할 때 CA에서 서명을 받아 사용하려면 **자체 서명된 인증서 만들기**를 클릭합니다. **Windows PowerShell 웹 액세스**와 같이 자체 서명된 인증서에 알기 쉬운 이름을 지정합니다. 이 방법은 안전하지 않으므로 개인 테스트 환경용으로만 사용하는 것이 좋습니다.

4.  인증서를 만들거나 구한 다음, IIS 관리자 트리 창에서 인증서가 적용될 웹 사이트(예: **기본 웹 사이트**)를 IIS 관리자 트리 창에서 선택한 다음 **작업** 창에서 **바인딩**을 클릭합니다.

5.  해당 사이트의 바인딩이 표시되지 않은 경우, **사이트 바인딩 추가** 대화 상자에서 사이트의 **https** 바인딩을 추가합니다. 자체 서명된 인증서를 사용하지 않을 경우에는 이 절차의 3단계에서 설명된 호스트 이름을 지정합니다. 자체 서명된 인증서를 사용할 경우에는 이 단계가 필요하지 않습니다.

6.  이 절차의 3단계에서 얻거나 만든 인증서를 선택한 다음 **확인**을 클릭합니다.

<a href="" id="BKMK_using"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">웹 기반 Windows PowerShell 콘솔 사용</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

이 항목에 설명된 대로 Windows PowerShell 웹 액세스가 설치되고 게이트웨이 구성이 완료된 다음에는 Windows PowerShell 웹 기반 콘솔을 사용할 수 있습니다. 웹 기반 콘솔에서 시작하는 방법에 대한 자세한 내용은 [웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)을 참조하세요.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">참고 항목</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[IIS(인터넷 정보 서비스) 7.0 설명서](https://technet.microsoft.com/library/cc753433.aspx)
[IIS 관리자 7.0 도움말](https://technet.microsoft.com/library/cc732664.aspx)
[웹 서버 보안 구성(IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec 배포 리소스](https://technet.microsoft.com/network/bb531150)

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


