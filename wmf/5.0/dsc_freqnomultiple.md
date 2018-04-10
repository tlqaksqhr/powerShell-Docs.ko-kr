---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="8138e-102">RefreshMode 및 ConfigurationMode의 빈도가 서로의 배수일 필요가 없음</span><span class="sxs-lookup"><span data-stu-id="8138e-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="8138e-103">이전 버전의 DSC에서 LCM은 `RefreshFrequencyMins` 및 `ConfigurationModeFrequencyMins`를 서로의 배수로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8138e-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="8138e-104">WMF 5.0 RTM에서 이러한 속성은 서로 독립적으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="8138e-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="8138e-105">자세한 내용은 [로컬 구성 관리자 구성](https://msdn.microsoft.com/powershell/dsc/metaconfig)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8138e-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>