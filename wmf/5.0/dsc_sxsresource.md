---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="3b52a-102">DSC 리소스의 Side-By-Side 모듈 버전 관리 지원</span><span class="sxs-lookup"><span data-stu-id="3b52a-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="3b52a-103">DSC 리소스를 포함하는 모듈은 병렬로 설치할 수 있으며, DSC 구성에서는 시스템에 설치되어 있는 특정 버전의 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b52a-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="3b52a-104">자세한 내용은 [여러 버전의 리소스 사용](https://msdn.microsoft.com/powershell/dsc/sxsresource)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b52a-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="3b52a-105">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="3b52a-105">Known issues</span></span>

<span data-ttu-id="3b52a-106">이번 릴리스에서 병렬 설치에는 다음과 같은 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b52a-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="3b52a-107">동일한 구성 내에서 두 가지 다른 버전의 DSC 리소스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b52a-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>