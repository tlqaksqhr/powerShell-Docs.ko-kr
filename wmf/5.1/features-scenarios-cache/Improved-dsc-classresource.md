---
title: "향상된 DSC 클래스 리소스"
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: b24e70c1e1aaf71487b00fbccaf6edb0f375b888

---

## 향상된 DSC 클래스 리소스

이 릴리스에서는 다음과 같은 WMF 5.0의 알려진 문제가 해결되었습니다.
* 클래스 기반 DSC 리소스의 Get() 함수에서 복합/해시 테이블 형식을 반환하는 경우 Get-DscConfiguration에서 빈 값(null) 또는 오류를 반환할 수 있습니다.
* DSC 구성에 RunAs 자격 증명이 사용된 경우 Get-DscConfiguration에서 오류를 반환합니다.
* 복합 구성에서는 클래스 기반 리소스를 사용할 수 없습니다.
* 클래스 기반 리소스에 자체 형식의 속성이 있는 경우 Start-DscConfiguration이 중단됩니다.
* 클래스 기반 리소스를 단독 리소스로 사용할 수 없습니다.



<!--HONumber=Jul16_HO3-->


