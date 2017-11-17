---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell SDK 설치"
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: c6acba828e469e716c80603ec2432176652a7280
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2017
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="db0de-103">Windows PowerShell SDK 설치</span><span class="sxs-lookup"><span data-stu-id="db0de-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="db0de-104">다음 항목에서는 여러 버전의 Windows에 PowerShell SDK를 설치하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="db0de-105">Windows 8 및 Windows Server 2012용 Windows PowerShell 3.0 SDK 설치</span><span class="sxs-lookup"><span data-stu-id="db0de-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="db0de-106">Windows PowerShell 3.0은 Windows 8 및 Windows Server 2012와 함께 자동으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="db0de-107">또한 Windows 8 SDK의 일부로써 Windows PowerShell 3.0의 참조 어셈블리를 다운로드하고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="db0de-108">이러한 어셈블리를 사용하여 Windows PowerShell 3.0에 대한 cmdlet, 공급자 및 호스트 프로그램을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="db0de-109">Windows 8용 Windows SDK를 설치하면 Windows PowerShell 어셈블리가 참조 어셈블리 폴더(\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0)에 자동으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="db0de-110">자세한 내용은 [Windows 8 SDK 다운로드 사이트](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db0de-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="db0de-111">Windows PowerShell 코드 샘플은 개발자 센터에서도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="db0de-112">자세한 내용은 [개발자 센터 사이트](http://code.msdn.microsoft.com/windowsdesktop/)에서 데스크톱 코드 샘플 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db0de-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="db0de-113">또한 Windows PowerShell 3.0은 다수의 코드 샘플이 포함된 이전 버전인 Windows PowerShell 2.0 SDK와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="db0de-114">Windows PowerShell 2.0 SDK를 다운로드하는 방법에 대한 자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db0de-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="db0de-115">(2.0 코드 샘플은 Windows 8 및 Windows PowerShell 3.0과 호환되지만 Windows 8 플랫폼에 Windows PowerShell 2.0을 설치할 수 없습니다.)</span><span class="sxs-lookup"><span data-stu-id="db0de-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="db0de-116">Windows 7 및 Windows Server 2008 R2용 Windows PowerShell 3.0 SDK 설치</span><span class="sxs-lookup"><span data-stu-id="db0de-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="db0de-117">Windows 7 및 Windows Server 2008 R2는 PowerShell 2.0을 자동으로 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="db0de-118">또한 이러한 시스템에 PowerShell 3.0을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="db0de-119">자세한 내용은 [Windows PowerShell 설치](Installing-Windows-PowerShell.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db0de-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="db0de-120">위에서 설명한 대로, Windows 7 및 Windows Server 2008 R2에서도 Windows 8 SDK를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="db0de-121">Windows 7, Vista, XP, Server 2003 및 Server 2008용 Windows PowerShell 2.0 SDK 설치</span><span class="sxs-lookup"><span data-stu-id="db0de-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="db0de-122">Windows PowerShell 2.0 SDK는 cmdlet, 공급자 및 호스팅 응용 프로그램을 작성하는 데 필요한 참조 어셈블리를 제공하고 코드 작성을 시작할 때 시작 지점으로 사용할 수 있는 C# 샘플 코드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="db0de-123">이 SDK를 설치하려면 [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db0de-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="db0de-124">참조 어셈블리</span><span class="sxs-lookup"><span data-stu-id="db0de-124">Reference assemblies</span></span>

<span data-ttu-id="db0de-125">참조 어셈블리는 기본적으로 다음 위치에 설치됩니다. `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`</span><span class="sxs-lookup"><span data-stu-id="db0de-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="db0de-126">**참고**: Windows PowerShell 2.0 어셈블리에 대해 컴파일된 코드는 Windows PowerShell 1.0 설치에 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="db0de-127">그러나 Windows PowerShell 1.0 어셈블리에 대해 컴파일되는 코드는 Windows PowerShell 2.0 설치에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="db0de-128">샘플</span><span class="sxs-lookup"><span data-stu-id="db0de-128">Samples</span></span>

<span data-ttu-id="db0de-129">코드 샘플은 기본적으로 다음 위치에 설치됩니다. `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`</span><span class="sxs-lookup"><span data-stu-id="db0de-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="db0de-130">다음 섹션에서는 각 샘플의 용도에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="db0de-131">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="db0de-131">Cmdlet samples</span></span>
<span data-ttu-id="db0de-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="db0de-132">**GetProcessSample01**</span></span>

<span data-ttu-id="db0de-133">로컬 컴퓨터에 있는 모든 프로세스를 가져오는 간단한 cmdlet을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="db0de-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="db0de-134">**GetProcessSample02**</span></span>

<span data-ttu-id="db0de-135">cmdlet에 매개 변수를 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="db0de-136">cmdlet은 하나 이상의 프로세스 이름을 사용하고 일치하는 프로세스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="db0de-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="db0de-137">**GetProcessSample03**</span></span>

<span data-ttu-id="db0de-138">파이프라인의 입력을 허용하는 매개 변수를 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="db0de-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="db0de-139">**GetProcessSample04**</span></span>

<span data-ttu-id="db0de-140">종료되지 않는 오류를 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="db0de-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="db0de-141">**GetProcessSample05**</span></span>

<span data-ttu-id="db0de-142">지정한 프로세스 목록을 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="db0de-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="db0de-143">**SelectObject**</span></span>

<span data-ttu-id="db0de-144">특정 개체만 선택하는 필터를 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="db0de-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="db0de-145">**SelectString**</span></span>

<span data-ttu-id="db0de-146">파일에서 지정한 패턴을 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="db0de-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="db0de-147">**StopProcessSample01**</span></span>

<span data-ttu-id="db0de-148">*PassThru* 매개 변수를 구현하는 방법과 [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) 및 [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) 메서드를 호출하여 사용자 피드백을 요청하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="db0de-149">사용자는 cmdlet에서 강제로 개체를 반환하려는 경우 *PassThru* 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="db0de-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="db0de-150">**StopProcessSample02**</span></span>

<span data-ttu-id="db0de-151">특정 프로세스를 중지하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="db0de-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="db0de-152">**StopProcessSample03**</span></span>

<span data-ttu-id="db0de-153">매개 변수의 별칭을 선언하는 방법과 와일드카드를 지원하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="db0de-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="db0de-154">**StopProcessSample04**</span></span>

<span data-ttu-id="db0de-155">매개 변수 집합을 선언하는 방법 및 cmdlet이 입력으로 사용하는 개체를 선언하는 방법, 그리고 사용할 기본 매개 변수 집합을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="db0de-156">원격 샘플</span><span class="sxs-lookup"><span data-stu-id="db0de-156">Remoting samples</span></span>

<span data-ttu-id="db0de-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="db0de-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="db0de-158">원격 연결을 설정하는 데 사용되는 원격 runspace를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="db0de-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="db0de-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="db0de-160">원격 runspace 풀을 생성하는 방법과 이 풀을 사용하여 여러 명령을 동시에 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="db0de-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="db0de-161">**Serialization01**</span></span>

<span data-ttu-id="db0de-162">기존 .NET 클래스를 살펴보고 이 클래스의 선택한 공용 속성 정보가 직렬화/역직렬화에서 유지되는지 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="db0de-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="db0de-163">**Serialization02**</span></span>

<span data-ttu-id="db0de-164">기존 .NET 클래스를 살펴보고 이 클래스 인스턴스의 정보가 클래스의 공용 속성에 제공되지 않는 경우, 해당 정보가 직렬화/역직렬화에서 유지되는지 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="db0de-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="db0de-165">**Serialization03**</span></span>

<span data-ttu-id="db0de-166">기존 .NET 클래스를 살펴보고 이 클래스 및 파생 클래스의 인스턴스가 라이브 .NET 개체로 역직렬화(리하이드레이션)되는지 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="db0de-167">이벤트 샘플</span><span class="sxs-lookup"><span data-stu-id="db0de-167">Event samples</span></span>

<span data-ttu-id="db0de-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="db0de-168">**Event01**</span></span>

<span data-ttu-id="db0de-169">ObjectEventRegistrationBase에서 파생하여 이벤트 등록용 cmdlet을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="db0de-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="db0de-170">**Event02**</span></span>

<span data-ttu-id="db0de-171">원격 컴퓨터에서 생성된 Windows PowerShell 이벤트 알림을 수신하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="db0de-172">[Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) 클래스를 통해 노출되는 PSEventReceived 이벤트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="db0de-173">호스팅 응용 프로그램 샘플</span><span class="sxs-lookup"><span data-stu-id="db0de-173">Hosting application samples</span></span>

<span data-ttu-id="db0de-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="db0de-174">**Runspace01**</span></span>

<span data-ttu-id="db0de-175">[PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 클래스를 사용하여 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet을 동기적으로 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="db0de-176">[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet은 로컬 컴퓨터에서 실행 중인 각 프로세스에 대해 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="db0de-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="db0de-177">**Runspace02**</span></span>

<span data-ttu-id="db0de-178">[PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 클래스를 사용하여 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) 및 [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlet을 동기적으로 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="db0de-179">[Get-process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet은 로컬 컴퓨터에서 실행 중인 각 프로세스에 대해 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 개체를 반환하고, Sort-Object는 해당 [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) 속성을 기준으로 개체를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="db0de-180">이러한 명령의 결과는 [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) 컨트롤을 사용하여 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="db0de-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="db0de-181">**Runspace03**</span></span>

<span data-ttu-id="db0de-182">[PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 클래스를 사용하여 동기적으로 스크립트를 실행하는 방법과 종료되지 않는 오류를 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="db0de-183">스크립트는 프로세스 이름 목록을 받은 다음 해당 프로세스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="db0de-184">스크립트를 실행할 때 생성된 종료되지 않는 오류를 포함하여 스크립트의 결과가 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="db0de-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="db0de-185">**Runspace04**</span></span>

<span data-ttu-id="db0de-186">[PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 클래스를 사용하여 명령을 실행하는 방법과 명령을 실행할 때 발생한 종료 오류를 잡는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="db0de-187">두 개의 명령이 실행되는데, 마지막 명령은 유효하지 않은 매개 변수 인수를 전달받습니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="db0de-188">따라서 개체가 반환되지 않고 종료 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="db0de-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="db0de-189">**Runspace05**</span></span>

<span data-ttu-id="db0de-190">runspace를 열 때 스냅인의 cmdlet을 사용할 수 있도록 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 개체에 스냅인을 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="db0de-191">이 스냅인은 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 개체를 사용하여 동기적으로 실행되는 Get-Proc cmdlet([GetProcessSample01 샘플](https://technet.microsoft.com/library/ff602028.aspx)에서 정의)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="db0de-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="db0de-192">**Runspace06**</span></span>

<span data-ttu-id="db0de-193">runspace를 열 때 모듈이 로드되도록 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 개체에 모듈을 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="db0de-194">이 모듈은 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 개체를 사용하여 동기적으로 실행되는 Get-Proc cmdlet([GetProcessSample02 샘플](https://technet.microsoft.com/library/ff602027.aspx)에서 정의)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="db0de-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="db0de-195">**Runspace07**</span></span>

<span data-ttu-id="db0de-196">runspace를 만들고 해당 runspace를 사용하여 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 개체를 통해 두 개의 cmdlet을 동기적으로 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="db0de-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="db0de-197">**Runspace08**</span></span>

<span data-ttu-id="db0de-198">[PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 개체의 파이프라인에 명령 및 인수를 추가하는 방법과 동기적으로 명령을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="db0de-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="db0de-199">**Runspace09**</span></span>

<span data-ttu-id="db0de-200">[PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 개체의 파이프라인에 스크립트를 추가하는 방법과 비동기적으로 스크립트를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="db0de-201">이벤트는 스크립트의 출력을 처리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="db0de-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="db0de-202">**Runspace10**</span></span>

<span data-ttu-id="db0de-203">기본 초기 세션 상태를 만드는 방법, [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx)에 cmdlet을 추가하는 방법, 초기 세션 상태를 사용하는 runspace를 만드는 방법 및 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 개체를 사용하여 명령을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="db0de-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="db0de-204">**Runspace11**</span></span>

<span data-ttu-id="db0de-205">[ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) 클래스를 사용하여 기존 cmdlet을 호출하지만 사용 가능한 매개 변수 집합을 제한하는 프록시 명령을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="db0de-206">프록시 명령은 제한된 runspace를 만드는 데 사용되는 초기 세션 상태에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="db0de-207">따라서 사용자가 프록시 명령을 통해서만 cmdlet의 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="db0de-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="db0de-208">**PowerShell01**</span></span>

<span data-ttu-id="db0de-209">[InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 개체를 사용하여 제한된 runspace를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="db0de-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="db0de-210">**PowerShell02**</span></span>

<span data-ttu-id="db0de-211">runspace 풀을 사용하여 여러 명령을 동시에 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="db0de-212">호스트 샘플</span><span class="sxs-lookup"><span data-stu-id="db0de-212">Host samples</span></span>

<span data-ttu-id="db0de-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="db0de-213">**Host01**</span></span>

<span data-ttu-id="db0de-214">사용자 지정 호스트를 사용하는 호스트 응용 프로그램을 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="db0de-215">이 샘플에서는 사용자 지정 호스트를 사용하는 runspace를 만든 다음 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API를 사용하여 "종료"를 호출하는 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="db0de-216">호스트 응용 프로그램은 스크립트의 출력을 살펴보고 결과를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="db0de-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="db0de-217">**Host02**</span></span>

<span data-ttu-id="db0de-218">사용자 지정 호스트 구현과 함께 Windows PowerShell 런타임을 사용하는 호스트 응용 프로그램을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="db0de-219">호스트 응용 프로그램은 호스트 문화권을 독일어로 설정하고, [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet을 실행한 다음 pwrsh.exe를 사용하여 보이는 대로 결과를 표시하고 현재 날짜와 시간을 독일어로 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="db0de-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="db0de-220">**Host03**</span></span>

<span data-ttu-id="db0de-221">명령줄에서 명령을 읽고 명령을 실행한 후 콘솔에 결과를 표시하는 대화형 콘솔 기반 호스트 응용 프로그램을 구축하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="db0de-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="db0de-222">**Host04**</span></span>

<span data-ttu-id="db0de-223">명령줄에서 명령을 읽고 명령을 실행한 후 콘솔에 결과를 표시하는 대화형 콘솔 기반 호스트 응용 프로그램을 구축하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="db0de-224">이 호스트 응용 프로그램은 사용자가 여러 선택 항목을 지정할 수 있는 프롬프트 표시도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="db0de-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="db0de-225">**Host05**</span></span>

<span data-ttu-id="db0de-226">명령줄에서 명령을 읽고 명령을 실행한 후 콘솔에 결과를 표시하는 대화형 콘솔 기반 호스트 응용 프로그램을 구축하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="db0de-227">이 호스트 응용 프로그램은 [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) 및 [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlet을 사용한 원격 컴퓨터 호출도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="db0de-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="db0de-228">**Host06**</span></span>

<span data-ttu-id="db0de-229">명령줄에서 명령을 읽고 명령을 실행한 후 콘솔에 결과를 표시하는 대화형 콘솔 기반 호스트 응용 프로그램을 구축하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="db0de-230">또한 이 샘플에서는 토크나이저 API를 사용하여 사용자가 입력하는 텍스트의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="db0de-231">공급자 샘플</span><span class="sxs-lookup"><span data-stu-id="db0de-231">Provider samples</span></span>

<span data-ttu-id="db0de-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="db0de-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="db0de-233">[CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) 클래스에서 직접 파생되는 공급자 클래스를 선언하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="db0de-234">여기서는 참조용으로만 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-234">It is included here only for completeness.</span></span>

<span data-ttu-id="db0de-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="db0de-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="db0de-236">New-PSDrive 및 Remove-PSDrive cmdlet 호출을 지원하기 위해 [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) 및 [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="db0de-237">이 샘플의 공급자 클래스는 [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) 클래스에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="db0de-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="db0de-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="db0de-239">Get-Item 및 Set-Item cmdlet 호출을 지원하기 위해 [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) 및 [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="db0de-240">이 샘플의 공급자 클래스는 [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) 클래스에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="db0de-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="db0de-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="db0de-242">Copy-Item, Get-ChildItem, New-Item 및 Remove-Item cmdlet 호출을 지원하기 위해 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="db0de-243">이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="db0de-244">컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="db0de-245">이 샘플의 공급자 클래스는 [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) 클래스에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="db0de-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="db0de-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="db0de-247">Move-Item 및 Join-Path cmdlet 호출을 지원하기 위해 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="db0de-248">이러한 메서드는 사용자가 컨테이너 내의 항목을 이동해야 하고 데이터 저장소에 중첩된 컨테이너가 포함되는 경우에 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="db0de-249">이 샘플의 공급자 클래스는 [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) 클래스에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="db0de-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="db0de-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="db0de-251">Clear-Content, Get-Content 및 Set-Content cmdlet 호출을 지원하기 위해 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="db0de-252">이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="db0de-253">이 샘플의 공급자 클래스는 [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) 클래스에서 파생되며, [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="db0de-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>

