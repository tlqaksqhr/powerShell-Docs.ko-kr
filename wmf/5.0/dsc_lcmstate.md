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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="50873-102">LCM 상태에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="50873-102">Detailed information about LCM state</span></span>

<span data-ttu-id="50873-103">LCM 상태에 대한 세부 정보를 노출하는 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50873-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="50873-104">이제 Get-DscLocalConfigurationManager에서 반환되는 LCMState에 다음과 같은 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50873-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="50873-105">**유휴 상태**</span><span class="sxs-lookup"><span data-stu-id="50873-105">**Idle**</span></span>
* <span data-ttu-id="50873-106">**사용 중**</span><span class="sxs-lookup"><span data-stu-id="50873-106">**Busy**</span></span>
* <span data-ttu-id="50873-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="50873-107">**PendingReboot**</span></span>
* <span data-ttu-id="50873-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="50873-108">**PendingConfiguration**</span></span>

<span data-ttu-id="50873-109">또한 상태에 대한 자세한 정보를 포함하는 LCMStateDetail 속성이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50873-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

