---
title: 이전 버전의 Windows에서 Windows PowerShell 시작
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---
# 이전 버전의 Windows에서 Windows PowerShell 시작
이 섹션에서는 [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)], [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] 및 [!INCLUDE[lserver](../Token/lserver_md.md)]에서 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 및 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]을 시작하는 방법을 설명합니다. 또한 [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] 및 [!INCLUDE[lserver](../Token/lserver_md.md)]의 [!INCLUDE[psversion2](../Token/psversion2_md.md)]에서 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]에 대한 선택적 기능을 사용하도록 설정하는 방법을 설명합니다.

지원되는 시스템에 [!INCLUDE[psversion4](../Token/psversion4_md.md)]을 설치하려면 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)을 다운로드하여 설치합니다. 자세한 내용은 [Windows PowerShell 설치](../Topic/Installing-Windows-PowerShell.md)를 참조하세요.

지원되는 시스템에 [!INCLUDE[psversion3](../Token/psversion3_md.md)]을 설치하려면 [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290)을 다운로드하여 설치합니다. 자세한 내용은 [Windows PowerShell 설치](../Topic/Installing-Windows-PowerShell.md)를 참조하세요.

## 이전 버전의 Windows에서 [!INCLUDE[mshshort](../Token/mshshort_md.md)]을 시작하는 방법
다음 방법 중 하나를 사용하여 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 또는 [!INCLUDE[psversion4](../Token/psversion4_md.md)]의 설치된 버전을 시작합니다(해당하는 경우).

#### 시작 메뉴

-   **시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 클릭합니다.

-   **시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell**을 차례로 클릭합니다.

#### 명령 프롬프트

-   Cmd.exe, [!INCLUDE[wps_2](../Token/wps_2_md.md)] 또는 [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE에서 [!INCLUDE[wps_2](../Token/wps_2_md.md)]을 시작하려면 다음과 같이 입력합니다.

    ```
    PowerShell
    ```

    PowerShell.exe 프로그램의 매개 변수를 사용하여 세션을 사용자 지정할 수도 있습니다. 자세한 내용은 [PowerShell.exe 명령줄 도움말](../Topic/PowerShell.exe-Command-Line-Help.md)을 참조하세요.

#### 관리자 권한("관리자 권한으로 실행")

1.  **시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.

## 이전 릴리스의 Windows에서 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]를 시작하는 방법
다음 방법 중 하나를 사용하여 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]를 시작합니다.

#### 시작 메뉴

-   **시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 클릭합니다.

-   **시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell ISE**를 차례로 클릭합니다.

#### 명령 프롬프트

-   Cmd.exe, [!INCLUDE[wps_2](../Token/wps_2_md.md)] 또는 [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE에서 [!INCLUDE[wps_2](../Token/wps_2_md.md)]을 시작하려면 다음과 같이 입력합니다.

    ```
    PowerShell_ISE
    ```

    또는

    ```
    ISE
    ```

#### 관리자 권한("관리자 권한으로 실행")

1.  **시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.

## 이전 릴리스의 Windows에서 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]를 사용하도록 설정하는 방법
[!INCLUDE[psversion4](../Token/psversion4_md.md)] 및 [!INCLUDE[psversion3](../Token/psversion3_md.md)]의 경우 모든 버전의 Windows에서 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]가 기본적으로 사용됩니다. 아직 사용되지 않는 경우 Windows Management Framework 4.0 또는 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]에서 사용하도록 설정합니다.

[!INCLUDE[psversion2](../Token/psversion2_md.md)]의 경우 [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)]에서 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]가 기본적으로 사용됩니다. 그러나 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 및 [!INCLUDE[lserver](../Token/lserver_md.md)]에서는 선택적 기능입니다.

[!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 또는 [!INCLUDE[lserver](../Token/lserver_md.md)]의 [!INCLUDE[psversion2](../Token/psversion2_md.md)]에서 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]를 사용하도록 설정하려면 다음 절차를 따르세요.

#### [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]를 사용하도록 설정하려면

1.  서버 관리자를 시작합니다.

2.  **기능**을 클릭한 다음 **기능 추가**를 클릭합니다.

3.  기능 선택에서 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]를 클릭합니다.



<!--HONumber=Apr16_HO1-->


