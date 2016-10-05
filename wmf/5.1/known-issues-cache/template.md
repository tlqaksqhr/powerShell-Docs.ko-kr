---
title: "알려진 문제 및 제한 사항 기록에 대한 예제 템플릿"
contributor: 
translationtype: Human Translation
ms.sourcegitcommit: a952a27ec1695ce9951c352446194cf72d18f50a
ms.openlocfilehash: cfe0a6562743f1df81acb81e33c120cb67f9042c

---

>참고: 제안된 설명이 포함된 제목과 간단한 설명을 제공합니다.

## 예: 잘못된 ExecutionPolicy 오류 ##
Windows 7에서 PowerShell 모듈 및 DSC 리소스를 사용하면 ExecutionPolicy에 대해 오류가 보고될 수 있습니다.

### 해결 방법

해결하려면 다음 명령을 관리자 권한 PowerShell 세션에서 실행(관리자 권한으로 실행)하여 **ExecutionPolicy**를 **RemoteSigned**로 설정합니다.

```powershell
Set-ExecutionPolicy RemoteSigned
```



<!--HONumber=Aug16_HO3-->


