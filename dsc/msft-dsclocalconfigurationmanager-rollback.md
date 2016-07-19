---
title: "MSFT_DSCLocalConfigurationManager 클래스의 RollBack 메서드"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 771a9c7b50aba26f89dbf6b24eb3df67bafeac0a

---


# MSFT_DSCLocalConfigurationManager 클래스의 RollBack 메서드

이전 버전으로 구성을 롤백합니다.

구문
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

매개 변수
----------

*configurationNumber* \[in\]  
요청한 구성을 지정합니다. 

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


