---
title: 명령에 대한 정보 가져오기
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
---
# 명령에 대한 정보 가져오기
Windows PowerShell **Get\-Command** cmdlet은 현재 세션에서 사용할 수 있는 모든 명령을 가져옵니다. Windows PowerShell 프롬프트에 **Get\-Command**를 입력할 경우 다음과 비슷한 출력이 표시됩니다.

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

이 출력은 내부 명령을 표 형식으로 요약하는 Cmd.exe의 도움말 출력과 흡사합니다. 위에 표시된 **Get\-Command** 명령 출력의 발췌 부분에서 표시되는 모든 명령의 CommandType은 Cmdlet입니다. cmdlet은 Windows PowerShell의 고유한 명령 유형으로, Cmd.exe의 **dir** 및 **cd** 명령과 거의 일치하고 UNIX 셸(예: BASH)에 기본 제공되는 유형입니다.

**Get\-Command** 명령의 출력에서는 모든 정의를 줄임표(...)로 끝내서 PowerShell에서 사용 가능한 공간에 내용을 모두 표시할 수 없음을 나타냅니다. Windows PowerShell에서는 출력을 표시할 때 출력 형식을 텍스트로 지정한 다음 데이터가 창에 맞도록 정렬합니다. 이에 대해서는 나중에 포맷터 섹션에서 설명하겠습니다.

**Get\-Command** cmdlet에는 각 cmdlet의 구문을 가져오는 **Syntax** 매개 변수가 있습니다. Get\-Help cmdlet의 구문을 가져오려면 다음 명령을 사용합니다.

**Get\-Command Get\-Help \-Syntax**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### 사용 가능한 명령 유형 표시
**Get\-Command** 명령은 Windows PowerShell에서 사용할 수 있는 명령을 모두 표시하지 않습니다. 대신 **Get\-Command** 명령은 현재 세션에 있는 cmdlet만 표시합니다. Windows PowerShell에서는 실제로 다양한 유형의 명령을 지원합니다. 별칭, 함수, 스크립트 등은 Windows PowerShell 사용자 가이드에서 자세히 설명하지 않지만 Windows PowerShell 명령입니다. 실행할 수 있거나 등록된 파일 형식 처리기가 있는 외부 파일도 명령으로 분류됩니다.

세션의 모든 명령을 가져오려면 다음과 같이 입력하세요.

```
Get-Command *
```

이 목록에는 검색 경로에 있는 외부 파일이 포함되므로 수천 개의 항목이 포함될 수 있습니다. 찾을 명령의 수를 줄이는 것이 좋습니다.

다른 형식의 네이티브 명령을 가져오려면 **Get\-Command** cmdlet의 **CommandType** 매개 변수를 사용합니다.

> [!NOTE]
> 별표(\*)는 Windows PowerShell 명령 인수에서 와일드카드 일치에 사용됩니다. \*는 "하나 이상의 문자 일치"를 의미합니다. 문자 "a"로 시작하는 모든 명령을 찾으려면 **Get\-Command a\&#42;**를 입력할 수 있습니다. Cmd.exe의 와일드카드 일치와 달리 Windows PowerShell의 와일드카드는 점(.)도 일치시킵니다.

명령에 할당된 애칭인 명령 별칭을 가져오려면 다음과 같이 입력하세요.

```
Get-Command -CommandType Alias
```

현재 세션의 함수를 가져오려면 다음과 같이 입력하세요.

```
Get-Command -CommandType Function
```

Windows PowerShell의 검색 경로에 스크립트를 표시하려면 다음과 같이 입력하세요.

```
Get-Command -CommandType Script
```



<!--HONumber=Apr16_HO1-->


