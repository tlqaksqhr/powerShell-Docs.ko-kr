---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC 스크립트 리소스"
ms.openlocfilehash: 81718de0b0c8463189e33e565dc9ff39692dbe8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-script-resource"></a><span data-ttu-id="341dd-103">DSC 스크립트 리소스</span><span class="sxs-lookup"><span data-stu-id="341dd-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="341dd-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="341dd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="341dd-105">Windows PowerShell DSC(필요한 상태 구성)의 **스크립트** 리소스에서는 대상 노드에서 Windows PowerShell 스크립트 블록을 실행하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="341dd-106">`Script` 리소스에 `GetScript`, `SetScript`, 및 `TestScript` 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="341dd-107">이러한 속성은 각 대상 노드에서 실행될 스크립트 블록에 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="341dd-108">`GetScript` 스크립트 블록은 현재 노드의 상태를 나타내는 해시 테이블을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="341dd-109">해시 테이블에는 `Result` 키 하나만 포함해야 하며 값은 `String` 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="341dd-110">아무것도 반환할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-110">It is not required to return anything.</span></span> <span data-ttu-id="341dd-111">DSC는 스크립트 블록의 출력을 사용해 아무런 작업도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="341dd-112">`TestScript` 스크립트 블록이 현재 노드를 수정해야 하는지 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="341dd-113">노드 최신 상태이면 `$true`를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="341dd-114">노드의 구성이 최신 상태가 아니면 `$false`를 반환하고 `SetScript` 스크립트 블록으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="341dd-115">`TestScript` 스크립트 블록이 DSC에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="341dd-116">`SetScript` 스크립트 블록에서 노드를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="341dd-117">`TestScript` 블록이 `$false`를 차단하는 경우 DSC에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="341dd-118">`GetScript`, `TestScript` 또는 `SetScript` 스크립트 블록에서 구성 스크립트의 변수를 사용해야 하는 경우 `$using:` 범위를 사용하세요(아래 예제 참조).</span><span class="sxs-lookup"><span data-stu-id="341dd-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="341dd-119">구문</span><span class="sxs-lookup"><span data-stu-id="341dd-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="341dd-120">속성</span><span class="sxs-lookup"><span data-stu-id="341dd-120">Properties</span></span>

|  <span data-ttu-id="341dd-121">속성</span><span class="sxs-lookup"><span data-stu-id="341dd-121">Property</span></span>  |  <span data-ttu-id="341dd-122">설명</span><span class="sxs-lookup"><span data-stu-id="341dd-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="341dd-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="341dd-123">GetScript</span></span>| <span data-ttu-id="341dd-124">[Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet을 호출할 때 실행되는 Windows PowerShell 스크립트 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="341dd-125">이 블록은 해시 테이블을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-125">This block must return a hashtable.</span></span> <span data-ttu-id="341dd-126">해시 테이블에는 **결과** 키 하나만 포함해야 하며 값은 **문자열**형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="341dd-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="341dd-127">SetScript</span></span>| <span data-ttu-id="341dd-128">Windows PowerShell 스크립트 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="341dd-129">[Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하면 **TestScript** 블록이 가장 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="341dd-130">**TestScript** 블록에서 **$false**를 반환한다면, **SetScript** 블록이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="341dd-131">**TestScript** 블록에서 **$true**를 반환한다면, **SetScript** 블록이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="341dd-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="341dd-132">TestScript</span></span>| <span data-ttu-id="341dd-133">Windows PowerShell 스크립트 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="341dd-134">[Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하면 이 블록이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="341dd-135">**$false**를 반환한다면, SetScript 블록이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="341dd-136">**$true**를 반환한다면, SetScript 블록이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="341dd-137">[Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet을 호출하면 **TestScript** 블록도 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="341dd-138">그러나 이 경우에서는 TestScript 블록이 어떤 값을 반환하는지 관계없이 **SetScript** 블록이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="341dd-139">실제 구성이 현재 필요한 상태 구성과 일치하는 경우 **TestScript** 블록은 True를 반환해야 하고, 일치하지 않는 경우에는 False를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="341dd-140">(현재 필요한 상태 구성은 DSC를 사용하는 노드에서 시행된 마지막 구성입니다.)</span><span class="sxs-lookup"><span data-stu-id="341dd-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="341dd-141">자격 증명</span><span class="sxs-lookup"><span data-stu-id="341dd-141">Credential</span></span>| <span data-ttu-id="341dd-142">자격 증명이 필요한 경우 이 스크립트를 실행하는 데 사용할 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="341dd-143">DependsOn</span><span class="sxs-lookup"><span data-stu-id="341dd-143">DependsOn</span></span>| <span data-ttu-id="341dd-144">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="341dd-145">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="341dd-146">예제 1</span><span class="sxs-lookup"><span data-stu-id="341dd-146">Example 1</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="341dd-147">예 2</span><span class="sxs-lookup"><span data-stu-id="341dd-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Version' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Version'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = { 
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="341dd-148">이 리소스는 텍스트 파일에 구성의 버전을 쓰는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="341dd-149">이 버전은 클라이언트 컴퓨터에서 사용할 수 있지만, 어느 노드에도 없으므로 PowerShell의 `using` 범위를 가진 `Script` 리소스의 각 스크립트 블록에 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="341dd-150">노드의 MOF 파일을 생성할 때 `$version` 변수의 값을 클라이언트 컴퓨터의 텍스트 파일로부터 읽어옵니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="341dd-151">DSC는 각 스크립트 블록의 `$using:version` 변수를 `$version` 변수의 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="341dd-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

