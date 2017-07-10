---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드

구성 상태 기록을 가져옵니다.

<a id="syntax" class="xliff"></a>
구문
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a id="parameters" class="xliff"></a>
매개 변수
----------

*All* \[in\]  
이 메서드가 구성 응용 프로그램 및 일관성 확인을 포함하여 컴퓨터에서 실행되는 모든 구성에 관한 정보를 반환하면 **true**입니다.

*configurationStatus* \[out\]  
반환 시 설정을 정의하는 **MSFT_DSCConfigurationStatus** 클래스의 포함 인스턴스가 들어 있습니다.

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


 

 



