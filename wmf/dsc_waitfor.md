# 노든 간 종속성 지정

이제 기본 제공 WaitFor\* 리소스(WaitForAll, WaitForAny 및 WaitForSome)를 사용하여 외부 오케스트레이션 없이 구성 실행 중 컴퓨터 간에 종속성을 지정할 수 있습니다. 동작이나 각 WaitFor\* 리소스는 다음과 같습니다.

* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAll</ctype="x-NOTFOUND"> NodeName 속성에 정의된 <ctype="x-NOTFOUND" mdpre="*" mdpost="*">모든</ctype="x-NOTFOUND"> 대상 노드에서 지정된 리소스가 원하는 상태가 될 때까지 대기합니다.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAny</ctype="x-NOTFOUND"> NodeName 속성에 정의된 <ctype="x-NOTFOUND" mdpre="*" mdpost="*">임의</ctype="x-NOTFOUND"> 대상 노드에서 지정된 리소스가 원하는 상태가 될 때까지 대기합니다.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForSome</ctype="x-NOTFOUND"> NodeName 속성에 정의된 특정 개수(NodeCount 속성으로 정의)의 대상 노드에서 지정된 리소스가 원하는 상태가 될 때까지 대기합니다.

이러한 리소스는 WS-Man 프로토콜을 통한 CIM 연결을 사용하여 노드 간 동기화를 제공합니다. 이러한 리소스를 사용하여 구성은 자체 구성을 계속하기 전에 다른 컴퓨터의 특정 리소스 상태가 변경될 때까지 대기할 수 있습니다. 

예를 들어 다음 구성에서 대상 노드는 도메인에 가입하기 전에 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">xADDomain</ctype="x-NOTFOUND"> 리소스가 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">MyDC</ctype="x-NOTFOUND"> 노드에서 몇 번의 다시 시도를 완료할 때까지 대기합니다.

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

    WaitForAll DC
    {
        ResourceName      = '[xADDomain]NewDomain'
        NodeName          = 'MyDC'
        RetryIntervalSec  = 15
        RetryCount        = 30
    }

    xComputer JoinDomain
    {
        Name             = 'MyPC'
        DomainName       = 'Contoso.com'
        Credential       = (get-credential)
        DependsOn        ='[WaitForAll]DC'
    }
}
```
<ctype="x-NOTFOUND" mdpre="**" mdpost="**">힌트:</ctype="x-NOTFOUND"> 기본적으로 WaitFor\* 리소스는 한 번 시도한 다음 실패하므로 필수는 아니지만, 일반적으로 다시 시도 간격 및 횟수를 지정합니다.


<!--HONumber=Mar16_HO3-->


