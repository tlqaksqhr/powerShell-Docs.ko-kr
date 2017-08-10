---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 설치"
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
ms.openlocfilehash: 2b4cdec52dfc98649a81ab2265a204fcdb0bd8d7
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="5d703-103">Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-103">Installing Windows PowerShell</span></span>
<span data-ttu-id="5d703-104">Windows® 8 및 Windows Server® 2012에는 Windows PowerShell 3.0과 모든 필수 구성 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-104">Windows® 8 and Windows Server® 2012 include Windows PowerShell 3.0 and all of its prerequisites.</span></span> <span data-ttu-id="5d703-105">Windows PowerShell 3.0을 사용할 수 없는 이전 버전의 호스트 프로그램과 호환성을 위해 시스템에 Windows PowerShell 2.0 엔진도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-105">The system also includes the Windows PowerShell 2.0 engine for backward compatibility with host programs that cannot use Windows PowerShell 3.0.</span></span>

<span data-ttu-id="5d703-106">이 항목에서는 이전 시스템에 Windows PowerShell 3.0을 설치하고 필요한 기능을 설치하여 사용하도록 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-106">This topic explains how to install Windows PowerShell 3.0 on earlier systems and install and enable the required features.</span></span>

<span data-ttu-id="5d703-107">이 항목에는 다음 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-107">This topic includes the following sections:</span></span>

-   [<span data-ttu-id="5d703-108">Windows 8 및 Windows Server 2012에 Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-108">Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [<span data-ttu-id="5d703-109">Windows 7 및 Windows Server 2008 R2에 Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-109">Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [<span data-ttu-id="5d703-110">Windows Server 2008에 Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-110">Installing Windows PowerShell on Windows Server 2008</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [<span data-ttu-id="5d703-111">Server Core에 Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-111">Installing Windows PowerShell on Server Core</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [<span data-ttu-id="5d703-112">Windows PowerShell 웹 액세스 배포</span><span class="sxs-lookup"><span data-stu-id="5d703-112">Deploying Windows PowerShell Web Access</span></span>](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [<span data-ttu-id="5d703-113">Windows PowerShell 2.0 엔진 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-113">Installing the Windows PowerShell 2.0 Engine</span></span>](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <span data-ttu-id="5d703-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Windows 8 및 Windows Server 2012에 Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>
<span data-ttu-id="5d703-115">Windows PowerShell 3.0은 설치 및 구성되고 사용 준비가 완료된 상태로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-115">Windows PowerShell 3.0 arrives installed, configured, and ready to use.</span></span> <span data-ttu-id="5d703-116">Windows PowerShell ISE(통합 스크립팅 환경)를 설치하고 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-116">Windows PowerShell Integrated Scripting Environment (ISE) is installed and enabled.</span></span> <span data-ttu-id="5d703-117">Windows PowerShell을 시작하는 방법에 대한 자세한 내용은 [Starting Windows PowerShell on Windows 8(Windows 8에서 Windows PowerShell 시작)](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) 및 [Starting Windows PowerShell on Windows Server 2012(Windows Server 2012에서 Windows PowerShell 시작)](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d703-117">For information about starting Windows PowerShell, see [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) and [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell).</span></span>

## <span data-ttu-id="5d703-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Windows 7 및 Windows Server 2008 R2에 Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>
<span data-ttu-id="5d703-119">이 지침에서는 Windows 7 서비스 팩1 및 Windows Server 2008 R2 서비스 팩 1을 실행하는 컴퓨터에 Windows PowerShell 3.0을 설치하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-119">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows 7 with Service Pack 1 and Windows Server 2008 R2 with Service Pack 1.</span></span> <span data-ttu-id="5d703-120">Windows Server 2008 R2의 Server Core 설치 옵션으로 실행되는 컴퓨터를 위한 별도의 설치 지침은 아래에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-120">There are separate installation instructions below for computers running with the Server Core installation option of Windows Server 2008 R2.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="5d703-121">설치 준비</span><span class="sxs-lookup"><span data-stu-id="5d703-121">Getting ready to install</span></span>

-   <span data-ttu-id="5d703-122">Windows Management Framework 3.0을 설치하기 전에 Windows Management Framework 3.0의 이전 버전을 모두 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-122">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="5d703-123">Windows PowerShell 3.0을 설치하려면</span><span class="sxs-lookup"><span data-stu-id="5d703-123">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="5d703-124">Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547))에서 Microsoft .NET Framework 4(dotNetFx40_Full_setup.exe) 전체 설치를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-124">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="5d703-125">또는 Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919))에서 Microsoft .NET Framework 4.5(dotNetFx45_Full_setup.exe)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-125">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

2.  <span data-ttu-id="5d703-126">Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290))에서 Windows Management Framework 3.0을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-126">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

<span data-ttu-id="5d703-127">Windows PowerShell 3.0을 시작하는 방법에 대한 자세한 내용은 [이전 버전의 Windows에서 Windows PowerShell 시작](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d703-127">For information about starting Windows PowerShell 3.0, see [Starting Windows PowerShell on Earlier Versions of Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).</span></span>

## <span data-ttu-id="5d703-128"><a name="BKMK_InstallingOnServerCore"></a>Server Core에 Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-128"><a name="BKMK_InstallingOnServerCore"></a>Installing Windows PowerShell on Server Core</span></span>
<span data-ttu-id="5d703-129">이 지침에서는 Windows Server 2008 R2 서비스 팩 1의 Server Core 설치 옵션을 실행하는 컴퓨터에 Windows PowerShell 3.0을 설치하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-129">These instructions explain how to install Windows PowerShell 3.0 on computers running the Server Core installation option of Windows Server 2008 R2 with Service Pack 1.</span></span>

<span data-ttu-id="5d703-130">절차의 첫 번째 단계에서는 DISM(배포 이미지 서비스 및 관리) 명령을 사용하여 Server Core용 Microsoft .NET Framework 2.0 및 Windows PowerShell 2.0을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-130">The first steps in the procedure use Deployment Image Servicing and Management (DISM) commands to install Microsoft .NET Framework 2.0 for Server Core and Windows PowerShell 2.0.</span></span> <span data-ttu-id="5d703-131">이러한 프로그램은 이후 단계에서 설치되는 Windows Management Framework 3.0에 대한 필수 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-131">These programs are prerequisites for Windows Management Framework 3.0, which is installed in a subsequent step.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="5d703-132">설치 준비</span><span class="sxs-lookup"><span data-stu-id="5d703-132">Getting ready to install</span></span>

-   <span data-ttu-id="5d703-133">Windows Management Framework 3.0을 설치하기 전에 Windows Management Framework 3.0의 이전 버전을 모두 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-133">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="5d703-134">Windows PowerShell 3.0을 설치하려면</span><span class="sxs-lookup"><span data-stu-id="5d703-134">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="5d703-135">Cmd.exe 시작</span><span class="sxs-lookup"><span data-stu-id="5d703-135">Start Cmd.exe</span></span>

2.  <span data-ttu-id="5d703-136">다음 DISM 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-136">Run the following DISM commands.</span></span> <span data-ttu-id="5d703-137">이 명령은 .NET Framework 2.0 및 Windows PowerShell 2.0을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-137">These commands install .NET Framework 2.0 and Windows PowerShell 2.0.</span></span>

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  <span data-ttu-id="5d703-138">Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450))에서 Server Core용 Microsoft .NET Framework 4.0 전체 설치를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-138">Install Microsoft .NET Framework 4.0 full installation for Server Core from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).</span></span>

