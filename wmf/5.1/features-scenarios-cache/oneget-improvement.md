---
title: "향상된 PackageManagement(OneGet이라고도 함)"
contributor: jianyunt, quoctruong
translationtype: Human Translation
ms.sourcegitcommit: 3b5a3bb0ef9cf123c0cee4a36890ac61431c85ff
ms.openlocfilehash: bb1129e6aa20b64e94ddb6d7b7cf7b51b1df9ca3

---

>참고: 제안된 설명이 포함된 제목과 간단한 설명을 제공합니다.

## 향상된 PackageManagement(OneGet이라고도 함) ##
다음은 WMF 5.0의 일부 사용자 환경 차이를 해결하기 위해 WMF 5.1에서 만든 수정입니다. 

1 **버전 별칭**

**시나리오**: 시스템에 P1 패키지의 버전 1.0 및 2.0이 설치되어 있고 이제 버전 1.0을 제거하려고 "uninstall-package -name P1 -version 1.0"을 실행한다고 가정합니다. 이 cmdlet을 실행하면 버전 1.0이 제거되어야 합니다. 그러나 결과로 버전 2.0이 제거됩니다. 
    
이 문제의 원인은 "-version" 매개 변수가 "-minimumversion" 매개 변수의 별칭이기 때문입니다. OneGet에서 최소 버전이 1.0인 정규화된 패키지를 찾을 경우 최신 버전을 반환합니다. 대부분의 사용자는 최신 버전을 찾기 원하므로 일반적인 경우 이 동작이 필요합니다. 그러나 uninstall-package 사례에는 적용하지 않아야 합니다.
    
**해결 방법**: OneGet 및 PowerShellGet에서 -version 별칭을 완전히 제거했습니다. 

2 **NuGet 공급자를 부트스트래핑할지 묻는 메시지 여러 번 표시**

**시나리오**: 컴퓨터에서 Find-Module, install-module 또는 기타 OneGet cmdlet을 처음으로 실행할 경우 OneGet에서 NuGet 공급자를 부트스트래핑하려고 합니다. PowershellGet 공급자도 NuGet 공급자를 사용하여 PowerShell 모듈을 다운로드하기 때문입니다. 그런 다음 OneGet에서는 NuGet 공급자 설치를 허용할지 묻는 메시지를 표시합니다. 사용자가 부트스트래핑에 대해 “예"를 선택하면 NuGet 공급자의 최신 버전이 설치됩니다. 
    
그러나 컴퓨터에 이전 버전의 NuGet 공급자가 설치된 경우 이전 버전의 NuGet이 PowerShell 세션에 먼저 로드되는 경우가 있습니다. 즉, OneGet에서 경합 상태가 발생합니다. 그러나 PowerShellGet이 작동하려면 최신 버전의 NuGet 공급자가 필요하므로 PowerShellGet에서는 OneGet에 Nuget 공급자를 다시 부트스트래핑하도록 요청합니다. 이 때문에 NuGet 공급자를 부트스트래핑하라는 메시지가 여러 번 표시될 수 있습니다.

**해결 방법**: 이제 OneGet에서는 NuGet 공급자를 부트스트래핑하라는 메시지가 여러 번 표시되지 않도록 최신 버전의 NuGet 공급자를 로드합니다.

$env:ProgramFiles\PackageManagement\ProviderAssemblies 또는 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies에 있는 경우 NuGet 공급자(NuGet-Anycpu.exe)의 이전 버전을 수동으로 삭제하는 방법도 있습니다.


3 **인트라넷만 사용하는 컴퓨터**

**시나리오**: 기업 시나리오로 사용자가 인터넷에 연결되어 있지 않고 인트라넷만 있는 환경에서 작업하는 사례가 있습니다. WMF 5.0에서 OneGet은 이 사례를 지원하지 않습니다.

**해결 방법**:
- 인터넷에 연결된 다른 컴퓨터에서 "Install-PackageProvider -Name NuGet" 명령으로 NuGet 공급자를 다운로드할 수 있습니다.

- $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget 또는 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget에서 방금 설치한 NuGet 공급자를 찾습니다. 

- 이 이진 파일을 컴퓨터(인터넷에 연결되지 않은 컴퓨터)에서 액세스할 수 있는 폴더 또는 네트워크 공유 위치에 복사하고 "Install-PackageProvider NuGet -Source <Path to folder>"로 NuGet 공급자를 설치합니다.


4 **이벤트 로그**

패키지를 설치하면 컴퓨터 상태가 변경됩니다. 진단을 위해 이제 OneGet에서는 패키지 설치, 제거 및 저장에 대한 이벤트를 Windows 이벤트 로그에 기록합니다. 이벤트 채널은 PowerShell과 동일한 Microsoft Windows PowerShell, Operational입니다.

5 **인증 지원** 이제 OneGet에서는 기본 인증이 필요한 리포지토리에서 패키지를 찾고 설치할 수 있습니다. Find-Package 및 Install-Package cmdlet에 자격 증명을 제공할 수 있습니다. 예:
``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
6 **프록시 뒤에서 OneGet 사용**

이제 OneGet에서 프록시 매개 변수 -ProxyCredential 및 -Proxy를 사용합니다. 이러한 매개 변수를 사용하면 OneGet cmdlet에 프록시 URL과 프록시 자격 증명을 지정할 수 있습니다(기본적으로 시스템 프록시 설정 사용). 예:
``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


