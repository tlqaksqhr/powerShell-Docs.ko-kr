---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC 구성"
ms.openlocfilehash: 3fdee72d5701433a3903697c5a0a32b112136592
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-configurations"></a><span data-ttu-id="7491c-103">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="7491c-103">DSC Configurations</span></span>

><span data-ttu-id="7491c-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7491c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7491c-105">DSC 구성은 특별한 형식의 함수를 정의하는 PowerShell 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="7491c-106">구성을 정의하려면 PowerShell 키워드 **Configuration**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
} 

MyDscConfiguration 
```

<span data-ttu-id="7491c-107">스크립트를 .ps1 파일로 저장하세요.</span><span class="sxs-lookup"><span data-stu-id="7491c-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="7491c-108">구성 구문</span><span class="sxs-lookup"><span data-stu-id="7491c-108">Configuration syntax</span></span>

<span data-ttu-id="7491c-109">구성 스크립트는 다음의 부분들로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="7491c-110">**Configuration** 블록.</span><span class="sxs-lookup"><span data-stu-id="7491c-110">The **Configuration** block.</span></span> <span data-ttu-id="7491c-111">가장 바깥쪽 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-111">This is the outermost script block.</span></span> <span data-ttu-id="7491c-112">**Configuration** 키워드를 사용하고 이름을 제공하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="7491c-113">이 경우 구성의 이름은 "MyDscConfiguration"입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="7491c-114">하나 이상의 **Node** 블록.</span><span class="sxs-lookup"><span data-stu-id="7491c-114">One or more **Node** blocks.</span></span> <span data-ttu-id="7491c-115">이 블록에서는 구성 중인 노드(컴퓨터 또는 VM)를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="7491c-116">위의 구성에는 "TEST-PC1"이라는 컴퓨터를 대상으로 하는 하나의 **Node** 블록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="7491c-117">하나 이상의 리소스 블록.</span><span class="sxs-lookup"><span data-stu-id="7491c-117">One or more resource blocks.</span></span> <span data-ttu-id="7491c-118">이 블록은 구성으로 구성 중인 리소스에 대한 속성을 설정하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="7491c-119">이 경우 두 개의 리소스 블록이 있으며, 각각 "WindowsFeature" 리소스를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="7491c-120">**Configuration** 블록 내에서는 PoweShell 함수에서 일반적으로 수행할 수도 있는 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="7491c-121">예를 들어 앞의 예에서는, 구성에서 대상 컴퓨터의 이름을 하드 코드하지 않으려는 경우 노드 이름에 대한 매개 변수를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}

MyDscConfiguration 
```

<span data-ttu-id="7491c-122">이 예제에서는 구성을 컴파일할 때 **ComputerName** 매개 변수로 전달하여 노드의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuraton.</span></span> <span data-ttu-id="7491c-123">이름의 기본값은 "localhost"입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="7491c-124">구성 컴파일</span><span class="sxs-lookup"><span data-stu-id="7491c-124">Compiling the configuration</span></span>

<span data-ttu-id="7491c-125">구성을 시행할 수 있으려면 먼저 MOF 문서로 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="7491c-126">PowerShell 함수에 대해 하는 것처럼 구성을 호출하여 이렇게 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-126">You do this by calling the configuration like you would a PowerShell function.</span></span>  
<span data-ttu-id="7491c-127">구성의 이름만을 포함하는 예제의 마지막 줄은 구성을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="7491c-128">**참고:** 구성을 호출하려면 (다른 PowerShell 함수에서 처럼) 함수가 전역 범위에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> 
><span data-ttu-id="7491c-129">스크립트를 "도트 소싱"하거나, F5 키를 사용하거나 ISE에서 **스크립트 실행** 단추를 클릭하여 구성 스크립트를 실행하면 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> 
><span data-ttu-id="7491c-130">스크립트를 도트 소싱하려면 명령을 `. .\myConfig.ps1`을 실행합니다. 여기서 `myConfig.ps1`은 구성을 포함하는 스크립트 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="7491c-131">구성을 호출하면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="7491c-132">모든 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-132">Resolves all variables</span></span> 
- <span data-ttu-id="7491c-133">현재 디렉터리에 구성과 같은 이름으로 폴더를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="7491c-134">새 디렉터리에 _NodeName_.mof라는 파일을 생성합니다. _NodeName_은 구성의 대상 노드 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> 
    <span data-ttu-id="7491c-135">노드가 두 개 이상 있을 경우에는 각 노드에 대해 MOF 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="7491c-136">**참고**: MOF 파일은 대상 노드에 대한 모든 구성 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="7491c-137">이 때문에 안전하게 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-137">Because of this, it’s important to keep it secure.</span></span> 
