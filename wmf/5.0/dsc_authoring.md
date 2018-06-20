---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1595a3e817fd711c35128f06927fd57df7a63fb8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218249"
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="af0ea-102">PowerShell ISE를 사용하여 작성 기능 향상</span><span class="sxs-lookup"><span data-stu-id="af0ea-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="af0ea-103">Windows PowerShell ISE에서는 다음과 같은 기능이 향상되어 DSC 구성을 훨씬 더 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af0ea-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="af0ea-104">**구성** 블록이나 **노드** 블록 내 빈 줄에 **Ctrl+Space**를 입력하여 해당 블록 내의 모든 DSC 리소스 나열</span><span class="sxs-lookup"><span data-stu-id="af0ea-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="af0ea-105">**열거형** 형식인 리소스 속성 자동 완성</span><span class="sxs-lookup"><span data-stu-id="af0ea-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="af0ea-106">구성에 있는 다른 리소스 인스턴스에 따라 DSC 리소스의 **DependsOn** 속성 자동 완성</span><span class="sxs-lookup"><span data-stu-id="af0ea-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="af0ea-107">리소스 속성 값의 탭 완성 기능 향상</span><span class="sxs-lookup"><span data-stu-id="af0ea-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="af0ea-108">**참고:** Ctrl+Space를 사용하여 옵션을 나열하려면 먼저 리소스 속성 값에 대해 빈 문자열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af0ea-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="af0ea-109">**Tab** 키를 누르면 옵션이 차례대로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="af0ea-109">Pressing **Tab** cycles through options.</span></span>
