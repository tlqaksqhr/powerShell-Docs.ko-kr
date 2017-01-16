---
title: "WMF 5.1 릴리스 정보"
ms.date: 2016-07-27
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: jkeithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 0a499bbfd2517c1f44e41f1096cda0c23b1c3df8
ms.sourcegitcommit: f06ef671c0a646bdd277634da89cc11bc2a78a41
translationtype: HT
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>WMF(Windows Management Framework) 5.1 릴리스 정보 #

WMF 5.1에는 Windows Server 2016과 함께 릴리스되는 PowerShell, WMI, WinRM 및 SIL(소프트웨어 인벤토리 및 라이선스) 구성 요소가 포함됩니다. WMF 5.1은 Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 및 2012 R2에 설치할 수 있으며 WMF 5.0 RTM보다 개선된 많은 기능을 제공합니다.

- 새 cmdlet: 로컬 사용자 및 그룹; Get-ComputerInfo
- 서명된 모듈, JEA 모듈 설치 등의 PowerShellGet 개선 사항
- PackageManagement에서 컨테이너, CBS 설치, EXE 기반 설치, CAB 패키지에 대한 지원 추가
- DSC 및 PowerShell 클래스에 대한 디버깅 개선 사항
- 끌어오기 서버에서 나오는 카탈로그 서명 모듈 적용 및 PowerShellGet cmdlet을 사용할 경우를 비롯한 보안 향상
- 다양한 사용자 요청 및 문제에 대한 응답

**중요:**

- **WMF 5.1을 사용하려면 .NET Framework 4.6이 필요합니다**. .NET 4.6이 설치되어 있지 않은 경우 설치는 되지만 주요 기능이 작동하지 않습니다. 지침은 [WMF 5.1 설치 및 구성](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) 항목에서 확인할 수 있습니다. 
- WMF 5.1 RTM을 설치하기 전에 먼저 WMF 5.1 Preview를 제거해야 합니다.
- WMF 5.1은 WMF 5.0 또는 WMF 4.0 위에 바로 설치할 수 있습니다.
- Windows 7 및 Windows Server 2008 R2에서는 WMF 5.1을 설치하기 전에 먼저 WMF 4.0을 설치할 __필요가 없습니다__. 이는 WMF 5.1 Preview 릴리스의 문제였으며 해결되었습니다.  


