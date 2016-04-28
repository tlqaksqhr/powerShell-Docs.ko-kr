---
title: Windows PowerShell ISE의 새로운 기능
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
---
# Windows PowerShell ISE의 새로운 기능
이 항목에서는 [!INCLUDE[ise_1](../Token/ise_1_md.md)] 버전에서 도입된 새로운 기능과 업데이트된 기능에 대해 설명합니다.

## <a name="overview"></a>기능 설명
[!INCLUDE[ise_2](../Token/ise_2_md.md)]는 그래픽 환경 및 직관적인 환경에서 스크립트 및 모듈을 작성, 실행 및 테스트할 수 있는 호스트 응용 프로그램입니다. 구문 색 지정, 탭 완성, 시각적 디버깅, 유니코드 규정 준수 및 상황에 맞는 도움말 같은 주요 기능을 통해 풍부한 스크립팅 환경을 제공합니다.

[!INCLUDE[ise_2](../Token/ise_2_md.md)]의 개요는 [Windows PowerShell 통합 스크립팅 환경 개요](assetId:///3c1892c2-bf84-4cb6-af26-1f453be9e671)를 참조하세요.

## <a name="versions"></a>Windows PowerShell ISE의 새로운 기능 및 변경된 기능
다음 표에는 [!INCLUDE[wps_2](../Token/wps_2_md.md)]에서 도입된 이 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 릴리스용 새로운 기능과 변경된 기능이 나와 있습니다.

|기능|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 4.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[Intellisense.](#BKMK_Intellisense)**|X|X||
|**[코드 조각](#bkmk_snippets)**|X|X||
|**[추가 기능 도구](#BKMK_AddOnTools)**|X|X||
|**[관리자 다시 시작 및 자동 저장](#BKMK_RestartMgr)**|X|X||
|**[콘솔 창](#BKMK_ConsolePane)**|X|X||
|**[가장 최근에 사용한 목록](#BKMK_MRU)**|X|X||
|**[명령줄 스위치](#BKMK_CommandLine)**|X|X||
|**[새 편집기 기능](#BKMK_NewEditorFeatures)**|X|X||
|**[새 도움말 뷰어 창](#BKMK_NewHelpViewer)**|X|X||
|**[Show-Command cmdlet](#BKMK_ShowCommand)**|X|X||

### <a name="BKMK_Intellisense"></a>Intellisense
**ISE 3.0에서 추가되었습니다.**

Intellisense는 [!INCLUDE[ise_2](../Token/ise_2_md.md)]의 일부인 자동 완성 지원 기능입니다. Intellisense는 입력하는 동안 잠재적으로 일치하는 cmdlet, 매개 변수, 매개 변수 값, 파일 또는 폴더가 포함된 클릭 가능한 메뉴를 표시합니다.

**이와 같은 변경을 통해 더해지는 가치**

Intellisense를 추가하면 [!INCLUDE[ise_2](../Token/ise_2_md.md)]를 사용하여 스크립트를 작성할 때 cmdlet과 구문을 더 쉽게 검색할 수 있습니다. 새 스크립트를 만드는 동안 [!INCLUDE[ise_2](../Token/ise_2_md.md)]를 사용하여 [!INCLUDE[wps_2](../Token/wps_2_md.md)]에 대해 알아볼 수도 있습니다.

**달라진 기능**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 이상에서 cmdlet을 입력하면 스크롤 및 클릭 가능한 메뉴가 표시되므로 적절한 명령을 찾아서 선택할 수 있습니다.

### <a name="BKMK_Snippets"></a>코드 조각
**ISE 3.0에서 추가되었습니다.**

*코드 조각*은 [!INCLUDE[wps_2](../Token/wps_2_md.md)]에서 만든 스크립트에 삽입할 수 있는 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 코드의 짧은 섹션입니다. [!INCLUDE[ise_2](../Token/ise_2_md.md)]에는 기본 코드 조각 집합이 포함되어 있습니다. [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 작업하는 동안 **New\-Snippet** cmdlet을 사용하여 코드 조각을 추가할 수 있습니다.

**이와 같은 변경을 통해 더해지는 가치**

코드 조각을 사용하면 빠르게 스크립트를 조합하고 만들어 사용자 환경을 자동화할 수 있습니다.

**달라진 기능**

[!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0 이상에서 코드 조각을 사용하려면 **편집** 메뉴에서 **조각 시작**을 클릭하거나 **Ctrl\-J**를 누릅니다.

### <a name="BKMK_AddOnTools"></a>추가 기능 도구
**PowerShell 3.0에서 추가되었습니다.**

이제 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 개체 모델을 사용하여 추가된 WPF(Windows Presentation Foundation) 컨트롤인 추가 기능 도구를 지원합니다. 추가 기능 도구는 콘솔의 세로 창이나 가로 창으로 표시할 수 있습니다. 하나의 창에 있는 여러 가지 추가 기능 도구는 탭 컨트롤로 표시됩니다. 타사에서 만든 추가 기능 도구를 추가하거나 제거할 수도 있습니다. 추가 기능 도구를 가져오거나 제거하는 방법에 대한 자세한 내용은 [Windows PowerShell ISE 작업](http://technet.microsoft.com/library/cc732148.aspx)을 참조하세요.

**이와 같은 변경을 통해 더해지는 가치**

추가 기능을 사용하면 스크립팅 환경을 향상하거나 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에 기능을 추가할 수 있는 도구로 [!INCLUDE[ise_2](../Token/ise_2_md.md)]를 확장하고 사용자 지정할 수 있습니다.

**달라진 기능**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 이상에는 **Commands** 추가 기능이 포함되어 있습니다. **Commands** 추가 기능을 사용하면 cmdlet을 찾고 **스크립트** 창과 **콘솔** 창에서 cmdlet에 대한 도움말을 나란히 액세스할 수 있습니다.

**추가 기능** 메뉴의 **추가 기능 도구 웹 사이트 열기** 명령을 사용하여 추가 기능을 더 찾을 수 있습니다.

### <a name="BKMK_RestartMgr"></a>관리자 다시 시작 및 자동 저장
**PowerShell 3.0에서 추가되었습니다.**

이제 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 열려 있는 스크립트를 2분마다 개별 위치에 자동으로 저장합니다.  [!INCLUDE[ise_2](../Token/ise_2_md.md)]의 작동이 중지되거나 운영 체제가 다시 시작되는 경우 [!INCLUDE[ise_2](../Token/ise_2_md.md)]를 다시 시작하면 스크립트를 저장하지 않은 경우에도 마지막 세션에 열려 있던 스크립트가 복구됩니다.

자동 저장 간격을 변경하려면 콘솔 창에서 **$psise.Options.AutoSaveMinuteInterval** 명령을 실행합니다.

**이와 같은 변경을 통해 더해지는 가치**

이제 예상치 않게 다시 시작될 경우 열려 있는 스크립트가 자동으로 저장된다는 것을 알고 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 내에서 작업할 수 있습니다.

**달라진 기능**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0에서는 다시 시작될 경우 스크립트를 자동으로 저장하지 않습니다.

### <a name="BKMK_MRU"></a>가장 최근에 사용한 목록
**PowerShell 3.0에서 추가되었습니다.**

이제 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에 가장 최근에 사용한 파일 목록이 있습니다. [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 파일을 열면 **파일** 메뉴의 가장 최근에 사용한 목록에 해당 파일이 추가됩니다.

가장 최근에 사용한 목록의 기본 파일 수를 변경하려면 콘솔 창에서 다음 명령을 실행합니다. **$psise.Options.MruCount**.

**이와 같은 변경을 통해 더해지는 가치**

이제 가장 최근에 사용한 목록을 통해 최근에 사용한 파일을 쉽게 액세스할 수 있습니다.

**달라진 기능**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0에는 가장 최근에 사용한 목록이 없습니다.

### <a name="BKMK_ConsolePane"></a>콘솔 창
**PowerShell 3.0에서 추가되었습니다.**

[!INCLUDE[ise_2](../Token/ise_2_md.md)]의 첫 번째 릴리스에서 제공된 별도의 명령 및 출력 창이 단일 콘솔 창으로 결합되었습니다. 콘솔 창의 기능과 모양은 일반적인 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 콘솔과 유사하지만 다음과 같은 기능이 향상되었습니다(대부분 이 항목에 설명되어 있음).

-   XML 구문을 포함하여 입력 텍스트(출력 텍스트가 아님)의 구문 색 지정

-   Intellisense.

-   중괄호 일치

-   오류 표시

-   전체 유니코드 지원

-   **F1** 상황에 맞는 도움말

-   **Ctrl\+F1** 상황에 맞는 Show\-Command

-   복잡한 스크립트 및 오른쪽에서 왼쪽으로 쓰는 언어 지원

-   글꼴 지원

-   확대/축소

-   줄 선택 및 블록 선택 모드

-   **위쪽** 화살표를 눌러 콘솔에서 기록을 볼 때 명령줄에 입력된 콘텐츠 유지

**이와 같은 변경을 통해 더해지는 가치**

이러한 콘솔 창 변경 내용이 추가되어 콘솔 인터페이스와 보다 일치하는 스크립팅 환경을 제공합니다.

**달라진 기능**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0에는 별도의 명령 창과 출력 창이 있습니다.

### <a name="BKMK_CommandLine"></a>명령줄 스위치
**PowerShell 3.0에서 추가되었습니다.**

**Powershell\_ise.exe**를 입력하여 명령줄에서 [!INCLUDE[ise_2](../Token/ise_2_md.md)]을 시작하면 다음과 같은 새 명령줄 스위치를 추가할 수 있습니다.

-   *\-NoProfile*: **$profile**을 실행하지 않고 [!INCLUDE[ise_2](../Token/ise_2_md.md)]을 시작합니다.

-   *\-Help*: 도움말 창을 표시합니다.

-   *\-mta*: 다중 스레드 아파트 모드로 [!INCLUDE[ise_2](../Token/ise_2_md.md)]을 시작합니다. [!INCLUDE[ise_2](../Token/ise_2_md.md)]에 대한 기본 작업 모드는 단일 스레드 아파트 모드, 즉 *\-sta*입니다.

**이와 같은 변경을 통해 더해지는 가치**

이러한 명령줄 스위치가 추가되어 [!INCLUDE[ise_2](../Token/ise_2_md.md)]이 실행되는 환경을 제어할 수 있습니다.

**달라진 기능**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0에서는 이러한 명령줄 스위치를 인식할 수 없습니다.

### <a name="BKMK_NewEditorFeatures"></a>새 편집기 기능
**PowerShell 3.0에서 추가되었습니다.**

다른 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 편집 기능에는 다음이 포함됩니다.

-   **XML 구문 색 지정**이제 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 구문에 색을 지정하는 것과 동일한 방법으로 XML 구문에 색을 지정합니다.

-   **중괄호 일치** [!INCLUDE[ise_2](../Token/ise_2_md.md)]에는 중괄호 일치 및 강조 표시가 포함되어 있으며, 다음과 같은 방법으로 사용할 수 있습니다. 예를 들어 여는 중괄호가 선택되어 있는 경우 **일치 항목으로 이동** 명령 또는 **Ctrl\+]**를 사용하면 닫는 중괄호를 찾습니다.

-   **개요 보기** 스크립트 창에서 개요 기능을 지원하므로 왼쪽 여백의 더하기 또는 빼기 기호를 클릭하여 코드의 섹션을 축소하거나 확장할 수 있습니다. 중괄호 또는 **\#regio** 및 **\#endregion** 태그를 사용하여 축소 가능한 섹션의 시작이나 끝을 표시할 수 있습니다. 모든 영역을 확장하거나 축소하려면 **Ctrl\+M**을 누릅니다.

-   **텍스트 끌어서 놓기**이제 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 텍스트 끌어서 놓기를 지원합니다. 텍스트 블록을 선택한 다음 텍스트를 편집기 또는 콘솔의 다른 위치로 끌어서 이동할 수 있습니다. Ctrl 키를 누른 채 선택한 텍스트를 끄는 경우 마우스 단추를 놓으면 텍스트가 새 위치에 복사됩니다. 이 버전의 [!INCLUDE[ise_2](../Token/ise_2_md.md)]와 이전 버전의 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 파일을 [!INCLUDE[ise_2](../Token/ise_2_md.md)]로 끌어다 놓으면 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 파일이 열립니다.

-   **구문 분석 오류 표시** 빨간색 밑줄을 사용하여 구문 분석 오류를 표시합니다. 표시된 오류 위에 마우스를 놓으면 코드에서 검색된 문제가 도구 설명 텍스트에 표시됩니다.

-   **확대/축소** 확대/축소 슬라이더([!INCLUDE[ise_2](../Token/ise_2_md.md)] 창의 오른쪽 맨 아래에 있음)를 사용하거나 콘솔 창에 **$psise.options.Zoom** 명령을 입력하여 콘솔 콘텐츠의 확대/축소 비율을 설정할 수 있습니다.

-   **서식 있는 텍스트 복사 및 붙여넣기** [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 클립보드로 복사하면 원래 선택 항목의 글꼴, 크기 및 색상 정보가 유지됩니다.

-   **블록 선택** Alt 키를 누른 채 스크립트 창에서 마우스로 텍스트를 선택하거나 **Alt\+Shift\+화살표**를 눌러 텍스트 블록을 선택할 수 있습니다.

**이와 같은 변경을 통해 더해지는 가치**

추가 편집 기능은 보다 일관되고 강력한 편집 환경을 제공합니다.

**달라진 기능**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0에는 이러한 향상된 편집 기능이 없었습니다.

### <a name="BKMK_NewHelpViewer"></a>새 도움말 뷰어 창
**PowerShell 3.0에서 추가되었습니다.**

커서가 cmdlet에 있을 때 **F1** 키를 누르거나 cmdlet 일부를 강조 표시하면 강조 표시된 cmdlet에 대한 상황에 맞는 도움말이 새 도움말 뷰어에 표시됩니다. [!INCLUDE[wps_2](../Token/wps_2_md.md)] About 도움말을 표시하려면 콘솔 창에 **operators** 입력한 다음 **F1** 키를 누릅니다.

이 기능을 사용하려면 먼저 Microsoft 웹 사이트에서 최신 버전의 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 도움말 항목을 다운로드합니다. 도움말 항목을 다운로드하는 가장 간단한 방법은 관리자 권한으로 [!INCLUDE[ise_2](../Token/ise_2_md.md)]를 실행할 때 콘솔 창에서 **Update\-Help** cmdlet을 실행하는 것입니다.

**F1** 키가 도움말을 찾는 위치를 변경할 수 있습니다. **도구**\/**옵션** 메뉴의 **일반 설정** 탭에서 **기타 설정** 아래에 있는 **온라인 콘텐츠 대신 로컬 도움말 콘텐츠 사용** 확인란을 설정하거나 선택을 취소할 수 있습니다. 이 확인란을 선택할 경우 클라이언트는 모듈 폴더에 다운로드된 도움말에서 cmdlet 도움말을 찾습니다.  이 확인란의 선택을 취소할 경우 클라이언트는 TechNet 라이브러리에서 cmdlet 도움말을 찾습니다.

**이와 같은 변경을 통해 더해지는 가치**

현재 cmdlet 또는 스크립트를 종료하지 않는 상황에 맞는 도움말은 매끄러운 학습 환경을 제공합니다.

**달라진 기능**

이전 버전의 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 F1 키를 누르면 로컬 컴퓨터의 도움말 파일이 열렸습니다. [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 이상에서는 검색 및 구성할 수 있는 cmdlet 도움말이 포함된 창이 열립니다. 이 도움말 환경은 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0의 새로운 기능이며, 업데이트 가능한 도움말은 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0의 새로운 기능입니다.

### <a name="BKMK_ShowCommand"></a>Show\-Command cmdlet
**PowerShell 3.0에서 추가되었습니다.**

**Show\-Command** cmdlet을 사용하면 그래픽 양식에 입력하여 cmdlet 또는 함수를 작성하거나 실행할 수 있습니다. 이 양식을 사용하면 사용자가 그래픽 환경에서 [!INCLUDE[wps_2](../Token/wps_2_md.md)]을 사용할 수 있습니다. 또한 **Show\-Command**를 사용하면 고급 스크립터가 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 기반 GUI를 빠르게 만들 수 있습니다.

**이와 같은 변경을 통해 더해지는 가치**

[!INCLUDE[wps_2](../Token/wps_2_md.md)] 스크립트에서 **Show\-Command**를 사용하면 익숙한 그래픽 환경을 사용자에게 제공할 수 있습니다. **Show\-Command**는 초급 사용자가 [!INCLUDE[wps_2](../Token/wps_2_md.md)]을 익히는 데 도움이 될 수도 있습니다.

**달라진 기능**

Show\-Command는 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0의 새로운 기능입니다.

## <a name="BKMK_LINKS"></a>참고 항목
[!INCLUDE[wps_2](../Token/wps_2_md.md)]에서 [!INCLUDE[ise_2](../Token/ise_2_md.md)]를 사용하는 방법에 대한 자세한 내용은 다음 링크를 참조하세요.

-   [Windows PowerShell 통합 스크립팅 환경 사용](assetId:///777ea82b-dd73-4269-b61a-69a17e6ff16f)

-   [TechNet Wiki의 ISE](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)

-   [스크립트 센터](http://technet.microsoft.com/scriptcenter/default)



<!--HONumber=Apr16_HO1-->


