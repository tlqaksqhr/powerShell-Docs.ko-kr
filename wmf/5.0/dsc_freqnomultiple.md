---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="dcc34-102">RefreshMode 및 ConfigurationMode의 빈도가 서로의 배수일 필요가 없음</span><span class="sxs-lookup"><span data-stu-id="dcc34-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="dcc34-103">이전 버전의 DSC에서 LCM은 `RefreshFrequencyMins` 및 `ConfigurationModeFrequencyMins`를 서로의 배수로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc34-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="dcc34-104">WMF 5.0 RTM에서 이러한 속성은 서로 독립적으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcc34-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="dcc34-105">자세한 내용은 [로컬 구성 관리자 구성](https://msdn.microsoft.com/powershell/dsc/metaconfig)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dcc34-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
