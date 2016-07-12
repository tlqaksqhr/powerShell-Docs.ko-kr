---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "명령을 제한하는 경우의 고려 사항"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 9f3f79a29e0fb7ec5a5111284bb7985548e17749

---

### 명령을 제한하는 경우의 고려 사항
이 단계에 대해 유의할 한 가지 중요한 사항이 있습니다.
JEA를 통해 노출된 모든 기능이 관리자 제한 영역에 위치해야 합니다.
관리자가 아닌 사용자는 JEA 끝점을 통해 사용된 스크립트를 수정할 수 없어야 합니다.

이와 관련하여 JEA 사용자에게 자신의 JEA 세션 내에서 JEA 구성 및 허용된 스크립트를 덮어쓰는 기능을 제공하지 않아야 합니다.
`Copy-Item`과 같은 명령을 노출하는 경우에는 특히 주의하세요.




<!--HONumber=Jul16_HO1-->


