# <a name="contributing-to-powershell-documentation"></a>PowerShell 설명서에 참가

PowerShell 설명서에 관심을 가져 주셔서 감사합니다. 기술 설명서에 참가할 수 있는 방법에 대한 자세한 내용은 아래를 참조하세요.

>Git 및 GitHub를 시작하는 방법에 대한 일반적인 정보는 [GitHub Help](https://help.github.com/)(GitHub 도움말)를 참조하세요. 

## <a name="sign-a-cla"></a>CLA 서명

PowerShell 리포지토리에 참가하기 전에 [Microsoft CLA(참가 사용권 계약)에 서명](https://cla.microsoft.com/)해야 합니다. 이전에 이미 PowerShell 리포지토리에 참가한 경우 축하합니다. 이 단계를 이미 완료했습니다.

## <a name="providing-feedback-on-powershell-documentation"></a>PowerShell 설명서에 대한 피드백 제공

[PowerShell-Docs 리포지토리 문제 페이지](https://github.com/PowerShell/PowerShell-Docs/issues)에서 [문제를 생성하여](https://help.github.com/articles/creating-an-issue/) 오류를 지적하거나 변경 사항을 제안하거나 새로운 항목을 요청할 수 있습니다.

PowerShell 설명서 팀의 구성원들이 정기적으로 문제를 검토하여 적절하게 심사하고 할당하고 처리합니다.

## <a name="writing-powershell-documentation"></a>PowerShell 설명서 작성

PowerShell에 참가하는 가장 쉬운 방법은 설명서 작성과 편집을 돕는 것입니다. GitHub에 있는 모든 설명서는 [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/)을 사용하여 작성됩니다.

## <a name="making-minor-edits-to-existing-topics"></a>기존 항목을 약간 편집

[기존 파일을 편집](https://help.github.com/articles/editing-files-in-another-user-s-repository/)하려면 파일로 이동하고 "Edit(편집)" 단추를 클릭합니다. GitHub는 변경할 수 있는 리포지토리의 고유한 분기를 자동으로 만듭니다. 작업을 완료하면 편집 내용을 저장하고 [끌어오기 요청](https://help.github.com/articles/creating-a-pull-request/)을 [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 리포지토리의 *준비* 분기에 제출합니다. 끌어오기 요청을 만든 후 PowerShell 설명서 팀에서 변경 내용을 검토한 후 *준비* 분기로 병합합니다.

## <a name="making-major-edits-to-existing-topics"></a>기존 항목에 주요 편집 작업 수행

기존 문서를 많이 변경하거나, 이미지를 추가 또는 변경하거나, 새 문서에 참가하는 경우, GitHub 분기를 수동으로 만든 다음 로컬 컴퓨터에 해당 분기를 복제해야 합니다. 분기는 GitHub 계정에서 GitHub 기반의 기본 리포지토리 복제본으로, 격리 상태에서 사용할 수 있는 작업 복사본을 제공합니다. 사용자의 분기에서 끌어오기 요청을 만듭니다. 마찬가지로 복제는 로컬 기반의 리포지토리 복제본으로, 이 경우 분기의 복제본이 됩니다. 복제를 사용하면 Git 리포지토리에서 더 강력한 네이티브 소프트웨어/도구를 사용하여 오프라인으로 작업할 수 있습니다.

기존 설명서를 많이 편집하는 워크플로는 다음과 같습니다.

1. [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 리포지토리의 [분기를 만듭니다](https://help.github.com/articles/fork-a-repo/).
2. 로컬 컴퓨터에 [분기의 복제본을 만듭니다](https://help.github.com/articles/cloning-a-repository/).
3. 복제된 리포지토리에 새 로컬 분기를 만듭니다.
4. Markdown 편집기에서 업데이트하려는 파일을 변경합니다. 
   일반적으로 사용하는 Markdown 편집기에 대해서는 아래를 참조하세요.
5. [로컬 분기를](https://help.github.com/articles/pushing-to-a-remote/) 사용자의 분기로 푸시합니다.
6. [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 리포지토리의 *준비* 분기로 [끌어오기 요청을 만듭니다](https://help.github.com/articles/creating-a-pull-request/).

## <a name="creating-new-topics"></a>새 항목 만들기

새 설명서에 참가하려면 먼저 ["진행 중"으로 태그가 지정된 문제](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress)를 확인하여 중복 작업을 하지 않도록 합니다.
계획한 작업을 아무도 하고 있지 않은 경우:

* 새 문제를 열고 "진행 중"으로 레이블을 지정하거나(PowerShell 조직의 구성원인 경우) "진행 중"을 메모로 추가하여 작업하는 항목을 다른 사람들에게 알립니다.
* 기존 항목을 많이 편집하는 경우 위에 설명된 것과 같은 워크플로를 따릅니다.
* `TOC.md` 항목(각 설명서 집합의 최상위 폴더에 있음)을 편집하여 새 항목을 목차에 추가합니다. 
  새 항목이 목차에 속하는 위치를 결정하고 항목에 대한 링크와 함께 적절한 수준의 제목을 추가합니다(`[My topic title](relative path to my topic)`).

## <a name="markdown-editors"></a>Markdown 편집기

사용해 볼 수 있는 Markdown 편집기는 다음과 같습니다.

* [Visual Studio Code](https://code.visualstudio.com)
* [Markdown Pad](http://markdownpad.com/)
* [Atom](https://atom.io/)
* [Sublime Text](http://www.sublimetext.com/)


## <a name="github-flavored-markdown-gfm"></a>GFM(GitHub Flavored Markdown)

이 리포지토리의 모든 문서는 [GFM(GitHub Flavored Markdown)](https://help.github.com/articles/github-flavored-markdown/)을 사용합니다.

기본 GFM 구문 중 일부는 다음과 같습니다.

* **줄 바꿈 및 단락:** Markdown에는 HTML `<br />` 또는 `<p />` 요소가 없습니다. 대신 두 텍스트 블록 사이에 빈 줄로 새 단락이 지정됩니다.

> **참고**: 각 문장 뒤에 단일 줄 바꿈을 추가하여 차이점 및 기록에 대한 명령줄 출력을 간소화하세요.
현재 모든 PowerShell-Docs에서 채택되지는 않지만 앞으로 채택될 것입니다. 기꺼이 도와주세요. 

* **기울임꼴:** HTML `<em>some text</em>` 요소는 `*some text*`로 작성됩니다.
* **굵게:** HTML `<strong>some text</strong>` 요소는 `**some text**`로 작성됩니다.
* **제목:** HTML 제목은 줄 시작에 `#` 문자를 사용하여 지정됩니다. 
  `#` 문자 수가 제목의 계층 구조와 일치합니다(예: `#` = `<h1>` 및 `###` = ```<h3>```).
* **번호 매기기 목록:** 번호 매기기(순서가 지정된) 목록을 `1. `과 함께 줄을 시작하도록 합니다.  
  단일 목록 요소 내의 여러 요소를 원하는 경우 목록의 형식을 다음과 같이 지정합니다.
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
이 출력을 가져오려면 다음과 같이 합니다.

1.  (다음과 같은) 첫 번째 요소의 경우 1 뒤에 탭 정지를 삽입합니다. 

    (다음과 같은) 두 번째 요소를 포함하려면 첫 번째 요소 뒤에 줄 바꿈을 삽입하고 들여쓰기를 정렬합니다.

* **글머리 기호 목록:** 글머리 기호(순서가 지정되지 않은) 목록은 순서가 지정된 목록과 거의 같습니다. 단, `1. `이 `* `, `- ` 또는 `+ `로 대체됩니다. 여러 요소 목록은 순서가 지정된 목록과 같은 방식으로 작동합니다.
* **링크:** 하이퍼링크에 대한 구문은 `[visible link text](link URL)`입니다.
* **동일한 docset 내에서 다른 항목에 링크:** docset은 이 리포지토리에서 최상위 폴더입니다(예: "dsc", "scripting").
    동일한 docset 내에서 항목에 대한 하이퍼링크의 구문은 `[topic title](relative path to topic)`입니다. 
    자세한 내용은 [Relative links in READMEs](https://help.github.com/articles/relative-links-in-readmes/)(추가 정보의 상대 링크)를 참조하세요. 
    다른 최상위 폴더의 항목에 연결하려면 위에서 설명한 것처럼 게시된 페이지의 URL을 사용하세요.
