## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 오픈 소스 규정

이 프로젝트에서는 [Microsoft 오픈 소스 규정](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.
자세한 내용은 [규정 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하고, 질문이나 의견이 더 있는 경우는 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.

[![빌드 상태](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

# <a name="powershell-documentation"></a>PowerShell 설명서

공식 Windows PowerShell 설명서가 있는 PowerShell-Docs 리포지토리를 시작합니다. 

## <a name="repository-structure"></a>리포지토리 구조
이 리포지토리의 각 폴더는 [MSDN](https://msdn.microsoft.com/en-us/powershell)에 내용을 게시합니다. 다음 PowerShell 자산에 해당되는 폴더:
* [/dsc/](https://msdn.microsoft.com/en-us/powershell/dsc/)는 필요한 상태 구성 기능에 사용
* [/gallery/](https://msdn.microsoft.com/powershell/gallery)는 [PowerShell 갤러리](https://www.powershellgallery.com/)에 사용
* [/jea/](https://msdn.microsoft.com/powershell/jea/)는 Just Enough Administration 기능에 사용
* [/reference/](https://msdn.microsoft.com/powershell/reference/)는 버전 2.0, 3.0, 4.0, 5.0, 5.1 및 6.0 간의 PowerShell 모듈 참조에 사용
  * 이 콘텐츠는 앞으로 `Get-Help` cmdlet을 통해 검색될 예정
* [/scripting/](https://msdn.microsoft.com/en-us/powershell/scripting/)은 일반 PowerShell 참조 콘텐츠
* [/wmf](https://msdn.microsoft.com/en-us/powershell/wmf/readme)에는 새 버전의 PowerShell을 이전 버전의 Windows에 배포하는 데 사용되는 패키지인 Windows Management Framework의 릴리스 정보를 포함. 



## <a name="contributing"></a>참가

Microsoft는 *준비* 분기로 [끌어오기 요청](https://help.github.com/articles/using-pull-requests/)을 통해 적극적으로 이 리포지토리로 참가하도록 모읍니다. 끌어오기 요청을 제출하기 전에 [참가 사용권 계약에 서명](https://cla.microsoft.com/)하여 커뮤니티에서 제출한 사항을 자유롭게 사용할 수 있도록 해야 합니다.
참가에 대한 자세한 내용은 [참가 가이드](CONTRIBUTING.md)를 참조하세요.
기여하기 전에 검토해야 할 [스타일 가이드](./STYLE.md) 초안이 있습니다.
설명서 버전 간에 일관성을 유지할 수 있도록 문제 및 끌어오기 요청 템플릿을 사용하세요. 
