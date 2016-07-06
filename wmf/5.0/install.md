# 설치 지침

운영 체제 및 아키텍처에 맞는 올바른 패키지를 다운로드하세요.

| 운영 체제       | 아키텍처 | 패키지 이름              | 
|------------------------|--------------|---------------------------| 
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) | 
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) | 
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Windows 탐색기(또는 Windows Server 2012 R2 및 Windows 8.1의 파일 탐색기)에서 WMF 5.0을 설치하려면**

1. MSU 파일을 다운로드한 폴더로 이동합니다.

2. MSU를 두 번 클릭하여 실행합니다.

**명령 프롬프트에서 WMF 5.0을 설치하려면** 

1. 컴퓨터의 아키텍처에 맞는 올바른 패키지를 다운로드한 후 관리자 권한(관리자 권한으로 실행)으로 명령 프롬프트 창을 엽니다. Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1의 Server Core 설치 옵션에서는 명령 프롬프트가 기본적으로 관리자 권한으로 열립니다.

2. WMF 5.0 설치 패키지를 다운로드하거나 복사한 폴더로 디렉터리를 변경합니다.

3. 다음 명령 중 하나를 실행합니다.
    - Windows Server 2012 R2 또는 Windows 8.1 x64를 실행 중인 컴퓨터에서는 **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**를 실행합니다.
    - Windows Server 2012를 실행 중인 컴퓨터에서는 **W2K12-KB3134759-x64.msu /quiet**를 실행합니다.
    - Windows Server 2008 R2 SP1 또는 Windows 7 SP1 x64를 실행 중인 컴퓨터에서는 **Win7AndW2K8R2-KB3134760-x64.msu /quiet**를 실행합니다.
    - Windows 8.1 x86을 실행 중인 컴퓨터에서는 **Win8.1-KB3134758-x86.msu /quiet**를 실행합니다.
    - Windows 7 SP1 x86을 실행 중인 컴퓨터에서는 **Win7-KB3134760-x86.msu /quiet**를 실행합니다.

**Windows Server 2008 SP1 및 Windows 7 SP1에 대한 추가 설치 참고 사항:**

다음 필수 조건이 충족되었는지 확인하세요.
- 최신 서비스 팩이 설치되어 있습니다.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)이 설치되어 있습니다.

*WinRM 종속성:* Windows PowerShell DSC(원하는 상태 구성)는 WinRM에 종속됩니다. WinRM은 Windows Server 2008 R2 및 Windows 7에서 기본적으로 사용하도록 설정되지 않습니다. WinRM을 사용하도록 설정하려면 Windows PowerShell 관리자 권한 세션에서 **Set-WSManQuickConfig**를 실행합니다.




<!--HONumber=Jun16_HO4-->


