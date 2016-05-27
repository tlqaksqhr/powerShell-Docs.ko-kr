---
title:   DSC 문제 해결
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# DSC 문제 해결

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

이 항목에서는 오류 없이 실행할 DSC(필요한 상태 구성) 스크립트를 가져오기 위한 메서드에 대해 설명합니다. 로그를 효과적으로 사용하여 오류를 추적하고, 캐시를 재활용하여 리소스 변경에 대한 즉각적인 결과를 확인하는 방법을 이해하면 DSC 문제를 보다 효과적으로 해결할 수 있습니다. 이러한 기술은 두 섹션에서 설명합니다.

* 스크립트가 실행되지 않습니다: **DSC 로그를 사용하여 스크립트 오류 진단**
* 리소스가 업데이트되지 않습니다: **캐시 재설정 방법**

## 스크립트가 실행되지 않습니다: DSC 로그를 사용하여 스크립트 오류 진단

모든 Windows 소프트웨어와 마찬가지로, DSC에서는 [이벤트 뷰어](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer)에서 볼 수 있는 [로그](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx)에 오류와 이벤트를 기록합니다. 이러한 로그를 검사하면 특정 작업이 실패한 이유와 나중에 오류를 방지하는 방법을 이해하는 데 도움이 될 수 있습니다. 구성 스크립트 작성은 까다로울 수 있으므로, 작성자로서 오류 추적을 보다 쉽게 하려면, DSC 로그 리소스를 사용하여 분석 DSC 이벤트 로그에 있는 구성의 진행률을 추적합니다.

## DSC 이벤트 로그는 어디에 있나요?

이벤트 뷰어에서 DSC 이벤트는 **응용 프로그램 및 서비스 로그/Microsoft/Windows/필요한 상태 구성**에 있습니다.

해당 PowerShell cmdlet인 [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx)를 실행해도 이벤트 로그를 볼 수도 있습니다.

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

