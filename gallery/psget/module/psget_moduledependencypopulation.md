---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="f16d7-103">게시 작업 중 모듈 종속성을 준비하기 위한 논리</span><span class="sxs-lookup"><span data-stu-id="f16d7-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="f16d7-104">RequiredModules의 일부로 나열되는 모듈은 종속성으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="f16d7-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="f16d7-105">모듈 베이스가 지정된 모듈 베이스 아래에 없는 NestedModules의 일부로 나열된 모듈은 종속성으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="f16d7-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="f16d7-106">위의 종속성을 동일한 대상 리포지토리에서 사용할 수 있어야 합니다. 사용할 수 없는 경우 게시 작업 시 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f16d7-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="f16d7-107">예: 리포지토리에서 'SnippetPx'를 사용할 수 없는 경우 아래 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f16d7-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="f16d7-108">일부 모듈 종속성은 외부에서 관리할 수 있으며, 이 경우 모듈 매니페스트의 PSData 섹션에 있는 ExternalModuleDependencies 항목에 종속성을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f16d7-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="f16d7-109">위의 오류 메시지에서 아래쪽 부분</span><span class="sxs-lookup"><span data-stu-id="f16d7-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="f16d7-110">*모듈을 설치하는 동안 위의 준비된 종속성 목록은 종속성을 설치하는 데 사용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="f16d7-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="f16d7-111">*게시 작업 중 시스템의 $env:PSModulePath에서 모듈의 종속성을 사용할 수 있는지 확인합니다.*</span><span class="sxs-lookup"><span data-stu-id="f16d7-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>