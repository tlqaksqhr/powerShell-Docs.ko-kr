---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: fa972b68015d9b6e14508ccda562cfa5ebd632ac
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="4a758-102">모듈의 버전 범위 선언(1.\* 등) 지원</span><span class="sxs-lookup"><span data-stu-id="4a758-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="4a758-103">**-MinimumVersion**과 함께 **-MaximumVersion**을 사용하여 사용자는 특정 범위 내의 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a758-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="4a758-104">매개 변수에 지원 합니다. **.**\*입니다.</span><span class="sxs-lookup"><span data-stu-id="4a758-104">The parameter also support \*\*.\*\*\*.</span></span> <span data-ttu-id="4a758-105">다음 예제에서는 작동 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4a758-105">The following example shows how it works:</span></span>

```powershell
Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:

PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

