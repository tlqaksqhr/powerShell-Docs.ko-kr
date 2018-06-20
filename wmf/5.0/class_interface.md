---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225490"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="554bf-102">구현된 인터페이스 선언</span><span class="sxs-lookup"><span data-stu-id="554bf-102">Declare Implemented Interface</span></span>

<span data-ttu-id="554bf-103">구현된 인터페이스는 기본 형식 다음이나 지정된 기본 형식이 없는 경우 콜론(:) 바로 다음에 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554bf-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="554bf-104">쉼표를 사용하여 모든 형식 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="554bf-104">Separate all type names by using commas.</span></span> <span data-ttu-id="554bf-105">C# 구문과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="554bf-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```
