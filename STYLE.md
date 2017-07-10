<a id="style-guide-for-powershell-docs" class="xliff"></a>
# PowerShell 스타일 가이드-문서


<a id="titlesheadings" class="xliff"></a>
## 제목/머리글

* 제목/머리글(앞에 \#이 추가된 모든 것) 뒤에는 줄 바꿈이 있어야 합니다.
* 제목과 그 제목에 있는 고유 명사는 첫 번째 글자만 대문자로 표기합니다.
* H1은 문서당 하나만 사용합니다.
* 참조 콘텐츠를 편집할 때는 H2를 platyPS로 규정해야 하며, 빌드 중단이 되지 않도록 추가 또는 제거를 피해야 합니다.
* \# 스타일 헤더만 사용합니다(= 또는 \- 스타일 헤더 금지).

<a id="correct" class="xliff"></a>
### 맞음

```
# Header 1

## Header 2

### Header 3

```

<a id="incorrect" class="xliff"></a>
### 틀림

```
Header 1
========

Header 2
--------

### Header 3
```

<a id="syntax" class="xliff"></a>
## 구문

* 단락에 있는 cmdlet에 대해 말할 때 \`를 사용하여 cmdlet 이름을 강조 표시
  * 올바른 예제: 이 `Write-Host` cmdlet은...
  * 잘못된 예제: 이 **Write-Host** cmdlet은 ... 작업을 수행할 수 있으며 out-file cmdlet에 파이프라인하여...
* 참조 콘텐츠가 아닌 기사를 작성할 때, 처음으로 나오는 cmdlet 이름 인스턴스는 cmdlet 문서의 링크여야 함
* 모든 PowerShell 구문 블록에 &#96;&#96;&#96;powershell을 사용
* PowerShell 명령은 "`PS C:\>`"로 시작 금지
  * 올바른 예제:
  ```powershell
  Get-Process
  ```
  * 잘못된 예제:
  ```powershell
  PS C:\> Get-Process
  ```
* PowerShell 명령을 사용하여 내보낸 출력은 구문 강조를 받지 않도록 주석 처리
* 속성 이름 및 매개 변수 이름은 **굵게** 표시
* PowerShell cmdlet은 "[파스칼식 대/소문자로 지정](https://en.wikipedia.org/wiki/PascalCase)"됩니다. 동사와 명사는 하이픈으로 구분됩니다.

<a id="lists" class="xliff"></a>
## 목록

* 목록 항목의 끝에 마침표를 사용하지 않음 (여러 문장이 있는 경우만 허용)
* 목록에 여러 문장이 있을 경우 기본 아이디어 아래에 헤더 3/4/5를 적절하게 사용할 것을 고려

<a id="links" class="xliff"></a>
## 링크

* 링크는 항상 MarkDown 구문 `[friendlyname](url)`을 사용하여 마크업
* 링크에는 가능한 한 친숙한 이름 사용(대개는 링크된 페이지의 제목)
  * **예외**: Microsoft 이외 사이트로 이동하는 링크는 URL만 사용
* 맨 아래의 "관련 링크" 섹션에 있는 항목은 모두 하이퍼링크로 처리해야 합니다. 

<a id="line-breaks" class="xliff"></a>
## 줄 바꿈

* 유의적 줄 바꿈을 반드시 포함
* 한 줄은 100자로 제한(항목 열기: 확인에 도움이 되는 도구 사용)
* PS4+에서는 추가 줄 바꿈을 제거할 수 있으나 ps3에서는 불가(유효성 검사 필요)
