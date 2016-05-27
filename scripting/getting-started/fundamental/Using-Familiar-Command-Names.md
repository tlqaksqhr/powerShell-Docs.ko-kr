---
title:  친숙한 명령 이름 사용
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  021e2424-c64e-4fa5-aa98-aa6405758d5d
---

# 친숙한 명령 이름 사용
Windows PowerShell에서는 *별칭*이라고 하는 메커니즘을 사용하여 대체 이름으로 명령을 나타낼 수 있습니다. 별칭은 다른 셸을 사용해 본 경험이 있는 사용자가 이미 알고 있는 일반적인 명령 이름을 다시 사용하여 Windows PowerShell에서 유사한 작업을 수행할 수 있도록 해줍니다. 따라서 이 설명서에서 Windows PowerShell 별칭을 자세히 설명하지 않지만 Windows PowerShell 시작부터 이러한 별칭을 사용할 수 있습니다.

별칭은 사용자가 입력하는 명령 이름을 다른 명령과 연결합니다. 예를 들어 Windows PowerShell에는 출력 창을 지우는 **Clear\-Host**라는 내부 함수가 있습니다. 명령 프롬프트에서 **cls** 또는 **clear** 명령을 입력하면 Windows PowerShell은 이러한 명령을 **Clear\-Host** 함수의 별칭으로 해석하고 **Clear\-Host** 함수를 실행합니다.

이 기능은 사용자가 Windows PowerShell을 익히는 데 도움이 됩니다. 첫째, 대부분의 Cmd.exe 및 UNIX 사용자는 많은 명령의 이름을 이미 알고 있기 때문에, Windows PowerShell에서 이러한 명령이 동일한 결과를 나타내지는 않더라도 그 형태가 유사하여 따로 이름을 외우지 않아도 Windows PowerShell 명령을 사용하여 작업을 수행할 수 있습니다. 둘째, 다른 셸에 이미 익숙한 사용자가 새 셸을 익히는 데 있어서 가장 어려운 점은 손에 익은 습관 때문에 발생하는 실수입니다. 예를 들어 Cmd.exe를 몇 년 동안 사용한 사용자의 경우 화면에 표시된 출력 내용을 모두 지우고자 할 때 반사적으로 **cls** 명령을 입력한 다음 Enter 키를 누를 수 있습니다. Windows PowerShell에 **Clear\-Host** 함수에 대한 별칭이 없다면 "**'cls' is not recognized as a cmdlet, function, operable program, or script file.**"이라는 오류 메시지만 표시되고, 출력 내용을 어떻게 지울 수 있는지에 대한 어떠한 정보도 표시되지 않습니다.

다음은 Windows PowerShell에서 사용할 수 있는 일반적인 Cmd.exe 및 UNIX 명령에 대한 간단한 목록입니다.

|||||
|-|-|-|-|
|cat|dir|탑재|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|형식|
|del|lp|r|write|
|diff|ls|ren||

사용자 자신이 이러한 명령 중 하나를 반사적으로 사용하고 있음을 알아채고 기본 Windows PowerShell 명령의 실제 이름을 확인하려면 다음과 같이 **Get\-Alias** 명령을 사용하면 됩니다.

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

일반적으로 이 Windows PowerShell 사용자 가이드에서는 읽기 쉽도록 예제에 별칭을 사용하지 않습니다. 그러나 별칭을 많이 알고 있으면 다른 곳에서 가져온 임의의 Windows PowerShell 코드 조각을 사용하여 작업하는 경우나 사용자 고유의 별칭을 정의하려는 경우 유용할 수 있습니다. 이 섹션의 나머지 부분에서는 표준 별칭과 사용자 고유의 별칭을 정의하는 방법을 설명합니다.

### 표준 별칭 해석
위에서 설명한 별칭은 다른 인터페이스와의 이름 호환성을 위해 개발된 반면 Windows PowerShell에 기본 제공된 별칭은 주로 명령 이름을 간략하게 표현하기 위해 개발되었습니다. 이러한 약식 이름은 빨리 입력할 수는 있지만 참조 대상을 모르면 해석할 수 없습니다.

Windows PowerShell에서는 일반적인 동사와 명사에 대한 약식 이름을 기반으로 하는 일련의 표준 별칭을 제공하여 명확하면서도 간결한 별칭을 만들기 때문에 약식 이름만 알면 해석할 수 있는 일반적인 cmdlet에 대한 핵심 별칭 집합을 사용할 수 있습니다. 예를 들어 표준 별칭에서 동사 **Get**은 **g**로, 동사 **Set**은 **s**로, 명사 **Item**은 **i**로, 명사 **Location**은 **l**로, 명사 Command는 **cm**으로 축약됩니다.

다음은 이러한 방식으로 별칭을 만드는 방법을 보여 주는 간단한 예입니다. Get\-Item의 표준 별칭은 Get을 나타내는 **g**와 Item을 나타내는 **i**를 결합한 **gi**입니다. Set\-Item의 표준 별칭은 Set을 나타내는 **s**와 Item을 나타내는 **i**를 결합한 **si**입니다. Get\-Location의 표준 별칭은 Get을 나타내는 **g**와 Location을 나타내는 **l**을 결합한 **gl**입니다. Set\-Location의 표준 별칭은 Set을 나타내는 **s**와 Location을 나타내는 **l**을 결합한 **sl**입니다. Get\-Command의 표준 별칭은 Get을 나타내는 **g**와 Command를 나타내는 **cm**을 결합한 **gcm**입니다. Set\-Command cmdlet은 실제로 없지만 있다고 가정할 경우 표준 별칭은 Set을 나타내는 **s**와 Command를 나타내는 **cm**을 결합한 **scm**입니다. 또한 Windows PowerShell 별칭에 익숙한 사용자는 **scm**을 보면 이 별칭이 Set\-Command를 나타낸다는 것을 짐작할 수 있습니다.

### 새 별칭 만들기
Set\-Alias cmdlet을 사용하여 사용자 고유의 별칭을 만들 수 있습니다. 예를 들어 다음 문은 표준 별칭 해석에서 설명한 표준 cmdlet 별칭을 만듭니다.

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

내부적으로 Windows PowerShell은 시작할 때 이와 같은 명령을 사용하지만 이러한 별칭은 변경할 수 없습니다. 실제로 이러한 명령 중 하나를 실행하려고 하면 다음과 같이 별칭을 수정할 수 없다는 오류 메시지가 나타납니다. 예:

<pre>PS> Set-Alias -Name gi -Value Get-Item Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10 + Set-Alias  <<<< -Name gi -Value Get-Item</pre>



<!--HONumber=May16_HO2-->


