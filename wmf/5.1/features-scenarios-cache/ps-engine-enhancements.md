---
title: "PowerShell 엔진 향상된 기능"
author: jasonsh
translationtype: Human Translation
ms.sourcegitcommit: 6813902aec214aee9ede27ff79dd291364e9f443
ms.openlocfilehash: f864850128f118704d7545b09110835ab1d51b8e

---

# PowerShell 엔진 향상된 기능 #

PowerShell 5.1에서는 핵심 PowerShell 엔진에 대한 다음과 같은 개선 사항이 구현되었습니다.


## 성능 ##

몇 가지 중요한 영역에서 성능이 향상되었습니다.

1. 시작
2. ForEach-Object 및 Where-Object와 같은 cmdlet에 대한 파이프라이닝이 약 50% 더 빠릅니다. 

몇 가지 예제 개선 사항(하드웨어에 따라 결과가 달라질 수 있음): 

| 시나리오 | 5.0 시간(밀리초) | 5.1 시간(밀리초) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| 처음 PowerShell 실행: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| 빌드된 명령 분석 캐시: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
시작과 관련된 한 가지 변경이 몇 가지(지원되지 않는) 시나리오에 영향을 줄 수 있습니다. PowerShell은 더 이상 `$pshome\*.ps1xml` 파일을 읽지 않습니다. xml 파일 처리의 일부 파일 및 cpu 오버헤드를 방지하기 위해 이러한 파일이 C#으로 변환되었습니다. 이러한 파일은 V2를 나란히 지원하기 위해 여전이 있으므로 파일 콘텐츠를 변경하는 경우 V5에는 아무 영향이 없고 V2에만 영향을 줍니다. 이러한 파일의 콘텐츠를 변경하는 시나리오는 지원되지 않았습니다.

또 하나의 뚜렷한 변경 사항은 PowerShell이 시스템에 설치된 모듈에 대해 내보낸 명령 및 기타 정보를 캐시하는 방법입니다. 이전이 이 캐시는 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 디렉터리에 저장되었습니다. WMF 5.1에서 이 캐시는 단일 파일 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`입니다.
자세한 내용은 [analysis_cache.md]()를 참조하세요.

PowerShell은 버전 5.1부터 기능 집합 및 플랫폼 호환성이 다른 여러 버전으로 제공됩니다.



## 버그 수정 ##

다음과 같은 주목할 만한 버그가 수정되었습니다.

### 모듈 자동 검색에서 완전히 적용함 `$env:PSModulePath` ###

모듈 자동 검색(명령을 호출할 때 명시적 Import-Module 없이 모듈을 자동으로 로드)이 WMF3에 도입되었습니다. 도입될 때 PowerShell에서는 `$env:PSModulePath`를 사용하기 전에 `$PSHome\Modules`에 있는 명령을 확인했습니다.

WMF5.1에서는 `$env:PSModulePath`를 완전히 적용하도록 이 동작을 변경합니다. 따라서 PowerShell에서 제공하는 명령(예: `Get-ChildItem`)을 정의하는 사용자 작업 모듈이 자동으로 로드되고 기본 제공 명령을 올바로 재정의할 수 있습니다.

### 파일 리디렉션에서 더 이상 하드 코드하지 않음 `-Encoding Unicode` ###

PowerShell의 모든 이전 버전에서는 PowerShell에서 `-Encoding Unicode`를 추가했으므로 파일 리디렉션 연산자(예: `get-childitem > out.txt`)를 사용하여 파일 인코딩을 제어할 수 없습니다.

WMF 5.1부터 이제 `$PSDefaultParameterValues`를 설정하여 리디렉션의 파일 인코딩을 변경할 수 있습니다. 예를 들면 다음과 같습니다.

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### 구성원 액세스에서의 회귀 수정 `System.Reflection.TypeInfo` ###

WMF5에 도입된 회귀가 `System.Reflection.RuntimeType`의 구성원(예: `[int].ImplementedInterfaces`) 액세스를 중단시켰습니다.
이 버그는 WMF5.1에서 수정되었습니다.


### COM 개체의 몇 가지 문제 수정 ###

WMF5에서는 COM 개체에 대한 메서드를 호출하고 COM 개체의 속성에 액세스하는 새로운 COM 바인더를 도입했습니다.
이 새 바인더는 성능을 크게 향상했지만 몇 가지 버그도 도입했습니다. 이 버그는 WMF5.1에서 수정되었습니다.

#### 인수 변환이 올바로 수행되지 않을 수도 있었음 ####

다음 예제에서,

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

SendKeys 메서드에는 문자열이 필요하지만 PowerShell은 문자를 문자열로 변환하지 않고 IDispatch::Invoke에서 변환을 수행하게 했습니다. IDispatch::Invoke는 VariantChangeType을 사용하여 변환을 수행하므로 이 예에서는 Volume.Mute 키 대신 '1', '7' 및 '3' 키가 보내졌습니다.

#### 열거 가능 COM 개체가 올바로 처리되지 않을 수도 있음 ####

PowerShell에서는 대부분의 열거 가능 개체를 정상적으로 열거하지만 WMF5에 도입된 회귀로 인해 IEnumerable을 구현하는 COM 개체가 열거되지 못했습니다.  예:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

위의 예에서 WMF5는 키 값 쌍을 열거하지 않고 Scripting.Dictionary를 파이프라인에 잘못 썼습니다.


### `[ordered]` 는 클래스 내에서 허용되지 않았음 ###

WMF5에서는 클래스에 사용된 형식 리터럴의 유효성을 검사하는 클래스를 도입했습니다.  `[ordered]` 는 형식 리터럴로 보이지만 실제 .Net 형식이 아닙니다.  WMF5에서는 클래스 내에 있는 `[ordered]`에 대해 오류를 잘못 보고했습니다.

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### 여러 버전이 있는 정보 항목에 대한 도움말이 작동하지 않음 ###

WMF5.1 이전에는 모듈의 여러 버전이 설치되어 있고 이들 버전이 모두 about_PSReadline과 같은 하나의 도움말 항목을 공유한 경우 `help about_PSReadline`에서 여러 항목을 반환하므로 실제 도움말을 볼 수 있는 방법이 명확히 없었습니다.

WMF5.1에서는 항목의 최신 버전에 대한 도움말을 반환하여 이 문제를 수정합니다.

Get-Help에는 도움말이 필요한 버전을 지정하는 방법이 없으므로 모듈 디렉터리로 이동하고 즐겨 사용하는 편집기와 같은 도구에서 직접 도움말을 보는 것이 해결 방법입니다. 



<!--HONumber=Jul16_HO2-->


