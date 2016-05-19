#  Windows PowerShell 웹 액세스 제거

업데이트됨: 2013년 6월 24일

적용 대상: Windows Server 2012 R2, Windows Server 2012

Windows Server 2012 R2 또는 Windows Server 2012를 실행하는 게이트웨이 서버에서 Windows PowerShell 웹 액세스 웹 사이트 및 응용 프로그램을 삭제하려면 이 항목의 단계를 수행합니다. 시작하기 전에 웹 기반 콘솔의 사용자에게 웹 사이트가 제거됨을 알립니다.

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

게이트웨이 서버에서 Windows PowerShell 웹 액세스를 제거하기 전에 <span class="code">Uninstall-PswaWebApplication</span> cmdlet을 실행하여 웹 사이트와 Windows PowerShell 웹 액세스 웹 응용 프로그램을 제거하거나, IIS 관리자 절차 [IIS 관리자를 사용하여 Windows PowerShell 웹 액세스 웹 사이트와 웹 응용 프로그램을 삭제하려면](#BKMK_delsite)을 사용합니다..

자동으로 설치된 IIS나 기타 기능은 Windows PowerShell 웹 액세스에서 실행되어야 하므로, Windows PowerShell 웹 액세스를 제거해도 제거되지 않습니다. 제거 프로세스에서는 Windows PowerShell 웹 액세스가 종속된 기능을 설치된 상태로 남겨 두기 때문에 필요한 경우 이러한 기능을 별도로 제거할 수 있습니다.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">권장(빠른) 제거</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

이 섹션의 절차를 따라서 Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스 웹 응용 프로그램 및 Windows PowerShell 웹 액세스 기능을 모두 제거할 수 있습니다.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">1단계: 웹 응용 프로그램 삭제</span></a>

------------------------------------------------------------------------

고유의 사용자 지정 웹 사이트 이름을 지정한 경우 <span class="code">WebsiteName</span> 매개 변수를 명령에 추가하고 웹 사이트 이름을 지정합니다. 기본 응용 프로그램(**pswa**)이 아닌 사용자 지정 웹 응용 프로그램을 사용한 경우 <span class="code">WebApplicationName</span> 매개 변수를 명령에 추가하고 웹 응용 프로그램의 이름을 지정합니다.

#### Uninstall-PswaWebApplication cmdlet을 사용하여 웹 사이트와 웹 응용 프로그램을 삭제하려면

1.  다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.

    -   Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다..

2.  **Uninstall-PswaWebApplication**을 입력하고 **Enter** 키를 누릅니다..

3.  테스트 인증서를 사용하는 경우, 다음 예에서와 같이 cmdlet에 <span class="code">DeleteTestCertificate</span> 매개 변수를 추가합니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "클립보드에 복사.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">2단계: Windows PowerShell 웹 액세스 제거</span></a>

------------------------------------------------------------------------

#### Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 제거하려면

1.  다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다. 세션이가 이미 열려 있으면 다음 단계로 이동합니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다..

    -   Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다..

2.  다음을 입력하고 **Enter** 키를 누릅니다. 여기서 *computer\_name*은 Windows PowerShell 웹 액세스를 제거할 원격 서버를 나타냅니다. 제거 작업에 필요한 경우 <span class="code">–Restart</span> 매개 변수를 추가하여 대상 서버를 자동으로 다시 시작할 수 있습니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "클립보드에 복사.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    역할 및 기능을 오프라인 VHD에서 제거하려는 경우에는 <span class="code">-ComputerName</span> 매개 변수와 <span class="code">-VHD</span> 매개 변수를 모두 추가해야 합니다. <span class="code">-ComputerName</span> 매개 변수에는 VHD를 탑재할 서버의 이름이 포함되며, <span class="code">-VHD</span> 매개 변수에는 지정된 서버에서의 VHD 파일 경로가 포함됩니다.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "클립보드에 복사.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess –VHD <path> -ComputerName <computer_name> -Restart

3.  제거가 완료되면 서버 관리자에서 **모든 서버** 페이지를 열고 기능을 제거한 서버를 선택한 후 선택한 서버 페이지에서 **역할 및 기능** 타일을 확인하여 Windows PowerShell 웹 액세스가 제거되었는지 확인합니다. 선택한 서버를 대상으로 <span class="code">Get-WindowsFeature</span> cmdlet(Get-WindowsFeature -ComputerName &lt;*computer\_name*&gt;)을 실행하여 서버에 설치된 역할 및 기능 목록을 볼 수도 있습니다.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">사용자 지정 제거</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

이 섹션의 절차를 따라서 서버 관리자의 역할 및 기능 제거 마법사 및 IIS 관리자 콘솔을 사용하여 Windows PowerShell 웹 액세스 웹 응용 프로그램 및 Windows PowerShell 웹 액세스 기능을 모두 제거할 수 있습니다.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">1단계: 웹 응용 프로그램 삭제</span></a>

------------------------------------------------------------------------

#### IIS 관리자를 사용하여 Windows PowerShell 웹 액세스의 웹 사이트와 웹 응용 프로그램을 삭제하려면

1.  다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다. 콘솔이 이미 열려 있으면 다음 단계로 이동합니다.

    -   Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다. 서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다..

    -   Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다. **응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.

2.  IIS 관리자의 트리 창에서 Windows PowerShell 웹 액세스 웹 응용 프로그램이 실행 중인 웹 사이트를 선택합니다.

3.  **작업** 창의 **웹 사이트 관리**에서 **중지**를 클릭합니다..

4.  트리 창에서 Windows PowerShell 웹 액세스 웹 응용 프로그램이 실행 중인 웹 사이트의 웹 응용 프로그램을 마우스 오른쪽 단추로 클릭한 다음 **제거**를 클릭합니다..

5.  트리 창에서 **응용 프로그램 풀**을 선택하고 Windows PowerShell 웹 액세스 응용 프로그램 폴더를 선택한 후 **작업** 창에서 **중지**를 선택하고 내용 창에서 **제거**를 클릭합니다.

6.  IIS 관리자를 닫습니다.

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
    <td><p>인증서는 제거 과정에서 제거되지 않습니다. 자체 서명된 인증서를 만들었거나 테스트 인증서를 사용한 경우에 이 인증서를 제거하려면 IIS 관리자에서 해당 인증서를 삭제합니다.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">2단계: Windows PowerShell 웹 액세스 제거</span></a>

------------------------------------------------------------------------

#### 역할 및 기능 제거 마법사를 사용하여 Windows PowerShell 웹 액세스를 제거하려면

1.  서버 관리자가 이미 열려 있으면 다음 단계로 이동합니다. 서버 관리자가 아직 열려 있지 않으면 다음 중 하나를 수행하여 엽니다.

    -   Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.

    -   Windows **시작** 화면에서 **서버 관리자**를 클릭합니다..

2.  **관리** 메뉴에서 **역할 및 기능 제거**를 클릭합니다..

3.  **대상 서버 선택** 페이지에서 기능을 제거할 서버나 오프라인 VHD를 선택합니다. 오프라인 VHD를 선택하려면 먼저 VHD가 탑재될 서버를 선택한 다음 VHD 파일을 선택합니다. 대상 서버를 선택하고 나면 **다음**을 클릭합니다..

4.  다시 **다음**을 클릭하여 **기능 제거** 페이지로 이동합니다.

5.  **Windows PowerShell 웹 액세스** 확인란의 선택을 취소하고 **다음**을 클릭합니다..

6.  **제거 선택 확인** 페이지에서 **제거**를 클릭합니다..

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">참고 항목</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Install and Use Windows PowerShell Web Access(Windows PowerShell 웹 액세스 설치 및 사용)](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS 관리자 7.0 도움말](https://technet.microsoft.com/library/cc732664.aspx)

<span>표시:</span> 상속됨 보호됨

<span class="stdr-votetitle">이 페이지가 도움이 되었나요?</span>
예
아니요

추가 피드백

<span class="stdr-count"><span class="stdr-charcnt">1500</span>자 남음</span>
제출
건너뛰기

<span class="stdr-thankyou">감사합니다!</span> <span class="stdr-appreciate">피드백에 감사드립니다.</span>

[프로필 관리](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 사이트 피드백</a>
사이트 피드백

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

사용 환경에 대한 의견을 제공해주세요...

페이지가 빨리 로드되었나요?

<span> 예<span> </span></span> <span> 아니요<span> </span></span>

페이지 디자인이 마음에 드세요?

<span> 예<span> </span></span> <span> 아니요<span> </span></span>

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


