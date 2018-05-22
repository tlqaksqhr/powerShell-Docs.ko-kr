---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 리소스 디버그
ms.openlocfilehash: 30d49768fc2301b5306d0001e157d60e2e991883
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="e89c6-103">DSC 리소스 디버그</span><span class="sxs-lookup"><span data-stu-id="e89c6-103">Debugging DSC resources</span></span>

> <span data-ttu-id="e89c6-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e89c6-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e89c6-105">PowerShell 5.0에서는 구성이 적용됨에 따라 DSC 리소스를 디버그할 수 있도록 해주는 새로운 기능이 DSC(필요한 상태 구성)에 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="e89c6-106">DSC 디버그 사용</span><span class="sxs-lookup"><span data-stu-id="e89c6-106">Enabling DSC debugging</span></span>
<span data-ttu-id="e89c6-107">리소스를 디버그할 수 있으려면 먼저, [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet을 호출하여 디버그할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span></span>
<span data-ttu-id="e89c6-108">이 cmdlet은 필수 매개 변수인 **BreakAll**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="e89c6-109">[Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx)를 호출한 결과를 보면 디버그할 수 있도록 되어 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span></span>

<span data-ttu-id="e89c6-110">다음의 PowerShell 출력은 디버그 사용의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="e89c6-111">디버그를 사용하도록 설정된 구성 시작</span><span class="sxs-lookup"><span data-stu-id="e89c6-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="e89c6-112">DSC 리소스를 디버그하려면 해당 리소스를 호출하는 구성을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="e89c6-113">예를 들어 [WindowsFeature](windowsfeatureResource.md)를 호출하여 "WindowsPowerShellWebAccess" 기능이 설치되어 있는지 확인하는 간단한 구성을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="e89c6-114">구성을 컴파일한 후에는 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx)을 호출하여 구성을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span></span>
<span data-ttu-id="e89c6-115">이 구성은 LCM(로컬 구성 관리자)이 구성의 첫 번째 리소스를 호출하면 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="e89c6-116">`-Verbose` 및 `-Wait` 매개 변수를 사용하는 경우, 출력에 디버그를 시작하려면 입력해야 하는 줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="e89c6-117">이 시점에서 LCM은 리소스를 호출하고 첫 번째 중단점으로 이동했습니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="e89c6-118">출력의 마지막 세 줄에는 프로세스에 연결하여 리소스 스크립트의 디버그를 시작하는 방법이 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="e89c6-119">리소스 스크립트 디버그</span><span class="sxs-lookup"><span data-stu-id="e89c6-119">Debugging the resource script</span></span>

<span data-ttu-id="e89c6-120">PowerShell ISE의 새 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="e89c6-121">콘솔 창에서 `Start-DscConfiguration` 출력으로부터 나온 결과의 마지막 세 줄을 명령으로 입력하여 `<credentials>`를 올바른 사용자 자격 증명으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="e89c6-122">이제 다음과 유사한 프롬프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="e89c6-123">리소스 스크립트가 스크립트 창에 열리고 디버거가 **Test-TargetResource** 함수(클래스 기반 리소스의 **Test()** 메서드)의 첫째 줄에서 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="e89c6-124">이제 ISE에서 디버그 명령을 사용하여 리소스 스크립트 단계별 실행, 변수 값 확인, 호출 스택 보기 등을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span>
<span data-ttu-id="e89c6-125">PowerShell ISE에서 디버그하는 방법에 대한 자세한 내용은 [How to Debug Scripts in Windows PowerShell ISE(Windows PowerShell ISE에서 스크립트를 디버그하는 방법)](https://technet.microsoft.com/en-us/library/dd819480.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e89c6-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span>
<span data-ttu-id="e89c6-126">리소스 스크립트 (또는 클래스)의 모든 줄은 중단점으로 설정된다는 점을 기억하세요.</span><span class="sxs-lookup"><span data-stu-id="e89c6-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="e89c6-127">DSC 디버그 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="e89c6-127">Disabling DSC debugging</span></span>

<span data-ttu-id="e89c6-128">[Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx)를 호출한 후 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx)을 호출하면 항상 구성으로 인해 디버거가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-128">After calling [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="e89c6-129">구성이 정상적으로 실행되도록 하려면 [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet을 호출하여 디버깅을 사용하지 않도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="e89c6-130">**참고:** 재부팅해도 LCM의 디버그 상태가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="e89c6-131">디버깅을 사용하도록 설정하는 경우 재부팅 후 구성을 시작하면 여전히 디버거가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="e89c6-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="e89c6-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e89c6-132">See Also</span></span>
- [<span data-ttu-id="e89c6-133">Writing a custom DSC resource with MOF(MOF를 사용하여 사용자 지정 DSC 리소스 작성)</span><span class="sxs-lookup"><span data-stu-id="e89c6-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="e89c6-134">PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성</span><span class="sxs-lookup"><span data-stu-id="e89c6-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)