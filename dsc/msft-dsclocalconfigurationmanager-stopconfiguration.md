---
title: "MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 9721486cca6f94d6b156c6ee1992eced6652c123

---

# MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드

진행 중인 구성 변경을 중지합니다.

구문
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

매개 변수
----------

*force* \[in\]  
**true**이면 구성을 강제로 중지합니다.

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