위와 같이 DSC의 기본 로그 이름은 **Microsoft->Windows->DSC**(Windows 아래의 다른 로그 이름은 간결하게 하기 위해 표시하지 않음)입니다. 기본 이름을 채널 이름에 추가하여 전체 로그 이름이 만들어집니다. DSC 엔진은 [작업, 분석 및 디버그 로그](https://technet.microsoft.com/library/cc722404.aspx), 이렇게 주로 세 가지 유형의 로그에 기록합니다. 분석 및 디버그 로그는 기본적으로 해제 되어 있으므로, 이벤트 뷰어에서 설정해야 합니다. 이렇게 하려면 Windows PowerShell에서 Show-EventLog를 입력하여 이벤트 뷰어를 엽니다. 또는 **시작** 단추, **제어판**, **관리 도구**, **이벤트 뷰어**를 차례로 클릭합니다. 이벤트 뷰어의 **보기** 메뉴에서 **분석 및 디버그 로그 표시**를 클릭합니다. 분석 채널에 대한 로그 이름은 **Microsoft-Windows-Dsc/Analytic**이고, 디버그 채널은 **Microsoft-Windows-Dsc/Debug**입니다. 다음 예에서 보듯이, [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) 유틸리티를 사용하여 로그를 사용할 수도 있습니다.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## DSC 로그에 들어 있는 내용은 무엇인가요?

DSC 로그는 메시지의 중요도에 따라 3개의 로그 채널로 분할됩니다. DSC의 작업 로그는 모든 오류 메시지를 포함하며, 문제를 파악하는 데 사용될 수 있습니다. 분석 로그는 더 많은 양의 이벤트를 포함하며, 오류가 발생한 위치를 식별할 수 있습니다. 이 채널은 자세한 정보 메시지도 포함합니다(있는 경우). 디버그 로그는 오류가 발생하는 방식을 이해하는 데 도움이 될 수 있는 로그를 포함합니다. DSC 이벤트 메시지는 모든 이벤트 메시지가 고유하게 DSC 작업을 나타내는 작업 ID로 시작되도록 구조화되어 있습니다. 아래 예제는 작업 DSC 로그에 로그되는 첫 번째 이벤트에서 메시지 가져오기를 시도합니다.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

DSC 이벤트는 사용자가 하나의 DSC 작업에서 이벤트를 집계할 수 있도록 해주는 특정 구조로 로그됩니다. 구조는 다음과 같습니다.

**작업 ID: <Guid>**
**<Event Message>**

## 단일 DSC 작업에서 이벤트 수집

DSC 이벤트 로그에는 다양한 DSC 작업에서 생성된 이벤트가 포함됩니다. 그러나 우리는 일반적으로 하나의 특정 작업에 대한 세부 정보에 관심이 있습니다. 모든 DSC 로그는 각 DSC 작업에 대해 고유한 작업 ID 속성으로 그룹화할 수 있습니다. 작업 ID는 모든 DSC 이벤트에서 첫 번째 속성 값으로 표시됩니다. 다음 단계에서는 그룹화된 배열 구조에서 모든 이벤트를 누적하는 방법을 설명합니다.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}  
```

여기, 변수 `$SeparateDscOperations`는 작업 ID로 그룹화된 로그를 포함합니다. 이 변수의 각 배열 요소는 로그에 대한 추가 정보에 액세스할 수 있도록 다른 DSC 작업을 통해 로그되는 이벤트 그룹을 나타냅니다.

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

[Where-Object](https://technet.microsoft.com/library/ee177028.aspx)를 사용하여 `$SeparateDscOperations` 변수에서 데이터를 추출할 수 있습니다. 다음은 DSC 문제 해결을 위해 데이터를 추출해야 하는 다섯 개의 시나리오입니다.

### 1: 작업 오류

모든 이벤트에는 [심각도](https://msdn.microsoft.com/library/dd996917(v=vs.85))가 있습니다. 오류 이벤트를 식별하는 데 이 정보를 사용할 수 있습니다.

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### 2: 마지막 30분 안에 실행되는 작업의 세부 정보

`TimeCreated`모든 Windows 이벤트의 속성으로, 이벤트가 만들어진 시간을 기술합니다. 이 속성을 특정 날짜/시간 개체와 비교하여 모든 이벤트를 필터링할 수 있습니다.

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### 3: 최신 작업의 메시지

최신 작업은 배열 그룹 `$SeparateDscOperations`의 첫 번째 인덱스에 저장됩니다. 인덱스 0에 대한 그룹의 메시지를 쿼리하면 최신 작업에 대한 모든 메시지가 반환됩니다.

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### 4: 최근 실패한 작업에 대해 로그된 오류 메시지

`$SeparateDscOperations[0].Group` 최신 작업에 대한 이벤트 집합이 포함되어 있습니다. 수준 표시 이름에 따라 이벤트를 필터링하려면 `Where-Object` cmdlet을 실행하세요. 결과는 이벤트 메시지를 가져오기 위해 추가적으로 분석할 수 있는 `$myFailedEvent` 변수에 저장됩니다.

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### 5: 특정 작업 ID에 대해 생성된 모든 이벤트

`$SeparateDscOperations` 고유한 작업 ID로서 각각 이름이 있는 그룹의 배열입니다. `Where-Object` cmdlet을 실행하면 특정 작업 ID를 가지고 있는 이벤트들의 그룹을 추출할 수 있습니다.

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## xDscDiagnostics를 사용하여 DSC 로그 분석

**xDscDiagnostics**는 컴퓨터에서 DSC 실패를 분석하는 데 도움이 되는 두 개의 간단한 함수 `Get-xDscOperation`과 `Trace-xDscOperation`으로 구성된 PowerShell 모듈입니다. 이 함수들은 지난 DSC 작업의 모든 로컬 이벤트나 원격 컴퓨터의 DSC 이벤트(유효한 자격 증명 사용)를 식별하는 데 유용할 수 있습니다. 여기에서 DSC 작업이라는 용어는 시작부터 끝까지 하나의 고유한 DSC 실행을 정의하는 데 사용됩니다. 예를 들어 `Test-DscConfiguration`은 별도의 DSC 작업입니다. 마찬가지로, DSC에 있는 모든 다른 cmdlet(예: `Get-DscConfiguration`, `Start-DscConfiguration` 등)은 각각 별도의 DSC 작업으로 식별될 수 있습니다. 두 함수에 대해서는 [xDscDiagnostics](https://powershellgallery.com/packages/xDscDiagnostics) PowerShell 모듈(DSC Resource Kit)과 아래에 자세히 설명되어 있습니다. `Get-Help <cmdlet name>`을 실행하여 도움말을 사용할 수 있습니다.

## Get-xDscOperation

이 함수는 하나 또는 여러 컴퓨터에서 실행되는 DSC 작업의 결과를 찾을 수 있도록 해주며, 각 DSC 작업에서 생성된 이벤트의 컬렉션을 포함하는 개체를 반환합니다. 예를 들어 다음의 출력에서는 세 가지 명령이 실행되었습니다. 첫 번째 명령은 통과했고, 다른 두 개는 실패했습니다. 이 결과는 `Get-xDscOperation`의 출력에 요약되어 있습니다.

TODO: Get-xDscOperation 출력을 보여 주는 이 이미지 교체

### 매개 변수

* **Newest**: 표시할 작업의 수를 나타내는 정수 값을 받아들입니다. 기본적으로 10개의 최신 작업을 반환합니다. 예를 들면 다음과 같습니다. TODO: Get-xDscOperation -Newest 5 표시
* **ComputerName**: 각각 DSC 이벤트 로그 데이터를 수집하려는 컴퓨터의 이름을 포함하는 문자열의 배열을 받는 매개 변수입니다. 기본적으로 로컬 컴퓨터에서 데이터를 수집합니다. 이 기능을 사용하려면 이벤트 컬렉션을 허용하도록 승격된 모드로, 원격 컴퓨터에서 다음 명령을 실행해야 합니다.
```powershell
  New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
* **Credential**: ComputerName 매개 변수에 지정된 컴퓨터에 액세스하는 데 도움이 될 수 있는 PSCredential 유형의 매개 변수입니다.

### 반환된 개체

cmdlet은 개체의 배열을 반환하며, 각 형식은 **Microsoft.PowerShell.xDscDiagnostics.GroupedEvents**입니다. 이 배열에 있는 각 개체는 다른 DSC 작업에 적용됩니다. 이 개체에 대한 기본 표시에는 다음 속성이 있습니다.
* **SequenceID**: 시간에 따라 DSC 작업에 할당된 증가하는 번호를 지정합니다. 예를 들어, 마지막으로 실행된 작업은 1이라는 SequenceID를 갖고, 마지막 DSC 작업에서 두 번째 작업은 2라는 SequenceID를 갖는 방식으로 지정합니다. 이 번호는 반환된 배열에 있는 각 개체에 대한 또 다른 식별자입니다.
* **TimeCreated**: DSC 작업이 시작되는 시간을 나타내는 DateTime 값입니다.
* **ComputerName**: 결과가 집계되는 컴퓨터 이름입니다.
* **Result**: 각각 DSC 작업에 오류가 발생했는지 여부를 나타내며, 값이 **Failure** 또는 **Success**인 문자열입니다.
* **AllEvents**: DSC 작업에 의해 생성된 이벤트의 컬렉션을 나타내는 개체입니다.

예를 들어 다음의 출력은 여러 컴퓨터의 마지막 작업에 대한 결과를 보여 줍니다. TODO: 원격 컴퓨터 로그 표시를 위해 Get-xDscOperation에 대한 그림 바꾸기

## Trace-xDscOperation

이 cmdlet은 이벤트의 컬렉션, 해당 이벤트 형식 및 특정 DSC 작업으로 생성된 메시지 출력을 포함하는 개체를 반환합니다. 일반적으로 `Get-xDscOperation`을 사용하는 작업 중에 오류가 발생하면, 오류를 초래한 이벤트를 찾기 위해 해당 작업을 추적하게 됩니다.

### 매개 변수

* **SequenceID**: 특정 컴퓨터에 관련된 모든 작업에 할당된 정수 값입니다. 예를 들어 4라는 시퀀스 ID를 지정하면, 마지막에서 4번째였던 DSC 작업에 대한 추적이 출력됩니다.

