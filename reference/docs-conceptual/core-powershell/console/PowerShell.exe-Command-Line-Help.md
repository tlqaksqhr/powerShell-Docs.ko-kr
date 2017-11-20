---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShell.exe 명령줄 도움말"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 262c21e44e509746314ed44d91bb3de16a4b854b
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2017
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe 명령줄 도움말
Windows PowerShell 세션. PowerShell.exe를 사용하여 Cmd.exe와 같은 다른 도구의 명령줄에서 PowerShell 세션을 시작하거나, PowerShell 명령줄에서 사용하여 새 세션을 시작할 수 있습니다. 매개 변수를 사용하여 세션을 사용자 지정합니다.

## <a name="syntax"></a>구문

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
        

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>매개 변수

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>
명령의 Base 64로 인코드된 문자열 버전을 허용합니다. 이 매개 변수를 사용하여 명령을 큰따옴표 또는 중괄호가 필요한 PowerShell로 전송합니다.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>
현재 세션에 대한 기본 실행 정책을 설정하고 $env:PSExecutionPolicyPreference 환경 변수에 저장합니다. 이 매개 변수는 레지스트리에 설정된 PowerShell 실행 정책을 변경하지는 않습니다. 유효한 값 목록을 비롯한 PowerShell 실행 정책에 대한 자세한 내용은 about_Execution_Policies(http://go.microsoft.com/fwlink/?LinkID=135170)를 참조하세요.

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]
스크립트에서 만드는 함수와 변수를 현재 세션에서 사용할 수 있도록 지정한 스크립트를 로컬 범위("dot-sourced")에서 실행합니다. 스크립트 파일의 경로와 매개 변수를 입력합니다. **File** 매개 변수 이름 뒤에 입력한 모든 문자는 차례로 스크립트 파일 경로, 스크립트 매개 변수 및 해당 값으로 해석되기 때문에 **File**은 명령의 마지막 매개 변수여야 합니다.

**File** 매개 변수의 값에 스크립트 매개 변수 및 매개 변수 값을 포함할 수 있습니다. 예: `-File .\Get-Script.ps1 -Domain Central` 스크립트에 전달되는 매개 변수는 리터럴 문자열로 전달됩니다(현재 셸에서 해석한 후).
예를 들어 cmd.exe에 있고 환경 변수 값을 전달하려는 경우 cmd.exe 구문 `powershell -File .\test.ps1 -Sample %windir%`를 사용합니다. PowerShell 구문을 사용한다면 이 예에서 스크립트는 해당 환경 변수 `powershell -File .\test.ps1 -Sample $env:windir` 값이 아니라 리터럴 “$env:windir”을 받게 됩니다.

일반적으로 스크립트의 스위치 매개 변수는 포함되거나 생략됩니다. 예를 들어 다음 명령은 Get-Script.ps1 스크립트 파일의 **All** 매개 변수를 사용합니다.`-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}
PowerShell로 전송되는 데이터 형식을 설명합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

### <a name="-mta"></a>-Mta
다중 스레드 아파트를 사용하여 PowerShell을 시작합니다. 이 매개 변수는 PowerShell 3.0에서 도입되었습니다. PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다. PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다.

### <a name="-noexit"></a>-NoExit
시작 명령을 실행한 후 종료하지 않습니다.

### <a name="-nologo"></a>-NoLogo
시작 시 저작권 배너를 숨깁니다.

### <a name="-noninteractive"></a>-NonInteractive
사용자에게 대화형 프롬프트를 표시하지 않습니다.

### <a name="-noprofile"></a>-NoProfile
PowerShell 프로필을 로드하지 않습니다.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}
PowerShell의 출력 형식을 결정합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>
지정된 PowerShell 콘솔 파일을 로드합니다. 콘솔 파일의 경로와 이름을 입력합니다. 콘솔 파일을 만들려면 PowerShell에서 [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet을 사용합니다.

### <a name="-sta"></a>-Sta
단일 스레드 아파트를 사용하여 PowerShell을 시작합니다. PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다. PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다.

### <a name="-version-powershell-version"></a>버전 <PowerShell Version>
지정된 버전의 PowerShell을 시작합니다. 지정한 버전이 시스템에 설치되어 있어야 합니다. 컴퓨터에 PowerShell 3.0이 설치되어 있는 경우 유효한 값은 "2.0"과 "3.0"입니다. 기본값은 "3.0"입니다.

PowerShell 3.0이 설치되지 않은 경우 유효한 값은 "2.0"뿐입니다. 다른 값은 무시됩니다.

자세한 내용은 [PowerShell 시작 [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd)에서 "PowerShell 설치"를 참조하세요.

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>
세션에 대한 창 스타일을 설정합니다. 유효한 값은 Normal, Minimized, Maximized 및 Hidden입니다.

### <a name="-command"></a>-Command
지정된 명령(및 매개 변수)을 PowerShell 명령 프롬프트에서 입력된 것처럼 실행한 다음 NoExit 매개 변수가 지정되지 않은 경우 종료합니다.
근본적으로 `-Command` 뒤에 있는 모든 텍스트는 PowerShell에 단일 명령줄로 전송됩니다(이는 `-File`이 스크립트에 전송된 매개 변수를 처리하는 방법과 다름).

명령의 값은 "-", 문자열 또는 스크립트 블록일 수 있습니다. 명령의 값이 "-"인 경우 표준 입력에서 명령 텍스트를 읽어옵니다.

스크립트 블록은 중괄호({})로 묶어야 합니다. PowerShell에서 PowerShell.exe를 실행하는 경우에만 스크립트 블록을 지정할 수 있습니다. 스크립트의 결과는 라이브 개체가 아니라 역직렬화된 XML 개체로 부모 셸에 반환됩니다.

명령의 값이 문자열인 경우 명령 뒤에 입력한 문자는 모두 명령 인수로 해석되므로 **Command**가 명령의 마지막 매개 변수여야 합니다.

PowerShell 명령을 실행하는 문자열을 작성하려면 다음 형식을 사용합니다.

```
"& {<command>}"
```

여기서 따옴표는 문자열을 나타내고 호출 연산자(&)는 명령이 실행되게 합니다.

### <a name="-help---"></a>-Help, -?, /?
이 메시지를 표시합니다. PowerShell에서 PowerShell.exe 명령을 입력하는 경우 명령 매개 변수 앞에 슬래시(/)가 아니라 하이픈(-)을 추가합니다. Cmd.exe에서는 하이픈 또는 슬래시를 사용할 수 있습니다.

> [!NOTE]
> 문제 해결 참고: PowerShell 2.0에서 Windows PowerShell 콘솔을 통해 일부 프로그램을 시작하면 실패하고 LastExitCode 0xc0000142가 표시됩니다.

## <a name="examples"></a>예제

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

