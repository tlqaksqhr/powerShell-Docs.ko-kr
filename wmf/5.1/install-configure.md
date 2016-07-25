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
ms.sourcegitcommit: 26da6c80568327faadc6746099ac9869f2018fcf
ms.openlocfilehash: 8a10903c421f62311a28c9f32e352bba75f21052

---

# WMF 5.1(Preview) 설치 및 구성 #

***참고:*** 
*이 콘텐츠는 자리 표시자입니다. 아래 링크는 WMF 5.0 버전을 가리키며 이진 파일이 릴리스되면 업데이트됩니다.*

설치하려는 운영 체제 및 아키텍처에 맞는 WMF 5.1 패키지를 다운로드합니다.

| 운영 체제       | 아키텍처 | 패키지 이름              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


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

> **WinRM 종속성:** - Windows PowerShell DSC(필요한 상태 구성)는 WinRM에 종속됩니다. WinRM은 Windows Server 2008 R2 및 Windows 7에서 기본적으로 사용하도록 설정되지 않습니다. WinRM을 사용하도록 설정하려면 Windows PowerShell 관리자 권한 세션에서 `Set-WSManQuickConfig`를 실행합니다.




<!--HONumber=Jul16_HO2-->


