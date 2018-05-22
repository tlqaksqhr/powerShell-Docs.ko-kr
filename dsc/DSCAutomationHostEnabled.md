---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSCAutomationHostEnabled 레지스트리 키
ms.openlocfilehash: 0cecbadc6802938cadb4ffb9745a23e6b98544be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
>적용 대상: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled 레지스트리 키

DSC에서는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** 아래의 **DSCAutomationHostEnabled** 레지스트리 키를 사용하여 초기 부팅 시 컴퓨터를 구성할 수 있도록 합니다.
DSCAutomationHostEnabled는 다음의 세 가지 모드를 지원합니다.

|  DSCAutomationHostEnabled 값  |  설명   |
|---|---|
0 | 부팅 시 컴퓨터를 구성하지 않도록 설정합니다. |
1 | 부팅 시 컴퓨터를 구성하도록 설정합니다. |
2 | DSC가 보류 중 또는 현재 상태인 경우에만 컴퓨터를 구성하도록 설정합니다. 기본값입니다. |

## <a name="see-also"></a>참고 항목

이 기능을 사용하여 초기 부팅 시 구성을 실행하는 방법에 대한 예는 [초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성](bootstrapDsc.md)을 참조하세요.