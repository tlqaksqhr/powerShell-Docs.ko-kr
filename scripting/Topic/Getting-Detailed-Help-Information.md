---
title: 자세한 도움말 정보 보기
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
---
# 자세한 도움말 정보 보기
Windows PowerShell에는 Windows PowerShell 개념과 Windows PowerShell 언어를 설명하는 자세한 도움말 항목이 포함되어 있습니다. 각 cmdlet 및 공급자에 대한 도움말 항목과 많은 함수 및 스크립트에 대한 도움말 항목도 있습니다.

명령 프롬프트에서 이러한 도움말 항목을 표시하거나 Microsoft TechNet 라이브러리에서 이러한 항목의 가장 최근에 업데이트된 버전을 볼 수 있습니다. Windows PowerShell 통합 스크립팅 환경 등 Windows PowerShell을 호스트하는 대부분의 프로그램은 상황에 맞는 도움말, 컴파일된 도움말 파일(.chm) 등의 추가 도움말 기능을 제공합니다.

## Cmdlet에 대한 도움말 보기
Windows PowerShell cmdlet에 대한 도움말을 보려면 [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet을 사용합니다. 예를 들어 [Get-Childitem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet에 대한 도움말을 보려면 다음과 같이 입력합니다.

```
get-help get-childitem
```

또는

```
get-childitem -?
```

Get\-Help cmdlet에 대한 도움말을 볼 수도 있습니다. 예:

```
get-help get-help
```

세션에 있는 모든 cmdlet 도움말 항목의 목록을 보려면 다음과 같이 입력합니다.

```
get-help -category cmdlet
```

각 도움말 항목을 한 번에 한 페이지씩 표시하려면 **help** 함수 또는 해당 별칭 **man**을 사용합니다. 예를 들어 Get\-ChildItem cmdlet에 대한 도움말을 표시하려면 다음과 같이 입력합니다.

```
man get-childitem
```

또는

```
help get-childitem
```

해당 매개 변수 및 사용 예제에 대한 설명을 포함하여 cmdlet, 함수 또는 스크립트에 대한 자세한 정보를 표시하려면 Get\-Help cmdlet의 *Detailed* 매개 변수를 사용합니다. 예를 들어 Get\-ChildItem cmdlet에 대한 자세한 정보를 보려면 다음과 같이 입력합니다.

```
get-help get-childitem -detailed
```

도움말 항목의 모든 내용을 표시하려면 Get\-Help cmdlet의 *Full* 매개 변수를 사용합니다. 예를 들어 Get\-ChildItem cmdlet에 대한 도움말 항목의 모든 내용을 표시하려면 다음과 같이 입력합니다.

```
get-help get-childitem -full
```

cmdlet의 매개 변수에 대한 자세한 도움말을 보려면 Get\-Help cmdlet의 *Parameter* 매개 변수를 사용합니다. 예를 들어 Get\-ChildItem cmdlet의 모든 매개 변수에 대한 자세한 도움말을 보려면 다음과 같이 입력합니다.

```
get-help get-childitem -parameter *
```

도움말 항목의 예제만 표시하려면 Get\-Help의 *Example* 매개 변수를 사용합니다. 예를 들어 Get\-ChildItem cmdlet에 대한 도움말 항목의 예제만 표시하려면 다음과 같이 입력합니다.

```
get-help get-childitem -examples
```

작성하는 cmdlet의 도움말 항목을 작성하는 방법에 대한 자세한 내용은 MSDN에서 "Cmdlet 도움말 작성 방법" 항목을 참조하세요.

## 개념 도움말 보기
Get\-Help cmdlet은 Windows PowerShell 언어에 대한 항목을 포함하여 Windows PowerShell의 개념 항목에 대한 정보도 표시합니다. 개념 도움말 항목은 "about\_" 접두사로 시작합니다(예: about\_line\_editing). 개념 항목의 이름은 영어가 아닌 Windows PowerShell 버전에서도 영어로 입력해야 합니다.

개념 항목 목록을 표시하려면 다음과 같이 입력합니다.

```
get-help about_*
```

특정 도움말 항목을 표시하려면 다음과 같이 항목 이름을 입력합니다.

```
get-help about_command_syntax
```

*Detailed*, *Parameter* 및 *Examples*와 같은 Get\-Help의 매개 변수는 개념 도움말 항목의 표시에 영향을 주지 않습니다.

## 공급자에 대한 도움말 보기
Get\-Help cmdlet은 Windows PowerShell 공급자에 대한 정보를 표시합니다. 공급자에 대한 도움말을 보려면 "Get\-Help"를 입력한 다음 공급자 이름을 입력합니다. 예를 들어 레지스트리 공급자에 대한 도움말을 보려면 다음과 같이 입력합니다.

```
get-help registry
```

세션에 있는 모든 공급자 도움말 항목의 목록을 보려면 다음과 같이 입력합니다.

```
get-help -category provider
```

*Detailed*, *Parameter* 및 *Examples*와 같은 Get\-Help의 매개 변수는 공급자 도움말 항목의 표시에 영향을 주지 않습니다.

## 스크립트 및 함수에 대한 도움말 보기
Windows PowerShell의 많은 스크립트 및 함수에는 도움말 항목이 있습니다. Get\-Help cmdlet을 사용하여 스크립트 및 함수에 대한 도움말 항목을 표시할 수 있습니다.

함수에 대한 도움말을 표시하려면 "get\-help"를 입력한 다음 함수 이름을 입력합니다. 예를 들어 Disable\-PSRemoting 함수에 대한 도움말을 보려면 다음과 같이 입력합니다.

```
get-help disable-psremoting
```

스크립트에 대한 도움말을 표시하려면 스크립트 파일의 정규화된 경로를 입력합니다. 스크립트가 Path 환경 변수에 표시된 경로에 있으면 명령에서 경로를 생략할 수 있습니다.

예를 들어 C:\\PS\-Test 디렉터리에 "TestScript.ps1"이라는 스크립트가 있는 경우 이 스크립트의 도움말 항목을 표시하려면 다음과 같이 입력합니다.

```
get-help c:\ps-test\TestScript.ps1
```

*Detailed*, *Full*, *Examples* 및 *Parameter*와 같이 cmdlet 도움말을 표시하도록 설계된 매개 변수는 스크립트 도움말 및 함수 도움말에서도 사용됩니다. 그러나 "get\-help \*"를 입력하여 모든 도움말을 표시할 때는 함수 및 스크립트에 대한 도움말이 나타나지 않습니다.

함수 및 스크립트에 대한 도움말 항목을 작성하는 방법에 대한 자세한 내용은 [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) 및 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)를 참조하세요.

## 온라인 도움말 보기
인터넷에 연결된 경우에는 온라인에서 도움말 항목을 보는 것이 가장 좋은 방법 중 하나입니다. 온라인 항목은 업데이트하기 쉽기 때문에 최신 내용이 제공될 가능성이 높습니다.

온라인 도움말을 보려면 Get\-Help cmdlet의 *Online* 매개 변수를 사용합니다. Get\-Help cmdlet의 *Online* 매개 변수는 cmdlet 도움말, 함수 도움말 및 스크립트 도움말에서만 사용할 수 있습니다. 개념(About) 항목이나 공급자 도움말 항목에서는 *Online* 매개 변수를 사용할 수 없습니다. 또한 이 기능은 선택 항목이기 때문에 일부 cmdlet, 함수 또는 스크립트 도움말 항목에서는 작동하지 않습니다.

그러나 공급자 도움말 및 개념(About) 도움말 항목을 포함하여 Windows PowerShell과 함께 제공되는 모든 도움말 항목은 Microsoft TechNet 라이브러리의 [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) 섹션에서 온라인으로 볼 수 있습니다.

Get\-Help cmdlet의 *Online* 매개 변수를 사용하려면 다음 명령 형식을 사용합니다.

```
get-help <command-name> -online
```

예를 들어 Get\-ChildItem cmdlet에 대한 온라인 버전의 도움말 항목을 보려면 다음과 같이 입력합니다.

```
get-help get-childitem -online
```

온라인 버전의 도움말 항목이 있는 경우 기본 브라우저에서 열립니다.

도움말 항목에 대해 온라인 도움말이 지원되는 경우 도움말 항목의 인터넷 주소(URL)도 볼 수 있습니다. 인터넷 주소는 도움말 항목의 관련 링크 섹션에 나타납니다.

예를 들어 Add\-Computer cmdlet의 온라인 버전에 대한 URL을 보려면 다음과 같이 입력합니다.

```
get-help add-computer
```

항목의 관련 링크 섹션에 있는 첫 번째 줄은 아래와 같이 표시됩니다.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

도움말 항목의 온라인 지원을 제공하는 방법에 대한 자세한 내용은 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)와 MSDN(Microsoft Developer Network) 라이브러리의 "How to Write Cmdlet Help(Cmdlet 도움말 작성 방법)"([http://go.microsoft.com/fwlink/?LinkID=123415](http://go.microsoft.com/fwlink/?LinkID=123415))를 참조하세요.

## 참고 항목
[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
[about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
[about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)



<!--HONumber=Apr16_HO2-->


