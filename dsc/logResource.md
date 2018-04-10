---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC 로그 리소스
ms.openlocfilehash: f1a528767508d4a0e7f0ea2e58fd27a6a4d7ec75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-log-resource"></a>DSC 로그 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)의 __Log__ 리소스에서는 메시지를 Microsoft-Windows-필요한 상태 구성/분석 이벤트 로그에 쓰는 메커니즘을 제공합니다.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

참고: 기본적으로 DSC에 대한 작업 로그만 사용됩니다.
분석 로그를 사용할 수 있거나 볼 수 있으려면 먼저 사용하도록 설정해야 합니다.
다음 문서를 참조하세요.

[DSC 이벤트 로그는 어디에 있나요?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>속성
|  속성  |  설명   |
|---|---|
| 메시지| Microsoft-Windows-필요한 상태 구성/분석 이벤트 로그에 쓸 메시지를 나타냅니다.|
| DependsOn | 이 로그 메시지가 작성되려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.|

## <a name="example"></a>예제

다음 예제에서는 Microsoft-Windows-필요한 상태 구성/분석 이벤트 로그에 메시지를 포함하는 방법을 보여 줍니다.

> **참고**: 이 리소스를 구성한 상태에서 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)을 실행하는 경우 항상 **$false**를 반환합니다.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```