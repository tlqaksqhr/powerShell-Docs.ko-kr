---
title: Windows PowerShell 시스템 요구 사항
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
---
# Windows PowerShell 시스템 요구 사항
이 항목에서는 Windows PowerShell 3.0 및 Windows PowerShell 4.0과 특수 기능(예: Windows PowerShell ISE(통합 스크립팅 환경), CIM 명령 및 워크플로)에 대한 시스템 요구 사항을 보여 줍니다.

WindowsÂ® 8.1 및 Windows ServerÂ® 2012 R2에는 필요한 모든 프로그램이 포함되어 있습니다. 이 항목은 이전 버전의 Windows 사용자를 위한 것입니다.

## 운영 체제 요구 사항
Windows PowerShell 4.0은 다음 버전의 Windows에서 실행됩니다.

-   Windows 8.1, 기본적으로 설치됨

-   Windows Server 2012 R2, 기본적으로 설치됨

-   WindowsÂ® 7 서비스 팩 1, Windows PowerShell 4.0을 실행하려면 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) 설치

-   Windows ServerÂ® 2008 R2 서비스 팩 1, Windows PowerShell 4.0을 실행하려면 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) 설치

Windows PowerShell 3.0은 다음 버전의 Windows에서 실행됩니다.

-   Windows 8, 기본적으로 설치됨

-   Windows Server 2012, 기본적으로 설치됨

-   WindowsÂ® 7 서비스 팩 1, Windows PowerShell 3.0을 실행하려면 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 설치

-   Windows ServerÂ® 2008 R2 서비스 팩 1, Windows PowerShell 3.0을 실행하려면 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 설치

-   Windows Server 2008 서비스 팩 2, Windows PowerShell 3.0을 실행하려면 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 설치

## Microsoft .NET Framework 요구 사항
Windows PowerShell 4.0을 사용하려면 Microsoft .NET Framework 4.5 전체 설치가 필요합니다. Windows 8.1 및 Windows Server 2012 R2에는 Microsoft .NET Framework 4.5가 기본적으로 포함되어 있습니다.

Windows PowerShell 3.0을 사용하려면 Microsoft .NET Framework 4 전체 설치가 필요합니다. Windows 8 및 Windows Server 2012에는 이 요구 사항을 충족하는 Microsoft .NET Framework 4.5가 기본적으로 포함되어 있습니다.

Microsoft .NET Framework 4.5(dotNetFx45\_Full\_setup.exe)를 설치하려면 Microsoft 다운로드 센터에서 [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919)를 참조하세요.

Microsoft .NET Framework 4 전체 설치(dotNetFx40\_Full\_setup.exe)를 설치하려면 Microsoft 다운로드 센터에서 [Microsoft .NET Framework 4(웹 설치 관리자)](http://go.microsoft.com/fwlink/?LinkID=212931)를 참조하세요.

## WS\-Management 3.0
Windows PowerShell 3.0 및 Windows PowerShell 4.0을 사용하려면 WinRM 서비스 및 WSMan 프로토콜을 지원하는 WS\-Management 3.0이 필요합니다. 이 프로그램은 Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 및 Windows Management Framework 3.0에 포함되어 있습니다.

## Windows Management Instrumentation 3.0
Windows PowerShell 3.0 및 Windows PowerShell 4.0을 사용하려면 WMI(Windows Management Instrumentation) 3.0이 필요합니다. 이 프로그램은 Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 및 Windows Management Framework 3.0에 포함되어 있습니다. 이 프로그램이 컴퓨터에 설치되어 있지 않으면 WMI가 필요한 기능(예: CIM 명령)이 실행되지 않습니다.

## 공용 언어 런타임 4.0
Windows PowerShell 3.0 및 Windows PowerShell 4.0은 CLR(공용 언어 런타임) 4.0에 대해 컴파일됩니다.

## 그래픽 사용자 인터페이스 요구 사항
Windows PowerShell은 그래픽 사용자 인터페이스를 요구하지 않는 콘솔 기반 응용 프로그램입니다. 따라서 Windows Server 2012 R2 또는 Windows Server 2012의 Server Core 설치 옵션과 같이 화면 또는 모니터나 사용자 인터페이스가 없는 컴퓨터에 적합합니다.

그러나 다음과 같은 일부 항목에는 그래픽 사용자 인터페이스가 필요합니다. 자세한 내용은 각 항목에 대한 도움말 항목을 참조하세요.

-   Windows PowerShell ISE(통합 스크립팅 환경)

-   Cmdlet

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   매개 변수

    1.  [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet의 **ShowWindow** 매개 변수

    2.  [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) 및 [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlet의 **ShowSecurityDescriptorUi** 매개 변수

## Windows PowerShell 엔진 요구 사항
Windows PowerShell 4.0은 이전 버전인 Windows PowerShell 3.0 및 Windows PowerShell 2.0과 호환되도록 설계되었습니다. Windows PowerShell 2.0 및 Windows PowerShell 3.0용으로 작성된 cmdlet, 공급자, 스냅인, 모듈 및 스크립트는 Windows PowerShell 4.0에서 변경하지 않고 실행됩니다.

그러나 Microsoft .NET Framework 4의 런타임 정품 인증 정책 변경으로 인해 Windows PowerShell 2.0용으로 작성되고 CLR(공용 언어 런타임) 2.0으로 컴파일된 Windows PowerShell 호스트 프로그램은 CLR 4.0으로 컴파일된 Windows PowerShell 3.0에서 수정 없이 실행할 수 없습니다.

Windows PowerShell 2.0 엔진에는 최소한 Microsoft .NET Framework 2.0.50727이 필요합니다. 이 요구 사항은 Microsoft .NET Framework 3.5 서비스 팩 1에 의해 충족됩니다. Microsoft .NET Framework 4 이상 릴리스의 Microsoft .NET Framework에서는 이 요구 사항이 충족되지 않습니다.

Windows PowerShell 2.0 엔진을 추가 또는 설치하는 방법과 필수 버전의 Microsoft .NET Framework를 추가 또는 설치하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 설치](Installing-the-Windows-PowerShell-2.0-Engine.md)를 참조하세요. Windows PowerShell 2.0 엔진을 시작하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 시작](Starting-the-Windows-PowerShell-2.0-Engine.md)을 참조하세요..

## Windows 사전 설치 환경
Windows PowerShell 2.0, Windows PowerShell 3.0 및 Windows PowerShell 4.0은 Winows PE(Windows 사전 설치 환경)에서 실행됩니다. 그러나 다음 cmdlet은 지원되지 않습니다.

-   [BITS(Background Intelligent Transfer Service) cmdlet](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent[PSITPro5_Diagnostic]](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

또한 Windows PE에는 **WinRm** 서비스가 없습니다.

## 참고 항목
[Windows PowerShell 시작](../getting-started/Getting-Started-with-Windows-PowerShell.md)
[Windows PowerShell 설치](Installing-Windows-PowerShell.md)
[Windows PowerShell 시작 [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=May16_HO2-->


