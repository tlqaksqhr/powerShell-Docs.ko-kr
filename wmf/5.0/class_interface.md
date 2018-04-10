---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="49cba-102">구현된 인터페이스 선언</span><span class="sxs-lookup"><span data-stu-id="49cba-102">Declare Implemented Interface</span></span>

<span data-ttu-id="49cba-103">구현된 인터페이스는 기본 형식 다음이나 지정된 기본 형식이 없는 경우 콜론(:) 바로 다음에 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49cba-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="49cba-104">쉼표를 사용하여 모든 형식 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="49cba-104">Separate all type names by using commas.</span></span> <span data-ttu-id="49cba-105">C# 구문과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="49cba-105">It’s very similar to C# syntax.</span></span>

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