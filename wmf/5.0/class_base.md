---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: fc517cd204b8f2647b824f0b9ee8f0f8f62fb821
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="declare-base-class"></a><span data-ttu-id="9f3f5-102">기본 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="9f3f5-102">Declare Base Class</span></span>
<span data-ttu-id="9f3f5-103">Windows PowerShell 클래스를 다른 Windows PowerShell 클래스의 기본 형식으로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f3f5-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```PowerShell
class bar
{
   [int]foo() 
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="9f3f5-104">또한 기존 .NET Framework 형식을 기본 클래스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f3f5-104">You can also use existing .NET Framework types as base classes:</span></span>

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

