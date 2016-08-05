---
title: "WMF 5.1 릴리스 정보(Preview)"
ms.date: 2016-07-27
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 5eb9eae6257cdb57f4f778b5dddf5aa7ef9d10bb
ms.openlocfilehash: 12f2c084ab92134b733ee037c3d9fbd512af2e4c

---

# WMF(Windows Management Framework) 5.1 Preview 릴리스 정보 #

WMF 5.1 Preview에는 Windows Server 2016과 함께 릴리스되는 PowerShell, WMI, WinRM 및 SIL(Software Inventory and Licensing) 구성 요소가 포함됩니다. WMF 5.1은 Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 및 2012 R2에 설치할 수 있으며 WMF 5.0 RTM보다 개선된 많은 기능을 제공합니다.

- 새 cmdlet: 로컬 사용자 및 그룹; Get-ComputerInfo
- 서명된 모듈, JEA 모듈 설치 등의 PowerShellGet 개선 사항
- PackageManagement에서 컨테이너, CBS 설치, EXE 기반 설치, CAB 패키지에 대한 지원 추가
- DSC 및 PowerShell 클래스에 대한 디버깅 개선 사항
- 끌어오기 서버에서 나오는 카탈로그 서명 모듈 적용 및 PowerShellGet cmdlet을 사용할 경우를 비롯한 보안 향상
- 다양한 사용자 요청 및 문제에 대한 응답

**중요:**

- **WMF 5.1 Preview를 사용하려면 Windows Management Framework 4.6이 필요합니다**. .Net 4.6이 설치되어 있지 않은 경우 설치는 되지만 주요 기능이 작동하지 않습니다. 지침은 [WMF 5.1(Preview) 설치 및 구성](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) 항목에서 확인할 수 있습니다. 
- 현재 **WMF 5.1 Preview는 프로덕션 배포용으로 지원되지 않습니다**. 이 버전은 릴리스의 기능에 대한 정보를 조기에 제공하고 PowerShell 팀에 피드백을 제공할 기회를 주기 위한 것입니다.
- WMF 5.1 Preview를 WMF 5.0 위에 바로 설치할 수 있습니다.
- Windows 7 및 Windows Server 2008에서 WMF 5.1 Preview를 설치하려면 현재 WMF 4.0이 필요한 것은 알려진 문제입니다. 이 요구 사항은 최종 릴리스 전에 제거될 예정됩니다.
- RTM 버전을 비롯해 이후 버전의 WMF 5.1을 설치하려면 WMF 5.1 Preview를 제거해야 합니다.



<!--HONumber=Jul16_HO5-->


