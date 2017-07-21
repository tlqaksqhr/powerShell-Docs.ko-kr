---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "여러 버전의 리소스 사용"
ms.openlocfilehash: c3397775a6767d74c182e15d07371e830f98e9a9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="15ef2-103">여러 버전의 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="15ef2-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="15ef2-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="15ef2-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="15ef2-105">PowerShell 5.0에서 DSC 리소스는 여러 버전이 있을 수 있으며, 이러한 버전들을 컴퓨터에 병렬로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="15ef2-106">이는 동일한 모듈 폴더에 포함된 여러 버전의 리소스 모듈에 의해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="15ef2-107">여러 리소스 버전을 병렬로 설치</span><span class="sxs-lookup"><span data-stu-id="15ef2-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="15ef2-108">[Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet의 **MinimumVersion**, **MaximumVersion** 및 **RequiredVersion**를 사용하여 설치할 모듈 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="15ef2-109">버전을 지정하지 않고 **Install-Module**을 호출하면 가장 최근 버전이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="15ef2-110">예를 들어 **xFailOverCluster** 모듈의 여러 버전이 있고, 각 버전에는 **xCluster** 리소스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="15ef2-111">버전 번호를 지정하지 않고 **Install-Module**을 호출한 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="15ef2-112">**Install-Module**을 다시 호출하고 **RequiredVersion** 1.1.0.0을 지정하면 그 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="15ef2-113">구성에서 리소스 버전 지정</span><span class="sxs-lookup"><span data-stu-id="15ef2-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="15ef2-114">컴퓨터에 여러 리소스가 설치되어 있으면, 해당 리소스의 버전을 지정한 후 구성에서 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="15ef2-115">이 작업은 **Import-DscResource** 키워드의 **ModuleVersion** 매개 변수를 지정하여 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="15ef2-116">하나가 넘는 버전이 설치된 리소스의 리소스 모듈 버전을 지정하지 않으면 구성에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="15ef2-117">다음 구성에서는 호출할 리소스의 버전을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-117">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

><span data-ttu-id="15ef2-118">참고: Import-DscResource의 ModuleVersion 매개 변수는 PowerShell 4.0에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="15ef2-119">PowerShell 4.0에서는 모듈 사양 개체를 Import-DscResource의 ModuleName 매개 변수로 전달하여 모듈 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="15ef2-120">모듈 사양 개체는 ModuleName 및 RequiredVersion 키가 포함된 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="15ef2-121">예:</span><span class="sxs-lookup"><span data-stu-id="15ef2-121">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

<span data-ttu-id="15ef2-122">이 작업은 PowerShell 5.0에서도 동작하지만, 이 경우 **ModuleVersion** 매개 변수를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="15ef2-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="15ef2-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15ef2-123">See also</span></span>
* [<span data-ttu-id="15ef2-124">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="15ef2-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="15ef2-125">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="15ef2-125">DSC Resources</span></span>](resources.md)

