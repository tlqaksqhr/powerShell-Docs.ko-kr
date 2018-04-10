---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 갤러리 계정 만들기
ms.openlocfilehash: c9c263a1926957cbdf059e062326b1903c117f46
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
## <a name="creating-a-powershell-gallery-account"></a>PowerShell 갤러리 계정 만들기

PowerShell 갤러리에 항목을 게시하기 전에 PowerShell 갤러리 계정을 설정해야 합니다.
PowerShell 갤러리 계정은 전자 메일을 사용하도록 설정된 Azure Active Directory 계정 또는 도메인이 outlook.com, hotmail.com 등인 Microsoft 전자 메일 계정에 연결해야 합니다.

PowerShell 갤러리 계정을 만들려면 https://PowerShellGallery.com으로 이동하여 아래 이미지에 표시된 대로 "등록"을 클릭합니다.

![새 계정 등록](./images/CreatingAccount-Register.png)

다음 페이지에서 Azure Active Directory 계정을 사용하려면 "회사 또는 학교 계정"을 선택하고 자신의 계정으로 로그인합니다.
Hotmail.com 또는 Outlook.com 도메인의 계정과 같은 Microsoft 계정을 사용하려면 "개인 계정"을 선택하고 로그인합니다.

로그인하면 PowerShell 갤러리의 사용자 이름을 만들라는 메시지가 표시됩니다.
링크로 제공되는 사용 약관 및 개인 정보 취급 방침을 검토하고 사용자 이름을 입력한 후에 등록을 클릭합니다.

참고: 이 계정 이름은 만들고 나면 변경할 수 없습니다.
계정 이름과 관련한 추가 세부 정보는 [항목 소유자 관리](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners)를 참조하세요.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>PowerShell 갤러리 계정 관련 권장 사례

PowerShell 갤러리 계정에 사용하는 전자 메일 계정은 자주 모니터링해야 합니다.
PowerShell 갤러리 항목 소유자는 PowerShell 갤러리 계정과 연결된 주소를 사용하여 전자 메일을 통해 모든 연락을 처리합니다.
항목 소유자에게 연락을 할 수 없는 경우에는 운영 팀이 상황에 따라 항목을 삭제해야 할 수도 있습니다.

PowerShell 갤러리에 항목을 자주 게시하는 조직은 Outlook.com이나 기타 Microsoft 계정 도메인에서 게시용으로 고유한 계정을 만듭니다.
하지만 대부분의 조직에서는 이 계정을 정기적으로 모니터링하지 않습니다.
이러한 경우에는 Outlook 전달 기능을 사용하여 항목 소유자가 모니터링할 다른 계정(대개 조직 내의 계정)으로 전자 메일을 전송하는 모범 사례를 사용하는 것이 좋습니다.

항목과 연결된 소유자가 여러 명이면 PowerShell 갤러리로부터의 모든 연락 사항은 모든 소유자에게 전송됩니다.
항목에 소유자를 추가하는 방법과 관련한 추가 세부 정보는 [항목 소유자 관리](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners)를 참조하세요.