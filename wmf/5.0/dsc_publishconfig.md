---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>구성 문서를 적용하지 않고 제공

[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet은 구성 MOF 파일을 대상 노드에 복사하지만 구성을 적용하지는 않습니다.
이 구성은 다음 일관성 검사 중이나 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet을 실행할 때 적용됩니다.