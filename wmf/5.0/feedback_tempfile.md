---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
경우에 따라 스크립트에서 임시 파일을 만들어야 합니다. **New-TemporaryFile** cmdlet을 사용하면 쉽게 만들 수 있습니다.

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp
