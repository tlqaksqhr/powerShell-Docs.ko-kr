---
title:   노드 간 종속성 지정
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 노드 간 종속성 지정

> 적용 대상: Windows PowerShell 5.0

DSC는 다른 노드에서 구성에 대한 종속성을 지정하기 위한 구성에 사용할 수 있는 특별한 리소스 **WaitForAll**, **WaitForAny** 및 **WaitForSome**을 제공합니다. 이러한 리소스의 동작은 다음과 같습니다.

* **WaitForAll**: **NodeName** 속성에 정의된 모든 대상 노드에서 지정된 리소스가 원하는 상태이면 성공합니다.
* **WaitForAny**: **NodeName** 속성에 정의된 대상 노드 중 최소 하나 이상에서 지정된 리소스가 원하는 상태이면 성공합니다.
* **WaitForSome**: **NodeName** 속성과 더불어 **NodeCount** 속성을 지정합니다. **NodeCount**에서 지정되고 **NodeName** 속성에서 정의된 최소 숫자의 노드에서 리소스가 원하는 상태이면 리소스가 성공합니다. 

## WaitForXXXX 리소스 사용

**WaitForXXXX** 리소스를 사용하려면 해당 리소스 유형의 리소스 블록을 만들어 대기할 노드 및 DSC 리소스를 지정해야 합니다. 그런 다음 구성의 다른 리소스 블록에 있는 **DependsOn** 속성을 사용하여 **WaitForXXXX** 노드에 정의된 조건이 성공할 때까지 대기할 수 있습니다.

예를 들어 다음 구성에서 대상 노드는 대상 노드가 도메인에 가입하기 전에 **xADDomain** 리소스가 **MyDC** 노드에서 최대 30번의 시도를 15초 간격으로 완료할 때까지 대기합니다.

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

    Node myDomainJoinedServer
    {

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
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**참고:** 기본적으로 WaitForXXX 리소스는 한 번 시도한 후에 실패합니다. 필수는 아니지만, 일반적으로 다시 시도 간격 및 횟수를 지정합니다.

## 참고 항목
* [DSC 구성](configurations.md)
* [DSC 리소스](resources.md)
* [로컬 구성 관리자 구성](metaConfig.md)



<!--HONumber=Jun16_HO3-->


