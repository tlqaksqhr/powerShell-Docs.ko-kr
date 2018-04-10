---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: 알려진 문제 및 제한 사항 기록에 대한 예제 템플릿
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
>참고: 제안된 설명이 포함된 제목과 간단한 설명을 제공합니다.

## <a name="example-erroneous-executionpolicy-errors"></a>예: 잘못된 ExecutionPolicy 오류 ##
Windows 7에서 PowerShell 모듈 및 DSC 리소스를 사용하면 ExecutionPolicy에 대해 오류가 보고될 수 있습니다.

### <a name="resolution"></a>해결 방법

해결하려면 다음 명령을 관리자 권한 PowerShell 세션에서 실행(관리자 권한으로 실행)하여 **ExecutionPolicy**를 **RemoteSigned**로 설정합니다.

```powershell
Set-ExecutionPolicy RemoteSigned
```