---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a>LCM 상태에 대한 자세한 정보

LCM 상태에 대한 세부 정보를 노출하는 기능이 향상되었습니다. 이제 Get-DscLocalConfigurationManager에서 반환되는 LCMState에 다음과 같은 값이 포함될 수 있습니다.

* **유휴 상태**
* **사용 중**
* **PendingReboot**
* **PendingConfiguration**

또한 상태에 대한 자세한 정보를 포함하는 LCMStateDetail 속성이 추가되었습니다.

