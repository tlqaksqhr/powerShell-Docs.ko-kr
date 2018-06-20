---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220345"
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="cc57a-102">DSC 구성의 요청 시 끌어오기</span><span class="sxs-lookup"><span data-stu-id="cc57a-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="cc57a-103">새로운 Update-DscConfiguration cmdlet은 메타 구성에 정의된 끌어오기 서버에서 끌어오기를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="cc57a-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="cc57a-104">이러한 동작을 종종 '지금 끌어오기'라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc57a-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="cc57a-105">트리거된 끌어오기는 일반적인 주기 중에 트리거된 경우와 정확히 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="cc57a-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="cc57a-106">현재 구성에 대한 체크섬을 끌어오기 서버의 구성에 대한 체크섬과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="cc57a-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="cc57a-107">동일한 경우 구성을 적용하지 않고 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="cc57a-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="cc57a-108">다른 경우 구성을 끌어오기 서버에서 아래로 끌어와 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc57a-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="cc57a-109">**참고:** 메타 구성 RefreshMode = 'Push'이면 이 cmdlet에서 오류가 반환되므로 이 cmdlet은 대상 노드가 '밀어넣기' 모드일 경우 항상 아무 작업도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc57a-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
