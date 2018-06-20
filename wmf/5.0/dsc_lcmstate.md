---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219864"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="4fd8c-102">LCM 상태에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="4fd8c-102">Detailed information about LCM state</span></span>

<span data-ttu-id="4fd8c-103">LCM 상태에 대한 세부 정보를 노출하는 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4fd8c-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="4fd8c-104">이제 Get-DscLocalConfigurationManager에서 반환되는 LCMState에 다음과 같은 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fd8c-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="4fd8c-105">**유휴 상태**</span><span class="sxs-lookup"><span data-stu-id="4fd8c-105">**Idle**</span></span>
* <span data-ttu-id="4fd8c-106">**사용 중**</span><span class="sxs-lookup"><span data-stu-id="4fd8c-106">**Busy**</span></span>
* <span data-ttu-id="4fd8c-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="4fd8c-107">**PendingReboot**</span></span>
* <span data-ttu-id="4fd8c-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="4fd8c-108">**PendingConfiguration**</span></span>

<span data-ttu-id="4fd8c-109">또한 상태에 대한 자세한 정보를 포함하는 LCMStateDetail 속성이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4fd8c-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
