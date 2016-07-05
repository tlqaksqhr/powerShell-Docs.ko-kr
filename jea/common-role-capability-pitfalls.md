---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "일반적인 역할 기능 문제"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0e221c840f083ce0b8ecbcbb34c184bcdbc0c73e

---

### 일반적인 역할 기능 문제
이 프로세스를 직접 진행할 때 몇 가지 일반적인 문제가 발생할 수 있습니다.
새 끝점을 수정하거나 만들 때 이러한 문제를 식별하고 수정하는 방법을 설명하는 간단한 지침은 다음과 같습니다.

#### 함수와 Cmdlet
PowerShell에서 작성된 PowerShell 명령이 PowerShell 함수이고,
특수화된 .NET 클래스로 작성된 PowerShell 명령이 PowerShell Cmdlet입니다.
`Get-Command`를 실행하여 명령 유형을 확인할 수 있습니다.

#### VisibleProviders
명령에 필요한 공급자를 노출해야 합니다.
가장 일반적인 공급자는 FileSystem 공급자이지만 레지스트리 공급자 등의 다른 공급자도 노출해야 할 수 있습니다.
공급자에 대한 소개는 [Hey, Scripting Guy 블로그 게시물](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)을 참조하세요.
공급자를 노출할 때 JEA 세션에서 공급자를 직접 노출하는 대신 기본 공급자와 작동하는 함수를 직접 정의하는 것이 효과적인 경우가 많습니다.
이러한 방식으로 사용자가 파일, 레지스트리 키 등을 사용하여 작업하도록 계속 허용할 수 있지만 사용자 지정 유효성 검사 논리를 사용하여 작업할 수 있는 파일 및 레지스트리 키 **항목**에 대한 제어를 유지할 수 있습니다.




<!--HONumber=Jun16_HO4-->


