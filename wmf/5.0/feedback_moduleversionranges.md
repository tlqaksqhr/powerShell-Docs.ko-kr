---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225694"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="43b8c-102">모듈의 버전 범위 선언(1.\* 등) 지원</span><span class="sxs-lookup"><span data-stu-id="43b8c-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="43b8c-103">**-MinimumVersion**과 함께 **-MaximumVersion**을 사용하여 사용자는 특정 범위 내의 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b8c-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="43b8c-104">이 매개 변수는 **.**\*도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="43b8c-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="43b8c-105">다음 예제에서는 작동 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="43b8c-105">The following example shows how it works:</span></span>

<span data-ttu-id="43b8c-106">이제 **-MinimumVersion** 및 **-MaximumVersion**을 결합하여 특정 범위 내의 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b8c-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
