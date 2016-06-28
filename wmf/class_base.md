# 기본 클래스 선언
Windows PowerShell 클래스를 다른 Windows PowerShell 클래스의 기본 형식으로 선언할 수 있습니다.

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

또한 기존 .NET Framework 형식을 기본 클래스로 사용할 수 있습니다.

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

<!--HONumber=Jun16_HO4-->


