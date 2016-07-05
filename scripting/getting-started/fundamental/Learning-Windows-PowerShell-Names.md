---
title: "Windows PowerShell 이름 학습"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: bc504fbde14d0ba743accf644ee5114810afb609

---

# Windows PowerShell 이름 학습
명령 및 명령 매개 변수의 이름을 학습하려면 대부분의 명령줄 인터페이스에서 상당한 시간이 소요됩니다. 문제는 패턴이 거의 없으므로 정기적으로 사용해야 하는 각 명령과 각 매개 변수를 기억하는 것이 유일한 학습 방법이라는 점입니다.

새 명령이나 매개 변수로 작업하는 경우 일반적으로 이미 알고 있는 사항을 사용할 수 없으므로 새 이름을 찾아서 학습해야 합니다. 인터페이스가 작은 도구 집합에서 점점 기능을 추가하는 방식을 살펴보면 표준 구조가 아닌 이유를 쉽게 알 수 있습니다. 특히 명령 이름의 경우 각 명령이 개별 도구이므로 논리적인 것 같지만 명령 이름을 처리하는 더 나은 방법이 있습니다.

대부분의 명령은 서비스나 프로세스와 같은 운영 체제 또는 응용 프로그램의 요소를 관리하도록 작성되었습니다. 명령에는 패밀리에 맞거나 맞지 않을 수 있는 다양한 이름이 있습니다. 예를 들어 Windows 시스템에서는 **net start** 및 **net stop** 명령을 사용하여 서비스를 시작하고 중지할 수 있습니다. **net** 서비스 명령의 명명 패턴에 맞지 않는 **sc**라는 완전히 다른 이름을 가진 보다 일반화된 다른 Windows용 서비스 제어 도구도 있습니다. 프로세스 관리의 경우 Windows에는 프로세스를 표시하는 **tasklist** 명령과 프로세스를 중단하는 **taskkill** 명령이 있습니다.

매개 변수를 사용하는 명령에는 불규칙한 매개 변수 사양이 있습니다. **net start** 명령을 사용하여 원격 컴퓨터에서 서비스를 시작할 수는 없습니다. **sc** 명령은 원격 컴퓨터에서 서비스를 시작하지만 원격 컴퓨터를 지정하기 위해 해당 이름 앞에 이중 백슬래시를 추가해야 합니다. 예를 들어 DC01이라는 원격 컴퓨터에서 스풀러 서비스를 시작하려면 **sc \\\\DC01 start spooler**를 입력합니다. DC01에서 실행 중인 작업을 표시하려면 다음과 같이 **\/S**("system") 매개 변수를 사용하고 백슬래시 없이 DC01 이름을 입력해야 합니다. **tasklist \/S DC01**.

서비스와 프로세스 간에는 중요한 기술적 차이가 있지만 둘 다 잘 정의된 수명 주기를 가진 컴퓨터 관리 가능 요소의 예입니다. 서비스나 프로세스를 시작 또는 중지하거나, 현재 실행 중인 모든 서비스나 프로세스의 목록을 가져올 수 있습니다. 즉, 서비스와 프로세스는 서로 다르지만 서비스나 프로세스에서 수행하는 작업은 개념적으로 동일한 경우가 많습니다. 또한 매개 변수를 지정하여 작업을 사용자 지정하기 위해 선택할 수 있는 사항도 개념적으로 유사할 수 있습니다.

Windows PowerShell은 이러한 유사성을 이용하여 cmdlet을 이해하고 사용하기 위해 알아야 하는 고유 이름 수를 줄입니다.

### 쉽게 기억할 수 있는 Cmdlet에 동사\-명사 이름 사용
Windows PowerShell은 각 cmdlet 이름이 표준 동사와 특정 명사를 하이픈으로 연결하여 구성되는 "동사\-명사" 명명 시스템을 사용합니다. Windows PowerShell 동사는 영어 동사가 아닐 수도 있지만 Windows PowerShell에서 특정 작업을 나타냅니다. 명사는 모든 언어의 명사와 매우 비슷하며, 시스템 관리에서 중요한 특정 유형의 개체를 설명합니다. 동사와 명사의 몇 가지 예를 살펴보면 두 부분으로 이루어진 이러한 이름이 학습에 어떻게 도움이 되는지를 쉽게 확인할 수 있습니다.

명사는 덜 제한적이지만 항상 명령의 실행 대상을 나타내야 합니다. Windows PowerShell에는 **Get\-Process**, **Stop\-Process**, **Get\-Service**, **Stop\-Service** 등의 명령이 있습니다.

