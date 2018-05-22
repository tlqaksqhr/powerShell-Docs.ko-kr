---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6a25908de746e296bef91e05c3d4e250aa77c9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="nonewline-parameter"></a>NoNewLine 매개 변수
**Out-File**, **Add-Content** 및 **Set-Content**는 단순히 출력 뒤에 오는 새 줄을 생략하는 새로운 **–NoNewline** 스위치를 제공합니다.
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
**–NoNewline**을 지정하지 않으면 각 조각이 별도의 줄에 있게 됩니다.
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
