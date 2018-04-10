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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="fbbf4-102">LCM 상태에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="fbbf4-102">Detailed information about LCM state</span></span>

<span data-ttu-id="fbbf4-103">LCM 상태에 대한 세부 정보를 노출하는 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbf4-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="fbbf4-104">이제 Get-DscLocalConfigurationManager에서 반환되는 LCMState에 다음과 같은 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbf4-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="fbbf4-105">**유휴 상태**</span><span class="sxs-lookup"><span data-stu-id="fbbf4-105">**Idle**</span></span>
* <span data-ttu-id="fbbf4-106">**사용 중**</span><span class="sxs-lookup"><span data-stu-id="fbbf4-106">**Busy**</span></span>
* <span data-ttu-id="fbbf4-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="fbbf4-107">**PendingReboot**</span></span>
* <span data-ttu-id="fbbf4-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fbbf4-108">**PendingConfiguration**</span></span>

<span data-ttu-id="fbbf4-109">또한 상태에 대한 자세한 정보를 포함하는 LCMStateDetail 속성이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbf4-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>