---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="afd52-102">클래스 기반 DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="afd52-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="afd52-103">클래스를 사용하여 DSC 리소스 정의</span><span class="sxs-lookup"><span data-stu-id="afd52-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="afd52-104">피드백에 따라 클래스 기반 DSC 리소스 작성을 보다 간단하고 이해하기 쉽게 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="afd52-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="afd52-105">클래스 기반 DSC 리소스와 cmdlet DSC 리소스 공급자의 주요 차이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="afd52-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="afd52-106">스키마에 대한 MOF 파일이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="afd52-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="afd52-107">모듈 폴더에서 **DSCResource** 하위 폴더가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="afd52-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="afd52-108">PowerShell 모듈 파일에 여러 가지 DSC 리소스 클래스가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afd52-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="afd52-109">자세한 내용은 [PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성](https://msdn.microsoft.com/powershell/dsc/authoringresource)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="afd52-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>