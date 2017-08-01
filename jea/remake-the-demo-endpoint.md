---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "데모 끝점 다시 만들기"
ms.technology: powershell
ms.openlocfilehash: 4a56272b6f995500d443d441f5e03db85dac6f96
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="remake-the-demo-endpoint"></a><span data-ttu-id="c233d-103">데모 끝점 다시 만들기</span><span class="sxs-lookup"><span data-stu-id="c233d-103">Remake the Demo Endpoint</span></span>
<span data-ttu-id="c233d-104">이 섹션에서는 위의 섹션에서 사용한 데모 끝점의 정확한 복제본을 생성하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-104">In this section, you will learn how to generate an exact replica of the demo endpoint you used in the above section.</span></span>
<span data-ttu-id="c233d-105">여기에서는 PowerShell 세션 구성 및 역할 기능을 비롯하여 JEA를 이해하는 데 필요한 핵심 개념을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-105">This will introduce core concepts that are necessary to understand JEA, including PowerShell Session Configurations and Role Capabilities.</span></span>

## <a name="powershell-session-configurations"></a><span data-ttu-id="c233d-106">PowerShell 세션 구성</span><span class="sxs-lookup"><span data-stu-id="c233d-106">PowerShell Session Configurations</span></span>
<span data-ttu-id="c233d-107">위의 섹션에서 JEA를 사용할 때 다음 명령을 실행하여 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-107">When you used JEA in the above section, you started by running the following command:</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

<span data-ttu-id="c233d-108">대부분의 매개 변수가 쉽게 이해되지만 *ConfigurationName* 매개 변수는 처음에 혼동을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-108">While most of the parameters are self-explanatory, the *ConfigurationName* parameter may seem confusing at first.</span></span>
<span data-ttu-id="c233d-109">이 매개 변수는 연결되어 있는 PowerShell 세션 구성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-109">That parameter specified the PowerShell Session Configuration to which you were connecting.</span></span>

<span data-ttu-id="c233d-110">*PowerShell 세션 구성*은 PowerShell 끝점을 멋지게 표현한 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-110">*PowerShell Session Configuration* is a fancy term for a PowerShell endpoint.</span></span>
<span data-ttu-id="c233d-111">이 용어는 사용자가 연결하고 PowerShell 기능에 액세스하는 "장소"를 비유적으로 나타낸 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-111">It is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="c233d-112">세션 구성을 설정하는 방법에 따라 세션 구성은 연결하는 사용자에게 서로 다른 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-112">Based on how you set up a Session Configuration, it can provide different functionality to connecting users.</span></span>
<span data-ttu-id="c233d-113">JEA의 경우 PowerShell을 제한된 기능 집합으로 제한하고 권한 있는 가상 계정으로 실행하는 데 세션 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-113">For JEA, we use Session Configurations to restrict PowerShell to a limited set of functionality and to run as a privileged virtual account.</span></span>

<span data-ttu-id="c233d-114">컴퓨터에서 각각 약간 다르게 설정된 PowerShell 세션 구성을 이미 여러 개 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-114">You already have several registered PowerShell Session Configurations on your machine, each set up slightly differently.</span></span>
<span data-ttu-id="c233d-115">대부분의 세션 구성은 Windows와 함께 제공되지만 "JEA_Demo" 세션 구성은 [필수 조건](prerequisites.md) 섹션에서 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-115">Most of them come with Windows, but the "JEA_Demo" Session Configuration was set up in the [prerequisites](prerequisites.md) section.</span></span>
<span data-ttu-id="c233d-116">관리자 PowerShell 프롬프트에서 다음 명령을 실행하여 등록된 모든 세션 구성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-116">You can see all registered Session Configurations by running the following command in an Administrator PowerShell prompt:</span></span>

```PowerShell
Get-PSSessionConfiguration
```

## <a name="powershell-session-configuration-files"></a><span data-ttu-id="c233d-117">PowerShell 세션 구성 파일</span><span class="sxs-lookup"><span data-stu-id="c233d-117">PowerShell Session Configuration Files</span></span>
<span data-ttu-id="c233d-118">새로운 *PowerShell 세션 구성 파일*을 등록하여 세션 구성을 새로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-118">You can make new Session Configurations by registering new *PowerShell Session Configuration Files*.</span></span>
<span data-ttu-id="c233d-119">세션 구성 파일의 확장명은 ".pssc"입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-119">Session Configuration Files have ".pssc" file extensions.</span></span>
<span data-ttu-id="c233d-120">New-PSSessionConfigurationFile cmdlet을 사용하여 세션 구성 파일을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-120">You can generate Session Configuration Files with the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="c233d-121">다음으로, JEA에 대한 새 세션 구성을 만들고 등록하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-121">Next, you are going to create and register a new Session Configuration for JEA.</span></span>

## <a name="generate-and-modify-your-powershell-session-configuration"></a><span data-ttu-id="c233d-122">PowerShell 세션 구성 생성 및 수정</span><span class="sxs-lookup"><span data-stu-id="c233d-122">Generate and Modify your PowerShell Session Configuration</span></span>
<span data-ttu-id="c233d-123">다음 명령을 실행하여 PowerShell 세션 구성 "기본" 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-123">Run the following command to generate a PowerShell Session Configuration "skeleton" file.</span></span>

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> <span data-ttu-id="c233d-124">**팁:** 가장 일반적인 구성 설정만 기본 파일에 기본적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-124">**TIP:** Only the most common configuration settings are included in the skeleton file by default.</span></span>
> <span data-ttu-id="c233d-125">생성된 PSSC에 적용 가능한 모든 설정을 포함하려면 `-Full` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-125">Use the `-Full` parameter to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="c233d-126">PowerShell ISE 또는 원하는 텍스트 편집기에서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-126">Open the file in PowerShell ISE, or your favorite text editor.</span></span>

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="c233d-127">파일의 다음 필드를 아래의 값으로 업데이트합니다(자신의 비관리자 보안 그룹에서 대체해야 함).</span><span class="sxs-lookup"><span data-stu-id="c233d-127">Update the following fields in the file with the values below (remember to substitute in your own non-administrator security group):</span></span>

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

<span data-ttu-id="c233d-128">해당하는 각 항목의 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-128">Here is what each of those entries mean:</span></span>

1.  <span data-ttu-id="c233d-129">*SessionType* 필드는 이 끝점과 함께 사용할 미리 설정된 기본 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-129">The *SessionType* field defines preset default settings to use with this endpoint.</span></span>
<span data-ttu-id="c233d-130">*RestrictedRemoteServer*는 원격 관리에 필요한 최소 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-130">*RestrictedRemoteServer* defines the minimal settings necessary for remote management.</span></span>
<span data-ttu-id="c233d-131">기본적으로 *RestrictedRemoteServer* 끝점은 Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host 및 Out-Default를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-131">By default, a *RestrictedRemoteServer* endpoint will expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default.</span></span>
<span data-ttu-id="c233d-132">이 끝점은 *ExecutionPolicy*를 *RemoteSigned*로 설정하고, *LanguageMode*를 *NoLanguage*로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-132">It will set the *ExecutionPolicy* to *RemoteSigned*, and the *LanguageMode* to *NoLanguage*.</span></span>
<span data-ttu-id="c233d-133">이러한 설정을 통해 끝점을 구성하기 위한 최소한의 안전한 시작점을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-133">The net effect of these settings is a secure and minimal starting point for configuring your endpoint.</span></span>

2.  <span data-ttu-id="c233d-134">*RoleDefinitions* 필드는 역할 기능을 특정 그룹에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-134">The *RoleDefinitions* field assigns Role Capabilities to specific groups.</span></span>
<span data-ttu-id="c233d-135">이 필드는 누가 권한 있는 계정으로 무엇을 수행할 수 있는지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-135">It defines who can do what as a privileged account.</span></span>
<span data-ttu-id="c233d-136">이 필드를 통해 그룹 구성원 자격에 따라 연결하는 사용자가 사용할 수 있는 기능을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-136">With this field, you can specify the functionality available to any connecting user based on group membership.</span></span>
<span data-ttu-id="c233d-137">이는 JEA의 RBAC 기능의 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-137">This is the core of JEA's RBAC functionality.</span></span>
<span data-ttu-id="c233d-138">이 예에서는 미리 만든 "유지 관리" RoleCapability를 "Contoso\JEA_NonAdmin_Operator" 그룹의 구성원에게 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-138">In this example, you are exposing the pre-made "Maintenance" RoleCapability to members of the "Contoso\JEA_NonAdmin_Operator" group.</span></span>

