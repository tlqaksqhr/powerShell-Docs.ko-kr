---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "추가 정보"
ms.technology: powershell
ms.sourcegitcommit: 47593773fb0f34e0b52d35617522d7b1db7f48e6
ms.openlocfilehash: 1cecf1b6bf5a55ed785c8ff43bdd4a0a41e96cd0

---

# JEA(Just Enough Administration)
JEA(Just Enough Administration)는 PowerShell로 관리할 수 있는 모든 것에 대한 위임된 관리를 가능하게 하는 보안 기술입니다.
JEA를 사용하면 다음이 가능합니다.
- **컴퓨터의 관리자 수 감소**: 일반 사용자를 대신하여 권한 있는 작업을 수행하는 가상 계정을 활용합니다.
- **사용자가 수행할 수 있는 작업 제한**: 사용자가 실행할 수 있는 cmdlet, 함수 및 외부 명령을 지정합니다.
- **사용자가 수행하고 있는 작업을 보다 효과적으로 이해**: 사용자가 세션 중에 실행한 명령을 정확하게 보여 주는 "Over-the-Shoulder" 기록을 사용합니다.

**JEA가 중요한 이유는 무엇일까요?**  
DNS 서버가 Active Directory 도메인 컨트롤러와 함께 있는 일반적인 시나리오를 살펴보겠습니다.
DNS 관리자는 DNS 서버의 문제를 해결하기 위해 로컬 관리자 권한이 있어야 하지만 이를 위해서는 권한 수준이 높은 "Domain Admins" 보안 그룹의 구성원으로 DNS 관리자를 만들어야 합니다.
이 접근 방식을 통해 DNS 관리자는 효과적으로 전체 도메인을 제어하고 해당 컴퓨터의 모든 리소스에 액세스할 수 있습니다.

JEA가 설정된 경우 작업을 수행하기 위해 필요한 모든 명령에 대한 액세스 권한만 제공하는 역할을 DNS 관리자에 대해 구성할 수 있습니다.
즉, 손상된 DNS 캐시를 복구하는 데 적합한 액세스 권한만 제공하여 Active Directory에 액세스하거나 파일 시스템을 검색하거나 잠재적으로 위험한 스크립트를 실행할 수 있는 권한을 실수로 제공하는 문제를 방지할 수 있습니다.
JEA 세션이 일회성 권한 있는 가상 계정을 사용하도록 구성된 경우 DNS 관리자는 *권한 없는* 자격 증명을 사용하여 서버에 연결하고 권한 있는 명령을 실행할 수 있습니다.

## 가용성
JEA는 Windows Server 2016과 함께 개발되고 있으며 Windows Management Framework 업데이트를 통해 이전 버전의 Windows에서 사용할 수 있습니다.
JEA의 현재 릴리스는 다음과 같은 플랫폼에서 사용할 수 있습니다.

**Windows Server**
- Windows Server 2016 Technical Preview 4 이상
- [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)이 설치된 Windows Server 2012 R2, 2012 및 2008 R2\*

**Windows 클라이언트**
- 11월 업데이트(1511)가 설치된 Windows 10
- [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)이 설치된 Windows 8.1, 8 및 7\*

\* JEA 세션의 가상 계정에 대한 지원은 Windows Server 2008 R2 또는 Windows 7에서 현재 사용할 수 없습니다.


## 환경 탐색 가이드
사용자 고유의 JEA 끝점을 제작하고, 배포하고, 사용하는 방법을 알아볼 준비가 되었나요?

이 가이드에서는 미리 만들어진 JEA 끝점으로 신속하게 시작하여 최종 사용자가 어떻게 경험하는지를 파악하게 하고 끝점을 처음부터 다시 제작하는 과정을 안내하여 세션 구성 및 역할 기능과 같은 개념을 보여 줄 수 있습니다.

1.  [소개](introduction.md)   
JEA에 대해 관심을 가져야 하는 이유 간단히 검토

2.  [필수 구성 요소](prerequisites.md)  
환결 설정 방법 설명

3.  [JEA 사용](using-jea.md)  
운영자의 JEA 사용 경험을 이해하는 것에서 시작하도록 지원

4.  [데모 다시 만들기](remake-the-demo-endpoint.md)  
처음부터 JEA 세션 구성 만들기

5.  [역할 기능](role-capabilities.md)  
역할 기능 파일을 사용하여 JEA 기능을 사용자 지정하는 방법 알아보기

6.  [종단 간 - Active Directory](end-to-end---active-directory.md)  
Active Directory를 관리하기 위한 완전히 새로운 끝점 만들기

7.  [다중 컴퓨터 배포 및 유지 관리](multi-machine-deployment-and-maintenance.md)  
확장에 따라 배포와 작성이 변경되는 방식 알아보기

8.  [JEA에 대한 보고](reporting-on-jea.md)  
모든 JEA 작업 및 인프라에 대한 감사 및 보고 방법 알아보기

9.  부록
  - [이 가이드 전체에서 사용된 주요 개념](key-concepts-used-throughout-this-guide.md)  
  -  [도메인 컨트롤러 만들기](creating-a-domain-controller.md)  
  -  [블랙리스트에 올리기](on-blacklisting.md)  
  -  [명령을 제한하는 경우의 고려 사항](considerations-when-limiting-commands.md)  
  -  [일반적인 역할 기능 문제](common-role-capability-pitfalls.md)

## 사용자 고유의 JEA 끝점 제작 시작
JEA 끝점을 제작하는 것은 쉽습니다. JEA 사용 시스템과 텍스트 편집기(예: PowerShell ISE)만 있으면 됩니다.
시작하기 위한 한 가지 유용한 팁은 다른 인수 없이 `New-PSRoleCapabilityFile -Path <path>` 및 `New-PSSessionCapabilityFile -Path <Path>`를 사용하여 기본 파일을 만드는 것입니다.
이러한 기본 파일에는 적용 가능한 모든 구성 필드와 함께 각 필드의 용도에 대해 설명하는 유용한 설명이 포함되어 있습니다.

JEA 끝점을 훨씬 쉽게 제작하려면 세션 구성 및 역할 기능 파일을 제작할 수 있는 GUI를 제공하는 [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)를 참조하세요.
이 도구는 사용자가 작업을 수행하기 위해 일반적으로 실행하는 명령으로 시작할 수 있도록 PowerShell 로그를 기반으로 역할 기능을 생성하는 것까지 지원합니다.




<!--HONumber=Jun16_HO4-->


