---
title: 원격 명령 실행
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
---
# 원격 명령 실행
단일 Windows PowerShell 명령으로 한 대 이상의 컴퓨터에서 명령을 실행할 수 있습니다. Windows PowerShell에서는 WMI, RPC, WS\-Management 등과 같은 다양한 기술을 사용하여 원격 컴퓨팅을 지원합니다.

## 구성 없이 원격 작업
많은 Windows PowerShell cmdlet에서는 데이터를 수집하고 하나 이상의 원격 컴퓨터 설정을 변경할 수 있는 ComputerName 매개 변수를 사용합니다. 이러한 cmdlet은 다양한 통신 기술을 사용하고 대부분은 특별한 구성 없이도 Windows PowerShell에서 지원하는 모든 Windows 운영 체제에서 작동합니다.

이러한 cmdlet은 다음과 같습니다.

-   [Restart-Computer](assetId:///bd52bcf6-80ee-4866-9320-04ee1d1dca4a)

-   [Test-Connection](assetId:///87d293e5-10e2-489b-b0a9-922d77c05f3f)

-   [Clear-EventLog](assetId:///05d0de31-3c9d-4cd6-8e1a-dac19835464c)

-   [Get-EventLog [m2]](assetId:///a4372a60-b7d9-4b1c-a268-aa5240300141)

-   [Get-Hotfix](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process [m2]](assetId:///27a05dbd-4b69-48a3-8d55-b295f6225f15)

-   [Get-Service [m2]](assetId:///0a09cb22-0a1c-4a79-9851-4e53075f9cf6)

-   [Set-Service [m2]](assetId:///b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

-   [Get-WinEvent](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-WmiObject [m2]](assetId:///a4c499fa-deec-4c4b-b3fb-6e195d48a396)

일반적으로 특별한 구성 없이 원격 작업을 지원하는 cmdlet에는 ComputerName 매개 변수는 있지만 Session 매개 변수는 없습니다. 세션에서 이러한 cmdlet을 찾으려면 다음과 같이 입력합니다.

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Windows PowerShell 원격 작업
WS\-Management 프로토콜을 사용하는 Windows PowerShell 원격 작업을 이용하면 한 대 이상의 원격 컴퓨터에서 Windows PowerShell 명령을 실행할 수 있습니다. 또한 여러 컴퓨터에서 영구 연결을 설정하고, 1:1 대화형 세션을 시작하고, 스크립트를 실행할 수 있습니다.

Windows PowerShell 원격 작업을 사용하려면 원격 관리를 위해 원격 컴퓨터를 구성해야 합니다. 자세한 내용과 지침은 [about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd)를 참조하세요.

Windows PowerShell 원격 작업을 구성한 후 다양한 원격 전략을 사용할 수 있습니다. 이 문서의 나머지 부분에서 일부 원격 전략을 나열합니다. 자세한 내용은 [about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970) 및 [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)를 참조하세요.

### 대화형 세션 시작
단일 원격 컴퓨터와 대화형 세션을 시작하려면 [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c) cmdlet을 사용합니다. 예를 들어 Server01 원격 컴퓨터와 대화형 세션을 시작하려면 다음과 같이 입력합니다.

```
enter-pssession Server01
```

명령 프롬프트가 변경되어 연결된 컴퓨터의 이름이 표시됩니다. 이제부터 프롬프트에 입력하는 명령이 원격 컴퓨터에서 실행되고 그 결과가 로컬 컴퓨터에 표시됩니다.

대화형 세션을 종료하려면 다음을 입력합니다.

```
exit-pssession
```

Enter-PSSession 및 Exit-PSSession cmdlet에 대한 자세한 내용은 [Enter\-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c) 및 [Exit\-PSSession](assetId:///b6daa1ce-48a5-41a3-ac4b-b64dbe03465d)을 참조하세요.

### 원격 명령 실행
한 대 이상의 원격 컴퓨터에서 명령을 실행하려면 [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462) cmdlet을 사용합니다. 예를 들어 Server01 및 Server02 원격 컴퓨터에서 [Get-UICulture [m2]](assetId:///99175c2e-e856-4208-970e-3dd2f6bac5b8) 명령을 실행하려면 다음과 같이 입력합니다.

```
invoke-command -computername Server01, Server02 {get-UICulture}
```

출력은 사용자의 컴퓨터에 반환됩니다.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

Invoke-Command cmdlet에 대한 자세한 내용은 [Invoke\-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)를 참조하세요.

### 스크립트 실행
한 대 이상의 원격 컴퓨터에서 스크립트를 실행하려면 Invoke\-Command cmdlet의 FilePath 매개 변수를 사용합니다. 스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에 액세스할 수 있어야 합니다. 결과는 로컬 컴퓨터에 반환됩니다.

예를 들어 다음 명령은 Server01 및 Server02 원격 컴퓨터에서 DiskCollect.ps1 스크립트를 실행합니다.

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

Invoke-Command cmdlet에 대한 자세한 내용은 [Invoke\-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)를 참조하세요.

### 영구 연결 설정
데이터를 공유하는 일련의 관련 명령을 실행하려면 원격 컴퓨터에서 세션을 만든 다음 Invoke\-Command cmdlet을 사용하여 해당 세션에서 명령을 실행합니다. 원격 세션을 만들려면 New\-PSSession cmdlet을 사용합니다.

예를 들어 다음 명령은 Server01 컴퓨터에서 원격 세션을 만들고 Server02 컴퓨터에서 다른 원격 세션을 만듭니다. 이 명령은 세션 개체를 $s 변수에 저장합니다.

```
$s = new-pssession -computername Server01, Server02
```

세션을 설정했으므로 이제 해당 세션에서 명령을 실행할 수 있습니다. 세션이 영구 세션이므로 명령을 실행하여 데이터를 수집하고 후속 명령에서 해당 데이터를 사용할 수 있습니다.

예를 들어 다음 명령은 $s 변수의 세션에서 Get\-Hotfix 명령을 실행하고 결과를 $h 변수에 저장합니다. $h 변수는 $s의 각 세션에서 생성되지만 로컬 세션에는 없습니다.

```
invoke-command -session $s {$h = get-hotfix}
```

이제 다음과 같이 후속 명령의 $h 변수에서 데이터를 사용할 수 있습니다. 결과는 로컬 컴퓨터에 표시됩니다.

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"
```

### 고급 원격 작업
Windows PowerShell 원격 관리가 여기에서 시작됩니다. Windows PowerShell과 함께 설치되는 cmdlet을 사용하여 로컬 끝점과 원격 끝점 모두에서 원격 세션을 설정하여 구성하고, 사용자 지정되고 제한된 세션을 만들고, 사용자가 원격 세션에서 암시적으로 실행되는 명령을 원격 세션에서 가져오도록 허용하고, 원격 세션의 보안을 구성하는 등과 같은 작업을 수행할 수 있습니다.

원격 구성을 쉽게 설정할 수 있도록 Windows PowerShell에는 WSMan 공급자가 포함되어 있습니다. 공급자가 만드는 WSMAN: 드라이브를 사용하여 로컬 컴퓨터와 원격 컴퓨터에서 구성 설정 계층을 탐색할 수 있습니다. WSMan 공급자에 대한 자세한 내용을 보려면 [WSMan Provider](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735) 및 [about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed)을 참조하거나 Windows PowerShell 콘솔에서 "get\-help wsman"을 입력합니다.

자세한 내용은 [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42), [Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25) 및 [Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d)을 참조하세요. 원격 오류에 대한 도움이 필요한 경우 [about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317)을 참조하세요.

## 참고 항목
[about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
[about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)
[about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd)
[about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317)
[about_PSSessions](assetId:///7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
[about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed)
[Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)
[Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
[New-PSSession](assetId:///59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
[Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25)
[WSMan 공급자](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735)



<!--HONumber=Apr16_HO1-->


