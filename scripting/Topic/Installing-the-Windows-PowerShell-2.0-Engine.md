---
title: Windows PowerShell 2.0 엔진 설치
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
---
# Windows PowerShell 2.0 엔진 설치
이 항목에서는 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진을 설치하는 방법을 설명합니다.

[!INCLUDE[psversion3](../Token/psversion3_md.md)]은 이전 버전인 [!INCLUDE[psversion2](../Token/psversion2_md.md)]과 호환되도록 설계되었습니다. [!INCLUDE[psversion2](../Token/psversion2_md.md)]용으로 작성된 cmdlet, 공급자, 스냅인, 모듈 및 스크립트는 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 및 [!INCLUDE[psversion4](../Token/psversion4_md.md)]에서 변경하지 않고 실행됩니다. 그러나 Microsoft .NET Framework 4의 런타임 정품 인증 정책 변경으로 인해 [!INCLUDE[psversion2](../Token/psversion2_md.md)]용으로 작성되고 CLR(공용 언어 런타임) 2.0으로 컴파일된 Windows PowerShell 호스트 프로그램은 CLR 4.0으로 컴파일된 [!INCLUDE[wps_2](../Token/wps_2_md.md)]의 이후 릴리스에서 수정 없이 실행할 수 없습니다.

이러한 변경의 영향을 받는 이전 버전의 명령 및 호스트 프로그램과 호환성을 유지하기 위해 [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] 및 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 엔진은 나란히 실행되도록 설계되었습니다. 또한 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 및 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]에는 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진이 포함되어 있습니다. [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진은 기존 스크립트 또는 호스트 프로그램이 [!INCLUDE[psversion3](../Token/psversion3_md.md)], [!INCLUDE[psversion4](../Token/psversion4_md.md)] 또는 Microsoft .NET Framework 4와 호환되지 않아 실행할 수 없는 경우에만 사용됩니다. 이러한 경우는 많지 않을 것으로 예상됩니다.

[!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진은 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] 및 [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)]의 선택적 기능입니다. 이전 버전의 Windows에서 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]을 설치하면 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 설치가 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 설치 디렉터리의 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 설치를 완전히 바꿉니다. 그러나 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진은 유지됩니다.

[!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진을 시작하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 시작](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)을 참조하세요.

## [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] 및 [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]
[!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] 및 [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]에서는 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진 기능이 기본적으로 설정되어 있습니다. 그러나 이 기능을 사용하려면 필요한 Microsoft .NET Framework 3.5에 대한 옵션을 설정해야 합니다. 이 섹션에서는 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진 기능을 설정 및 해제하는 방법도 설명합니다.

#### .NET Framework 3.5를 설정하려면

1.  **시작** 화면에서 **Windows 기능**을 입력합니다.

2.  **앱** 바에서 **설정**을 클릭한 다음 **Windows 기능 설정 또는 해제**를 클릭합니다.

3.  **Windows 기능** 상자에서 **.NET Framework 3.5(.NET 2.0 및 3.0 포함)**을 클릭하여 선택합니다.

    **.NET Framework 3.5(.NET 2.0 및 3.0 포함)**를 선택하면 상자가 채워져 기능의 일부만 선택되었음을 나타냅니다. 그러나 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진에는 이것만으로 충분합니다.

#### [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진을 설정 및 해제하려면

1.  **시작** 화면에서 **Windows 기능**을 입력합니다.

2.  **앱** 바에서 **설정**을 클릭한 다음 **Windows 기능 설정 또는 해제**를 클릭합니다.

3.  **Windows 기능** 상자에서 **[!INCLUDE[psversion2](../Token/psversion2_md.md)]** 노드를 확장하고 **[!INCLUDE[psversion2](../Token/psversion2_md.md)]엔진** 상자를 클릭하여 선택하거나 선택을 취소합니다.

## [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 및 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]
[!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진과 Microsoft .NET Framework 3.5 기능을 추가하려면 다음 절차를 따르세요. [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진에는 최소한 Microsoft .NET Framework 2.0.50727이 필요합니다. 이 요구 사항은 Microsoft .NET Framework 3.5에 의해 충족됩니다.

#### .NET Framework 3.5 기능을 추가하려면

1.  **서버 관리자**의 **관리** 메뉴에서 **역할 및 기능 추가**를 선택합니다.

    또는 **서버 관리자**에서 **모든 서버**를 클릭하고 서버 이름 마우스 오른쪽 단추로 클릭한 다음 **역할 및 기능 추가**를 선택합니다.

2.  **설치 유형** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다.

3.  **기능** 페이지에서 **.NET 3.5 Framework 기능** 노드를 확장하고 **.NET Framework 3.5(.NET 2.0 및 3.0 포함)**를 선택합니다.

    해당 노드 아래에 있는 다른 옵션은 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진에 필요하지 않습니다.

#### [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진 기능을 추가하려면

-   **서버 관리자**의 **관리** 메뉴에서 **역할 및 기능 추가**를 선택합니다.

    또는 **서버 관리자**에서 **모든 서버**를 클릭하고 서버 이름 마우스 오른쪽 단추로 클릭한 다음 **역할 및 기능 추가**를 선택합니다.

-   **설치 유형** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다.

-   **기능** 페이지에서 **[!INCLUDE[mshshort](../Token/mshshort_md.md)](설치됨)** 노드를 확장하고 **[!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진**을 선택합니다.

[!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진을 시작하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 시작](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)을 참조하세요.

## 이전 시스템
[!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 및 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]에 [!INCLUDE[psversion4](../Token/psversion4_md.md)]을 설치하는 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 패키지에는 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진이 포함되어 있습니다. 추가 설치, 설정 또는 구성 없이 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진을 사용할 수 있고 사용할 준비가 됩니다.

[!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 및 [!INCLUDE[lserver](../Token/lserver_md.md)]에 [!INCLUDE[psversion3](../Token/psversion3_md.md)]을 설치하는 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 패키지에는 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진이 포함되어 있습니다. 추가 설치, 설정 또는 구성 없이 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 엔진을 사용할 수 있고 사용할 준비가 됩니다.

## 참고 항목
[Windows PowerShell 시스템 요구 사항](../Topic/Windows-PowerShell-System-Requirements.md)
[Windows PowerShell 설치](../Topic/Installing-Windows-PowerShell.md)
[Windows PowerShell 시작 [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
[Windows PowerShell 2.0 엔진 시작](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)



<!--HONumber=Apr16_HO1-->


