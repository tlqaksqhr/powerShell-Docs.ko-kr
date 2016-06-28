---
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: b430e98c7ec287c0efcf2c2e2736253797242904

---

# MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드

구성 상태 기록을 가져옵니다.

구문
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

매개 변수
----------

*All* \[in\]  
이 메서드가 구성 응용 프로그램 및 일관성 확인을 포함하여 컴퓨터에서 실행되는 모든 구성에 관한 정보를 반환하면 **true**입니다.

*configurationStatus* \[out\]  
반환 시 설정을 정의하는 **MSFT_DSCConfigurationStatus** 클래스의 포함 인스턴스가 들어 있습니다.

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


