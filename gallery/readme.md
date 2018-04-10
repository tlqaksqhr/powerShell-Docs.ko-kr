---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery,psget,갤러리
title: PowerShell 갤러리
ms.openlocfilehash: 9519b8bcca9f43419a33db380c3b852e9bb354ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershell-gallery"></a>PowerShell 갤러리

PowerShell 갤러리는 PowerShell 콘텐츠에 대한 중앙 리포지토리입니다. 갤러리에서 새로운 PowerShell 명령 또는 DSC(필요한 상태 구성) 리소스를 찾을 수 있습니다.

## <a name="powershellget-overview"></a>PowerShellGet 개요

PowerShellGet 모듈에는 [PowerShell 갤러리](https://www.PowerShellGallery.com) 및 다른 개인 리포지토리에서 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 PowerShell 아티팩트를 검색, 설치, 업데이트 및 게시하기 위한 cmdlet이 포함되어 있습니다.

## <a name="getting-started-with-the-gallery"></a>갤러리 시작

갤러리에서 항목을 설치하려면 Windows 10, WMF(Windows Management Framework) 5.0 또는 MSI 기반 설치 관리자(PowerShell 3 및 4용)에서 사용할 수 있는 최신 버전의 PowerShellGet 모듈이 있어야 합니다.

- [**Windows 10 다운로드**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**WMF 5.0 다운로드**](http://go.microsoft.com/fwlink/?LinkId=398175)
- [**MSI 설치 관리자 다운로드**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

최신 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 모듈을 사용할 경우 다음을 수행할 수 있습니다.

-   [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 및 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)를 사용하여 갤러리에서 항목 검색
-   [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) 및 [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)를 사용하여 갤러리의 항목을 시스템에 저장
-   [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 및 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)를 사용하여 갤러리에서 항목 설치
-   [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) 및 [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)를 사용하여 갤러리에 항목 업로드
-   [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)를 사용하여 사용자 지정 리포지토리 추가

갤러리와 함께 PowerShellGet 명령을 사용하는 방법에 대한 자세한 내용은 [시작](psgallery/psgallery_gettingstarted.md) 페이지를 참조하세요. *Update-Help -Module PowerShellGet*을 실행하여 이러한 명령에 대한 로컬 도움말을 설치할 수도 있습니다.

## <a name="supported-operating-systems"></a>지원되는 운영 체제

**PowerShellGet** 모듈을 사용하려면 **PowerShell 3.0 이상**이 있어야 합니다.

따라서 **PowerShellGet**에는 다음 운영 체제 중 하나가 필요합니다.

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet**을 사용하려면 .NET Framework 4.5 이상도 있어야 합니다. .NET Framework 4.5 이상은 [여기](https://msdn.microsoft.com/library/5a4x27ek.aspx)에서 설치할 수 있습니다.


## <a name="got-a-question-have-feedback"></a>궁금한 점이 있나요? 피드백이 있습니까?

PowerShell 갤러리 및 PowerShellGet에 대한 자세한 내용은 [시작](psgallery/psgallery_gettingstarted.md) 페이지에서 확인할 수 있습니다. [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell)를 사용하여 피드백을 제공하고 문제를 신고하세요.