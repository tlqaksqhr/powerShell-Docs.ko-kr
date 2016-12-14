---
title: "MSFT_DSCLocalConfigurationManager 클래스의 ApplyConfiguration 메서드"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 6f9c6a8851732574ac72bc4f3a3db1a73fbbecf2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 클래스의 ApplyConfiguration 메서드

구성 에이전트를 사용해 보류 중인 구성을 적용합니다. 

보류 중인 구성이 없으면 이 메서드는 현재 구성을 다시 적용합니다.


## <a name="syntax"></a>구문
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>매개 변수
----------

*force* \[in\]  
**true**인 경우 현재 구성이 다시 적용됩니다. 보류 중인 구성이 있더라도 마찬가지입니다.

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

 

 



