---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3392db954c22030bb64ae5093619d23952e1fcdb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="uninstallation-instructions" class="xliff"></a>
# 제거 지침

<a id="using-command-prompt" class="xliff"></a>
## 명령 프롬프트 사용
1.  **명령 프롬프트**를 엽니다.
2.  아래와 같이 [Windows 업데이트 독립 실행형 시작 관리자](https://support.microsoft.com/en-us/kb/934307)를 실행합니다.

Windows Server 2012 R2 및 Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
Windows Server 2008 R2 SP1 및 Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

<a id="using-control-panel" class="xliff"></a>
## 제어판 사용
1.  **제어판**을 엽니다.
2.  **프로그램**을 연 다음 **프로그램 제거**를 엽니다.
3.  **설치된 업데이트 보기**를 클릭합니다.
4.  설치된 업데이트 목록에서 **Windows Management Framework 5.0**을 선택합니다. *KB3134758*, *KB3134759* 또는 *KB3134760*에 해당합니다. **제거**를 클릭합니다.

