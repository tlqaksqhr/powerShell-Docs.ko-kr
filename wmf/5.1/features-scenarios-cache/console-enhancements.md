---
title: "콘솔 환경의 향상된 기능"
author: jasonsh
translationtype: Human Translation
ms.sourcegitcommit: 9ce218a2807dd7b1c69f81efdbd6132321e6a815
ms.openlocfilehash: e6653a02421e3aec3910a70c64f7cf7cecd696ab

---

>참고: 제안된 설명이 포함된 제목과 간단한 설명을 제공합니다.

## 향상된 PowerShell 콘솔

콘솔 환경을 개선하기 위해 powershell.exe가 다음과 같이 변경되었습니다.

1. VT100 지원

Windows 10에서는 [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx)(VT100 이스케이프 스퀀스)에 대한 지원을 추가했습니다.
PowerShell에서는 표 너비를 계산할 때 특정 VT100 서식 이스케이프 시퀀스를 무시합니다.

또한 PowerShell에서는 VT100이 지원되는지 여부를 결정하는 서식 코드에 사용할 수 있는 새로운 API도 추가했습니다.  예:

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
다음은 Select-String의 일치 항목을 강조 표시하는 데 사용할 수 있는 전체 [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7)(예제)입니다.
예제를 `MatchInfo.format.ps1xml`이라는 파일로 저장하고 프로필 또는 다른 위치에서 사용하려면 `Update-FormatData -Prepend MatchInfo.format.ps1xml`을 실행합니다.

VT100 이스케이프 시퀀스는 Windows 10에 대한 Aniversary 업데이트부터만 지원되며 이전 시스템에서는 지원되지 않습니다.   

2. PSReadline의 Vi 모드 지원

[PSReadline](https://github.com/lzybkr/PSReadLine)은 vi 모드에 대한 지원을 추가합니다. Vi 모드를 사용하려면 `Set-PSReadline -EditMode vi`를 실행합니다.

3. 대화형 입력을 사용한 리디렉션된 stdin 

이전 버전에서는 stdin이 리디렉션되고 명령을 대화형으로 입력하려는 경우 `powershell -File -`을 사용하여 PowerShell을 시작해야 했습니다.

WMF 5.1에서 검색하기 어려운 이 옵션이 더 이상 필요하지 않으며 `powershell` 등과 같은 옵션 없이 powershell을 시작할 수 있습니다.

PSReadline에서는 현재 리디렉션된 stdin을 지원하지 않으며 리디렉션된 stdin을 사용하는 기본 제공 명령줄 편집 환경이 매우 제한되어 있습니다. 예를 들어 화살표 키가 작동하지 않습니다.  PSReadline의 이후 릴리스에서는 이 문제가 해결됩니다.   


<!--HONumber=Aug16_HO3-->


