# 구현된 인터페이스 선언

구현된 인터페이스는 기본 형식 다음이나 지정된 기본 형식이 없는 경우 콜론(:) 바로 다음에 선언할 수 있습니다. 쉼표를 사용하여 모든 형식 이름을 구분합니다. C# 구문과 매우 유사합니다.

```PowerShell
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

<!--HONumber=Jun16_HO4-->