><span data-ttu-id="7491c-138">자세한 내용은 [MOF 파일 보안](secureMOF.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7491c-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="7491c-139">위의 첫 번째 구성을 컴파일하면 다음 폴더 구조가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-139">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

<span data-ttu-id="7491c-140">구성에서 매개 변수를 사용하는 경우, 두 번째 예제에서처럼 컴파일 시 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="7491c-141">다음과 같은 모습이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-141">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## <a name="using-dependson"></a><span data-ttu-id="7491c-142">DependsOn 사용</span><span class="sxs-lookup"><span data-stu-id="7491c-142">Using DependsOn</span></span>

<span data-ttu-id="7491c-143">유용한 DSC 키워드는 **DependsOn**입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="7491c-144">일반적으로(늘 반드시 그렇지는 않지만), DSC는 구성 내에서 나타나는 순서로 리소스를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span> <span data-ttu-id="7491c-145">그러나 **DependsOn**은 다른 리소스에 종속되는 리소스를 지정하며, LCM은 이러한 리소스가 리소스 인스턴스가 정의된 순서에 관계없이 올바른 순서로 적용되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span> <span data-ttu-id="7491c-146">예를 들어, 구성은 **User** 리소스의 인스턴스가 **Group** 인스턴스의 존재 여부에 따라 달라진다고 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

DependsOnExample
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="7491c-147">구성에서 새 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="7491c-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="7491c-148">앞의 예제를 실행했다면 명시적으로 가져오지 않고 리소스를 사용하고 있다는 경고가 표시된 것을 보았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="7491c-149">오늘, DSC는 PSDesiredStateConfiguration 모듈의 일부로서 12개의 리소스와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span> <span data-ttu-id="7491c-150">외부 모듈의 다른 리소스는 LCM에서 인식할 수 있도록 `$env:PSModulePath`에 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span> <span data-ttu-id="7491c-151">새 cmdlet인 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)는 시스템에 설치되어 있고 LCM에서 사용할 수 있는 리소스를 파악하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span> <span data-ttu-id="7491c-152">이러한 모듈은 `$env:PSModulePath`에 배치되어 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)에 의해 제대로 인식된 후에도 여전히 구성 내에서 로드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span> 
<span data-ttu-id="7491c-153">**Import-DscResource**는 **구성** 블록 내에서만 인식될 수 있는 동적 키워드입니다(즉, cmdlet이 아님).</span><span class="sxs-lookup"><span data-stu-id="7491c-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span> 
<span data-ttu-id="7491c-154">**Import-DscResource**에서는 두 개의 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="7491c-155">**ModuleName**은 **Import-DscResource**를 사용하는 권장 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="7491c-156">가져올 리소스를 포함하는 모듈의 이름을 받습니다(모듈 이름으로 이루어진 문자열 배열도 받음).</span><span class="sxs-lookup"><span data-stu-id="7491c-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span> 
- <span data-ttu-id="7491c-157">**Name**은 가져올 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7491c-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="7491c-158">이 이름은 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)에 의해 "Name"으로 반환한 친숙한 이름이 아니라, 리소스 스키마를 정의할 때 사용된 클래스 이름입니다([Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)에 의해 **ResourceType**으로 반환됨).</span><span class="sxs-lookup"><span data-stu-id="7491c-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span></span> 

## <a name="see-also"></a><span data-ttu-id="7491c-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7491c-159">See Also</span></span>
* [<span data-ttu-id="7491c-160">Windows PowerShell 필요한 상태 구성 개요</span><span class="sxs-lookup"><span data-stu-id="7491c-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="7491c-161">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="7491c-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="7491c-162">로컬 구성 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="7491c-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

