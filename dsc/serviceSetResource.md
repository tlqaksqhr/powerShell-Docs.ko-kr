---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC ServiceSet 리소스"
ms.openlocfilehash: 92fa4a442eb42e89195162b7831f1a96d40b84f5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="dsc-serviceset-resource" class="xliff"></a>
# DSC ServiceSet 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0


Windows PowerShell DSC(필요한 상태 구성)의 **ServiceSet** 리소스에서는 대상 노드에 있는 서비스를 관리하는 메커니즘을 제공합니다. 이 리소스는 `Name` 속성에 지정된 각 서비스에 대해 [서비스 리소스](serviceResource.md)를 호출하는 [복합 리소스](authoringResourceComposite.md)입니다.

여러 서비스를 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.

<a id="syntax" class="xliff"></a>
## 구문

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

<a id="properties" class="xliff"></a>
## 속성

|  속성  |  설명   | 
|---|---| 
| 이름| 서비스 이름을 나타냅니다. 이 속성은 경우에 따라 표시 이름과 다릅니다. [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet으로 서비스 목록과 현재 상태를 가져올 수 있습니다.|
| StartupType| 서비스의 시작 유형을 나타냅니다. 이 속성에 허용된 값은 **Automatic**, **Disabled** 및 **Manual**입니다.|  
| BuiltInAccount| 서비스에 사용할 로그인 계정을 나타냅니다. 이 속성에 허용된 값은 **LocalService**, **LocalSystem**, 및 **NetworkService**입니다.| 
| State| 서비스에 대해 확인하려는 상태 즉, **중지됨** 또는 **실행 중**을 나타냅니다.| 
| Ensure| 서비스가 시스템에 있는지 여부를 지정합니다. 서비스가 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다. 서비스가 존재하도록 하려면 이 속성을 **Present**(기본값)로 설정합니다.|
| 자격 증명| 서비스 리소스가 실행될 계정에 대한 자격 증명을 나타냅니다. 이 속성과 **BuiltinAccount** 속성은 함께 사용할 수 없습니다.| 
| DependsOn| 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 *ResourceName*이고 해당 형식이 *ResourceType*일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.| 



<a id="example" class="xliff"></a>
## 예제

다음 구성에서는 "Windows 오디오" 및 "원격 데스크톱 서비스" 서비스를 시작합니다.

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

