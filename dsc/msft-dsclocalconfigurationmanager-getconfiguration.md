---
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetConfiguration 메서드"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 919438862ca9786447b690d2db10e905da0a7c42
ms.openlocfilehash: 19d4790f22491e0bb11de1e315d1ee3b07929d55

---

# MSFT_DSCLocalConfigurationManager 클래스의 GetConfiguration 메서드

구성 문서를 관리 노드로 보내고, 구성 에이전트의 **Get** 메서드를 사용해 구성을 적용합니다.

구문
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

매개 변수
----------

*configurationData* \[in\]  
보낼 구성 데이터를 지정합니다.

*configurations* \[out\]  
반환 시 구성의 포함 인스턴스가 들어 있습니다.

## 반환 값
------------

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## 설명

정적 메서드입니다.

## 요구 사항
------------
>**MOF:** DscCore.mof

>**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration


## 참고 항목


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
 

 






<!--HONumber=Jun16_HO4-->


