---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 74c044c329d8b6a305b86c9056a7041fb5fd046b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>요약

일련의 Windows PowerShell® 웹 액세스 권한 부여 규칙을 반환합니다.

## <a name="syntax"></a>구문

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>이름
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>설명

**Get-PswaAuthorizationRule** cmdlet은 Windows PowerShell® 웹 액세스 권한 부여 규칙의 집합을 반환합니다.
**Id** 매개 변수나 **RuleName** 매개 변수 중 아무것도 지정하지 않으면 모든 규칙이 나열됩니다. **Id** 매개 변수를 사용하여 결과를 필터링할 수 있습니다.

## <a name="parameters"></a>매개 변수

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

이 cmdlet이 가져올 규칙의 ID(식별자)를 지정합니다. ID를 지정하지 않으면 모든 권한 부여 규칙을 반환합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 2                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByValue, ByPropertyName)       |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String\[\]&gt;

검색할 권한 부여 규칙의 이름을 지정합니다. 이 매개 변수는 이 배열에 있는 문자열의 규칙 이름과 정확히 일치하는 모든 규칙을 반환합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 2                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByValue, ByPropertyName)       |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.
자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.

## <a name="inputs"></a>입력

### <a name="int"></a>int\[\]

이 cmdlet은 정수 배열 또는 문자열 값 배열을 입력으로 사용합니다.

### <a name="string"></a>String\[\]

이 cmdlet은 정수 배열 또는 문자열 값 배열을 입력으로 사용합니다.

## <a name="outputs"></a>출력

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

이 cmdlet은 PswaAuthorizationRule 개체를 출력으로 생성합니다.


## <a name="examples"></a>예제

### <a name="example-1"></a>예제 1

이 예제에서는 모든 규칙을 가져옵니다.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>예제 2

이 예제에서는 ID가 *2*인 규칙을 가져옵니다.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>예제 3 {#example-3 .subHeading}

이 예제에서는 cmdlet에서 파이프라인의 값을 사용하는 방법을 보여 줍니다.
이 cmdlet에서는 규칙 ID와 규칙 이름이 전달됩니다.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>관련 항목

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)