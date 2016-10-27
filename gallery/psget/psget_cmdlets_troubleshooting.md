---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: psget_cmdlets_troubleshooting
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 740c72620e1a5a114716f924f859c57cad125614

---

## "경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법




Install-Module 또는 Update-Module이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다.
조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다.
최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다.
아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다.
아래에서는 'Azure' 모듈을 예로 사용합니다.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```




<!--HONumber=Oct16_HO2-->


