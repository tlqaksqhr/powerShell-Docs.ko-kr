---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 8c6a7d55e40f64bde6c2a2074ca3adb9cd210322
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="nonewline-parameter"></a><span data-ttu-id="64132-102">NoNewLine 매개 변수</span><span class="sxs-lookup"><span data-stu-id="64132-102">NoNewLine parameter</span></span>
<span data-ttu-id="64132-103">**Out-File**, **Add-Content** 및 **Set-Content**는 단순히 출력 뒤에 오는 새 줄을 생략하는 새로운 **–NoNewline** 스위치를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64132-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="64132-104">**–NoNewline**을 지정하지 않으면 각 조각이 별도의 줄에 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64132-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```

