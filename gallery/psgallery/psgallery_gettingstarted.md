---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: 6b2119a736cc428598c245526e5af970d86af998
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2017
---
<a id="get-started-with-the-powershell-gallery" class="xliff"></a>
# PowerShell 갤러리 시작

<a id="what-is-the-powershell-gallery" class="xliff"></a>
## PowerShell 갤러리란?

PowerShell 갤러리는 PowerShell 콘텐츠에 대한 중앙 리포지토리입니다.
PowerShell 갤러리에서 PowerShell 명령 및 DSC(필요한 상태 구성) 리소스가 포함된 유용한 PowerShell 모듈을 찾을 수 있습니다. PowerShell 워크플로가 포함된 경우도 있으며 일련의 작업을 간략하게 설명하고 해당 작업 순서를 제공하는 PowerShell 스크립트를 찾을 수도 있습니다.
이러한 항목 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다.

<a id="requirements" class="xliff"></a>
## 요구 사항

PowerShell 갤러리에서 시스템으로 항목을 다운로드하려면 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 모듈이 필요합니다. 다음 중 하나에서 PowerShellGet 모듈을 찾을 수 있습니다. PowerShell 갤러리에서 항목을 다운로드하기 위해 로그인할 필요는 없습니다.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI 설치 관리자(PowerShell 3 및 4용)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet이 PowerShell 갤러리를 사용하려면 [NuGet 공급자](http://go.microsoft.com/fwlink/?LinkId=722208)도 필요합니다. NuGet 공급자가 다음 위치 중 하나에 없을 경우 PowerShellGet을 처음 사용할 때 NuGet 공급자를 자동으로 설치하라는 메시지가 표시됩니다.

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

또는 `Install-PackageProvider -Name NuGet -Force`를 실행하여 NuGet 공급자의 다운로드 및 설치를 자동화할 수 있습니다.

  
2.8.5.201 이전 버전의 NuGet이 있는 경우 다음 PowerShell cmdlet을 호출하여 최신 버전의 NuGet을 설치하고 전환해야 합니다.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  위의 설치 위치에서 이전 버전의 NuGet을 삭제합니다.

자세한 내용은 <http://oneget.org/>를 참조하세요.

  
참고: 패키지 형식이 변경되었으므로 최신 버전의 PowerShellGet 및 PackageManagement로 업데이트하여 최근에 업데이트된 항목을 설치하는 것이 좋습니다. PowerShellGet은 Windows 10에 포함되어 있습니다. 자세한 내용은 [여기](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)를 참조하세요.
PowerShellGet은 [여기](http://go.microsoft.com/fwlink/?LinkId=398175)서 다운로드할 수 있는 WMF(Windows Management Framework) 5.0의 일부이기도 합니다.

<a id="discovering-items-from-the-powershell-gallery" class="xliff"></a>
## PowerShell 갤러리에서 항목 검색

이 웹 사이트에서 **검색** 컨트롤을 사용하거나 모듈 및 스크립트 페이지를 검색하여 PowerShell 갤러리에서 항목을 찾을 수 있습니다. 항목 유형에 따라 [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 및 [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet을 `-Repository PSGallery`와 함께 사용하여 PowerShell 갤러리에서 항목을 찾을 수도 있습니다.

[**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 및 [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)의 다음 매개 변수를 사용하여 갤러리의 결과를 필터링할 수 있습니다.

- 이름
- AllVersions
- MinimumVersion
- RequiredVersion
- 태그
- Includes
- DscResource
- RoleCapability
- 명령
- 필터

갤러리에서 특정 DSC 리소스를 검색하는 데만 관심이 있는 경우 [**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet을 실행할 수 있습니다.
[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)는 갤러리에 포함된 DSC 리소스에 대한 데이터를 반환합니다. DSC 리소스는 항상 모듈의 일부로 제공되기 때문에 여전히 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)을 실행하여 이러한 DSC 리소스를 설치해야 합니다.

<a id="learning-about-items-in-the-powershell-gallery" class="xliff"></a>
## PowerShell 갤러리에 있는 항목에 대해 알아보기

관심 있는 항목을 식별했으면 자세히 알아보는 것이 좋습니다. 이렇게 하려면 갤러리에서 해당 항목의 특정 페이지를 검사합니다. 이 페이지에서 항목과 함께 업로드된 메타데이터를 모두 볼 수 있습니다. 항목에 대한 이 메타데이터는 항목의 작성자가 제공하며 Microsoft에서 확인하지 않습니다. 항목의 소유자는 항목을 게시하는 데 사용되는 갤러리 계정에 강하게 연결되어 있으며 작성자 필드보다 더 신뢰할 수 있습니다.

좋은 의도에서 게시되지 않은 것 같은 항목을 발견할 경우 해당 항목의 페이지에서 **신고하기**를 클릭합니다.

[**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 또는 [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)를 실행하는 경우 반환된 PSGetModuleInfo 개체에서 이 데이터를 볼 수 있습니다. 예를 들어 [**Find-Module -Name PSReadLine -Repository PSGallery | Get-Member**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)는 갤러리에 있는 PSReadLine 모듈에 대한 데이터를 반환합니다.

<a id="downloading-items-from-the-powershell-gallery" class="xliff"></a>
## PowerShell 갤러리에서 항목 다운로드

PowerShell 갤러리에서 항목을 다운로드하는 경우 다음 프로세스를 사용하는 것이 좋습니다.

<a id="inspect" class="xliff"></a>
### 검사

검사를 위해 갤러리에서 항목을 다운로드하려면 항목 유형에 따라 [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 또는 [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet을 실행합니다. 이렇게 하면 설치하지 않고 로컬에 항목을 저장한 다음 항목 내용을 검사할 수 있습니다. 저장된 항목을 수동으로 삭제해야 합니다.

이러한 항목 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다. 설치 전에 이 갤러리에 있는 항목의 내용과 코드를 검토하는 것이 좋습니다.

좋은 의도에서 게시되지 않은 것 같은 항목을 발견할 경우 해당 항목의 페이지에서 **신고하기**를 클릭합니다.

<a id="install" class="xliff"></a>
### 설치

사용을 위해 갤러리에서 항목을 설치하려면 항목 유형에 따라 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 또는 [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet을 실행합니다.

[**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)은 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Modules`에 모듈을 설치합니다. 이 경우 관리자 계정이 필요합니다. `-Scope
CurrentUser` 매개 변수를 추가하는 경우 모듈은 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`에 설치됩니다.

[**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)는 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Scripts`에 스크립트를 설치합니다. 이 경우 관리자 계정이 필요합니다. `-Scope
CurrentUser` 매개 변수를 추가하는 경우 스크립트는 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`에 설치됩니다.

기본적으로 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 및 [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)는 최신 버전의 항목을 설치합니다. 이전 버전의 항목을 설치하려면 `-RequiredVersion` 매개 변수를 추가합니다.

<a id="deploy" class="xliff"></a>
### 배포 게스트 클러스터에

PowerShell 갤러리의 항목을 Azure Automation에 배포하려면 항목 세부 정보 페이지에서 **Azure Automation에 배포**를 클릭합니다. Azure 관리 포털로 리디렉션되며, 여기서 Azure 계정 자격 증명을 사용하여 로그인합니다. 종속성과 함께 항목을 배포하면 모든 종속성이 Azure Automation에 배포됩니다. 항목 메타데이터에 **AzureAutomationNotSupported** 태그를 추가하면 'Azure Automation에 배포' 단추를 해제할 수 있습니다.

Azure Automation에 대한 자세한 내용은 [Azure Automation 웹 사이트](http://azure.microsoft.com/en-us/services/automation/)를 참조하세요.

<a id="updating-items-from-the-powershell-gallery" class="xliff"></a>
## PowerShell 갤러리에서 항목 업데이트

PowerShell 갤러리에서 설치된 항목을 업데이트하려면 [**Update-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 또는 [**Update-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet을 실행합니다. 추가 매개 변수 없이 실행하면 [**Update-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)이 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)을 실행하여 설치된 각 모듈을 업데이트하려고 합니다.
모듈을 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.

마찬가지로, 추가 매개 변수 없이 실행하면 [**Update-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)는 [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)를 실행하여 설치된 각 스크립트를 업데이트하려고 합니다.
스크립트를 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.

<a id="list-items-that-you-have-installed-from-the-powershell-gallery" class="xliff"></a>
## PowerShell 갤러리에서 설치한 항목 나열

PowerShell 갤러리에서 설치한 모듈을 찾으려면 [**Get-InstalledModule**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet을 실행합니다. 이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 모듈을 모두 나열합니다.

마찬가지로, PowerShell 갤러리에서 설치한 스크립트를 찾으려면 [**Get-InstalledScript**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet을 실행합니다. 이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 스크립트를 모두 나열합니다.

