---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a>LCM 상태에 대한 자세한 정보

LCM 상태에 대한 세부 정보를 노출하는 기능이 향상되었습니다. 이제 Get-DscLocalConfigurationManager에서 반환되는 LCMState에 다음과 같은 값이 포함될 수 있습니다.

* **유휴 상태**
* **사용 중**
* **PendingReboot**
* **PendingConfiguration**

또한 상태에 대한 자세한 정보를 포함하는 LCMStateDetail 속성이 추가되었습니다.
