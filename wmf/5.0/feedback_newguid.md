---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225592"
---
# <a name="new-guid"></a>New-Guid
종종 스크립트(또는 DSC 리소스 작성)에는 고유 식별자가 필요했습니다. GUID는 잘 작동하고 .NET Framework Guid 클래스를 호출하여 쉽게 생성할 수 있지만 cmdlet을 사용하면 .NET Framework 클래스에 익숙하지 않은 최종 사용자가 더 쉽게 검색할 수 있습니다.

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
