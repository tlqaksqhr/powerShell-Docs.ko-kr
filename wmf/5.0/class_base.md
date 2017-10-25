---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 5dbaa126cf9ae3917c3a8787ffc5ef5ac77b19c1
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2017
---
# <a name="declare-base-class"></a><span data-ttu-id="c6433-102">기본 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="c6433-102">Declare Base Class</span></span>
<span data-ttu-id="c6433-103">Windows PowerShell 클래스를 다른 Windows PowerShell 클래스의 기본 형식으로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6433-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
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

<span data-ttu-id="c6433-104">또한 기존 .NET Framework 형식을 기본 클래스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6433-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

