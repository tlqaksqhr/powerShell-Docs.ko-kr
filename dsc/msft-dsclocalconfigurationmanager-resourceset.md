---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 ResourceSet 메서드"
ms.openlocfilehash: 9cd9c1b3f58a5862db6c4eea0488423b8dfe7310
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="resourceset-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 클래스의 ResourceSet 메서드

DSC 리소스의 **Set** 메서드를 직접 호출합니다.

<a id="syntax" class="xliff"></a>
구문
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a id="parameters" class="xliff"></a>
매개 변수
----------

*ResourceType* \[in\]  
호출할 리소스의 이름입니다.

*ModuleName* \[in\]  
호출할 리소스를 포함하는 모듈의 이름입니다.

*resourceProperty* \[in\]  
해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다. [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.

*RebootRequired* \[out\]  
반환 시, 대상 노드를 다시 부팅해야 하면 이 속성이 **true**로 설정됩니다.

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

 

 



