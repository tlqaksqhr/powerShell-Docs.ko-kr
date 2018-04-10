# <a name="installing-powershell-core-on-windows"></a>Windows에서 PowerShell Core 설치

## <a name="msi"></a>MSI

Windows 클라이언트 또는 Windows Server(Windows 7 SP1, Server 2008 R2 이상에서 작동)에 PowerShell을 설치하려면 GitHub [릴리스][] 페이지에서 MSI 패키지를 다운로드합니다.

MSI 파일은 다음과 같습니다. - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.

설치하고 나면 시작 메뉴에 바로 가기가 생깁니다.

* 기본적으로 패키지는 `$env:ProgramFiles\PowerShell\`에 설치됩니다.
* 시작 메뉴 또는 `$env:ProgramFiles\PowerShell\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.

### <a name="prerequisites"></a>필수 구성 요소

WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.

* Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치합니다.
  직접 다운로드 또는 Windows 업데이트를 통해 사용할 수 있습니다.
  옵션 패키지를 포함하여 완전히 패치된 지원 시스템은 이미 설치되어 있습니다.
* Windows 7 및 Windows Server 2008 R2에 WMF(Windows Management Framework) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) 이상([5.1](https://www.microsoft.com/download/details.aspx?id=54616))을 설치합니다.

## <a name="zip"></a>ZIP

고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다.
ZIP 아카이브를 사용하면 MSI 패키지에서와 같이 전제 조건 확인을 받지 못하게 됩니다.
따라서 Windows 10 이전의 Windows 버전에서 WSMan을 원격으로 실행하려면 [전제 조건](#prerequisites)이 충족되는지 확인해야 합니다.

## <a name="deploying-on-nano-server"></a>Nano 서버에 배포

이 지침은 PowerShell 버전이 이미 Nano 서버 이미지에서 실행 중이며 [Nano 서버 이미지 작성기](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server)에 의해 생성된 것으로 가정합니다.
Nano 서버는 "헤드리스" OS이며 PowerShell Core 이진 파일은 다음 두 가지 방식으로 배포할 수 있습니다.

1. 오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.
1. 온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.

두 경우 모두 Windows 10 x64 Zip 릴리스 패키지가 필요하며 "관리자" PowerShell 인스턴스 내에서 명령을 실행해야 합니다.

### <a name="offline-deployment-of-powershell-core"></a>PowerShell Core의 오프라인 배포

1. 자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.
1. 이미지를 탑재 해제하고 부팅합니다.
1. Windows PowerShell의 받은 편지함 인스턴스에 연결합니다.
1. 지침에 따라 [다른 인스턴스 기법](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 끝점을 만듭니다.

### <a name="online-deployment-of-powershell-core"></a>PowerShell Core의 온라인 배포

다음 단계는 PowerShell Core를 실행 중인 Nano 서버 인스턴스에 배포하고 원격 끝점을 구성하는 과정을 안내합니다.

* Windows PowerShell의 받은 편지함 인스턴스에 연결

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* Nano 서버 인스턴스에 파일 복사

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* 세션 입력

```powershell
Enter-PSSession $session
```

* Zip 파일 추출

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [다른 인스턴스 기법](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 끝점을 만듭니다.

## <a name="instructions-to-create-a-remoting-endpoint"></a>원격 끝점 만들기 지침

PowerShell Core는 WSMan 및 SSH보다 PowerShell Remoting Protocol(PSRP)을 지원합니다. 자세한 내용은 다음을 참조하세요.

* [PowerShell Core에서의 SSH 원격 작업][ssh-remoting]
* [PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]

## <a name="artifact-installation-instructions"></a>아티팩트 설치 지침

[AppVeyor][]를 사용하여 모든 CI 빌드에 CoreCLR 비트가 있는 아카이브를 게시합니다.

## <a name="coreclr-artifacts"></a>CoreCLR 아티팩트

* 특정 빌드의 **아티팩트** 탭에서 zip 패키지를 다운로드합니다.
* zip 파일 차단 해제: 파일 탐색기에서 마우스 오른쪽 버튼을 클릭 -> 속성 -> '차단 해제' 확인란 선택 -> 적용
* zip 파일을 `bin` 디렉터리로 추출
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[릴리스]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell