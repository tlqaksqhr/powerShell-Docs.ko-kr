---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC on Nano Server 사용"
ms.openlocfilehash: 2233106bfd07144132f95ea7957ebfa3248ca219
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="1f7fc-103">DSC on Nano Server 사용</span><span class="sxs-lookup"><span data-stu-id="1f7fc-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="1f7fc-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1f7fc-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1f7fc-105">**DSC on Nano Server**는 Windows Server 2016 미디어의 `NanoServer\Packages` 폴더에 있는 선택적 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="1f7fc-106">이 패키지는 **Microsoft-NanoServer-DSC-Package**를 **New-NanoServerImage** 함수의 **Packages** 매개 변수 값으로 지정하여 Nano Server에 대한 VHD를 만들 때 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="1f7fc-107">예를 들어 가상 컴퓨터에 대한 VHD를 만드는 경우 다음과 같은 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="1f7fc-108">Nano Server 설치 및 사용과 PowerShell 원격으로 Nano Server를 관리하는 방법은 [Getting Started with Nano Server(Nano Server 시작)](https://technet.microsoft.com/en-us/library/mt126167.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="1f7fc-109">Nano Server에서 사용할 수 있는 DSC 기능</span><span class="sxs-lookup"><span data-stu-id="1f7fc-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="1f7fc-110">Nano Server는 처음 사용자용 Windows Server에 비해 제한된 일부 API만 지원하기 때문에 당분간은 전체 SKU에서 동작하는 완전한 기능을 하는 패리티가 DSC on Nano Server에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="1f7fc-111">DSC on Nano Server는 개발 중이므로 아직 모든 기능이 완성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>
 
 <span data-ttu-id="1f7fc-112">다음 DSC 기능은 현재 Nano Server에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-112">The following DSC features are currently available on Nano Server:</span></span> 


* <span data-ttu-id="1f7fc-113">밀어넣기 및 끌어오기 모드</span><span class="sxs-lookup"><span data-stu-id="1f7fc-113">Both push and pull modes</span></span>

