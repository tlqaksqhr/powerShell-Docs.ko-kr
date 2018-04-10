# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="b95a1-101">PowerShell Core에서 WSMan(WS-Management) 원격</span><span class="sxs-lookup"><span data-stu-id="b95a1-101">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="b95a1-102">원격 끝점 만들기 지침</span><span class="sxs-lookup"><span data-stu-id="b95a1-102">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="b95a1-103">Windows용 PowerShell Core 패키지의 `$PSHome`에는 WinRM 플러그인(`pwrshplugin.dll`) 및 설치 스크립트(`Install-PowerShellRemoting.ps1`)가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-103">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="b95a1-104">이러한 파일은 엔드포인트가 지정된 경우에 PowerShell이 들어오는 PowerShell 원격 연결을 수락하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-104">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="b95a1-105">동기</span><span class="sxs-lookup"><span data-stu-id="b95a1-105">Motivation</span></span>

<span data-ttu-id="b95a1-106">PowerShell을 설치하면 `New-PSSession` 및 `Enter-PSSession`을 사용하여 원격 컴퓨터에 대한 PowerShell 세션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-106">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="b95a1-107">들어오는 PowerShell 원격 연결을 수락하도록 허용하려면 사용자가 WinRM 원격 기능 엔드포인트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-107">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="b95a1-108">이는 사용자가 Install-PowerShellRemoting.ps1을 실행하여 WinRM 엔드포인트를 만드는 명시적인 옵트인 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-108">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="b95a1-109">설치 스크립트는 `Enable-PSRemoting`에 추가 기능을 추가하여 동일한 동작을 수행할 때까지 단기적인 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-109">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="b95a1-110">자세한 내용은 [#1193](https://github.com/PowerShell/PowerShell/issues/1193) 문제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b95a1-110">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="b95a1-111">스크립트 동작</span><span class="sxs-lookup"><span data-stu-id="b95a1-111">Script Actions</span></span>

<span data-ttu-id="b95a1-112">스크립트</span><span class="sxs-lookup"><span data-stu-id="b95a1-112">The script</span></span>

1. <span data-ttu-id="b95a1-113">%windir%\System32\PowerShell 내에 플러그인에 대한 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-113">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="b95a1-114">pwrshplugin.dll을 해당 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-114">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="b95a1-115">구성 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-115">Generates a configuration file</span></span>
1. <span data-ttu-id="b95a1-116">해당 플러그 인을 WinRM에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-116">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="b95a1-117">등록</span><span class="sxs-lookup"><span data-stu-id="b95a1-117">Registration</span></span>

<span data-ttu-id="b95a1-118">스크립트는 관리자 수준의 PowerShell 세션 내에서 실행되어야 하며, 두 가지 모드로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-118">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="b95a1-119">등록할 PowerShell의 인스턴스에서 실행</span><span class="sxs-lookup"><span data-stu-id="b95a1-119">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="b95a1-120">등록할 인스턴스 대신 PowerShell의 다른 인스턴스에서 실행</span><span class="sxs-lookup"><span data-stu-id="b95a1-120">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="b95a1-121">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-121">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="b95a1-122">**참고:** 원격 기능 등록 스크립트는 WinRM을 다시 시작하므로 스크립트가 실행된 후 기존의 모든 PSRP 세션이 즉시 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-122">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="b95a1-123">원격 세션 중에 실행될 경우 연결이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-123">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="b95a1-124">새 엔드포인트에 연결하는 방법</span><span class="sxs-lookup"><span data-stu-id="b95a1-124">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="b95a1-125">`-ConfigurationName "some endpoint name"`을 지정하여 새로운 PowerShell 엔드포인트에 대한 PowerShell 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-125">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="b95a1-126">위의 예제에서 PowerShell 인스턴스에 연결하려면 다음 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-126">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="b95a1-127">`-ConfigurationName`을 지정하지 않는 `New-PSSession` 및 `Enter-PSSession` 호출은 기본 PowerShell 엔드포인트인 `microsoft.powershell`을 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b95a1-127">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>