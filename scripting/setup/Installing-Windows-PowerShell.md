---
title: Windows PowerShell 설치
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---
# Windows PowerShell 설치
WindowsÂ® 8 및 Windows ServerÂ® 2012에는 Windows PowerShell 3.0과 모든 필수 구성 요소가 포함되어 있습니다. Windows PowerShell 3.0을 사용할 수 없는 이전 버전의 호스트 프로그램과 호환성을 위해 시스템에 Windows PowerShell 2.0 엔진도 포함되어 있습니다.

이 항목에서는 이전 시스템에 Windows PowerShell 3.0을 설치하고 필요한 기능을 설치하여 사용하도록 설정하는 방법을 설명합니다.

이 항목에는 다음 섹션이 포함되어 있습니다.

-   [Windows 8 및 Windows Server 2012에 Windows PowerShell 설치](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Windows 7 및 Windows Server 2008 R2에 Windows PowerShell 설치](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Windows Server 2008에 Windows PowerShell 설치](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Server Core에 Windows PowerShell 설치](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Windows PowerShell 웹 액세스 배포](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Windows PowerShell 2.0 엔진 설치](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Windows 8 및 Windows Server 2012에 Windows PowerShell 설치
Windows PowerShell 3.0은 설치 및 구성되고 사용 준비가 완료된 상태로 제공됩니다. Windows PowerShell ISE(통합 스크립팅 환경)를 설치하고 사용하도록 설정합니다. Windows PowerShell을 시작하는 방법에 대한 자세한 내용은 [Windows 8에서 Windows PowerShell 시작](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) 및 [Windows Server 2012에서 Windows PowerShell 시작](https://technet.microsoft.com/en-us/library/4fc0110a-cc0c-42a4-bbb5-3cc89a0fc968)을 참조하세요..

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Windows 7 및 Windows Server 2008 R2에 Windows PowerShell 설치
이 지침에서는 Windows 7 서비스 팩1 및 Windows Server 2008 R2 서비스 팩 1을 실행하는 컴퓨터에 Windows PowerShell 3.0을 설치하는 방법을 설명합니다. Windows Server 2008 R2의 Server Core 설치 옵션으로 실행되는 컴퓨터를 위한 별도의 설치 지침은 아래에 나와 있습니다.

#### 설치 준비

-   Windows Management Framework 3.0을 설치하기 전에 Windows Management Framework 3.0의 이전 버전을 모두 제거합니다.

#### Windows PowerShell 3.0을 설치하려면

1.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547))에서 Microsoft .NET Framework 4(dotNetFx40\_Full\_setup.exe) 전체 설치를 설치합니다..

    또는 Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919))에서 Microsoft .NET Framework 4.5(dotNetFx45\_Full\_setup.exe)를 설치합니다..

2.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290))에서 Windows Management Framework 3.0을 설치합니다..

Windows PowerShell 3.0을 시작하는 방법에 대한 자세한 내용은 [이전 버전의 Windows에서 Windows PowerShell 시작](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md)을 참조하세요..

## <a name="BKMK_InstallingOnServerCore"></a>Server Core에 Windows PowerShell 설치
이 지침에서는 Windows Server 2008 R2 서비스 팩 1의 Server Core 설치 옵션을 실행하는 컴퓨터에 Windows PowerShell 3.0을 설치하는 방법을 설명합니다.

절차의 첫 번째 단계에서는 DISM(배포 이미지 서비스 및 관리) 명령을 사용하여 Server Core용 Microsoft .NET Framework 2.0 및 Windows PowerShell 2.0을 설치합니다. 이러한 프로그램은 이후 단계에서 설치되는 Windows Management Framework 3.0에 대한 필수 구성 요소입니다.

#### 설치 준비

-   Windows Management Framework 3.0을 설치하기 전에 Windows Management Framework 3.0의 이전 버전을 모두 제거합니다.

#### Windows PowerShell 3.0을 설치하려면

1.  Cmd.exe 시작

2.  다음 DISM 명령을 실행합니다. 이 명령은 .NET Framework 2.0 및 Windows PowerShell 2.0을 설치합니다.

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450))에서 Server Core용 Microsoft .NET Framework 4.0 전체 설치를 설치합니다..

4.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290))에서 Windows Management Framework 3.0을 설치합니다..

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>Windows Server 2008에 Windows PowerShell 설치
이 지침에서는 Windows Server 2008 서비스 팩 2를 실행하는 컴퓨터에 Windows PowerShell 3.0을 설치하는 방법을 설명합니다.

Windows Server 2008 시스템에서 Windows Management Framework(Windows PowerShell 2.0, KB 968930)는 Windows Management Framework 3.0의 필수 구성 요소입니다. "인증에 대해 확장된 보호" 기능은 인증 전달 공격으로부터 컴퓨터를 보호하며, 원격 세션을 만들 때 **UseSSL** 매개 변수를 사용할 수 있게 합니다. Windows PowerShell 3.0 및 the Windows PowerShell 2.0 엔진을 설치하려면 다음 절차를 따르세요.

#### 설치 준비

-   Windows Management Framework 3.0을 설치하기 전에 Windows Management Framework 3.0의 이전 버전을 모두 제거합니다.

#### Windows PowerShell 3.0을 설치하려면

1.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910))에서 Microsoft .NET Framework 3.5 서비스 팩 1을 설치합니다..

2.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035))에서 Windows Management Framework(Windows PowerShell 2.0, KB 968930)를 설치합니다..

3.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547))에서 Microsoft .NET Framework 4(dotNetFx40\_Full\_setup.exe) 전체 설치를 설치합니다..

    또는 Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919))에서 Microsoft .NET Framework 4.5(dotNetFx45\_Full\_setup.exe)를 설치합니다..

4.  [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398)에서 "인증에 대한 확장된 보호"(KB 968389)를 설치합니다..

5.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290))에서 Windows Management Framework 3.0을 설치합니다..

## 참고 항목
[Windows PowerShell 시스템 요구 사항](Windows-PowerShell-System-Requirements.md)
[Windows PowerShell 시작 [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=May16_HO2-->