4.  <span data-ttu-id="5d703-139">Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290))에서 Windows Management Framework 3.0을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-139">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <span data-ttu-id="5d703-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Windows Server 2008에 Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="5d703-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installing Windows PowerShell on Windows Server 2008</span></span>
<span data-ttu-id="5d703-141">이 지침에서는 Windows Server 2008 서비스 팩 2를 실행하는 컴퓨터에 Windows PowerShell 3.0을 설치하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-141">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows Server 2008 with Service Pack 2.</span></span>

<span data-ttu-id="5d703-142">Windows Server 2008 시스템에서 Windows Management Framework(Windows PowerShell 2.0, KB 968930)는 Windows Management Framework 3.0의 필수 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-142">On Windows Server 2008 systems, Windows Management Framework (Windows PowerShell 2.0, KB 968930) is a prerequisite for Windows Management Framework 3.0.</span></span> <span data-ttu-id="5d703-143">"인증에 대해 확장된 보호" 기능은 인증 전달 공격으로부터 컴퓨터를 보호하며, 원격 세션을 만들 때 **UseSSL** 매개 변수를 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-143">The "Extended Protection for Authentication" feature protects the computer from authentication forwarding attacks and allows you to use the **UseSSL** parameter when creating remote sessions.</span></span> <span data-ttu-id="5d703-144">Windows PowerShell 3.0 및 the Windows PowerShell 2.0 엔진을 설치하려면 다음 절차를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="5d703-144">To install Windows PowerShell 3.0 and the Windows PowerShell 2.0 Engine, use the following procedure.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="5d703-145">설치 준비</span><span class="sxs-lookup"><span data-stu-id="5d703-145">Getting ready to install</span></span>

-   <span data-ttu-id="5d703-146">Windows Management Framework 3.0을 설치하기 전에 Windows Management Framework 3.0의 이전 버전을 모두 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-146">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="5d703-147">Windows PowerShell 3.0을 설치하려면</span><span class="sxs-lookup"><span data-stu-id="5d703-147">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="5d703-148">Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910))에서 Microsoft .NET Framework 3.5 서비스 팩 1을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-148">Install Microsoft .NET Framework 3.5 with Service Pack 1 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).</span></span>

2.  <span data-ttu-id="5d703-149">Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035))에서 Windows Management Framework(Windows PowerShell 2.0, KB 968930)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-149">Install Windows Management Framework (Windows PowerShell 2.0, KB 968930) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).</span></span>

3.  <span data-ttu-id="5d703-150">Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547))에서 Microsoft .NET Framework 4(dotNetFx40_Full_setup.exe) 전체 설치를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-150">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="5d703-151">또는 Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919))에서 Microsoft .NET Framework 4.5(dotNetFx45_Full_setup.exe)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-151">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

4.  <span data-ttu-id="5d703-152">[http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398)에서 "인증에 대해 확장된 보호"(KB 968389)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-152">Install "Extended Protection for Authentication" (KB 968389) from [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).</span></span>

5.  <span data-ttu-id="5d703-153">Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290))에서 Windows Management Framework 3.0을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d703-153">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d703-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d703-154">See Also</span></span>
- [<span data-ttu-id="5d703-155">Windows PowerShell 시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="5d703-155">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="5d703-156">Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="5d703-156">Starting Windows PowerShell</span></span>](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