* <span data-ttu-id="1f7fc-114">다음을 포함하여 Windows Server 전체 버전에 있는 모든 DSC cmdlet:</span><span class="sxs-lookup"><span data-stu-id="1f7fc-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span> 
  * [<span data-ttu-id="1f7fc-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1f7fc-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [<span data-ttu-id="1f7fc-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1f7fc-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [<span data-ttu-id="1f7fc-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="1f7fc-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="1f7fc-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="1f7fc-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [<span data-ttu-id="1f7fc-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f7fc-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="1f7fc-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f7fc-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="1f7fc-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f7fc-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="1f7fc-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f7fc-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [<span data-ttu-id="1f7fc-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="1f7fc-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [<span data-ttu-id="1f7fc-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f7fc-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="1f7fc-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f7fc-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="1f7fc-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="1f7fc-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="1f7fc-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="1f7fc-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="1f7fc-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="1f7fc-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="1f7fc-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="1f7fc-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="1f7fc-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="1f7fc-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="1f7fc-131">New-DSCCheckSum</span><span class="sxs-lookup"><span data-stu-id="1f7fc-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* <span data-ttu-id="1f7fc-132">구성 컴파일([DSC 구성](configurations.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="1f7fc-133">**문제:** 구성 컴파일 중 암호 암호화([MOF 파일 보안](securemof.md) 참조)가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="1f7fc-134">메타 구성 컴파일([로컬 구성 관리자 구성](metaConfig.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="1f7fc-135">사용자 컨텍스트에서 리소스 실행([사용자 자격 증명을 사용하여 DSC 실행(RunAs)](runAsUser.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="1f7fc-136">클래스 기반 리소스([PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성](authoringResourceClass.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="1f7fc-137">DSC 리소스 디버깅([DSC 리소스 디버그](debugresource.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>
  
  <span data-ttu-id="1f7fc-138">**문제:** 리소스가 PsDscRunAsCredential을 사용 중인 경우 작동하지 않습니다([사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="1f7fc-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="1f7fc-139">노드 간 종속성 지정</span><span class="sxs-lookup"><span data-stu-id="1f7fc-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md) 

* [<span data-ttu-id="1f7fc-140">리소스 버전 관리</span><span class="sxs-lookup"><span data-stu-id="1f7fc-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="1f7fc-141">끌어오기 클라이언트(구성 및 리소스)([구성 이름을 사용하여 끌어오기 클라이언트 설정](pullClientConfigNames.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="1f7fc-142">부분 구성(끌어오기 및 밀어넣기)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="1f7fc-143">끌어오기 서버에 보고</span><span class="sxs-lookup"><span data-stu-id="1f7fc-143">Reporting to pull server</span></span>](reportServer.md) 

* <span data-ttu-id="1f7fc-144">MOF 암호화</span><span class="sxs-lookup"><span data-stu-id="1f7fc-144">MOF encryption</span></span>

* <span data-ttu-id="1f7fc-145">이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="1f7fc-145">Event logging</span></span>

* <span data-ttu-id="1f7fc-146">Azure 자동화 DSC 보고</span><span class="sxs-lookup"><span data-stu-id="1f7fc-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="1f7fc-147">올바르게 작동하는 리소스</span><span class="sxs-lookup"><span data-stu-id="1f7fc-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="1f7fc-148">Archive</span><span class="sxs-lookup"><span data-stu-id="1f7fc-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="1f7fc-149">Environment</span><span class="sxs-lookup"><span data-stu-id="1f7fc-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="1f7fc-150">File</span><span class="sxs-lookup"><span data-stu-id="1f7fc-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="1f7fc-151">Log</span><span class="sxs-lookup"><span data-stu-id="1f7fc-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="1f7fc-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="1f7fc-152">ProcessSet</span></span>
  * [<span data-ttu-id="1f7fc-153">Registry</span><span class="sxs-lookup"><span data-stu-id="1f7fc-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="1f7fc-154">Script</span><span class="sxs-lookup"><span data-stu-id="1f7fc-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="1f7fc-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="1f7fc-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="1f7fc-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="1f7fc-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="1f7fc-157">WaitForAll([노드 간 종속성 지정](crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="1f7fc-158">WaitForAny([노드 간 종속성 지정](crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="1f7fc-159">WaitForSome([노드 간 종속성 지정](crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="1f7fc-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="1f7fc-160">부분적으로 작동하는 리소스</span><span class="sxs-lookup"><span data-stu-id="1f7fc-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="1f7fc-161">그룹</span><span class="sxs-lookup"><span data-stu-id="1f7fc-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="1f7fc-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="1f7fc-162">GroupSet</span></span>
  
  <span data-ttu-id="1f7fc-163">**문제:** 특정 인스턴스를 두 번 호출하는 경우(동일한 구성을 두 번 실행) 위 리소스가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>
  
  * [<span data-ttu-id="1f7fc-164">Service</span><span class="sxs-lookup"><span data-stu-id="1f7fc-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="1f7fc-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="1f7fc-165">ServiceSet</span></span>
  
  <span data-ttu-id="1f7fc-166">**문제:** 서비스 시작/중지(상태)에 대해서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="1f7fc-167">시작 유형, 자격 증명, 설명 등과 같은 다른 서비스 특성을 변경하려고 하면 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="1f7fc-168">발생하는 오류는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-168">The error thrown is similar to:</span></span>
  
  <span data-ttu-id="1f7fc-169">*유형[management.managementobject]을 찾을 수 없습니다. 이 유형이 포함된 어셈블리가 로드되어 있는지 검증하세요.*</span><span class="sxs-lookup"><span data-stu-id="1f7fc-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>
  
* <span data-ttu-id="1f7fc-170">작동하지 않는 리소스</span><span class="sxs-lookup"><span data-stu-id="1f7fc-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="1f7fc-171">User</span><span class="sxs-lookup"><span data-stu-id="1f7fc-171">User</span></span>](userResource.md)
  

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="1f7fc-172">Nano Server에서 사용할 수 없는 DSC 기능</span><span class="sxs-lookup"><span data-stu-id="1f7fc-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="1f7fc-173">다음 DSC 기능은 현재 Nano Server에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="1f7fc-174">암호화된 암호를 사용한 MOF 문서 암호 해독</span><span class="sxs-lookup"><span data-stu-id="1f7fc-174">Decrypting MOF document with encrypted password(s)</span></span> 
* <span data-ttu-id="1f7fc-175">끌어오기 서버--현재는 Nano Server에서 끌어오기 서버를 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="1f7fc-176">동작 기능 목록에 없는 모든 기능</span><span class="sxs-lookup"><span data-stu-id="1f7fc-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="1f7fc-177">Nano Server에서 사용자 지정 DSC 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="1f7fc-177">Using custom DSC resources on Nano Server</span></span>
 
<span data-ttu-id="1f7fc-178">Nano Server에서 사용할 수 있는 Windows API 집합과 CLR 라이브러리가 한정되어 있기 때문에 Windows 전체 CLR 버전에서 동작하는 DSC 리소스가 Nano Server에서 동작하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span> <span data-ttu-id="1f7fc-179">DSC 사용자 지정 리소스를 프로덕션 환경에 배포하기 전에 종단 간 테스트를 완료하세요.</span><span class="sxs-lookup"><span data-stu-id="1f7fc-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f7fc-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f7fc-180">See Also</span></span>
- [<span data-ttu-id="1f7fc-181">Nano Server 시작</span><span class="sxs-lookup"><span data-stu-id="1f7fc-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/en-us/library/mt126167.aspx)

