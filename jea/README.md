# JEA(Just Enough Administration)
JEA(Just Enough Administration)는 PowerShell로 관리할 수 있는 모든 것에 대한 위임된 관리를 가능하게 하는 보안 기술입니다.
JEA를 사용하면 다음이 가능합니다.
- **컴퓨터의 관리자 수 감소**: 일반 사용자를 대신하여 권한 있는 작업을 수행하는 가상 계정을 활용합니다.
- **사용자가 수행할 수 있는 작업 제한**: 사용자가 실행할 수 있는 cmdlet, 함수 및 외부 명령을 지정합니다.
- **사용자가 수행하고 있는 작업을 보다 효과적으로 이해**: 사용자가 세션 중에 실행한 명령을 정확하게 보여 주는 "Over-the-Shoulder" 기록을 사용합니다.

JEA가 중요한 이유는 무엇일까요?
DNS 서버가 Active Directory 도메인 컨트롤러와 함께 있는 일반적인 시나리오를 살펴보겠습니다.
DNS 관리자는 DNS 서버의 문제를 해결하기 위해 로컬 관리자 권한이 있어야 하지만 이를 위해서는 권한 수준이 높은 "Domain Admins" 보안 그룹의 구성원으로 DNS 관리자를 만들어야 합니다.
이를 통해 DNS 관리자는 전체 도메인을 제어하고 해당 컴퓨터의 모든 리소스에 액세스할 수 있게 됩니다.

JEA가 설정된 경우 작업을 수행하기 위해 필요한 모든 명령에 대한 액세스 권한만 제공하는 역할을 DNS 관리자에 대해 구성할 수 있습니다.
즉, Active Directory에 대한 권한 없이 손상된 DNS 캐시를 복구하거나, 파일 시스템을 검색하거나, 위험할 수 있는 스크립트를 실행하는 작업을 용이하게 수행할 수 있습니다.
JEA 세션이 일회성 권한 있는 가상 계정을 사용하도록 구성된 경우 DNS 관리자는 *권한 없는* 자격 증명을 사용하여 서버에 연결하고 권한 있는 명령을 실행할 수 있습니다.

## 시작하기

### 설치
JEA는 예정된 Windows Server 2016 릴리스와 함께 개발되고 있으며 Windows Management Framework 업데이트를 통해 이전 버전의 Windows에서 사용할 수 있습니다.
JEA의 현재 릴리스는 다음과 같은 플랫폼에서 사용할 수 있습니다.

**Windows Server**
- Windows Server 2016 Technical Preview 4 이상
- [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)이 설치된 Windows Server 2012 R2, 2012 및 2008 R2\*

**Windows 클라이언트**
- 11월 업데이트(1511)가 설치된 Windows 10
- [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)이 설치된 Windows 8.1, 8 및 7\*

\* JEA 세션의 가상 계정에 대한 지원은 Windows Server 2008 R2 또는 Windows 7에서 현재 사용할 수 없습니다.


### 핵심 개념
**JEA란 정확히 무엇인가요?**

JEA는 역할 정의, 가상 계정 및 몇 가지 기타 개선 기능을 추가하여 관리 끝점을 잠그기 훨씬 쉽게 만드는 PowerShell [제한된 끝점](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx)의 확장입니다.
JEA 끝점은 PowerShell 세션 구성 파일과 하나 이상의 역할 기능 파일로 구성됩니다.

**세션 구성 및 역할 기능 파일이란 무엇인가요?**

PowerShell 세션 구성 파일(.pssc)은 *누가* PowerShell 끝점에 연결할 수 있고 *어떻게* PowerShell 끝점이 구성되었는지를 정의합니다.
이 파일에서 사용자 및 보안 그룹을 특정 관리 역할에 매핑하고 가상 계정 및 기록 정책과 같은 전역 설정을 구성합니다.
세션 구성 파일은 각 컴퓨터에 한정되므로 원하는 경우 컴퓨터별로 액세스 권한을 제어할 수 있습니다.

PowerShell 역할 기능 파일(.psrc)은 역할에 속한 사용자가 시스템에서 수행할 수 있는 *작업*을 정의합니다.
여기서는 사용자가 JEA 세션에서 사용할 수 있는 cmdlet, 함수, 공급자 및 외부 프로그램을 제한할 수 있습니다.
역할 기능 파일은 처리되는 역할(DNS 관리자, 수준 1 지원 센터, 읽기 전용 인벤토리 감사 등)을 일반적으로 정의하며 PowerShell 모듈에 속하므로 사용자 환경과 다른 환경 간에 공유하기가 쉽습니다.

**JEA에서 가상 계정을 어떻게 활용하나요?**

PowerShell 세션 구성 파일에서 가상 "실행" 계정을 사용하도록 JEA 세션을 구성할 수 있습니다.
가상 계정은 특정 세션에서 연결하는 사용자에 대해 생성된 일회성 권한 있는 계정입니다. 이 세션의 컨텍스트에서 사용자의 명령이 실행됩니다.
가상 계정은 기본적으로 로컬 "Administrators" 보안 그룹에 속하지만 필요에 따라 지정한 보안 그룹에만 속하도록 구성될 수 있습니다.

### 환경 탐색 가이드
첫 번째 JEA 끝점을 만들 준비가 되었나요?
사용자 고유의 JEA 끝점을 제작하고, 배포하고, 사용하는 방법을 알아보려면 [JEA 환경 가이드](./JEA Guide.md)를 참조하세요.
이 가이드에서는 미리 만들어진 JEA 끝점으로 신속하게 시작하여 최종 사용자가 어떻게 경험하는지를 파악하게 하고 끝점을 처음부터 다시 제작하는 과정을 안내하여 세션 구성과 역할 기능에 대해 설명합니다.

### 사용자 고유의 JEA 끝점 제작 시작
JEA 끝점을 제작하는 것은 쉽습니다. JEA 사용 시스템과 텍스트 편집기(예: PowerShell ISE)만 있으면 됩니다.
시작하기 위한 한 가지 유용한 팁은 다른 인수 없이 `New-PSRoleCapabilityFile -Path <path>` 및 `New-PSSessionCapabilityFile -Path <Path>`를 사용하여 기본 파일을 만드는 것입니다.
이러한 기본 파일에는 적용 가능한 모든 구성 필드와 함께 각 필드의 용도에 대해 설명하는 유용한 설명이 포함되어 있습니다. 

JEA 끝점을 훨씬 쉽게 제작하려면 세션 구성 및 역할 기능 파일을 제작할 수 있는 GUI를 제공하는 [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)를 참조하세요.
이 도구는 사용자가 작업을 수행하기 위해 일반적으로 실행하는 명령으로 시작할 수 있도록 PowerShell 로그를 기반으로 역할 기능을 생성하는 것까지 지원합니다.


<!--HONumber=Jun16_HO1-->


