---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225677"
---
# <a name="deliver-a-configuration-document-without-applying"></a>구성 문서를 적용하지 않고 제공

[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet은 구성 MOF 파일을 대상 노드에 복사하지만 구성을 적용하지는 않습니다.
이 구성은 다음 일관성 검사 중이나 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet을 실행할 때 적용됩니다.
