---
title: PowerShell.exe 명령줄 도움말
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
---
# PowerShell.exe 명령줄 도움말
Windows PowerShell 세션을 시작합니다. PowerShell.exe를 사용하여 Cmd.exe와 같은 다른 도구의 명령줄에서 Windows PowerShell 세션을 시작하거나, Windows PowerShell 명령줄에서 사용하여 새 세션을 시작할 수 있습니다. 매개 변수를 사용하여 세션을 사용자 지정합니다.

## 구문

```
PowerShell[.exe]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
       [-File <FilePath> [<Args>]]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

## 매개 변수

### \-EncodedCommand <Base64EncodedCommand>
명령의 Base 64로 인코드된 문자열 버전을 허용합니다. 이 매개 변수를 사용하여 명령을 큰따옴표 또는 중괄호가 필요한 Windows PowerShell로 전송합니다.

### \-ExecutionPolicy <ExecutionPolicy>
현재 세션에 대한 기본 실행 정책을 설정하고 $env:PSExecutionPolicyPreference 환경 변수에 저장합니다. 이 매개 변수는 레지스트리에 설정된 Windows PowerShell 실행 정책을 변경하지는 않습니다. 유효한 값 목록을 포함하여 Windows PowerShell 실행 정책에 대한 자세한 내용은 about\_Execution\_Policies(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=135170)를 참조하세요.

### \-File <FilePath> \[<Parameters>]
스크립트에서 만드는 함수와 변수를 현재 세션에서 사용할 수 있도록 지정한 스크립트를 로컬 범위("dot\-sourced")에서 실행합니다. 스크립트 파일의 경로와 매개 변수를 입력합니다. **File** 매개 변수 이름 뒤에 입력한 모든 문자는 차례로 스크립트 파일 경로, 스크립트 매개 변수 및 해당 값으로 해석되기 때문에 **File**은 명령의 마지막 매개 변수여야 합니다.

**File** 매개 변수의 값에 스크립트 매개 변수 및 매개 변수 값을 포함할 수 있습니다. 예를 들면 다음과 같습니다. `-File .\Get-Script.ps1 -Domain Central`

일반적으로 스크립트의 스위치 매개 변수는 포함되거나 생략됩니다. 예를 들어 다음 명령은 Get\-Script.ps1 스크립트 파일의 **All** 매개 변수를 사용합니다. `-File .\Get-Script.ps1 -All`

드문 경우지만 스위치 매개 변수에 대해 부울 값을 제공해야 할 수도 있습니다. **File** 매개 변수의 값에 스위치 매개 변수의 부울 값을 제공하려면 다음과 같이 매개 변수 이름과 값을 중괄호로 묶습니다. `-File .\Get-Script.ps1 {-All:$False}`

### \-InputFormat {Text | XML}
Windows PowerShell로 전송되는 데이터 형식을 설명합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

### \-Mta
다중 스레드 아파트를 사용하여 Windows PowerShell을 시작합니다. [!INCLUDE[ps_sdk_paramintrodps3](../Token/ps_sdk_paramintrodps3_md.md)] [!INCLUDE[psversion3](../Token/psversion3_md.md)]에서는 STA(단일 스레드 아파트)가 기본값입니다. [!INCLUDE[psversion2](../Token/psversion2_md.md)]에서는 MTA(다중 스레드 아파트)가 기본값입니다.

### \-NoExit
시작 명령을 실행한 후 종료하지 않습니다.

### \-NoLogo
시작 시 저작권 배너를 숨깁니다.

### \-NonInteractive
사용자에게 대화형 프롬프트를 표시하지 않습니다.

### \-NoProfile
Windows PowerShell 프로필을 로드하지 않습니다.

### \-OutputFormat {Text | XML}
Windows PowerShell의 출력 형식을 결정합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

### \-PSConsoleFile <FilePath>
지정된 Windows PowerShell 콘솔 파일을 로드합니다. 콘솔 파일의 경로와 이름을 입력합니다. 콘솔 파일을 만들려면 Windows PowerShell에서 [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet을 사용합니다.

### \-Sta
단일 스레드 아파트를 사용하여 Windows PowerShell을 시작합니다. [!INCLUDE[psversion3](../Token/psversion3_md.md)]에서는 STA(단일 스레드 아파트)가 기본값입니다. [!INCLUDE[psversion2](../Token/psversion2_md.md)]에서는 MTA(다중 스레드 아파트)가 기본값입니다.

### \-Version <Windows PowerShell Version>
지정된 버전의 Windows PowerShell을 시작합니다. 지정한 버전이 시스템에 설치되어 있어야 합니다. 컴퓨터에 [!INCLUDE[psversion3](../Token/psversion3_md.md)]이 설치되어 있는 경우 유효한 값은 "2.0"과 "3.0"입니다. 기본값은 "3.0"입니다.

[!INCLUDE[psversion3](../Token/psversion3_md.md)]이 설치되지 않은 경우 유효한 값은 "2.0"뿐입니다. 다른 값은 무시됩니다.

자세한 내용은 [Windows PowerShell 시작 [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd)에서 "Windows PowerShell 설치"를 참조하세요.

### \-WindowStyle <Window style>
세션에 대한 창 스타일을 설정합니다. 유효한 값은 Normal, Minimized, Maximized 및 Hidden입니다.

### \-Command
지정된 명령(및 매개 변수)을 Windows PowerShell 명령 프롬프트에서 입력된 것처럼 실행한 다음 NoExit 매개 변수가 지정되지 않은 경우 종료합니다.

명령의 값은 "\-", 문자열 또는 스크립트 블록일 수 있습니다. 명령의 값이 "\-"인 경우 표준 입력에서 명령 텍스트를 읽어옵니다.

스크립트 블록은 중괄호({})로 묶어야 합니다. Windows PowerShell에서 PowerShell.exe를 실행하는 경우에만 스크립트 블록을 지정할 수 있습니다. 스크립트의 결과는 라이브 개체가 아니라 역직렬화된 XML 개체로 부모 셸에 반환됩니다.

명령의 값이 문자열인 경우 명령 뒤에 입력한 문자는 모두 명령 인수로 해석되기 때문에 **Command**가 명령의 마지막 매개 변수여야 합니다.

Windows PowerShell 명령을 실행하는 문자열을 작성하려면 다음 형식을 사용합니다.

```
"& {<command>}"
```

여기서 따옴표는 문자열을 나타내고 호출 연산자(&)는 명령이 실행되게 합니다.

### \-Help, \-?, \/?
이 메시지를 표시합니다. Windows PowerShell에서 PowerShell.exe 명령을 입력하는 경우 명령 매개 변수 앞에 슬래시(\/)가 아니라 하이픈(\-)을 추가합니다. Cmd.exe에서는 하이픈 또는 슬래시를 사용할 수 있습니다.

> [!NOTE]
> 문제 해결 참고: Windows PowerShell 2.0에서 Windows PowerShell 콘솔을 통해 일부 프로그램을 시작하면 실패하고 LastExitCode 0xc0000142가 표시됩니다.

## 예제

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```



<!--HONumber=Apr16_HO2-->


