---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
description: 게시자용 지침
title: PowerShell 갤러리 게시 지침 및 모범 사례
ms.openlocfilehash: 3aca76f8904c7eb64e5c96ae4f0f26014e0d2609
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190335"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShell 갤러리 게시 지침 및 모범 사례

이 항목에서는 PowerShell 갤러리에 게시하는 항목이 광범위하게 채택되어 사용자들이 더욱 유용하게 활용할 수 있도록 하기 위해 Microsoft 팀에서 사용하는 권장 단계에 대해 설명합니다. 이 항목의 설명은 PowerShell 갤러리에서 매니페스트 데이터를 처리하는 방식과 다수의 PowerShell 갤러리 사용자들이 제공한 피드백을 기반으로 합니다.
다음 지침에 따라 게시된 항목은 보다 많은 사용자가 설치하고 신뢰하며 관심을 가질 가능성이 높습니다.

아래에는 유용한 PowerShell 갤러리 항목을 만들기 위한 지침, 가장 중요한 선택적 매니페스트 설정, 초기 검토자와 [Powershell 스크립트 분석기](https://aka.ms/psscriptanalyzer)의 피드백을 반영하여 코드를 개선하는 방법, 공유한 항목의 사용 방법을 알려 주는 모듈/문서/테스트/예제의 버전을 관리하는 방법이 나와 있습니다.
이 문서의 대다수 내용은 [고품질 DSC 리소스 모듈](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md) 게시를 위한 지침을 따릅니다.

PowerShell 갤러리에 있는 항목을 게시하는 방법은 [항목 만들기 및 게시](https://msdn.microsoft.com/powershell/gallery/psgallery/creating-and-publishing-an-item)를 참조하세요.

이러한 지침에 대한 여러분의 피드백을 기다리고 있습니다. 피드백이 있는 경우 [Github 문서 리포지토리](https://github.com/powershell/powershell-docs/)에 해당 사안의 게시물을 작성하세요.

## <a name="best-practices-for-publishing-items"></a>항목 게시에 대한 모범 사례

아래에는 PowerShell 갤러리 항목 사용자들이 중요하다고 생각하는 모범 사례가 명목상의 우선 순위 순서대로 나열되어 있습니다.
이러한 지침을 따르는 항목은 다른 사용자들이 다운로드하여 채택할 가능성이 훨씬 높습니다.

- PSScriptAnalyzer 사용
- 설명서와 예제 포함
- 피드백에 적절하게 응답
- 스크립트가 아닌 모듈 제공
- 프로젝트 사이트에 대한 링크 제공
- 모듈에 테스트 포함
- 사용 조건 포함 및/또는 링크 제공
- 코드 서명
- 버전 관리용 [SemVer](http://semver.org/) 지침 준수
- 일반 PowerShell 갤러리 태그에 설명되어 있는 일반 태그 사용
- 로컬 리포지토리를 사용하여 게시 테스트

아래 섹션에서는 이러한 각 모범 사례에 대해 간략하게 설명합니다.

## <a name="use-psscriptanalyzer"></a>PSScriptAnalyzer 사용

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer)는 PowerShell 코드에서 작동하는 무료 정적 코드 분석 도구입니다.
PowerShell 코드에서 가장 흔히 발생하는 문제를 식별하며, 권장 문제 해결 방법을 제공하는 경우가 많습니다.
손쉽게 사용할 수 있는 이 도구는 문제를 오류(해결해야 하는 심각한 문제), 경고(검토하여 해결해야 하는 문제) 및 정보(모범 사례를 확인하면 좋은 문제)로 분류합니다.
PowerShell 갤러리에 게시하는 모든 항목은 PSScriptAnalyzer를 통해 검사되며 오류가 소유자에게 다시 보고됩니다. 그러면 소유자는 오류를 해결해야 합니다.

`-Recurse` 및 `-Severity` 경고를 포함하여 `Invoke-ScriptAnalyzer`를 실행하는 것이 모범 사례입니다.

실행 후에는 결과를 검토하여 다음 사항을 확인합니다.

- 설명서에서 모든 오류를 수정했거나 해결했습니다.
- 해당하는 경우 모든 경고를 검토하고 해결했습니다.

PowerShell 갤러리에서 항목을 가져오는 사용자는 PSScriptAnalyzer를 실행하여 모든 오류와 경고를 평가하는 것이 좋습니다.
사용자가 PSScriptAnalyzer에서 보고하는 오류가 있음을 확인하면 항목 소유자에게 문의할 가능성이 매우 높습니다.
항목에서 오류로 플래그가 지정된 코드를 유지해야 하는 이유가 있다면 같은 질문에 여러 번 대답하지 않아도 되도록 설명서에 해당 정보를 추가하세요.

## <a name="include-documentation-and-examples"></a>설명서와 예제 포함

사용자가 공유 코드를 효율적으로 활용할 수 있도록 하는 가장 좋은 수단이 설명서 및 예제입니다.

설명서는 PowerShell 갤러리에 게시하는 항목에 포함할 수 있는 가장 유용한 항목입니다.
사용자는 대개 설명서가 없는 항목을 건너뛰며, 대신 코드를 확인함으로써 해당 항목 및 사용 방법에 대해 파악합니다.
PowerShell 항목과 함께 설명서를 제공하는 방법을 설명하는 다음과 같은 여러 MSDN 문서를 참조할 수 있습니다.

- 도움말 제공 관련 지침은 [cmdlet 작성 방법 도움말](https://go.microsoft.com/fwlink/?LinkID=123415)에 나와 있습니다.
- 모든 PowerShell 스크립트, 함수 또는 cmdlet에 가장 유용한 항목인 cmdlet 도움말을 작성합니다.
  cmdlet 도움말을 작성하는 방법에 대한 자세한 내용을 확인하려면 MSDN 라이브러리에서 [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415)(Cmdlet 도움말을 작성하는 방법)를 먼저 검토하세요.
  스크립트 내에 도움말을 추가하려면 [주석 기반 도움말 정보](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_comment_based_help)를 참조하세요.
- 대부분의 모듈에는 Markdown 파일과 같이 텍스트 형식의 설명서도 포함되어 있습니다.
  이러한 설명서는 Markdown이 많이 사용되는 Github에 프로젝트 사이트가 있는 경우 특히 유용할 수 있습니다.
  따라서 [Github 지원 Markdown](https://help.github.com/categories/writing-on-github/)을 사용하는 것이 좋습니다.

예제는 사용자에게 항목의 올바른 사용 방식을 제시합니다.
대부분의 개발자는 설명서보다 먼저 예제를 확인하여 특정 작업 수행 방법을 파악합니다.
가장 효율적인 예제 유형은 기본적인 사용 방식과 실제 사용 사례 시뮬레이션을 제공하며, 코드 주석도 적절하게 작성되어 있습니다.
PowerShell 갤러리에 게시하는 모듈의 예제는 모듈 루트 아래의 Examples 폴더에 있어야 합니다.

적절한 예제 패턴은 [PSDscResource 모듈](https://www.powershellgallery.com/packages/PSDscResources)의 Examples\RegistryResource 폴더에서 확인할 수 있습니다.
이 폴더에는 4가지 샘플 사용 사례가 포함되어 있으며, 각 파일의 맨 위에는 해당 사용 사례에서 제시하는 사용 방식의 간략한 설명이 나와 있습니다.

## <a name="respond-to-feedback"></a>피드백에 응답

피드백에 적절하게 응답하는 항목 소유자는 커뮤니티에서 높은 평가를 받습니다.
특정 항목에 관심이 많아 항목 개선을 지원하고자 하여 건설적인 피드백을 제공하는 사용자에게는 적절하게 응답을 해야 합니다.

PowerShell 갤러리에서는 두 가지 피드백 방법이 제공됩니다.

- 소유자에게 문의: 사용자가 항목 소유자에게 전자 메일을 보낼 수 있습니다. 항목 소유자는 PowerShell 갤러리 항목에 사용하는 전자 메일 주소를 모니터링하여 제기되는 문제에 응답을 해야 합니다. 이 방법의 한 가지 단점은, 사용자와 소유자만이 교환하는 의견을 확인할 수 있으므로 소유자가 같은 질문에 여러 번 대답해야 할 수도 있다는 것입니다.
- 댓글: 항목 페이지의 맨 아래에는 댓글 필드가 있습니다.
  이 시스템의 장점은 다른 사용자들도 댓글과 응답을 볼 수 있으므로 질문 하나에 대답해야 하는 횟수를 줄일 수 있다는 것입니다.
  항목 소유자는 각 항목에 대한 댓글을 항목에 반영하는 것이 좋습니다.
자세한 방법은 [소셜 미디어나 댓글을 통해 피드백 제공](../how-to/working-with-items/social-media-feedback.md)을 참조하세요.

피드백에 건설적인 방식으로 응답하는 소유자는 커뮤니티에서 높은 평가를 받습니다.
보고서를 활용하여 필요에 따라 추가 정보를 요청하거나, 해결 방법을 제공하거나, 업데이트를 통해 문제가 해결되는지를 확인하세요.

이러한 통신 채널에서 부적절한 행위가 확인되는 경우 PowerShell 갤러리의 신고하기 기능을 사용하여 갤러리 관리자에게 문의하세요.

## <a name="modules-versus-scripts"></a>모듈과 스크립트 비교

다른 사용자와 스크립트를 공유하면 해당 사용자에게 발생했을 수 있는 문제를 해결하는 방법의 예를 제공할 수 있으므로 효율적입니다.
그런데 PowerShell 갤러리의 스크립트는 별도의 설명서, 예제 및 테스트가 없는 단일 파일입니다.

반면 PowerShell 모듈은 여러 폴더와 파일을 패키지에 포함할 수 있는 폴더 구조로 되어 있습니다.
이러한 모듈 구조를 활용하면 앞에서 모범 사례로 언급한 cmdlet 도움말, 설명서, 예제, 테스트 등의 기타 항목을 포함할 수 있습니다.
모듈의 가장 큰 단점은, 모듈 내의 스크립트를 노출하여 함수로 사용해야 한다는 것입니다.
모듈을 작성하는 방법에 대한 자세한 내용은 [Windows PowerShell 모듈 작성](http://go.microsoft.com/fwlink/?LinkId=144916)을 참조하세요.

스크립트가 사용자에게 보다 효율적인 환경을 제공하는 상황, 특히 DSC 구성을 사용하는 경우가 있습니다.
DSC 구성의 모범 사례는 문서, 예제, 테스트가 들어 있는 모듈을 포함하여 구성을 스크립트로 게시하는 것입니다. 
이 스크립트에서는 RequiredModules = @(모듈 이름) 형식을 사용하여 포함된 모듈이 나열됩니다.
모든 스크립트에서 이 방식을 사용할 수 있습니다.

사용자에 따라서는 다른 모범 사례를 따르는 독립 실행형 스크립트가 더욱 유용할 수도 있습니다.
PowerShell 갤러리에 스크립트를 게시할 때는 주석 기반 설명서와 프로젝트 사이트 링크를 제공하는 것이 좋습니다.

## <a name="provide-a-link-to-a-project-site"></a>프로젝트 사이트에 대한 링크 제공

프로젝트 사이트에서는 게시자가 PowerShell 갤러리 항목의 사용자와 직접 상호 작용할 수 있습니다.
사용자는 이러한 링크를 제공하는 항목을 선호합니다. 링크를 통해 항목에 대한 정보를 보다 쉽게 파악할 수 있기 때문입니다.
PowerShell 갤러리의 대다수 항목은 GitHub에서 개발되지만 웹 서비스 전문 조직에서 제공하는 항목도 있습니다.
이러한 각 조직을 프로젝트 사이트로 간주할 수 있습니다.

다음과 같이 매니페스트의 PSData 섹션에 ProjectURI를 포함하는 방식으로 링크를 추가합니다.

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

ProjectURI를 제공하면 PowerShell 갤러리의 항목 페이지 왼쪽에 프로젝트 사이트 링크가 포함됩니다.

## <a name="include-tests"></a>테스트 포함

사용자는 오픈 소스 코드를 사용하는 테스트가 항목에 포함되어 있는지를 중요하게 고려합니다. 테스트가 있으면 항목의 유효성이 검사되었음을 확인할 수 있으며 코드 작동 방식에 대한 정보를 파악할 수 있기 때문입니다. 또한 사용자가 환경에 맞게 코드를 수정하더라도 원래 기능이 손상되지 않도록 유지할 수 있습니다.

PowerShell 전용으로 설계된 Pester 테스트 프레임워크를 활용할 수 있도록 테스트를 작성하는 것이 좋습니다.
Pester는 [GitHub](https://github.com/Pester/Pester) 및 [PowerShell 갤러리](https://www.powershellgallery.com/packages/Pester/)에서 제공되며 Windows 10, Windows Server 2016, WMF 5.0, WMF 5.1에 기본적으로 포함되어 있습니다.

[GitHub의 Pester 프로젝트 사이트](https://github.com/Pester/Pester)에는 Pester 테스트 작성을 시작하는 단계에서 모범 사례에 이르기까지 전 과정을 설명하는 유용한 설명서가 포함되어 있습니다.

테스트 범위의 대상은 [고품질 리소스 모듈 설명서](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md)에 나와 있습니다. 단위 테스트 코드의 70%를 대상으로 포함하는 것이 좋습니다.

## <a name="include-andor-link-to-license-terms"></a>사용 조건 포함 및/또는 링크 제공

PowerShell 갤러리에 게시하는 모든 항목은 사용 조건을 지정하거나 [사용 약관](https://www.powershellgallery.com/policies/Terms)의 "증 A"에 포함된 라이선스에 따라 사용해야 합니다.
다른 라이선스를 지정하는 가장 효율적인 방식은 PSData에서 LicenseURI를 사용하여 라이선스 링크를 제공하는 것입니다.
해당 예제는 권장 매니페스트 필드 항목에서 확인할 수 있습니다.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>코드 서명

코드에 서명하면 사용자가 항목 게시자를 최대한 신뢰할 수 있으며 사용자가 다운로드하는 코드의 복사본이 게시자가 제공한 것과 정확히 일치함을 보장할 수 있습니다.
코드 서명에 대해 전반적으로 자세히 알아보려면 [코드 서명 소개](http://go.microsoft.com/fwlink/?LinkId=106296)를 참조하세요.
PowerShell에서는 두 가지 기본적인 방식을 통한 코드 서명 유효성 검사를 지원합니다.

- 스크립트 파일 서명
- 모듈 카탈로그 서명

PowerShell 파일에 서명하면 실행하는 코드가 신뢰할 수 있는 출처에서 제작되었으며 수정되지 않았음을 효율적으로 확인할 수 있습니다.
PowerShell 스크립트 파일에 서명하는 방법에 대한 자세한 내용은 [서명 정보](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_signing) 항목에 나와 있습니다.
요약하자면, 스크립트를 로드할 때 PowerShell에서 유효성을 검사하는 모든 .PS1 파일에 서명을 추가할 수 있습니다.
[실행 정책](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) cmdlet을 사용하면 서명된 스크립트를 사용하도록 PowerShell을 제한할 수 있습니다.

카탈로그 서명 모듈은 PowerShell 버전 5.1에 추가된 기능입니다.
모듈에 서명하는 방법은 [카탈로그 cmdlet](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/catalog-cmdlets) 항목에 나와 있습니다.
요약하자면, 모듈의 모든 파일에 대한 해시 값이 포함된 카탈로그 파일을 만들어 해당 파일에 서명하는 방식으로 카탈로그 서명을 수행합니다.
그러면 PowerShellGet publish-module, install-module, save-module 및 update-module cmdlet이 서명을 점검하여 유효한지를 확인한 다음 각 항목의 해시 값이 카탈로그에 포함된 값과 일치하는지를 확인합니다.
이전 버전의 모듈이 시스템에 설치되어 있으면 install-module은 새 버전의 서명 기관이 이전에 설치한 모듈의 기관과 일치하는지 확인합니다.
카탈로그 서명 방식은 스크립트 파일 서명 방식과 함께 사용할 수는 있지만 대신 사용할 수는 없습니다. PowerShell은 모듈 로드 시에 카탈로그 서명의 유효성을 검사하지 않습니다.

## <a name="follow-semver-guidelines-for-versioning"></a>버전 관리용 SemVer 지침 준수

[SemVer](http://semver.org/)는 변경 내용을 쉽게 해석할 수 있도록 버전 구성 및 변경 방법을 설명하는 공개 규칙입니다.
항목 버전을 매니페스트 데이터에 포함해야 합니다.

- 버전은 0.1.1 또는 4.11.192와 같이 마침표로 구분된 숫자 블록 3개로 구성해야 합니다.
- 버전이 "0"으로 시작하는 항목은 아직 프로덕션 환경에서 사용할 준비가 되지 않은 것입니다. 버전에서 숫자 "0"만 사용되는 경우에만 첫 번째 숫자를 "0"으로 시작해야 합니다.
- 첫 번째 숫자가 1.9.9999에서 2.0.0으로 바뀌는 등 변경되는 경우 버전 간에 중요한 변경 내용이 있는 것입니다.
- 두 번째 숫자가 1.01에서 1.02로 바뀌는 등 변경되는 경우에는 모듈에 새 cmdlet이 추가되는 등의 기능 수준 변경이 적용된 것입니다.
- 세 번째 숫자가 변경되는 경우에는 새 매개 변수, 업데이트된 샘플, 새 테스트 등의 일반적인 변경 내용이 있는 것입니다.
- PowerShell은 버전을 나열할 때 버전을 문자열로 정렬하므로 1.01.0이 1.001.0보다 더 큰 것으로 간주됩니다.

PowerShell은 SemVer가 게시되기 전에 제작되었으므로 SemVer의 대다수 요소를 지원하기는 하지만 다음과 같이 지원되지 않는 요소도 있습니다.

- 버전 번호의 시험판 문자열은 지원되지 않습니다. 시험판 문자열은 게시자가 버전 1.0.0을 제공한 후 새 주 버전의 미리 보기 릴리스를 제공하려는 경우에 유용합니다. 이 요소는 향후 PowerShell 갤러리 릴리스와 PowerShellGet cmdlet에서 지원될 예정입니다.
- PowerShell 및 PowerShell 갤러리에서는 세그먼트가 1개, 2개, 4개인 버전 문자열을 사용할 수 있습니다. 대부분의 초기 모듈은 이 지침을 따르지 않으며, Microsoft에서 릴리스된 제품에는 빌드 정보가 5.1.14393.1066에서와 같이 네 번째 숫자 블록으로 포함되어 있습니다. 버전 관리 측면에서는 이러한 차이가 무시됩니다.

## <a name="test-using-a-local-repository"></a>로컬 리포지토리를 사용하여 테스트

PowerShell 갤러리는 게시 프로세스를 테스트하기 위한 대상으로 설계되지 않았습니다.
PowerShell 갤러리에 대한 게시의 종단 간 프로세스를 테스트하는 가장 좋은 방법은 자체 로컬 리포지토리를 설정해서 사용하는 것입니다.
이 작업은 다음과 같은 몇 가지 방법으로 수행할 수 있습니다.

- GitHub의 [PS 전용 갤러리 프로젝트](https://github.com/PowerShell/PSPrivateGallery)를 사용하여 로컬 PowerShell 갤러리 인스턴스를 설정합니다. 이 미리 보기 프로젝트는 제어하고 테스트에 사용할 수 있는 PowerShell 갤러리 인스턴스를 설정하는 데 도움이 됩니다.
- [내부 Nuget 리포지토리](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/)를 설정합니다. 이렇게 하려면 설정하기 위해 수행할 작업이 더 많지만, 더 많은 요구 사항의 유효성을 검사할 수 있는 이점이 있으며, 특히 API 키 사용 유효성 검사가 가능하며 게시할 때 대상에 종속성이 있는지를 확인할 수 있습니다.
- 파일 공유를 테스트 “리포지토리”로 설정합니다. 이 설정은 쉽지만, 파일 공유이므로 위에서 설명한 유효성 검사가 수행되지 않습니다. 이 경우의 한 가지 잠재적 이점은 파일 공유에서 (필수) API 키를 확인하지 않으므로 PowerShell 갤러리에 게시하는 데 사용하는 키와 같은 키를 사용할 수 있다는 점입니다.

이러한 솔루션 중 원하는 솔루션을 사용하고 Register-PSRepository를 사용하여 Publish-Module의 -Repository 속성에 사용하는 새 “리포지토리”를 정의합니다.

게시 테스트에 대한 한 가지 추가 사항: PowerShell 갤러리에 게시하는 모든 항목은 게시하려는 항목에 종속된 항목이 없음을 확인할 운영 팀의 도움 없이는 삭제할 수 없습니다.
이러한 이유로 Microsoft에서는 PowerShell 갤러리를 테스트 대상으로 지원하지 않으며 이렇게 하는 게시자에게 연락합니다.

## <a name="recommended-workflow"></a>권장 워크플로

PowerShell 갤러리에 게시하는 항목을 가장 효율적으로 활용할 수 있는 방식은 다음과 같습니다.

- 오픈 소스 프로젝트 사이트에서 초기 개발을 수행합니다. PowerShell 팀은 Github를 사용합니다.
- 검토자와 [Powershell 스크립트 분석기](https://aka.ms/psscriptanalyzer)의 피드백을 활용하여 안정적인 상태의 코드를 작성합니다.
- 다른 사용자들이 작업한 코드의 사용 방식을 알 수 있도록 설명서를 포함합니다.
- 로컬 리포지토리를 사용하여 게시 작업을 테스트합니다.
- 프로젝트 사이트 링크와 설명서를 포함하여 안정적인 릴리스 또는 알파 릴리스를 PowerShell 갤러리에 게시합니다.
- 피드백을 수집하고 프로젝트 사이트에서 코드를 반복 실행해 본 다음 안정적인 업데이트를 PowerShell 갤러리에 게시합니다.
- 프로젝트와 모듈에 예제 및 Pester 테스트를 추가합니다.
- 항목에 코드로 서명할지를 결정합니다.
- 프로젝트가 프로덕션 환경에서 사용할 수 있는 상태가 되면 1.0.0 버전을 PowerShell 갤러리에 게시합니다.
- 계속 피드백을 수집하고 사용자 입력 내용을 바탕으로 코드를 반복 실행합니다.