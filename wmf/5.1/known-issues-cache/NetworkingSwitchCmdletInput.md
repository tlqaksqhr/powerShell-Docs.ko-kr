---
title: "네트워크 스위치 관리자 cmdlet 오류"
contributor: vaibch
translationtype: Human Translation
ms.sourcegitcommit: 34337749a77f4379b841a8478d4e6e3bc97e7ada
ms.openlocfilehash: 180158033e0c960f73dba66a3d77b15765e3e382

---

네트워크 스위치 관리자 cmdlet을 사용하면 WSMAN을 통해 네트워크 스위치를 관리할 수 있습니다. 이 모듈의 몇 가지 cmdlet에는 파이프라인을 통해 값을 적용할 수 있습니다. WMF 5.1 Preview에서는 파이프라인을 통해 값을 적용할 수 있는 cmdlet이 값이 파이프라인을 통해 전달되지 않는 경우 실행되지 않습니다.

"InputObject" 매개 변수를 사용하지 않는 경우 cmdlet이 오류 없이 계속 실행됩니다.

다음은 영향을 받는 cmdlet 목록입니다. 즉, 이러한 cmdlet은 파이프라인을 통해 "InputObject" 매개 변수의 값을 적용할 수 있습니다. 이 값이 파이프라인을 통해 전달되지 않는 경우 cmdlet이 실행되지 않습니다.

- Disable-NetworkSwitchEthernetPort
- Enable-NetworkSwitchEthernetPort
- Remove-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchPortMode
- Set-NetworkSwitchPortProperty
- Disable-NetworkSwitchFeature
- Enable-NetworkSwitchFeature
- Remove-NetworkSwitchVlan
- Set-NetworkSwitchVlanProperty

### 해결 방법
InputObject 매개 변수 값을 파이프라인을 통해 전달하면 cmdlet이 올바로 작동합니다. 위의 cmdlet에 대해 작동하는 몇 가지 예는 다음과 같습니다.

- Disable-NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```
- Enable-NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Remove-NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- Set-NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- Set-NetworkSwitchPortProperty
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- Disable-NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- Enable-NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- Set-NetworkSwitchVlanProperty
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```



<!--HONumber=Jul16_HO5-->


