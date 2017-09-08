---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: add pswaauthorizationrule
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 12f5cc30d4e3f9cfdd739cacbbab96134077e50a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2017
---
#  <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

##  <a name="synopsis"></a>요약

새로운 권한 부여 규칙을 Windows PowerShell® 웹 액세스 권한 부여 규칙 집합에 추가합니다.

## <a name="syntax"></a>구문

###  <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usergroupnamecomputername"></a>UserGroupNameComputerName
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputergroupname"></a>UserNameComputerGroupName
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputername"></a>UserNameComputerName
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>설명

**Add-PswaAuthorizationRule** cmdlet은 새로운 권한 부여 규칙을 Windows PowerShell® 웹 액세스 권한 부여 규칙 집합에 추가합니다.

이 규칙에 대한 사용자, 컴퓨터 및 Windows PowerShell 끝점을 지정해야 합니다. 개별 사용자 및 컴퓨터 이름을 지정하거나 그룹을 지정하여 사용자 및 컴퓨터를 모두 지정할 수 있습니다.

Active Directory 도메인에 가입된 컴퓨터의 경우 이 cmdlet은 컴퓨터의 SID(보안 식별자)를 사용하여 규칙을 만듭니다.
따라서 로그인 페이지의 **컴퓨터 이름** 필드에 약식 이름, FQDN(정규화된 도메인 이름 ) 또는 IP 주소를 사용할 수 있습니다.

Active Directory 도메인에 가입되지 않은 컴퓨터의 경우 이 cmdlet은 관리자가 제공한 컴퓨터 이름을 사용하여 규칙을 만듭니다. 이 컴퓨터에 연결하려면 최종 사용자는 컴퓨터 이름을 규칙에 표시된 대로 정확히 입력해야 합니다.

네트워크에서 같은 이름의 컴퓨터가 여럿 있는 경우에는 약식 이름을 사용하여 둘 이상의 컴퓨터를 확인할 수 있습니다. 따라서 연결을 설정할 때 모호해질 수 있습니다. 예를 들어 "*Server1*"이라는 작업 그룹 컴퓨터에 대한 규칙이 있고 *server1.contoso.com*이라는 새 컴퓨터가 네트워크에 가입된 경우 권한 부여 규칙을 사용한 유효성 검사가 성공하고 Windows PowerShell 웹 액세스가 "*Server1*"이라는 컴퓨터에 대한 연결을 설정하려고 합니다. 지정된 작업 그룹 컴퓨터와의 연결이 설정된다는 보장은 없으며, 작업 그룹 또는 "*Server1*"이라는 도메인 컴퓨터에 대해 연결이 시도될 수 있습니다. 모호성을 줄이기 위해 가능하면 대상 컴퓨터의 FQDN을 사용하여 권한 부여 규칙을 만드는 것이 좋습니다.

권한 부여 규칙에서는 대체 자격 증명(로그인 페이지의 **옵션 연결 설정** 섹션에 있는 두 번째 자격 증명 집합)이 아니라 Windows PowerShell 웹 액세스 사용자의 기본 로그인 자격 증명을 평가합니다. 관련 예제는 예제 6을 참조하세요.

## <a name="parameters"></a>매개 변수

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;String&gt;

이 규칙이 액세스 권한을 부여하는 AD DS(Active Directory 도메인 서비스)의 컴퓨터 그룹 또는 로컬 그룹의 이름을 지정합니다.

|||  
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByPropertyName)                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;String&gt;

이 규칙이 액세스 권한을 부여하는 컴퓨터 이름을 지정합니다.

|||  
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByPropertyName)                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;String&gt;

이 규칙이 액세스 권한을 부여하는 Windows PowerShell 세션 구성(runspace라고도 함)의 이름을 지정합니다.

|||  
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByPropertyName)                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Windows PowerShell 웹 액세스 권한 부여 규칙을 변경하는 데 사용할 사용자 계정에 대한 **PSCredential** 개체를 지정합니다. 이 매개 변수를 추가하지 않으면 현재 로그온한 사용자 계정이 사용됩니다. 권한 부여 규칙을 추가하는 데 필요한 **PSCredential**을 가져오려면 [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet을 실행합니다.

|||  
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-force"></a>-Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.\
또한, 단순하거나 짧은 컴퓨터 이름(예: 도메인 이름이 아니거나 정규화되지 않은 이름)을 입력할 경우 확인하는 메시지도 표시합니다. 확인은 보안 때문에 필요하므로 컴퓨터가 작업 그룹에 있는 경우에만 단순 이름을 사용하여 컴퓨터를 추가할 수 있습니다.

|||  
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | false                                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String&gt;

이 규칙의 이름을 지정합니다.

|||  
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | false                                |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByPropertyName)                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;String\[\]&gt;

이 규칙이 액세스 권한을 부여하는 AD DS의 사용자 그룹 하나 이상 또는 로컬 그룹의 이름을 지정합니다.

|||  
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 명명됨                                |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByPropertyName)                |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;String\[\]&gt;

