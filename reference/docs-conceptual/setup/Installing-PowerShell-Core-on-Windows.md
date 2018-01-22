# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="30a2f-101">Windows에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="30a2f-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="30a2f-102">MSI</span><span class="sxs-lookup"><span data-stu-id="30a2f-102">MSI</span></span>

<span data-ttu-id="30a2f-103">Windows 클라이언트 또는 Windows Server(Windows 7 SP1, Server 2008 R2 이상에서 작동)에 PowerShell을 설치하려면 GitHub [릴리스][] 페이지에서 MSI 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="30a2f-104">MSI 파일은 다음과 같습니다. - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="30a2f-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="30a2f-105">다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="30a2f-106">설치하고 나면 시작 메뉴에 바로 가기가 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="30a2f-107">기본적으로 패키지는 `$env:ProgramFiles\PowerShell\`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="30a2f-108">시작 메뉴 또는 `$env:ProgramFiles\PowerShell\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="30a2f-109">전제 조건</span><span class="sxs-lookup"><span data-stu-id="30a2f-109">Prerequisites</span></span>

<span data-ttu-id="30a2f-110">WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="30a2f-111">Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="30a2f-112">직접 다운로드 또는 Windows 업데이트를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="30a2f-113">옵션 패키지를 포함하여 완전히 패치된 지원 시스템은 이미 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="30a2f-114">Windows 7 및 Windows Server 2008 R2에 WMF(Windows Management Framework) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) 이상([5.1](https://www.microsoft.com/download/details.aspx?id=54616))을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-114">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="30a2f-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="30a2f-115">ZIP</span></span>

<span data-ttu-id="30a2f-116">고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="30a2f-117">ZIP 아카이브를 사용하면 MSI 패키지에서와 같이 전제 조건 확인을 받지 못하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="30a2f-118">따라서 Windows 10 이전의 Windows 버전에서 WSMan을 원격으로 실행하려면 [전제 조건](#prerequisites)이 충족되는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="30a2f-119">Nano 서버에 배포</span><span class="sxs-lookup"><span data-stu-id="30a2f-119">Deploying on Nano Server</span></span>

<span data-ttu-id="30a2f-120">이 지침은 PowerShell 버전이 이미 Nano 서버 이미지에서 실행 중이며 [Nano 서버 이미지 작성기](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server)에 의해 생성된 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-120">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="30a2f-121">Nano 서버는 "헤드리스" OS이며 PowerShell Core 이진 파일은 다음 두 가지 방식으로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-121">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="30a2f-122">오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-122">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="30a2f-123">온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-123">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="30a2f-124">두 경우 모두 Windows 10 x64 Zip 릴리스 패키지가 필요하며 "관리자" PowerShell 인스턴스 내에서 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-124">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="30a2f-125">PowerShell Core의 오프라인 배포</span><span class="sxs-lookup"><span data-stu-id="30a2f-125">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="30a2f-126">자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-126">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="30a2f-127">이미지를 탑재 해제하고 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-127">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="30a2f-128">Windows PowerShell의 받은 편지함 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-128">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="30a2f-129">지침에 따라 [다른 인스턴스 기법](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 끝점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-129">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="30a2f-130">PowerShell Core의 온라인 배포</span><span class="sxs-lookup"><span data-stu-id="30a2f-130">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="30a2f-131">다음 단계는 PowerShell Core를 실행 중인 Nano 서버 인스턴스에 배포하고 원격 끝점을 구성하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-131">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="30a2f-132">Windows PowerShell의 받은 편지함 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="30a2f-132">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="30a2f-133">Nano 서버 인스턴스에 파일 복사</span><span class="sxs-lookup"><span data-stu-id="30a2f-133">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="30a2f-134">세션 입력</span><span class="sxs-lookup"><span data-stu-id="30a2f-134">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="30a2f-135">Zip 파일 추출</span><span class="sxs-lookup"><span data-stu-id="30a2f-135">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="30a2f-136">WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [다른 인스턴스 기법](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 끝점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-136">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="30a2f-137">원격 끝점 만들기 지침</span><span class="sxs-lookup"><span data-stu-id="30a2f-137">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="30a2f-138">PowerShell Core는 WSMan 및 SSH보다 PowerShell Remoting Protocol(PSRP)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-138">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="30a2f-139">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30a2f-139">For more information, see:</span></span>

* <span data-ttu-id="30a2f-140">[PowerShell Core에서의 SSH 원격 작업][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="30a2f-140">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="30a2f-141">[PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="30a2f-141">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="30a2f-142">아티팩트 설치 지침</span><span class="sxs-lookup"><span data-stu-id="30a2f-142">Artifact Installation Instructions</span></span>

<span data-ttu-id="30a2f-143">[AppVeyor][]를 사용하여 모든 CI 빌드에 CoreCLR 비트가 있는 아카이브를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-143">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="30a2f-144">CoreCLR 아티팩트</span><span class="sxs-lookup"><span data-stu-id="30a2f-144">CoreCLR Artifacts</span></span>

* <span data-ttu-id="30a2f-145">특정 빌드의 **아티팩트** 탭에서 zip 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2f-145">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="30a2f-146">zip 파일 차단 해제: 파일 탐색기에서 마우스 오른쪽 버튼을 클릭 -> 속성 -> '차단 해제' 확인란 선택 -> 적용</span><span class="sxs-lookup"><span data-stu-id="30a2f-146">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="30a2f-147">zip 파일을 `bin` 디렉터리로 추출</span><span class="sxs-lookup"><span data-stu-id="30a2f-147">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[릴리스]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
