---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '구성 문서를 관리 노드로 보내고, 현재 구성에 대해 테스트합니다.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_testconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 클래스의 TestConfiguration 메서드'
---

# MSFT_DSCLocalConfigurationManager 클래스의 TestConfiguration 메서드

구성 문서를 관리 노드로 보내고, 문서에 대해 현재 구성을 확인합니다.

구문
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

매개 변수
----------

*configurationData* \[in\]  
구성에 대한 환경 데이터입니다.

*InDesiredState* \[out\]  
반환 시, 관리 노드가 구성 문서에서 지정한 상태인지 여부를 지정합니다.

*ResourcesInDesiredState* \[out\]  
반환 시, 원하는 상태인 리소스를 지정하는 **MSFT_ResourceInDesiredState** 클래스의 포함 인스턴스가 들어 있습니다.

*ResourcesNotInDesiredState* \[out\]  
반환 시, 원하는 상태가 아닌 리소스를 지정하는 **MSFT_ResourceNotInDesiredState** 클래스의 포함 인스턴스가 들어 있습니다.

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


 

 





<!--HONumber=Apr16_HO2-->


