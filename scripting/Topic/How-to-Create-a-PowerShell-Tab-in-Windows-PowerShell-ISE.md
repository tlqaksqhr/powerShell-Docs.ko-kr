---
title: Windows PowerShell ISE에서 PowerShell 탭을 만드는 방법
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
---
# Windows PowerShell ISE에서 PowerShell 탭을 만드는 방법
[!INCLUDE[ise_1](../Token/ise_1_md.md)] 탭을 사용하면 동일한 응용 프로그램 내에 여러 실행 환경을 동시에 만들고 사용할 수 있습니다. 각 PowerShell 탭은 별개의 실행 환경 또는 세션에 해당합니다.

> [!NOTE]
> 하나의 탭에서 만드는 변수, 함수 및 별칭은 다른 탭으로 이전되지 않습니다. 서로 다른 Windows PowerShell 세션입니다.

다음 단계를 수행하여 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 탭을 열거나 닫습니다. 탭의 이름을 바꾸려면 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 탭 스크립팅 개체의 [DisplayName](assetId:///a9b58556-951b-4f48-b3ae-b351b7564360#Displayname) 속성을 설정합니다.

## 새 PowerShell 탭을 만들고 사용하려면
**파일** 메뉴에서 **새 PowerShell 탭**을 클릭합니다. 새 PowerShell 탭은 항상 활성 창으로 열립니다. PowerShell 탭은 열리는 순서대로 번호가 매겨집니다. 각 탭은 해당 Windows PowerShell 콘솔 창에 연결되어 있습니다. 동시 최대 32개의 PowerShell 탭과 해당 세션을 열 수 있습니다([!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0에서는 8개로 제한됨).

도구 모음에서 **새로 만들기** 또는 **열기** 아이콘을 클릭할 때는 새 탭과 별개의 세션이 만들어지지 않습니다.  대신, 이러한 단추는 현재 활성 탭과 세션에서 새 스크립트 파일이나 기존 스크립트 파일을 엽니다. 각 탭과 세션에서 여러 개의 스크립트 파일을 열 수 있습니다. 세션에 대한 스크립트 탭은 연결된 세션이 활성 상태인 경우에만 세션 탭 아래에 나타납니다.

PowerShell 탭을 활성화하려면 탭을 클릭합니다. 열려 있는 모든 PowerShell 탭 중에서 선택하려면 **보기** 메뉴에서 사용할 PowerShell 탭을 클릭합니다.

## 새 원격 PowerShell 탭을 만들고 사용하려면
**파일** 메뉴에서 **새 원격 PowerShell 탭**을 클릭하여 원격 컴퓨터에서 세션을 설정합니다. 대화 상자가 나타나고 원격 연결을 설정하는 데 필요한 세부 정보를 입력하라는 메시지가 표시됩니다. 원격 탭은 로컬 PowerShell 탭과 똑같이 작동하지만 명령과 스크립트가 원격 컴퓨터에서 실행된다는 점만 다릅니다.

## PowerShell 탭을 닫으려면
탭을 닫으려면 다음 방법 중 하나를 사용할 수 있습니다.

-   닫으려는 탭을 클릭합니다.

-   **파일** 메뉴에서 **PowerShell 탭 닫기**를 클릭하거나 활성 탭에서 닫기 단추(**X**)를 클릭하여 탭을 닫습니다.

닫으려는 PowerShell 탭에 저장되지 않은 파일이 열려 있는 경우 파일을 저장할지 또는 삭제할지를 묻는 메시지가 표시됩니다. 스크립트를 저장하는 방법에 대한 자세한 내용은 [스크립트 저장 방법](assetId:///162f594d-efd3-4234-9960-45e56e6eadc8)을 참조하세요.

## 참고 항목
[Windows PowerShell ISE 사용](../Topic/Using-the-Windows-PowerShell-ISE.md)
[Windows PowerShell ISE에서 콘솔 창을 사용하는 방법](../Topic/How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


