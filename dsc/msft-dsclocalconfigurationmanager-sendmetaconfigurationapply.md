---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 SendMetaConfigurationApply 메서드"
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 클래스의 SendMetaConfigurationApply 메서드

구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 구성합니다.

<a id="syntax" class="xliff"></a>
구문
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
매개 변수
----------

*ConfigurationData* \[in\]  
구성에 대한 환경 데이터입니다.

*force* \[in\]  
**true**이면 구성을 강제로 중지합니다.

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


 

 



