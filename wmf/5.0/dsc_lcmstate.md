---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>LCM 상태에 대한 자세한 정보

LCM 상태에 대한 세부 정보를 노출하는 기능이 향상되었습니다. 이제 Get-DscLocalConfigurationManager에서 반환되는 LCMState에 다음과 같은 값이 포함될 수 있습니다.

* **유휴 상태**
* **사용 중**
* **PendingReboot**
* **PendingConfiguration**

또한 상태에 대한 자세한 정보를 포함하는 LCMStateDetail 속성이 추가되었습니다.