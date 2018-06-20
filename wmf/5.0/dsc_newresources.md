---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 18f77922a30e8b6fb73c08f0d218f2655a129bce
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225575"
---
# <a name="new-built-in-dsc-resources"></a><span data-ttu-id="75f7b-102">새로운 기본 제공 DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="75f7b-102">New built-in DSC resources</span></span>

<span data-ttu-id="75f7b-103">WMF 5.0 RTM은 다음과 같은 네 가지 새로운 DSC 리소스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="75f7b-103">WMF 5.0 RTM has 4 new DSC resources:</span></span>
* <span data-ttu-id="75f7b-104">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="75f7b-104">WindowsFeatureSet</span></span>
* <span data-ttu-id="75f7b-105">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="75f7b-105">WindowsOptionalFeatureSet</span></span>
* <span data-ttu-id="75f7b-106">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="75f7b-106">ServiceSet</span></span>
* <span data-ttu-id="75f7b-107">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="75f7b-107">ProcessSet</span></span>

<span data-ttu-id="75f7b-108">이러한 리소스를 사용하면 단일 리소스 호출을 통해 여러 리소스를 간단하게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75f7b-108">These resources provide an easy way to configure multiple instances using a single resource call.</span></span>

## <a name="windowsfeatureset"></a><span data-ttu-id="75f7b-109">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="75f7b-109">WindowsFeatureSet</span></span>

```powershell
# Get the syntax of WindowsFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsFeatureSet -Syntax

WindowsFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [Ensure = [String]]
    [Source = [String]]
    [IncludeAllSubFeature = [Boolean]]
    [Credential = [PSCredential]]
    [LogPath = [String]]
}
```

## <a name="windowsoptionalfeatureset"></a><span data-ttu-id="75f7b-110">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="75f7b-110">WindowsOptionalFeatureSet</span></span>

```powershell
# Get the syntax of WindowsOptionalFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsOptionalFeatureSet -Syntax

WindowsOptionalFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    Ensure = [String]
    [Source = [String[]]]
    [RemoveFilesOnDisable = [Boolean]]
    [LogPath = [String]]
    [NoWindowsUpdateCheck = [Boolean]]
    [LogLevel = [String]]
}
```

## <a name="serviceset"></a><span data-ttu-id="75f7b-111">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="75f7b-111">ServiceSet</span></span>

```powershell
# Get the syntax of ServiceSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ServiceSet -Syntax

ServiceSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [StartupType = [String]]
    [BuiltInAccount = [String]]
    [State = [String]]
    [Ensure = [String]]
    [Credential = [PSCredential]]
}
```

## <a name="processset"></a><span data-ttu-id="75f7b-112">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="75f7b-112">ProcessSet</span></span>

```powershell
# Get the syntax of ProcessSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ProcessSet -Syntax

ProcessSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Path = [String[]]
    [Credential = [PSCredential]]
    [Ensure = [String]]
    [StandardOutputPath = [String]]
    [StandardErrorPath = [String]]
    [StandardInputPath = [String]]
    [WorkingDirectory = [String]]
}
```
