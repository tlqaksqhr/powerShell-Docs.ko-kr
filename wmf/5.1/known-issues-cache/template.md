---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: "알려진 문제 및 제한 사항 기록에 대한 예제 템플릿"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="f433f-103">참고: 제안된 설명이 포함된 제목과 간단한 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f433f-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="f433f-104">예: 잘못된 ExecutionPolicy 오류</span><span class="sxs-lookup"><span data-stu-id="f433f-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="f433f-105">Windows 7에서 PowerShell 모듈 및 DSC 리소스를 사용하면 ExecutionPolicy에 대해 오류가 보고될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f433f-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="f433f-106">해결 방법</span><span class="sxs-lookup"><span data-stu-id="f433f-106">Resolution</span></span>

<span data-ttu-id="f433f-107">해결하려면 다음 명령을 관리자 권한 PowerShell 세션에서 실행(관리자 권한으로 실행)하여 **ExecutionPolicy**를 **RemoteSigned**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f433f-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

