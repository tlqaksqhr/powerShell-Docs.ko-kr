---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '구성 파일을 제거하는 중입니다.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_removeconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 클래스의 RemoveConfiguration 메서드'
---

# MSFT_DSCLocalConfigurationManager 클래스의 RemoveConfiguration 메서드

구성 파일을 제거합니다.

구문
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

매개 변수
----------

*Stage* \[in\]  
제거할 구성 문서를 지정합니다. 다음은 유효한 값입니다.

|Value |설명 |
|:--- |:---|
|**1** | **현재** 구성 문서(current.mof)입니다. |
|**2** | **보류 중인** 구성 문서(pending.mof)입니다.  |
|**4** | **이전** 구성 문서(previous.mof)입니다. |

*Force* \[in\]  
**true**이면 구성을 강제로 제거합니다.

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


