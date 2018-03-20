---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 ResourceTest 메서드"
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 클래스의 ResourceTest 메서드

DSC 리소스의 **Test** 메서드를 직접 호출합니다.

<a name="syntax"></a>구문
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a>매개 변수
----------

*ResourceType* \[in\]  
호출할 리소스의 이름입니다.

*ModuleName* \[in\]  
호출할 리소스를 포함하는 모듈의 이름입니다.

*resourceProperty* \[in\]  
해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다. [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.

*InDesiredState* \[out\]  
반환 시, 대상 노드가 원하는 상태이면 이 속성이 **true**로 설정됩니다.

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


 

 



