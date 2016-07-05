---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "JEA에 대한 보고"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: d867a6462e9fa8b6e16c8c2103899c72b380116c

---

# JEA에 대한 보고
JEA는 권한 없는 사용자가 권한 있는 컨텍스트에서 실행하도록 허용하기 때문에 로깅과 감사가 매우 중요합니다.
이 섹션에서는 로깅과 보고에 유용하게 사용할 수 있는 도구를 실행합니다.

## JEA 작업에 대한 보고
### Over-the-Shoulder 기록
PowerShell 세션에서 발생하고 있는 상황을 대략적으로 파악하는 가장 빠른 방법은 입력하는 사용자의 어깨너머로 보는 것입니다.
입력한 명령, 해당 명령의 출력 및 모두 정상인지를 확인할 수 있습니다.
정상이 아닌 경우에는 적어도 문제 상황을 알게 됩니다.
PowerShell 기록은 사건 뒤에 유사한 보기를 제공하도록 설계되었습니다.

세션 구성에서 "TranscriptDirectory" 필드를 사용할 때 PowerShell에서는 주어진 세션에서 수행된 모든 작업의 기록을 자동으로 생성합니다.
이 문서의 세션에서는 "$env:ProgramData\JEAConfiguration\Transcripts"에서 기록을 찾을 수 있습니다.

기록에는 "연결된" 사용자, "실행" 사용자, 세션에서 실행된 명령 등에 대한 정보가 포함됩니다.
PowerShell 기록에 대한 자세한 내용은 [이 블로그 게시물](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)을 참조하세요.

### PowerShell 이벤트 로그
모듈 로깅을 켠 경우 모든 PowerShell 작업은 일반 Windows 이벤트 로그에도 기록됩니다.
이벤트 로그는 기록과 비교할 때 다루기가 약간 더 복잡하지만 제공하는 세부 정보의 수준은 유용할 수 있습니다.

"PowerShell" 작업 로그에서 이벤트 ID 4104는 모듈 로깅을 사용하도록 설정한 경우 호출된 각 명령을 기록합니다.

### 기타 이벤트 로그
PowerShell 로그 및 기록과 달리, 다른 로깅 메커니즘은 "연결된 사용자"를 캡처하지 않습니다.
수행된 작업을 맞춰보기 위해 다른 로그와 PowerShell 로그 간의 상관 관계를 파악해야 합니다.

"Windows 원격 관리" 작업 로그에서 이벤트 ID 193은 이 상관 관계 파악에 도움을 주기 위해 연결하는 사용자의 SID 및 이름뿐만 아니라 실행 가상 계정의 SID를 기록합니다.
또한 실행 가상 계정 이름의 끝에 연결하는 사용자의 도메인 및 사용자 이름이 포함되어 있음을 확인할 수도 있습니다.

## JEA 구성에 대한 보고
### Get-PSSessionConfiguration
사용자 환경의 상태에 대해 정확하게 보고하기 위해 컴퓨터에서 설정한 JEA 끝점 수를 알아야 합니다.
`Get-PSSessionConfiguration` 은 이 작업을 수행합니다.

### Get-PSSessionCapability
JEA 끝점을 통한 지정된 사용자의 기능에 대해 수동으로 보고하는 것은 꽤 복잡할 수 있습니다.
몇 가지 역할 기능을 검사해야 할 수 있습니다.
다행히도 "Get-PSSessionCapability" cmdlet이 이 작업을 수행합니다.

이를 테스트하려면 관리자 PowerShell 프롬프트에서 다음 명령을 실행합니다.
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```




<!--HONumber=Jun16_HO4-->


