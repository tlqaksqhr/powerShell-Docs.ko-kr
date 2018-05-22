---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-constructor"></a>기본 클래스 생성자 호출

하위 클래스에서 기본 클래스 생성자를 호출하려면 **base** 키워드를 사용합니다.

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

기본 클래스에 기본(매개 변수 없음) 생성자가 있는 경우 명시적 생성자 호출을 생략할 수 있습니다.

```powershell
class C : B
{
    C([int]$c) {}
}
```
