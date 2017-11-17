---
title: "네트워크 스위치 관리자 cmdlet 오류"
contributor: vaibch
ms.openlocfilehash: e32e31762b665a7e2c6f6938fe494cb6127d4264
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
<span data-ttu-id="e29a7-102">네트워크 스위치 관리자 cmdlet을 사용하면 WSMAN을 통해 네트워크 스위치를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29a7-102">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="e29a7-103">이 모듈의 몇 가지 cmdlet에는 파이프라인을 통해 값을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29a7-103">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="e29a7-104">WMF 5.1 Preview에서는 파이프라인을 통해 값을 적용할 수 있는 cmdlet이 값이 파이프라인을 통해 전달되지 않는 경우 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e29a7-104">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="e29a7-105">"InputObject" 매개 변수를 사용하지 않는 경우 cmdlet이 오류 없이 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e29a7-105">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="e29a7-106">다음은 영향을 받는 cmdlet 목록입니다. 즉, 이러한 cmdlet은 파이프라인을 통해 "InputObject" 매개 변수의 값을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29a7-106">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="e29a7-107">이 값이 파이프라인을 통해 전달되지 않는 경우 cmdlet이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e29a7-107">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="e29a7-108">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="e29a7-108">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="e29a7-109">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="e29a7-109">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="e29a7-110">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="e29a7-110">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="e29a7-111">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="e29a7-111">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="e29a7-112">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="e29a7-112">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="e29a7-113">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="e29a7-113">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="e29a7-114">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="e29a7-114">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="e29a7-115">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="e29a7-115">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="e29a7-116">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="e29a7-116">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="e29a7-117">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="e29a7-117">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="e29a7-118">해결 방법</span><span class="sxs-lookup"><span data-stu-id="e29a7-118">Resolution</span></span>
<span data-ttu-id="e29a7-119">InputObject 매개 변수 값을 파이프라인을 통해 전달하면 cmdlet이 올바로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e29a7-119">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="e29a7-120">위의 cmdlet에 대해 작동하는 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e29a7-120">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="e29a7-121">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="e29a7-121">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```
- <span data-ttu-id="e29a7-122">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="e29a7-122">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="e29a7-123">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="e29a7-123">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="e29a7-124">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="e29a7-124">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="e29a7-125">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="e29a7-125">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="e29a7-126">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="e29a7-126">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="e29a7-127">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="e29a7-127">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="e29a7-128">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="e29a7-128">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
