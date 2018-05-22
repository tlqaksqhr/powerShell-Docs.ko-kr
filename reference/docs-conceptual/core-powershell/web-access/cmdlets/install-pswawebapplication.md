---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>요약

IIS에서 Windows PowerShell® 웹 액세스 웹 응용 프로그램을 구성합니다.

## <a name="syntax"></a>구문

### <a name="default"></a>Default
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>설명

**Install-PswaWebApplication** cmdlet은 Windows PowerShell 웹 액세스 웹 응용 프로그램을 구성합니다. 이 cmdlet은 웹 응용 프로그램을 설치하고, 웹 사이트와 연결하고, 선택적으로 **useTestCertificate** 매개 변수를 사용하여 테스트 SSL 인증서를 만듭니다. 보안을 위해 웹 관리자는 테스트 인증서는 프로덕션 환경에서만 사용해야 합니다.

## <a name="parameters"></a>매개 변수

### <a name="-usetestcertificate"></a>-UseTestCertificate

테스트 인증서를 만들도록 지정합니다. 이 매개 변수를 true로 설정하면 이 cmdlet은 테스트 인증서를 만들고 HTTPS 요청에 이 인증서를 사용하도록 Windows PowerShell 웹 액세스 웹 응용 프로그램을 구성합니다. 이 매개 변수를 false로 설정하면 인증서나 바인딩을 만들지 않습니다. Windows PowerShell 웹 액세스에 다른 인증서를 사용하는 경우 이 값을 false로 설정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | true                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;String&gt;

웹 응용 프로그램 이름을 지정합니다. Windows PowerShell 웹 액세스 URL의 마지막 부분으로 표시됩니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 1                                    |
| 기본값                        | pswa                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-websitenameltstringgt"></a>-WebSiteName&lt;String&gt;

이 Windows PowerShell 웹 액세스 웹 응용 프로그램 설치할 웹 서버(IIS) 웹 사이트의 이름을 지정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | Default Web Site                     |
| 파이프라인 입력 적용 여부               | false                                |
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

cmdlet이 실행될 경우 결과 동작을 표시합니다.
cmdlet이 실행되지 않습니다.

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

이 cmdlet은 입력이 없습니다.

## <a name="outputs"></a>출력

이 cmdlet은 출력을 생성하지 않습니다.

## <a name="examples"></a>예제

### <a name="example-1"></a>예제 1

이 예제에서는 **WebApplicationName**(*pswa*) 및 **WebSiteName**(*Default Web Site*) 매개 변수의 기본값을 사용하여 PSWA 웹 응용 프로그램을 설치합니다.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>예제 2

이 예제에서는 **WebApplicationName** 및 **WebSiteName** 매개 변수의 기본값을 사용하고 테스트 인증서를 사용하여 PSWA 웹 응용 프로그램을 설치합니다.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>관련 항목

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)