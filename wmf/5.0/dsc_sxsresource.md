---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="side-by-side-module-versioning-support-for-dsc-resources" class="xliff"></a>
# DSC 리소스의 Side-By-Side 모듈 버전 관리 지원

DSC 리소스를 포함하는 모듈은 병렬로 설치할 수 있으며, DSC 구성에서는 시스템에 설치되어 있는 특정 버전의 리소스를 사용할 수 있습니다.

자세한 내용은 [여러 버전의 리소스 사용](https://msdn.microsoft.com/powershell/dsc/sxsresource)을 참조하세요.

<a id="known-issues" class="xliff"></a>
## 알려진 문제

이번 릴리스에서 병렬 설치에는 다음과 같은 알려진 문제가 있습니다.

-   동일한 구성 내에서 두 가지 다른 버전의 DSC 리소스를 사용할 수 없습니다.

