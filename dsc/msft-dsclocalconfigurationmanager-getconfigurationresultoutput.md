---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationResultOutput 메서드"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationResultOutput 메서드

특정 작업에 연결된 구성 에이전트 출력을 검색합니다.

<a id="syntax" class="xliff"></a>
구문
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a id="parameters" class="xliff"></a>
매개 변수
----------

*jobId* \[in\]  
출력 데이터를 가져올 작업의 ID입니다.

*resumeOutputBookmark* \[in\]  
출력이 이전 책갈피의 연속이어야 함을 지정합니다.

*output* \[out\]  
지정한 작업의 출력입니다.

<a id="return-value" class="xliff"></a>
## 반환 값
------------

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

<a id="remarks" class="xliff"></a>
## 설명

정적 메서드입니다.

<a id="requirements" class="xliff"></a>
## 요구 사항
------------
>**MOF:** DscCore.mof

>**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## 참고 항목


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

 

 



