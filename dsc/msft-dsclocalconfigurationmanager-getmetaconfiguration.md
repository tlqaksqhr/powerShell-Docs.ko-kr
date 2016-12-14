---
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetMetaConfiguration 메서드"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 4662bfed62fce47be7d42a083ad5a7be801e6ff1
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 클래스의 GetMetaConfiguration 메서드

구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 가져옵니다.

<a name="syntax"></a>구문
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a>매개 변수
----------

*MetaConfiguration* \[out\]  
반환 시 설정을 정의하는 **MSFT_DSCMetaConfiguration** 클래스의 포함 인스턴스가 들어 있습니다.

## <a name="return-value"></a>반환 값
------------

성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

정적 메서드입니다.

## <a name="requirements"></a>요구 사항
------------
>**MOF:** DscCore.mof

>**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>참고 항목


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



