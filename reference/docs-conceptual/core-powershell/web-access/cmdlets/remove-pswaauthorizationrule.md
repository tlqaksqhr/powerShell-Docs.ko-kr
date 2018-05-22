---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>요약

지정된 권한 부여 규칙을 Windows PowerShell® 웹 액세스에서 제거합니다.

## <a name="syntax"></a>구문

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>규칙
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>설명

지정된 권한 부여 규칙을 Windows PowerShell 웹 액세스에서 제거합니다.

## <a name="parameters"></a>매개 변수

### <a name="-force"></a>-Force

확인 메시지를 표시하지 않고 cmdlet을 실행합니다. 기본적으로 cmdlet에서는 계속 진행하기 전에 확인하는 메시지를 표시합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

제거할 규칙 하나 이상의 ID(식별자)를 지정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 2                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByValue, ByPropertyName)       |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

제거할 규칙을 지정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 2                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByValue)                       |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-confirm"></a>-Confirm

cmdlet을 실행하기 전에 확인 메시지가 표시됩니다.

|||
|-|-|
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | false                                |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-whatif"></a>-WhatIf

cmdlet이 실행될 경우 결과 동작을 표시합니다. cmdlet이 실행되지 않습니다.

|||
|-|-|
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | false                                |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.
자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.

## <a name="inputs"></a>입력

### <a name="int"></a>int\[\]

이 cmdlet은 정수 배열 또는 PswaAuthorizationRule 개체의 배열을 허용합니다.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

이 cmdlet은 정수 배열 또는 PswaAuthorizationRule 개체의 배열을 허용합니다.

## <a name="outputs"></a>출력

이 cmdlet은 출력을 생성하지 않습니다.

## <a name="examples"></a>예제

### <a name="example-1"></a>예제 1

이 예제에서는 ID가 *2*인 권한 부여 규칙을 제거합니다.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>예제 2 {#example-2 .subHeading}

이 예제에서는 권한 부여 규칙을 모두 제거하고 사용자의 확인도 요청합니다.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>관련 항목

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)