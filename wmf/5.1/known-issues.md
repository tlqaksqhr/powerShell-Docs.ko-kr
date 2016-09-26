---
title: "WMF 5.1(Preview)의 알려진 문제"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: f413ba6470985622e55bb4bd175d7c5d4b94c7d9
ms.openlocfilehash: e545d49381a92ef3f7cc6a27316cbfc3a036a8c9

---

#WMF 5.1(Preview)의 알려진 문제 #

> 참고: 이 정보는 임시로 제공되며 변경될 수 있습니다.

##Pester
이 릴리스에는 Nano Server의 Pester를 사용할 때 알아야 하는 두 가지 문제가 있습니다.

* Pester 자체에 대한 테스트를 실행하면 FULL CLR 및 CORE CLR 간의 차이로 인해 몇 가지 오류가 발생할 수 있습니다. 특히 XmlDocument 형식에는 Validate 메서드를 사용할 수 없습니다. NUnit 출력 로그의 스키마 유효성 검사를 시도하는 여섯 가지 테스트에서 오류가 발생하는 것으로 알려져 있습니다. 
* *WindowsFeature* DSC 리소스가 Nano Server에 없기 때문에 하나의 코드 검사 테스트에서 현재 오류가 발생합니다. 그러나 이러한 오류는 일반적으로 심각하지 않으며 무시해도 됩니다.

##작업 유효성 검사 

* 작동하지 않는 도움말 URI로 인해 Microsoft.PowerShell.Operation.Validation 모듈에 대해 Update-Help가 실패함



<!--HONumber=Sep16_HO3-->


