---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "JEA 사용"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 3bac5932c3ed57713bdb08e3a9ed435b228518bc

---

# JEA 사용
이 섹션에서는 최종 사용자의 *JEA 사용* 경험을 이해하는 데 중점을 둡니다.
필수 조건 섹션에서 데모 JEA 끝점을 만들었습니다.
여기에서는 이 데모를 사용하여 JEA의 작동을 보여 줄 것입니다.
이후 섹션에서는 이 과정을 거꾸로 살펴보면서 최종 사용자 경험을 가능하게 한 작업과 파일을 소개합니다.

## 관리자가 아닌 사용자로 JEA 사용
JEA의 작동을 보여 주기 위해 관리자가 아닌 사용자인 것처럼 PowerShell 원격을 사용해야 합니다.
새 PowerShell 창에서 다음 명령을 실행합니다.   

```PowerShell
$NonAdminCred = Get-Credential
```

메시지가 표시되면 관리자가 아닌 계정에 대한 자격 증명을 입력합니다.
[사용자 및 그룹 설정](creating-a-domain-controller.md#set-up-users-and-groups) 섹션을 따른 경우 자격 증명은 다음과 같습니다.
-   사용자 이름 = "OperatorUser"
-   암호 = "pa$$w0rd"

다음 명령을 실행하여 제공한 자격 증명을 사용해 데모 끝점에 연결합니다.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

이제 로컬 컴퓨터에서 대화형 원격 PowerShell 세션에 들어갔습니다.
"Credential" 매개 변수를 사용하여 OperatorUser(또는 사용한 계정)*인 것처럼* 연결했습니다.
프롬프트에서 `[localhost]: PS>`로 변경된 것은 원격 세션을 대상으로 작업하고 있음을 나타냅니다.  

원격 명령 프롬프트에서 다음을 실행하여 사용할 수 있는 명령을 표시합니다.

```PowerShell
Get-Command
```

표시되는 명령은 일반적인 PowerShell 창에서 사용할 수 있는 명령(흔히 몇천 개의 명령이 포함될 수 있음)의 매우 제한된 하위 집합입니다.
특히 7가지 기본 JEA cmdlet(Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default, Select-Object)과 유지 관리 역할 기능 파일에 명시적으로 포함된 두 명령만 표시됩니다.

다음으로, 유지 관리 역할 기능 파일에 포함된 사용자 지정 함수를 호출하여 이 세션이 작동하고 있는 사용자 컨텍스트를 살펴보겠습니다.

```PowerShell
Get-UserInfo
```

이 함수의 출력에서는 "ConnectedUser"뿐만 아니라 "RunAsUser"가 표시됩니다.
연결된 사용자는 원격 세션에 연결한 계정(예: 사용자의 계정)입니다.
연결된 사용자에게는 관리자 권한이 없어도 됩니다.
"실행" 계정은 권한 있는 작업을 실제로 수행하는 계정입니다.
한 사용자로 연결하고 다른 권한 있는 사용자로 실행하면 관리 권한을 제공하지 않고도 권한 없는 사용자가 특정 관리 작업을 수행하도록 허용할 수 있습니다.

이를 보여 주기 위해 다음 명령을 실행합니다.

```PowerShell
Restart-Service -Name Spooler -Verbose
```

일반적으로 Restart-Service를 실행하려면 관리자 권한이 필요합니다.
그러나 JEA 가상 계정이 있으면 권한 없는 자격 증명을 사용하여 실행할 수 있습니다.

따라서 JEA는 이미 사용하는 명령을 이용하여 작업을 수행할 수 있도록 합니다.
하지만 사용하도록 허용되지 *않아야 하는* 명령의 경우는 어떨까요?
JEA 세션에서 `Restart-Computer` 등의 다른 명령을 실행해 보면 JEA에서 그러한 명령이 실행되지 못하게 하는 것을 확인할 수 있습니다.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

마지막으로, 제한된 JEA 끝점에서 나오려면 다음 명령을 실행합니다.

```PowerShell
Exit-PSSession
```

이렇게 하면 원격 PowerShell 세션에서 연결이 끊어집니다.




<!--HONumber=Jun16_HO4-->


