---
title: "MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 919438862ca9786447b690d2db10e905da0a7c42
ms.openlocfilehash: f74e9941180c00a1aae1bd1d7b48fa4de0c8790d

---


# MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드

DSC 리소스 디버깅을 사용하도록 설정합니다.

구문
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

매개 변수
----------

*BreakAll* \[in\]  
리소스 스크립트의 모든 줄에 중단점을 설정합니다.

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