명사 2개와 동사 2개를 사용하는 경우 일관성을 유지해도 학습이 크게 간소화되지 않습니다. 그러나 동사 10개와 명사 10개의 표준 집합을 살펴보면 20개의 단어만 이해해도 해당 단어를 사용하여 100개의 고유한 명령 이름을 구성할 수 있습니다.

이름을 통해 명령이 수행하는 작업을 인식할 수 있는 경우가 많으며, 일반적으로 새 명령에 어떤 이름을 사용해야 하는지가 명확합니다. 예를 들어 컴퓨터 종료 명령은 **Stop\-Computer**일 수 있습니다. 네트워크에 있는 모든 컴퓨터를 표시하는 명령은 **Get\-Computer**일 수 있습니다. 시스템 날짜를 가져오는 명령은 **Get\-Date**입니다.

**Get\-Command**의 **\-Verb** 매개 변수를 사용하여 특정 동사를 포함하는 모든 명령을 표시할 수 있습니다. **Get\-Command**는 다음 섹션에서 자세히 설명하겠습니다. 예를 들어 **Get** 동사를 사용하는 모든 cmdlet을 보려면 다음과 같이 입력합니다.

```
PS> Get-Command -Verb Get
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

**\-Noun** 매개 변수는 동일한 유형의 개체에 영향을 주는 명령 패밀리를 표시하므로 훨씬 더 유용합니다. 예를 들어 서비스 관리에 사용할 수 있는 명령을 보려는 경우 다음 명령을 입력합니다.

```
PS> Get-Command -Noun Service
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str... 
...
```

명령이 동사\-명사 명명 체계를 사용한다고 해서 반드시 cmdlet은 아닙니다. cmdlet은 아니지만 동사\-명사 이름을 가진 네이티브 Windows PowerShell 명령의 한 예로 콘솔 창을 지우는 명령인 Clear\-Host가 있습니다. 다음과 같이 Get\-Command를 실행하면 알 수 있듯이 Clear\-Host 명령은 실제로 내부 함수입니다.

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### 표준 매개 변수 사용
앞에서 설명한 대로 기존 명령줄 인터페이스에서 사용되는 명령에는 일반적으로 일관된 매개 변수 이름이 없습니다. 매개 변수에 이름이 없는 경우도 있습니다. 이름이 있어도 단일 문자나 약어로 되어 있어 신속하게 입력할 수는 있지만 새로운 사용자가 쉽게 이해하기 힘듭니다.

대부분의 다른 기존 명령줄 인터페이스와 달리 Windows PowerShell은 매개 변수를 직접 처리하며, 매개 변수에 대한 이러한 직접 액세스와 함께 개발자 지침을 사용하여 매개 변수 이름을 표준화합니다. 이렇게 해도 모든 cmdlet이 항상 표준 이름을 사용하는 것은 아니지만 표준화를 촉진합니다.

> [!NOTE]
> 매개 변수 이름을 사용할 때는 항상 '\-'이 앞에 추가되므로 Windows PowerShell이 명확하게 매개 변수로 식별할 수 있습니다. **Get\-Command \-Name Clear\-Host** 예제에서 매개 변수 이름은 **Name**이지만 \-**Name**으로 입력됩니다.

다음은 표준 매개 변수 이름 및 사용법의 몇 가지 일반적인 특성입니다.

#### 도움말 매개 변수(?)
**\-?** 매개 변수를 cmdlet에 지정하면 cmdlet이 실행되는 대신 cmdlet에 대한 도움말이 표시됩니다.

#### 일반 매개 변수
Windows PowerShell에는 *일반 매개 변수*라고 알려진 여러 매개 변수가 있습니다. 이러한 매개 변수는 Windows PowerShell 엔진에 의해 제어되므로 cmdlet에서 구현할 때마다 항상 동일한 방식으로 동작합니다. 일반 매개 변수로는 **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** 및 **OutBuffer**가 있습니다.

#### 권장 매개 변수
Windows PowerShell 핵심 cmdlet은 유사한 매개 변수에 표준 이름을 사용합니다. 매개 변수 이름을 반드시 사용해야 하는 것은 아니지만 Windows PowerShell에는 표준 이름 사용을 권장하는 명시적 지침이 있습니다.

예를 들어 이 지침에서는 Server, Host, System, Node 또는 기타 일반적인 대체 단어가 아니라 **ComputerName**과 같이 컴퓨터를 이름으로 참조하는 매개 변수 이름을 권장합니다. 이러한 권장 매개 변수 이름으로는 **Force**, **Exclude**, **Include**, **PassThru**, **Path** 및 **CaseSensitive**가 있습니다.




<!--HONumber=Jun16_HO4-->


