---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "이 가이드 전체에서 사용된 주요 개념"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 178fea44987b0c457b8e5d23fbe851ee12f03b31

---

# 이 가이드 전체에서 사용된 주요 개념
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

**PowerShell 원격**: PowerShell 원격을 사용하면 원격 컴퓨터에 대해 PowerShell 명령을 실행할 수 있습니다.
한 대 이상의 컴퓨터를 대상으로 작업하고 임시 또는 영구 연결을 사용할 수 있습니다.
이 데모에서는 대화형 세션으로 로컬 컴퓨터에 원격으로 연결했습니다.
JEA는 PowerShell 원격을 통해 사용할 수 있는 기능을 제한합니다.
PowerShell 원격에 대한 자세한 내용을 보려면 `Get-Help about_Remote`를 실행하세요.

**"실행" 사용자**: JEA를 사용할 때 관리자가 아닌 사용자가 권한 있는 "가상 계정으로 실행"합니다.
가상 계정은 원격 세션의 기간 동안만 지속됩니다.
즉, 가상 계정은 사용자가 끝점에 연결할 때 만들어지고 사용자가 세션을 종료할 때 제거됩니다.
기본적으로 가상 계정은 로컬 Administrators 그룹의 구성원이고,
도메인 컨트롤러에서는 Domain Admins의 구성원입니다.
가상 계정은 만들어진 컴퓨터에 로컬이며 해당 컴퓨터 외부에서는 권한이 없습니다.
즉, Active Directory에서 등록되어 있지 않습니다(RID가 할당되지 않음).
또한 허용되는 명령/스크립트가 로컬 컴퓨터 외부의 리소스에 액세스하려는 경우 가상 계정 ID가 아니라 컴퓨터의 ID로 해당 리소스에 액세스하게 됩니다.

**"연결된" 사용자**: JEA 끝점에 연결되고 역할이 할당된 관리자가 아닌 사용자입니다.
이 사용자가 실행하는 모든 명령은 실행 사용자 또는 가상 계정의 컨텍스트에서 실행됩니다.




<!--HONumber=Jul16_HO1-->


