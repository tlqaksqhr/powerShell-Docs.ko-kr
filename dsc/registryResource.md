---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC 레지스트리 리소스"
ms.openlocfilehash: 649cb60578c053c04a7fcc7446881fb76daee26a
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2017
---
<a id="dsc-registry-resource" class="xliff"></a>
# DSC 레지스트리 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

PowerShell DSC(필요한 상태 구성)의 **레지스트리** 리소스에서는 대상 노드에 있는 레지스트리 키와 값을 관리하는 메커니즘을 제공합니다.

<a id="syntax" class="xliff"></a>
## 구문

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

<a id="properties" class="xliff"></a>
## 속성
|  속성  |  설명   | 
|---|---| 
| 키| 특정 상태를 확인하려는 레지스트리 키의 경로를 나타냅니다. 이 경로는 하이브를 포함해야 합니다.| 
| ValueName| 레지스트리 값의 이름을 나타냅니다. 레지스트리 키를 추가하거나 제거하려면 ValueType 또는 ValueData를 지정하지 않고 이 속성을 빈 문자열로 지정합니다. 레지스트리 키의 기본값을 수정하거나 제거하려면 ValueType 또는 ValueData도 지정하고 이 속성을 빈 문자열로 지정합니다.| 
| Ensure| 키와 값의 존재 여부를 나타냅니다. 존재하도록 하려면 이 속성을 "Present"으로 설정합니다. 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다. 기본값은 "Present"입니다.| 
| Force| 지정된 레지스트리 키가 있을 경우, __Force__를 사용하면 새 값으로 덮어씁니다. 하위 키가 포함된 레지스트리 키를 삭제하는 경우에는 이 속성을 __$true__로 지정해야 합니다.| 
| Hex| 데이터가 16진수 형식으로 표현될 것인지 여부를 나타냅니다. 지정하는 경우 DWORD/QWORD 값 데이터가 16진수 형식으로 표시됩니다. 다른 형식에 대해서는 유효하지 않습니다. 기본값은 __$false__입니다.| 
| DependsOn| 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.| 
| ValueData| 레지스트리 값에 대한 데이터입니다.| 
| ValueType| 값의 형식을 나타냅니다. 지원되는 형식은 다음과 같습니다. 
<ul><li>문자열(REG_SZ)</li>


<li>이진수(REG-BINARY)</li>


<li>Dword 32비트(REG_DWORD)</li>


<li>Qword 64비트(REG_QWORD)</li>


<li>다중 문자열(REG_MULTI_SZ)</li>


<li>확장 가능한 문자열(REG_EXPAND_SZ)</li></ul>

<a id="example" class="xliff"></a>
## 예제
이 예제에서는 "ExampleKey"라는 키가 **HKEY\_LOCAL\_MACHINE** 하이브에 있는지 확인합니다.
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

>**참고:** **HKEY\_CURRENT\_USER** 하이브에서 레지스트리 설정을 변경하려면 구성이 시스템이 아닌 사용자 자격 증명을 사용하여 실행되어야 합니다.
>**PsDscRunAsCredential** 속성을 사용하여 구성에 대한 사용자 자격 증명을 지정할 수 있습니다. 예제는 [사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md)을 참조하세요.



