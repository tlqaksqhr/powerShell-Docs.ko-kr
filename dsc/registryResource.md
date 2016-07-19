---
title: "DSC 레지스트리 리소스"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 15e346ecd630a1256477d375bc1373f376e76f64

---

# DSC 레지스트리 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

PowerShell DSC(필요한 상태 구성)의 **레지스트리** 리소스에서는 대상 노드에 있는 레지스트리 키와 값을 관리하는 메커니즘을 제공합니다.

## 구문

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## 속성
|  속성  |  설명   | 
|---|---| 
| 키| 특정 상태를 확인하려는 레지스트리 키의 경로를 나타냅니다. 이 경로는 하이브를 포함해야 합니다.| 
| ValueName| 레지스트리 값의 이름을 나타냅니다.| 
| Ensure| 키와 값의 존재 여부를 나타냅니다. 존재하도록 하려면 이 속성을 "Present"으로 설정합니다. 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다. 기본값은 "Present"입니다.| 
| Force| 지정된 레지스트리 키가 있을 경우, __Force__를 사용하면 새 값으로 덮어씁니다.| 
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

## 예제
```powershell
Registry RegistryExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Key = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
    ValueName = "TestValue"
    ValueData = "TestData"
}
```




<!--HONumber=Jun16_HO4-->