이 규칙이 액세스 권한을 부여하는 하나 이상의 사용자를 지정합니다. 사용자 이름은 게이트웨이 컴퓨터의 로컬 사용자 계정 또는 AD DS의 사용자일 수 있습니다.
형식은 `domain\user` 또는 `computer\user`입니다.

|||  
|-|-|
| 별칭                              | 없음                                 |
| 필수 여부                            | true                                 |
| 위치                            | 1                                    |
| 기본값                        | 없음                                 |
| 파이프라인 입력 적용 여부               | True (ByValue, ByPropertyName)       |
| 와일드카드 문자 허용 여부          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.
자세한 내용은 [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters)를 참조하세요.

## <a name="inputs"></a>입력

###  <a name="string"></a>문자열

이 cmdlet은 문자열 또는 문자열 배열을 입력으로 사용합니다.

###  <a name="string"></a>String\[\]

이 cmdlet은 문자열 또는 문자열 배열을 입력으로 사용합니다.

##  <a name="outputs"></a>출력

###   <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

이 cmdlet은 권한 부여 규칙 개체를 반환합니다.

## <a name="examples"></a>예제

### <a name="example-1"></a>예제 1

이 예제에서는 *srv2*에서 *SMAdmins* 그룹의 사용자에게 세션 구성 *PSWAEndpoint*(제한된 runspace)에 대한 액세스 권한을 부여합니다.\
**참고**: 컴퓨터 이름은 FQDN(정규화된 도메인 이름)이어야 합니다. 관리자는 최종 사용자가 실행할 수 있는 제한된 범위의 cmdlet 및 작업인 제한 세션 구성 또는 runspace를 정의합니다. 제한된 runspace를 정의하면 사용자가 허용된 Windows PowerShell® runspace에 없는 다른 컴퓨터에 액세스하지 못하므로 더 안전한 연결을 제공합니다. 세션 구성에 대한 자세한 내용은 [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) 또는 [Windows PowerShell 웹 액세스 설치 및 사용](../install-and-use-windows-powershell-web-access.md)을 참조하세요.

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>예제 2

이 예제에서는 *srv2*에서 contoso\\user1, contoso\\user2 및 contoso\\user3이라는 사용자에게 기본 Windows PowerShell 세션 구성 `Microsoft.PowerShell`에 대한 액세스 권한을 부여합니다. 이 cmdlet은 세 개의 규칙(사용자당 1개)을 만듭니다.

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>예제 3

이 예제에서는 파이프라인을 통해 사용자 이름 값을 입력하는 방법을 보여 줍니다.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>예제 4

이 예제에서는 모든 매개 변수의 값을 속성 이름별로 파이프라인에서 가져오는 방법을 설명합니다.

\
###   <a name="section-subheading"></a>{#section .subHeading}

<div class="subSection">

<div id="code-snippet-5" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f'); "클립보드에 복사.")

</div>

</div>

<div id="CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o = New-Object -TypeName PSObject | Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

</div>

</div>

</div>

</div>

</div>

###   <a name="section-1-subheading"></a>{#section-1 .subHeading}

<div class="subSection">

<div id="code-snippet-6" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb'); "클립보드에 복사.")

</div>

</div>

<div id="CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

</div>

### <a name="example-5-example-5-subheading"></a>예제 5 {#example-5 .subHeading}

<div class="subSection">

이 예제에서는 *PswaServer\\ChrisLocal*이라는 로컬 사용자가 *srv1.contoso.com*이라는 서버에 액세스할 수 있도록 규칙을 추가합니다.

이 예제에서는 게이트웨이가 작업 그룹에 있고 대상 컴퓨터가 도메인에 있는 시나리오를 보여 줍니다. 권한 부여 규칙은 게이트웨이의 로컬 사용자에게 적용됩니다. Windows PowerShell 웹 액세스 로그인 페이지에서 인증하려면 사용자는 **옵션 연결 설정** 영역의 두 번째 자격 증명 집합을 입력해야 합니다. 게이트웨이 서버는 추가 자격 증명 집합을 사용하여 대상 컴퓨터인 *srv1.contoso.com*이라는 서버에서 사용자를 인증합니다.

\
<div id="code-snippet-7" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3'); "클립보드에 복사.")

</div>

</div>

<div id="CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

### <a name="example-6-example-6-subheading"></a>예제 6 {#example-6 .subHeading}

<div class="subSection">

이 예제에서는 모든 사용자가 모든 컴퓨터의 모든 끝점에 액세스할 수 있도록 합니다.
여기서는 기본적으로 권한 부여 규칙을 끕니다.\
**참고**: `*` 와일드카드 문자는 보안이 중요한 배포에서는 사용하지 않는 것이 좋으며 테스트 환경에서나 보안을 완화할 수 있는 배포에서만 사용해야 합니다.

\
<div id="code-snippet-8" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076'); "클립보드에 복사.")

</div>

</div>

<div id="CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *

</div>

</div>

</div>

</div>

</div>

</div>

<a name="related-topics"></a>관련 항목 
--------------


[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\
\
[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\
\
[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\
\
[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\
\
[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\
\
[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\
\
[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)