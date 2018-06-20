---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222057"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="c7f9c-102">제거 지침</span><span class="sxs-lookup"><span data-stu-id="c7f9c-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="c7f9c-103">명령 프롬프트 사용</span><span class="sxs-lookup"><span data-stu-id="c7f9c-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="c7f9c-104">**명령 프롬프트**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c7f9c-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="c7f9c-105">아래와 같이 [Windows 업데이트 독립 실행형 시작 관리자](https://support.microsoft.com/en-us/kb/934307)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7f9c-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="c7f9c-106">Windows Server 2012 R2 및 Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="c7f9c-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="c7f9c-107">Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="c7f9c-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="c7f9c-108">Windows Server 2008 R2 SP1 및 Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="c7f9c-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="c7f9c-109">제어판 사용</span><span class="sxs-lookup"><span data-stu-id="c7f9c-109">Using Control Panel</span></span>
1.  <span data-ttu-id="c7f9c-110">**제어판**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c7f9c-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="c7f9c-111">**프로그램**을 연 다음 **프로그램 제거**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c7f9c-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="c7f9c-112">**설치된 업데이트 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7f9c-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="c7f9c-113">설치된 업데이트 목록에서 **Windows Management Framework 5.0**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7f9c-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="c7f9c-114">*KB3134758*, *KB3134759* 또는 *KB3134760*에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c7f9c-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="c7f9c-115">**제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7f9c-115">Click **Uninstall.**</span></span>
