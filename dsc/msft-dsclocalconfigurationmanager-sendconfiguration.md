---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드
ms.openlocfilehash: b4d4c901268344ba67d77e4dc982042bfc2abd78
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드

구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.

<a name="syntax"></a>구문
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>매개 변수
----------

*ConfigurationData* \[in\] 구성에 대한 환경 데이터입니다.

*force* \[in\] **true**이면 구성을 강제로 중지합니다.

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