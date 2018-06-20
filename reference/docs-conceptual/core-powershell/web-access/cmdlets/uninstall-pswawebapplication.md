---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Uninstall-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221921"
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>요약

Windows PowerShell® 웹 응용 프로그램을 제거합니다.

## <a name="syntax"></a>구문

### <a name="default"></a>Default
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>설명

**Uninstall-PswaWebApplication** cmdlet은 Windows PowerShell 웹 응용 프로그램을 제거하고 IIS에서 해당 웹 사이트를 제거합니다. 이 cmdlet은 IIS나 Windows PowerShell 실행에 필요한 다른 설치된 기능은 제거하지 않습니다.

## <a name="parameters"></a>매개 변수

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

**Install\_PswaWebApplication** cmdlet(**UseTestCertificate** 매개 변수 사용)으로 만든 테스트 인증서를 삭제하도록 지정합니다.
**Install-PswaWebApplication** cmdlet으로 만든 인증서와 이름이 같은 테스트 인증서만 제거됩니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | true                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;String&gt;

제거할 웹 응용 프로그램의 이름을 지정합니다.

|||
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 1                                    |
| 기본값                        | pswa                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;String&gt;

웹 응용 프로그램이 설치되어 있는 웹 사이트의 이름을 지정합니다.

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

이 cmdlet은 출력을 반환하지 않습니다.

## <a name="examples"></a>예제

### <a name="example-1"></a>예제 1

이 명령은 Windows PowerShell 웹 응용 프로그램을 제거합니다.
Windows PowerShell 웹 응용 프로그램을 설치할 때 기본값을 사용한 경우 제거할 때 이 cmdlet을 사용할 수 있습니다.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>예제 2

이 명령은 Windows PowerShell 웹 응용 프로그램을 제거하고 응용 프로그램과 연결된 테스트 인증서를 삭제합니다.
Windows PowerShell 웹 응용 프로그램을 설치할 때 기본값을 사용하고 테스트 인증서를 만든 경우 제거할 때 이 cmdlet을 사용할 수 있습니다.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>예제 3 {#example-3 .subHeading}

Windows PowerShell 웹 응용 프로그램을 설치할 때 사용자 지정 웹 사이트 및 응용 프로그램을 지정한 경우 제거할 때 이 명령을 사용합니다.
이 명령은 *MySite*라는 웹 사이트와 *TestApplication*이라는 응용 프로그램을 제거하고 응용 프로그램과 연결된 테스트 인증서도 삭제하도록 지정합니다.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>관련 항목

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)