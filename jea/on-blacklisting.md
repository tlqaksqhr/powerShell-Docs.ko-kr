---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "블랙리스트에 올리기"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 8892e5e08a763fbc66d782bbc9252d1f3a7dcfcf

---

### 블랙리스트에 올리기
JEA를 사용하여 작업해 본 후 명령을 블랙리스트에 올리는 것이 가능한지 궁금할 수 있습니다.
이는 이해할 수 있는 요청이지만 블랙리스트에 올리는 기능은 다음과 같은 이유로 JEA에 대해 현재 계획되어 있지 않습니다.

1.  수행해야 하는 작업으로만 운영자를 제한하도록 JEA를 설계했습니다.
블랙 리스트는 이와 반대입니다.

2.  PowerShell 명령 작성자는 JEA를 염두에 두고 PowerShell 명령을 설계하지 않았습니다.
Windows Server 2016을 새로 설치한 경우 약 1520개의 명령을 즉시 사용할 수 있습니다.
이러한 명령에 대한 위협 모델에는 사용자가 권한이 더 많은 계정으로 명령을 실행할 것이라는 가능성이 포함되어 있지 않습니다.
예를 들어 특정 명령은 설계상 코드 주입을 고려합니다(예: 핵심 PowerShell 모듈의 Add-Type 및 Invoke-Command).
JEA는 Microsoft에서 알고 있는 특정 명령을 노출할 때 경고할 수 있지만, Microsoft에서는 새로운 위협 모델을 기초로 Windows의 다른 모든 명령을 다시 평가하지는 않았습니다.
JEA를 통해 노출하는 명령의 기능을 이해해야 합니다.  

3.  또한 JEA가 코드 주입에 취약한 모든 명령을 차단한다고 해도 악의적인 사용자가 블랙 리스트에 있는 작업을 다른 관련 명령으로 수행할 수 없다는 보장은 없습니다.
노출할 명령을 모두 이해하지 않는 한 특정 작업이 가능하지 않다고 보장하는 것은 불가능합니다.
허용 목록을 사용하든 블랙 리스트를 사용하든 간에 노출할 명령을 이해하는 것은 사용자의 책임입니다.
블랙 리스트로 노출할 명령 수는 관리할 수 없으므로 JEA는 대신 허용 목록을 사용하여 구현되었습니다.




<!--HONumber=Jun16_HO4-->


