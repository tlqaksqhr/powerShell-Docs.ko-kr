---
title: "WMF 5.1(Preview) 설치 및 구성"
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 0a53817d6af625822d9183d2a0d5bc7bf4d2b264
ms.openlocfilehash: 058d18deeb3d4926970ea25a157f92ad14836e4b

---

# WMF 5.1(Preview) 설치 및 구성 #

## .NET 4.6 설치
WMF 5.1을 사용하려면 .Net Framework 4.6을 설치해야 합니다. 이 설치는 새 카탈로그 서명 기능을 사용하기 위해 필요하며 WMF 5.1에서 모듈 및 스크립트 로드와 관련된 여러 영역에 영향을 줍니다. 

[.Net Framework 4.6은 KB 3045560으로 제공됩니다](https://support.microsoft.com/en-us/kb/3045560). 설치 지침은 다운로드 위치에서 확인할 수 있습니다.

> **참고:** WMF 5.1 Preview 설치 관리자에서 .Net 4.6 요구 사항을 검색하지 않는 것은 알려진 문제이므로 .NET 4.6을 설치하기 전에 WMF 5.1 Preview를 설치할 수 있습니다. Microsoft에서 테스트한 결과에 따르면 WMF 5.1 Preview를 설치한 후 .Net 4.6을 설치할 수 있습니다. 최종 버전의 WMF 5.1에서는 설치 전 이 필수 조건 요구 사항을 올바로 확인합니다. 

## WMF 5.1 Preview 다운로드 및 설치

설치하려는 운영 체제 및 아키텍처에 맞는 WMF 5.1 패키지를 다운로드합니다.

| 운영 체제       | 필수 구성 요소 | 패키지 링크             |
|------------------------|---------------|---------------------------|
| Windows Server 2012 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586)|
| Windows Server 2012    | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823587)|
| Windows Server 2008 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> [SHA-2 코드 서명](https://technet.microsoft.com/en-us/library/security/3033929) 보안 업데이트 | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) |
| Windows 8.1            | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | **x64:** [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586) </br> **x86:** [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823589) |
| Windows 7 SP1          | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> [SHA-2 코드 서명](https://technet.microsoft.com/en-us/library/security/3033929) 보안 업데이트 | **x64:** [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) </br> **x86:** [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823590) |


## Windows 탐색기(또는 Windows Server 2012 R2나 Windows 8.1의 파일 탐색기)에서 WMF 5.1 설치

1. MSU 파일을 다운로드한 폴더로 이동합니다.

2. MSU를 두 번 클릭하여 실행합니다.

## 명령 프롬프트에서 WMF 5.1 설치##

1. 컴퓨터의 아키텍처에 맞는 올바른 패키지를 다운로드한 후 관리자 권한(관리자 권한으로 실행)으로 명령 프롬프트 창을 엽니다. Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1의 Server Core 설치 옵션에서는 명령 프롬프트가 기본적으로 관리자 권한으로 열립니다.

2. WMF 5.1 설치 패키지를 다운로드하거나 복사한 폴더로 디렉터리를 변경합니다.

3. 다음 명령 중 하나를 실행합니다.
    - Windows Server 2012 R2 또는 Windows 8.1 x64를 실행하는 컴퓨터에서 `Win8.1AndW2K12R2-KB3156422-x64.msu /quiet`를 실행합니다.
    - Windows Server 2012를 실행하는 컴퓨터에서 `W2K12-KB3156423-x64.msu /quiet`를 실행합니다.
    - Windows Server 2008 R2 SP1 또는 Windows 7 SP1 x64를 실행하는 컴퓨터에서 `Win7AndW2K8R2-KB3156424-x64.msu /quiet`를 실행합니다.
    - Windows 8.1 X86을 실행하는 컴퓨터에서 `Win8.1-KB3156422-x86.msu /quiet`를 실행합니다.
    - Windows 7 SP1 x86을 실행하는 컴퓨터에서 `Win7-KB3156424-x86.msu /quiet`를 실행합니다.

## Windows Server 2008 SP1 및 Windows 7 SP1에 대한 추가 설치 참고 사항##
Windows Server 2008 SP1 or Windows 7 SP1에서 WMF 5.1을 설치하려면 다음이 설치되어 있어야 합니다.
- 최신 서비스 팩
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)
- WMF 5.1을 사용하려면 [Microsoft .NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560)이 필요합니다. 다운로드 위치에 있는 지침에 따라 Microsoft .NET Framework 4.6을 설치할 수 있습니다.
- [SHA-2 코드 서명](https://technet.microsoft.com/en-us/library/security/3033929) 보안 업데이트. 이 업데이트는 Windows 카탈로그 파일용 새 PowerShell cmdlet을 사용하는 데 필요합니다. 

> **WinRM 종속성:** - Windows PowerShell DSC(필요한 상태 구성)는 WinRM에 종속됩니다. WinRM은 Windows Server 2008 R2 및 Windows 7에서 기본적으로 사용하도록 설정되지 않습니다. WinRM을 사용하도록 설정하려면 Windows PowerShell 관리자 권한 세션에서 `Set-WSManQuickConfig`를 실행합니다.




<!--HONumber=Jul16_HO5-->