시퀀스 ID가 지정된 Trace-xDscOperation
* **JobID**: 작업을 고유하게 식별하기 위해 LCM xDscOperation으로 할당한 GUID 값입니다. JobID를 지정하면 해당하는 DSC 작업에 대한 추적이 출력됩니다.
  TODO: 매개 변수로서 JobID를 사용하는 Trace-xDscOperation에 대한 그림 바꾸기
* **ComputerName** 및 **Credential**: 이 매개 변수들은 원격 컴퓨터에서 추적을 수집하는 것을 허용합니다.
```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
  TODO: 다른 컴퓨터에서 실행되는 Trace-xDscOperation에 대한 그림 바꾸기

`Trace-xDscOperation`에서는 분석, 디버그 및 작업 로그에서 이벤트를 집계하므로, 위에서 설명한 대로 이러한 로그를 사용하도록 설정하라는 메시지가 표시됩니다.

### 반환된 개체

이 cmdlet은 개체의 배열을 반환하며, 각각 `Microsoft.PowerShell.xDscDiagnostics.TraceOutput` 형식입니다. 이 배열에 있는 각 개체에는 다음 필드가 포함됩니다.
* **ComputerName**: 로그를 수집하는 컴퓨터의 이름입니다.
* **EventType**: 이벤트의 형식에 대한 정보를 포함하는 열거자 유형 필드입니다. 다음 중 하나일 수 있습니다.
  - *Operational*: 작업 로그의 이벤트입니다.
  - *Analytic*: 분석 로그의 이벤트입니다.
  - *Debug*: 디버그 로그의 이벤트입니다.
  - *Verbose*: 실행하는 동안 이벤트가 자세한 정보 메시지로 출력됩니다. 자세한 정보 메시지를 사용하면 게시된 이벤트의 순서를 식별하기가 쉽습니다.
  - *Error*: 오류 이벤트입니다. 오류 이벤트를 검색하면 실패의 원인을 일반적으로 신속하게 찾을 수 있습니다.
* **TimeCreated**: 이벤트가 DSC에 의해 로그된 시간을 나타내는 DateTime 값입니다.
* **Message**: 이벤트 로그에 DSC에 의해 기록된 메시지입니다.

다음은 이 개체에 있는 필드로서, 이벤트에 대한 추가 정보가 필요할 때 사용할 수는 있지만 기본적으로 표시되지 않는 필드입니다.

* **JobID**: 해당 DSC 작업에 대한 작업 ID(GUID 형식)입니다.
* **SequenceID**: 해당 컴퓨터의 해당 DSC 작업에 고유한 SequenceID입니다.
* **이벤트**: `System.Diagnostics.Eventing.Reader.EventLogRecord` 형식의, DSC에 의해 로그된 실제 이벤트입니다. `Get-WinEvent` cmdlet을 실행하여 얻을 수도 있습니다. 작업, eventID, 이벤트의 수준 등의 자세한 정보를 포함합니다.

또는, `Trace-xDscOperation`의 출력을 변수에 저장하여 이벤트에 대한 정보를 수집할 수 있습니다. 다음 명령을 사용하여 특정 DSC 작업에 대한 모든 이벤트를 표시할 수 있습니다.

```powershell
(Trace-xDscOperation -SequenceID 3).Event
```

이렇게 하면 아래 출력과 같이 `Get-WinEvent` cmdlet과 동일한 결과가 표시됩니다. TODO: 어떤 출력인가요?

먼저 `Get-xDscOperation`을 사용하여 컴퓨터에서의 마지막 몇 개 DSC 구성 실행을 나열하는 것이 좋습니다. 그런 다음에 `Trace-xDscOperation`으로 단일 작업(해당 SequenceID 또는 JobID 사용)을 검사하여 백그라운드에서 수행한 작업을 검색할 수 있습니다.

## 리소스가 업데이트되지 않습니다: 캐시 재설정 방법

DSC 엔진은 효율성 향상을 위해 PowerShell 모듈로서 구현하는 리소스를 캐시합니다. 그러나 이렇게 하면 프로세스가 다시 시작되기 전까지 DSC가 캐시된 버전을 로드하게 되므로 리소스를 작성하고 동시에 테스트하는 경우 문제가 발생할 수 있습니다. DSC가 최신 버전을 로드하도록 하는 유일한 방법은 DSC 엔진을 호스팅하는 프로세스를 명시적으로 종료하는 것입니다.

마찬가지로, `Start-DscConfiguration`을 실행하는 경우, 사용자 지정 리소스를 추가하고 수정하면 컴퓨터를 다시 부팅하지 않으면, 또는 다시 부팅하기 전까지는 수정이 실행되지 않을 수 있습니다. 이것은 DSC가 WMI 공급자 호스트 프로세스(WmiPrvSE)에서 실행되고, 일반적으로 한 번에 실행되는 WmiPrvSE 인스턴스가 많기 때문입니다. 컴퓨터를 다시 부팅하면 호스트 프로세스가 다시 시작되고 캐시가 지워집니다.

다시 부팅하지 않고도 구성을 성공적으로 재활용하고, 캐시를 지우려면, 호스트 프로세스를 중지했다가 다시 시작해야 합니다. 이 작업은 인스턴스별로 수행할 수 있으며, 그에 따라 프로세스를 식별, 중지 및 다시 시작할 수 있습니다. 또는 아래 설명된 대로 `DebugMode`를 사용하여 PowerShell DSC 리소스를 다시 로드할 수 있습니다.

인스턴스별로 DSC 엔진을 호스트하고 중지하는 프로세스를 식별하기 위해 DSC 엔진을 호스팅하는 WmiPrvSE의 프로세스 ID를 나열할 수 있습니다. 그런 다음 공급자를 업데이트하려면, 아래 명령을 사용하여 WmiPrvSE 프로세스를 중지한 다음, **Start-DscConfiguration**을 다시 실행합니다.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## DebugMode 사용

호스트 프로세스를 다시 시작할 때 항상 캐시가 지워지도록 하기 위해 `DebugMode`를 사용하도록 DSC LCM(로컬 구성 관리자)를 구성할 수 있습니다. **TRUE**로 설정하면, 엔진이 항상 PowerShell DSC 리소스를 다시 로드합니다. 리소스를 작성을 완료하면, 다시 **FALSE**로 설정할 수 있으며, 엔진은 모듈을 캐싱하는 동작으로 되돌아갑니다.

다음은 `DebugMode`가 캐시를 자동으로 새로 고칠 수 있는 방법을 보여 주는 데모입니다. 우선, 기본 구성을 살펴보겠습니다.

```
PS C:\> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

