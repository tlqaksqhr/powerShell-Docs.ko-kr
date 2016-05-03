---
title: Windows PowerShell ISE에서 프로필을 사용하는 방법
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
---
# Windows PowerShell ISE에서 프로필을 사용하는 방법
이 항목에서는 [!INCLUDE[ise_1](../Token/ise_1_md.md)]에서 프로필을 사용하는 방법을 설명합니다. 이 섹션의 작업을 수행하기 전에 [about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054)를 검토하거나, 콘솔 창에서 "get\-help about\_profiles"를 입력하고 **Enter** 키를 누릅니다.

프로필은 새 세션을 시작할 때 자동으로 실행되는 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 스크립트입니다.  [!INCLUDE[ise_2](../Token/ise_2_md.md)]용 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 프로필을 하나 이상 만든 다음 이 프로필을 사용하여 제공하려는 변수, 별칭, 함수, 색 및 글꼴 기본 설정으로 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 또는 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 환경을 구성하고 사용하도록 준비할 수 있습니다. 프로필은 시작하는 모든 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 세션에 영향을 줍니다.

> [!NOTE]
> [!INCLUDE[wps_2](../Token/wps_2_md.md)] 실행 정책은 스크립트를 실행하고 프로필을 로드할 수 있는지 여부를 결정합니다. 기본 실행 정책인 "Restricted"는 프로필을 비롯한 모든 스크립트가 실행되지 못하게 합니다. "Restricted" 정책을 사용하는 경우 프로필을 로드할 수 없습니다. 실행 정책에 대한 자세한 내용은 [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6)를 참조하세요.

## Windows PowerShell ISE에서 사용할 프로필 선택
[!INCLUDE[ise_2](../Token/ise_2_md.md)]는 현재 사용자와 모든 사용자의 프로필을 지원합니다. 또한 모든 호스트에 적용되는 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 프로필을 지원합니다.

사용하는 프로필은 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 및 [!INCLUDE[ise_2](../Token/ise_2_md.md)]를 사용하는 방법에 따라 결정됩니다.

-   [!INCLUDE[ise_2](../Token/ise_2_md.md)]만 사용하여 Windows PowerShell을 실행하는 경우 모든 항목을 ISE 관련 프로필(예: [!INCLUDE[ise_2](../Token/ise_2_md.md)]용 CurrentUserCurrentHost 프로필 또는 [!INCLUDE[ise_2](../Token/ise_2_md.md)]용 AllUsersCurrentHost 프로필) 중 하나에 저장합니다.

-   여러 호스트 프로그램을 사용하여 Windows PowerShell을 실행하는 경우에는 함수, 별칭, 변수 및 명령은 모든 호스트 프로그램에 영향을 주는 프로필(예: CurrentUserAllHosts 또는 AllUsersAllHosts 프로필)에 저장하고 색 및 글꼴 사용자 지정과 같은 ISE 관련 기능은 [!INCLUDE[ise_2](../Token/ise_2_md.md)]용 CurrentUserCurrentHost 프로필 또는 [!INCLUDE[ise_2](../Token/ise_2_md.md)]용 AllUsersCurrentHost 프로필에 저장합니다.

다음은 [!INCLUDE[ise_2](../Token/ise_2_md.md)]에서 만들고 사용할 수 있는 프로필입니다. 각 프로필은 고유한 특정 경로에 저장됩니다.

|프로필 유형|프로필 경로|
|----------------|----------------|
|"현재 사용자, PowerShell ISE"|$profile.CurrentUserCurrentHost 또는 $profile|
|"모든 사용자, PowerShell ISE"|$profile.AllUsersCurrentHost|
|"현재 사용자, 모든 호스트"|$profile.CurrentUserAllHosts|
|"모든 사용자, 모든 호스트"|$profile.AllUsersAllHosts|

## 새 프로필을 만들려면
새 "현재 사용자, Windows PowerShell ISE" 프로필을 만들려면 다음 명령을 실행합니다.

```
if (!(test-path $profile )) 
{new-item -type file -path $profile -force}
```

새 "모든 사용자, Windows PowerShell ISE" 프로필을 만들려면 다음 명령을 실행합니다.

```
if (!(test-path $profile.AllUsersCurrentHost)) 
{new-item -type file -path $profile.AllUsersCurrentHost -force}
```

새 "현재 사용자, 모든 호스트" 프로필을 만들려면 다음 명령을 실행합니다.

```
if (!(test-path $profile.CurrentUserAllHosts)) 
{new-item -type file -path $profile.CurrentUserAllHosts -force}
```

새 "모든 사용자, 모든 호스트" 프로필을 만들려면 다음과 같이 입력합니다.

```
if (!(test-path $profile.AllUsersAllHosts)) 
{new-item -type file -path $profile.AllUsersAllHosts-force}
```

## 프로필을 편집하려면

1.  프로필을 열려면 편집할 프로필을 지정하는 변수와 함께 psedit 명령을 실행합니다. 예를 들어 "현재 사용자, Windows PowerShell ISE" 프로필을 열려면 다음과 같이 입력합니다. `psEdit $profile`

2.  프로필에 몇 개의 항목을 추가합니다. 다음은 시작하기 위한 몇 가지 예입니다.

    -   콘솔 창의 기본 배경색을 파란색으로 변경하려면 프로필 파일에서 다음과 같이 입력합니다. `$psISE.Options.OutputPaneBackground = 'blue'`. $psISE 변수에 대한 자세한 내용은 [Windows PowerShell ISE 개체 모델 참조](https://technet.microsoft.com/en-us/library/e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c)를 참조하세요.

    -   글꼴 크기를 20으로 변경하려면 프로필 파일에서 다음과 같이 입력합니다. `$psISE.Options.FontSize =20`

3.  프로필 파일을 저장하려면 **파일** 메뉴에서 **저장**을 클릭합니다. 다음에 [!INCLUDE[ise_2](../Token/ise_2_md.md)]를 열면 사용자 지정이 적용됩니다.

## 참고 항목
[about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[Windows PowerShell ISE 사용](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO2-->


