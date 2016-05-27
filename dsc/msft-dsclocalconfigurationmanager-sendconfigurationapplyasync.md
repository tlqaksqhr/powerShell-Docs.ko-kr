---
title:  MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApplyAsync 메서드
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---


# MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApplyAsync 메서드

구성 문서를 비동기적으로 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.

구문
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

매개 변수
----------

*ConfigurationData* \[in\]  
구성에 대한 환경 데이터입니다.

*force* \[in\]  
**true**이면 구성을 강제로 중지합니다.

*jobId* \[in\]  
구성을 보낼 작업의 ID입니다.

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


 

 





<!--HONumber=May16_HO3-->


