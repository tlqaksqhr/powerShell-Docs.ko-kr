---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '공급자에 대해 Get을 직접 실행합니다.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_resourceget'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 클래스의 ResourceGet 메서드'
---

# MSFT_DSCLocalConfigurationManager 클래스의 ResourceGet 메서드

DSC 리소스의 **Get** 메서드를 직접 호출합니다.

구문
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

매개 변수
----------

*ResourceType* \[in\]  
호출할 리소스의 이름입니다.

*ModuleName* \[in\]  
호출할 리소스를 포함하는 모듈의 이름입니다.

*resourceProperty* \[in\]  
해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다. 리소스 속성 및 해당 값을 검색하려면
[Get-dscresource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet을 사용합니다.

*configurations* \[out\]  
반환 시 구성의 포함 인스턴스가 들어 있습니다.

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


