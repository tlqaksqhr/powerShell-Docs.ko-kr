---
title: "WMF 5.1(Preview)의 향상된 PowerShell 엔진"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 1bbed7edf5c2b643b88311727dd9bd4e9de88944
ms.openlocfilehash: af0f58c5d84e21416cb15e4bd53c24369fa9c1b6

---

#향상된 PowerShell 엔진

WMF 5.1에서는 핵심 PowerShell 엔진에 대한 다음과 같은 개선 사항이 구현되었습니다.


## 성능 ##

몇 가지 중요한 영역에서 성능이 향상되었습니다.

- 시작
- ForEach-Object 및 Where-Object와 같은 cmdlet에 대한 파이프라이닝이 약 50% 더 빠릅니다. 

몇 가지 예제 개선 사항(하드웨어에 따라 결과가 달라질 수 있음): 

| 시나리오 | 5.0 시간(밀리초) | 5.1 시간(밀리초) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| 처음 PowerShell 실행: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| 빌드된 명령 분석 캐시: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
> 시작과 관련된 한 가지 변경으로 인해 몇 가지 지원되지 않는 시나리오에 영향이 있을 수 있습니다. PowerShell은 더 이상 `$pshome\*.ps1xml` 파일을 읽지 않습니다. XML 파일 처리의 일부 파일 및 CPU 오버헤드를 방지하기 위해 이러한 파일이 C#으로 변환되었습니다. 이러한 파일은 V2를 나란히 지원하기 위해 여전이 있으므로 파일 콘텐츠를 변경하는 경우 V5에는 아무 영향이 없고 V2에만 영향을 줍니다. 이러한 파일의 콘텐츠를 변경하는 시나리오는 지원되지 않았습니다.

또 하나의 뚜렷한 변경 사항은 PowerShell이 시스템에 설치된 모듈에 대해 내보낸 명령 및 기타 정보를 캐시하는 방법입니다. 이전이 이 캐시는 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 디렉터리에 저장되었습니다. WMF 5.1에서 이 캐시는 단일 파일 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`입니다.
자세한 내용은 [analysis_cache.md]()를 참조하세요.



<!--HONumber=Jul16_HO5-->


