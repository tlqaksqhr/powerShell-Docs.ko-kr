---
title:   PowerShell 필요한 상태 구성 시작 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# PowerShell 필요한 상태 구성 시작 #

이 가이드에서는 PowerShell 필요한 상태 구성 문서 작성을 시작하고 문서를 컴퓨터에 적용하는 방법에 대해 설명합니다. PowerShell cmdlet, 모듈 및 함수에 대한 기본 지식이 있는 것으로 가정합니다. 


## 구성 만들기 ##

[**구성**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)은 환경을 설명하는 문서입니다. 환경은 일반적으로 가상 컴퓨터나 물리적 컴퓨터인 "**노드**"로 구성됩니다. 

구성은 다양한 형태를 도입할 수 있습니다. 새 구성을 만드는 가장 쉬운 방법은 .ps1(PowerShell 스크립트) 파일을 만드는 것입니다. 이렇게 하려면 원하는 편집기를 엽니다. PowerShell ISE는 DSC를 기본적으로 이해하므로 좋은 선택입니다. 다음을 PS1로 저장합니다.

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## 구성의 부분 ##
**구성**은 PowerShell 4.0에 추가된 키워드로서, 필요한 상태 구성에서 사용하는 특별한 종류의 PowerShell 함수를 의미합니다. 이 예제에서 함수는 myFirstConfiguration이라고 합니다. 

다음 줄은 모듈을 가져오는 것과 비슷한 import 문입니다. 이에 대해서는 나중에 설명합니다.

"Node"는 이 구성이 작업을 수행하는 컴퓨터 이름을 정의합니다. 이 구성을 로컬로 편집하더라도, 구성이 원격 노드에 도달하여 원격 노드를 구성할 수 있습니다. 

노드는 컴퓨터 이름이나 IP 주소일 수 있습니다. 단일 구성 문서에 여러 노드를 포함할 수 있습니다. [구성 데이터](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)를 사용하면 동일한 구성을 여러 노드에 적용할 수도 있습니다. 이 경우에 노드는 로컬 컴퓨터라는 의미의 "localhost"입니다. 

다음 항목은 한 [**리소스**](https://msdn.microsoft.com/en-us/powershell/dsc/resources)입니다. 리소스는 구성의 구성 요소입니다. 각 리소스는 컴퓨터의 한 측면에 대한 구현 논리를 정의하는 모듈입니다. PowerShell에서 **Get-DscResource**를 실행하여 컴퓨터에서 모든 리소스를 볼 수 있습니다. 리소스가 로컬 컴퓨터에 있어야 하며 리소스를 이 구성의 두 번째 줄에 있는 **Import-DscResource**가 있는 구성에서 사용하려면 먼저 가져와야 합니다. 

**구성 시행**

위의 스크립트가 저장되어 있고 실행되는 경우, 출력이 생성되지 않습니다. 이것은 구성이 단순히 함수이고 위의 스크립트가 함수를 정의하기만 하고 함수를 실행하지는 않기 때문입니다. 함수를 정의했으면 함수를 호출해야 합니다.
```powershell
myFirstConfiguration
```

구성 함수는 실행되면 구성이 유효한지 유효성을 검사합니다. 실행하려면 먼저 구문 오류가 없어야 하고 리소스에 모든 필수 매개 변수가 정의되어 있어야 하며, 모든 리소스를 가져와야 합니다.

구성이 실행되면 구성에 있는 모든 노드에 대해 **.MOF 파일**을 포함하는 구성의 이름으로 폴더가 생성됩니다. .MOF 파일은 네트워크를 통해 통신하는 PowerShell DSC에 의해 사용되는 표준 기반 관리 형식입니다.

구성 시행:
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
이 스크립트는 구성에 있는 노드에 도달하여 구성 작업을 수행하는 PowerShell 작업을 만듭니다. 작업의 출력을 보려면 -Wait를 사용합니다. 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```



<!--HONumber=May16_HO3-->


