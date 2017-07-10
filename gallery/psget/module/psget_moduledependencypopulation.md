---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="logic-for-preparing-the-module-dependencies-during-publish-operation" class="xliff"></a>
# 게시 작업 중 모듈 종속성을 준비하기 위한 논리
1.  RequiredModules의 일부로 나열되는 모듈은 종속성으로 간주됩니다.
2.  모듈 베이스가 지정된 모듈 베이스 아래에 없는 NestedModules의 일부로 나열된 모듈은 종속성으로 간주됩니다.

3.  위의 종속성을 동일한 대상 리포지토리에서 사용할 수 있어야 합니다. 사용할 수 없는 경우 게시 작업 시 오류가 발생합니다.
    예: 리포지토리에서 'SnippetPx'를 사용할 수 없는 경우 아래 오류가 발생합니다.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  일부 모듈 종속성은 외부에서 관리할 수 있으며, 이 경우 모듈 매니페스트의 PSData 섹션에 있는 ExternalModuleDependencies 항목에 종속성을 추가해야 합니다.
    위의 오류 메시지에서 아래쪽 부분
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*모듈을 설치하는 동안 위의 준비된 종속성 목록은 종속성을 설치하는 데 사용됩니다.*

*게시 작업 중 시스템의 $env:PSModulePath에서 모듈의 종속성을 사용할 수 있는지 확인합니다.*

