---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSCAutomationHostEnabled 레지스트리 키"
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
>적용 대상: Windows PowerShell 5.0

<a id="dscautomationhostenabled-registry-key" class="xliff"></a>
# DSCAutomationHostEnabled 레지스트리 키

DSC에서는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** 아래의 **DSCAutomationHostEnabled** 레지스트리 키를 사용하여 초기 부팅 시 컴퓨터를 구성할 수 있도록 합니다.
DSCAutomationHostEnabled는 다음의 세 가지 모드를 지원합니다.

|  DSCAutomationHostEnabled 값  |  설명   | 
|---|---| 
0 | 부팅 시 컴퓨터를 구성하지 않도록 설정합니다. |
1 | 부팅 시 컴퓨터를 구성하도록 설정합니다. |
2 | DSC가 보류 중 또는 현재 상태인 경우에만 컴퓨터를 구성하도록 설정합니다. 기본값입니다. |

<a id="see-also" class="xliff"></a>
## 참고 항목

이 기능을 사용하여 초기 부팅 시 구성을 실행하는 방법에 대한 예는 [초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성](bootstrapDsc.md)을 참조하세요.


