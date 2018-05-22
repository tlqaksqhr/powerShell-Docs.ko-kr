---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Test-PswaAuthorizationRule
ms.openlocfilehash: 08248e65be229f9d0f4d606d6c0d039d86ced054
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>요약

지정된 사용자, 컴퓨터 또는 끝점에 대한 규칙이 있는지 확인합니다.

## <a name="syntax"></a>구문

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>설명

**Test-pswaauthorizationrule** cmdlet은 지정된 사용자, 컴퓨터 또는 끝점에 대한 규칙이 있는지 확인합니다.
권한 부여 규칙을 테스트하여 특정 사용자, 컴퓨터, 끝점 액세스 요청이 인증되었는지 확인하는 데에 이 cmdlet을 사용할 수도 있습니다.
기본적으로 이 cmdlet은 권한 부여 파일의 규칙을 모두 평가하지만,
규칙의 하위 집합을 지정하여 테스트할 수도 있습니다.

이 cmdlet을 사용하여 인증 오류 문제를 해결할 수도 있습니다.

이 cmdlet의 매개 변수는 Windows PowerShell® 웹 액세스 로그온 페이지의 필드에 해당합니다.

## <a name="parameters"></a>매개 변수

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;String&gt;

테스트할 컴퓨터의 이름을 지정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 2                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;String&gt;

테스트할 Windows PowerShell 세션 구성(끝점 또는 runspace라고도 함)의 이름을 지정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 3                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

테스트할 연결 URI를 지정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 2                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Windows PowerShell 웹 액세스 권한 부여 규칙을 테스트하는 데 사용할 사용자 계정에 대한 **PSCredential** 개체를 지정합니다. 이 매개 변수를 추가하지 않으면 현재 로그온한 사용자 계정이 사용됩니다. 권한 부여 규칙을 원격으로 테스트하는 데 필요한 **PSCredential**을 가져오려면 [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet을 실행합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

테스트할 규칙의 하위 집합을 지정합니다. 이 매개 변수를 지정하지 않으면 이 cmdlet은 모든 권한 부여 규칙을 기준으로 테스트합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByValue)                       |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;String&gt;

테스트할 사용자의 이름을 지정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 1                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.
자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.

## <a name="inputs"></a>입력

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

이 cmdlet은 PswaAuthorizationRule 개체 배열을 입력으로 사용합니다.

## <a name="outputs"></a>출력

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

이 cmdlet은 PswaAuthorizationRule 개체의 배열을 출력으로 생성합니다.

## <a name="examples"></a>예제

### <a name="example-1"></a>예제 1

이 예제에서는 *contoso\\mhanson* 사용자가 *srv2* 컴퓨터에 연결하고 *test*라는 Windows PowerShell 세션 구성을 사용할 수 있도록 허용하는 모든 규칙을 표시하기 위해 모든 권한 부여 규칙을 테스트합니다.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>예제 2

이 예제에서는 *contoso\\mhanson* 사용자에 적용되는 권한 부여 규칙을 확인하기 위해 모든 권한 부여 규칙을 테스트합니다.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>관련 항목

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)