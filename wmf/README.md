---
title: WMF(Windows Management Framework)
ms.date: 2016-12-07
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: b652613561655c4cbd63342b0fcc495195f83a80
ms.sourcegitcommit: b88151841dd44c8ee9296d0855d8b322cbf16076
translationtype: HT
---
# <a name="windows-management-framework"></a>Windows Management Framework

WMF(Windows Management Framework)는 다양한 Windows 및 Windows Server에서 일관된 관리 인터페이스를 제공하는 배달 메커니즘입니다.
WMF를 설치하면 고객은 환경에 함께 설치한 여러 OS를 원활히 상호 운용할 수 있습니다.
WMF는 지정된 릴리스의 Windows 및 Windows Server에 있는 관리 기능에 대한 업데이트를 Windows 및 Windows Server의 하위 버전(일반적으로 2개의 하위 버전)에서 설치할 수 있게 합니다.

WMF 설치는 다음 기능을 추가 및/또는 업데이트합니다.

- Windows PowerShell
- Windows PowerShell DSC(원하는 상태 구성)
- Windows PowerShell ISE(통합 스크립트 환경)
- WinRM(Windows Remote Management)
- WMI(Windows Management Instrumentation)
- Windows PowerShell 웹 서비스(관리 OData IIS 확장)
- 소프트웨어 인벤토리 로깅(SIL)
- 서버 관리자 CIM 공급자

## <a name="wmf-release-notes"></a>WMF 릴리스 정보

PowerShell 및 지정된 WMF의 다른 구성 요소에서 향상된 다양한 기능에 대해 알아보려면 아래 링크에서 릴리스 정보를 참조하세요.

- [WMF 5.1(Preview)](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)

## <a name="wmf-availability-across-windows-operating-systems"></a>Windows 운영 체제에서의 WMF 가용성

| 운영 체제 버전 | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | 함께 제공 |  |  |  |  |
| Windows 10 | 함께 제공 | 함께 제공  | | | |  
| Windows Server 2012 R2| 예 | 예 | 함께 제공 |  |  |
| Windows 8.1 | 예 | 예 |  함께 제공 |  |  |
| Windows Server 2012 | 예 | 예 | 예 |  함께 제공 | |
| Windows 8 |  |  |  | 함께 제공 | |
| Windows Server 2008 R2 SP1 | 예 | 예 | 예 |  예| 함께 제공 |
| Windows 7 SP1  | 예 | 예 | 예 | 예 | 함께 제공 |
| Windows Server 2008 SP2 | | | | 예 | 예 |
| Windows Vista | | | | | 예 |
| Windows Server 2003| | | |  | 예 |
| Windows XP | | | |  | 예 |

**"함께 제공"**: `specified WMF` 기능은 표시된 버전의 Windows 및 Windows Server에 제공되었습니다.
따라서 표시된 운영 체제 버전에는 `specified WMF`를 설치할 필요가 없습니다.