`DebugMode`가 **FALSE**로 설정된 것을 확인할 수 있습니다.

`DebugMode` 데모를 설정하려면 다음 PowerShell 리소스를 사용합니다.

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

이제, `TestProviderDebugMode`라는 위의 리소스를 사용하여 구성을 작성합니다.

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

파일 "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**"의 내용이 **1**인 것을 확인하게 될 것입니다.

이제, 다음 스크립트를 사용하여 공급자 코드를 업데이트합니다.

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

이 스크립트는 난수를 생성하고 그에 따라 공급자 코드를 업데이트합니다. `DebugMode`가 false로 설정되면 파일 "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**"의 내용은 결코 변경되지 않습니다.

이제, 구성 스크립트에서 `DebugMode`를 **TRUE**로 설정합니다.

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

다시 위의 스크립트를 실행하면 파일의 내용이 매번 다른 것을 보게 됩니다. (`Get-DscConfiguration`를 실행하여 확인할 수 있습니다.) 다음은 두 번의 추가 실행에 대한 결과입니다(결과는 스크립트를 실행하는 경우 다를 수 있음).

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14                                      localhost
```

## 참고 항목

### 참조
* [DSC 로그 리소스](logResource.md)

### 개념
* [사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드](authoringResource.md)

### 관련 자료
* [Windows PowerShell Desired State Configuration Cmdlets(Windows PowerShell 필요한 상태 구성 Cmdlet)](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)



<!--HONumber=May16_HO3-->


