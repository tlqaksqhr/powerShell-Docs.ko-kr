---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "노드 간 종속성 지정"
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="6311c-103">노드 간 종속성 지정</span><span class="sxs-lookup"><span data-stu-id="6311c-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="6311c-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6311c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6311c-105">DSC는 다른 노드에서 구성에 대한 종속성을 지정하기 위한 구성에 사용할 수 있는 특별한 리소스 **WaitForAll**, **WaitForAny** 및 **WaitForSome**을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="6311c-106">이러한 리소스의 동작은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="6311c-107">**WaitForAll**: **NodeName** 속성에 정의된 모든 대상 노드에서 지정된 리소스가 원하는 상태이면 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="6311c-108">**WaitForAny**: **NodeName** 속성에 정의된 대상 노드 중 최소 하나 이상에서 지정된 리소스가 원하는 상태이면 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="6311c-109">**WaitForSome**: **NodeName** 속성과 더불어 **NodeCount** 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="6311c-110">**NodeCount**에서 지정되고 **NodeName** 속성에서 정의된 최소 숫자의 노드에서 리소스가 원하는 상태이면 리소스가 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="6311c-111">WaitForXXXX 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="6311c-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="6311c-112">**WaitForXXXX** 리소스를 사용하려면 해당 리소스 유형의 리소스 블록을 만들어 대기할 노드 및 DSC 리소스를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="6311c-113">그런 다음 구성의 다른 리소스 블록에 있는 **DependsOn** 속성을 사용하여 **WaitForXXXX** 노드에 정의된 조건이 성공할 때까지 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="6311c-114">예를 들어 다음 구성에서 대상 노드는 대상 노드가 도메인에 가입하기 전에 **xADDomain** 리소스가 **MyDC** 노드에서 최대 30번의 시도를 15초 간격으로 완료할 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present' 
            Name = 'AD-Domain-Services' 
        }

        xADDomain NewDomain 
        { 
            DomainName = 'Contoso.com'            
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

><span data-ttu-id="6311c-115">**참고:** 기본적으로 WaitForXXX 리소스는 한 번 시도한 후에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="6311c-116">필수는 아니지만, 일반적으로 다시 시도 간격 및 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6311c-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="6311c-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6311c-117">See Also</span></span>
* [<span data-ttu-id="6311c-118">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="6311c-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="6311c-119">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="6311c-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="6311c-120">로컬 구성 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="6311c-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