3.  <span data-ttu-id="c233d-139">*RunAsVirtualAccount* 필드는 PowerShell이 이 끝점에서 가상 계정"으로 실행"되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-139">The *RunAsVirtualAccount* field indicates that PowerShell should "run as" a Virtual Account at this endpoint.</span></span>
<span data-ttu-id="c233d-140">기본적으로 가상 계정은 기본 제공 Administrators 그룹의 구성원입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-140">By default, the Virtual Account is a member of the built in Administrators group.</span></span>
<span data-ttu-id="c233d-141">도메인 컨트롤러에서는 기본적으로 Domain Administrators 그룹의 구성원이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-141">On a domain controller, it is also a member of the Domain Administrators group by default.</span></span>
<span data-ttu-id="c233d-142">이 가이드의 뒷부분에서는 가상 계정의 권한을 사용자 지정하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-142">Later in this guide, you will learn how to customize the privileges of the Virtual Account.</span></span>

4.  <span data-ttu-id="c233d-143">*TranscriptDirectory* 필드는 "Over-the-Shoulder" PowerShell 기록이 각 원격 세션 후 저장되는 위치를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-143">The *TranscriptDirectory* field defines where "over-the-shoulder" PowerShell transcripts are saved after each remote session.</span></span>
<span data-ttu-id="c233d-144">이러한 기록을 통해 각 세션에서 수행된 작업을 읽으며 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-144">These transcripts allow you to inspect the actions taken in each session in a readable way.</span></span>
<span data-ttu-id="c233d-145">PowerShell 기록에 대한 자세한 내용은 이 [블로그 게시물](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c233d-145">For more information about PowerShell transcripts, check out this [blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>
<span data-ttu-id="c233d-146">참고: 일반 Windows Eventing에서도 각 사용자가 PowerShell로 실행한 작업에 대한 정보를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-146">Note: regular Windows Eventing also captures information about what each user ran with PowerShell.</span></span>
<span data-ttu-id="c233d-147">기록은 좀 더 읽기 쉬울 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-147">Transcripts are just a bit more readable.</span></span>

<span data-ttu-id="c233d-148">마지막으로, 변경 내용을 *JEADemo2.pssc*에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-148">Finally, save your changes to *JEADemo2.pssc*.</span></span>

## <a name="apply-the-powershell-session-configuration"></a><span data-ttu-id="c233d-149">PowerShell 세션 구성 적용</span><span class="sxs-lookup"><span data-stu-id="c233d-149">Apply the PowerShell Session Configuration</span></span>

<span data-ttu-id="c233d-150">세션 구성 파일에서 끝점을 만들려면 파일을 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-150">To create an endpoint from a Session Configuration file, you need to register the file.</span></span>
<span data-ttu-id="c233d-151">이렇게 하려면 다음과 같은 몇 가지 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-151">This requires a few pieces of information:</span></span>

1. <span data-ttu-id="c233d-152">세션 구성 파일의 경로.</span><span class="sxs-lookup"><span data-stu-id="c233d-152">The path to the Session Configuration file.</span></span>
2. <span data-ttu-id="c233d-153">등록된 세션 구성의 이름.</span><span class="sxs-lookup"><span data-stu-id="c233d-153">The name of your registered Session Configuration.</span></span> <span data-ttu-id="c233d-154">이 이름은 사용자가 `Enter-PSSession` 또는 `New-PSSession`을 사용하여 끝점에 연결할 때 "ConfigurationName" 매개 변수에 제공하는 이름과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-154">This is the same name users provide to the "ConfigurationName" parameter when they connect to your endpoint with `Enter-PSSession` or `New-PSSession`.</span></span>

<span data-ttu-id="c233d-155">로컬 컴퓨터에서 세션 구성을 등록하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-155">To register the Session Configuration on your local machine, run the following command:</span></span>

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="c233d-156">축하합니다!</span><span class="sxs-lookup"><span data-stu-id="c233d-156">Congratulations!</span></span> <span data-ttu-id="c233d-157">JEA 끝점을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-157">You have set up your JEA endpoint.</span></span>

## <a name="test-out-your-endpoint"></a><span data-ttu-id="c233d-158">끝점 테스트</span><span class="sxs-lookup"><span data-stu-id="c233d-158">Test Out Your Endpoint</span></span>
<span data-ttu-id="c233d-159">[JEA 사용](using-jea.md) 섹션에 나열된 단계를 새 끝점에 대해 다시 실행하여 의도한 대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-159">Re-run the steps listed in the [Using JEA](using-jea.md) section against your new endpoint to confirm it is operating as intended.</span></span>
<span data-ttu-id="c233d-160">`Enter-PSSession`에 구성 이름을 제공할 때 새 끝점의 이름(JEADemo2)을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-160">Be sure to use the new endpoint name (JEADemo2) when providing the configuration name to `Enter-PSSession`.</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## <a name="key-concepts"></a><span data-ttu-id="c233d-161">주요 개념</span><span class="sxs-lookup"><span data-stu-id="c233d-161">Key Concepts</span></span>
<span data-ttu-id="c233d-162">**PowerShell 세션 구성**: *PowerShell 끝점*이라고도 하며 사용자가 연결하고 PowerShell 기능에 액세스하는 "장소"를 비유적으로 나타낸 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-162">**PowerShell Session Configuration**: Sometimes referred to as *PowerShell Endpoint*, this is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="c233d-163">`Get-PSSessionConfiguration`을 실행하여 시스템에 등록된 세션 구성을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-163">You can list the registered Session Configurations on your system by running `Get-PSSessionConfiguration`.</span></span>
<span data-ttu-id="c233d-164">특정한 방식으로 구성된 PowerShell 세션 구성을 *JEA 끝점*이라고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-164">When configured in a specific way, a PowerShell Session Configuration can be called a *JEA Endpoint*.</span></span>

<span data-ttu-id="c233d-165">**PowerShell 세션 구성 파일(.pssc)**: 등록된 경우 PowerShell 세션 구성에 대한 설정을 정의하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-165">**PowerShell Session Configuration File (.pssc)**: A file that, when registered, defines settings for a PowerShell Session Configuration.</span></span>
<span data-ttu-id="c233d-166">이 파일에는 끝점에 연결할 수 있는 사용자 역할, "실행" 가상 계정 등에 대한 지정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-166">It contains specifications for user roles that can connect to the endpoint, the "run as" Virtual Account, and more.</span></span>     

<span data-ttu-id="c233d-167">**역할 정의**: 연결하는 사용자에게 부여된 역할 기능을 정의하는 세션 구성 파일의 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-167">**Role Definitions**: The field in a Session Configuration File that defines the Role Capabilities granted to connecting users.</span></span>
<span data-ttu-id="c233d-168">이 필드는 *누가* 권한 있는 계정으로 *무엇*을 수행할 수 있는지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-168">It defines *who* can do *what* as a privileged account.</span></span>
<span data-ttu-id="c233d-169">이는 JEA의 RBAC 기능의 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-169">This is the core of JEA's RBAC capabilities.</span></span>

<span data-ttu-id="c233d-170">**SessionType**: 세션 구성에 대한 기본 설정을 나타내는 세션 구성 파일의 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-170">**SessionType**: A field in a Session Configuration File that represents default settings for a Session Configuration.</span></span>
<span data-ttu-id="c233d-171">JEA 끝점의 경우 이 필드를 RestrictedRemoteServer로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-171">For JEA endpoints, this must be set to RestrictedRemoteServer.</span></span>

<span data-ttu-id="c233d-172">**PowerShell 기록**: PowerShell 세션의 "Over-the-Shoulder" 뷰가 포함된 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-172">**PowerShell Transcript**: A file containing an "over-the-shoulder" view of a PowerShell session.</span></span>
<span data-ttu-id="c233d-173">TranscriptDirectory 필드를 사용하여 JEA 세션에 대한 기록을 생성하도록 PowerShell을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c233d-173">You can set PowerShell to generate transcripts for JEA sessions using the TranscriptDirectory field.</span></span>
<span data-ttu-id="c233d-174">기록에 대한 자세한 내용은 이 [블로그 게시물](https://technet.microsoft.com/en-us/magazine/ff687007.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c233d-174">For more information on transcripts, check out this [blog post](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span></span>

