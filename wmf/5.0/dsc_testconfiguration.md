---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="45097-102">Test-DscConfiguration cmdlet에서 참조 구성 지원</span><span class="sxs-lookup"><span data-stu-id="45097-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="45097-103">Test-DscConfiguration cmdlet은 비교할 참조 구성 문서를 지정하여 하나 이상 대상 노드의 원하는 구성 상태를 테스트할 수 있도록 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="45097-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="45097-104">다음과 같은 새 매개 변수 집합은 지정된 경로의 DSC 구성을 사용하여 테스트만 수행하고 지정된 대상 노드에서 각 구성을 적용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45097-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="45097-105">Start-DscConfiguration 및 다른 DSC cmdlet과 마찬가지로 각 MOF의 이름을 사용하여 구성을 테스트할 대상 노드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="45097-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span> 

```powershell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

<span data-ttu-id="45097-106">다음과 같은 새 매개 변수 집합은 단일 DSC 구성을 사용하여 테스트만 수행하고 지정된 대상 노드에서 구성을 적용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45097-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span> 

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

