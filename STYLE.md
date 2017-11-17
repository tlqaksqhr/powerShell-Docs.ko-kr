# <a name="style-guide-for-powershell-docs"></a><span data-ttu-id="36b4d-101">PowerShell 스타일 가이드-문서</span><span class="sxs-lookup"><span data-stu-id="36b4d-101">Style guide for PowerShell-Docs</span></span>


## <a name="titlesheadings"></a><span data-ttu-id="36b4d-102">제목/머리글</span><span class="sxs-lookup"><span data-stu-id="36b4d-102">Titles/Headings</span></span>

* <span data-ttu-id="36b4d-103">제목/머리글(앞에 \#이 추가된 모든 것) 뒤에는 줄 바꿈이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36b4d-103">Titles/headings (anything preprended by \#) should be followed with a newline</span></span>
* <span data-ttu-id="36b4d-104">제목과 그 제목에 있는 고유 명사는 첫 번째 글자만 대문자로 표기합니다.</span><span class="sxs-lookup"><span data-stu-id="36b4d-104">Only the first letter of a title and any proper nouns in that title should be capitalized</span></span>
* <span data-ttu-id="36b4d-105">H1은 문서당 하나만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36b4d-105">Only 1 H1 per document</span></span>
* <span data-ttu-id="36b4d-106">참조 콘텐츠를 편집할 때는 H2를 platyPS로 규정해야 하며, 빌드 중단이 되지 않도록 추가 또는 제거를 피해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36b4d-106">When editing reference content, the H2s are prescribed by platyPS and should not be added or removed as it will cause a build break</span></span>
* <span data-ttu-id="36b4d-107">\# 스타일 헤더만 사용합니다(= 또는 \- 스타일 헤더 금지).</span><span class="sxs-lookup"><span data-stu-id="36b4d-107">Only use \# style headers (as opposed to = or \- style headers)</span></span>

### <a name="correct"></a><span data-ttu-id="36b4d-108">맞음</span><span class="sxs-lookup"><span data-stu-id="36b4d-108">Correct</span></span>

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a><span data-ttu-id="36b4d-109">틀림</span><span class="sxs-lookup"><span data-stu-id="36b4d-109">Incorrect</span></span>

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a><span data-ttu-id="36b4d-110">구문</span><span class="sxs-lookup"><span data-stu-id="36b4d-110">Syntax</span></span>

* <span data-ttu-id="36b4d-111">단락에 있는 cmdlet에 대해 말할 때 \\`를 사용하여 cmdlet 이름을 강조 표시</span><span class="sxs-lookup"><span data-stu-id="36b4d-111">When talking about a cmdlet in paragraph, use \\` to highlight cmdlet names</span></span>
  * <span data-ttu-id="36b4d-112">올바른 예제: 이 `Write-Host` cmdlet은...</span><span class="sxs-lookup"><span data-stu-id="36b4d-112">Correct Example: This `Write-Host` Cmdlet can ...</span></span>
  * <span data-ttu-id="36b4d-113">잘못된 예제: 이 **Write-Host** cmdlet은 ... 작업을 수행할 수 있으며 out-file cmdlet에 파이프라인하여...</span><span class="sxs-lookup"><span data-stu-id="36b4d-113">Incorrect Example: This **Write-Host** Cmdlet can ... and pipeline to out-file Cmdlet to ...</span></span>
* <span data-ttu-id="36b4d-114">참조 콘텐츠가 아닌 기사를 작성할 때, 처음으로 나오는 cmdlet 이름 인스턴스는 cmdlet 문서의 링크여야 함</span><span class="sxs-lookup"><span data-stu-id="36b4d-114">When writing an article (as opposed to reference content), the first instance of a cmdlet name should be a link to the cmdlet documentation</span></span>
* <span data-ttu-id="36b4d-115">모든 PowerShell 구문 블록에 &#96;&#96;&#96;powershell을 사용</span><span class="sxs-lookup"><span data-stu-id="36b4d-115">All PowerShell syntax blocks should use &#96;&#96;&#96;powershell</span></span>
* <span data-ttu-id="36b4d-116">PowerShell 명령은 "`PS C:\>`"로 시작 금지</span><span class="sxs-lookup"><span data-stu-id="36b4d-116">Do not start PowerShell commands with "`PS C:\>`"</span></span>
  * <span data-ttu-id="36b4d-117">올바른 예제:</span><span class="sxs-lookup"><span data-stu-id="36b4d-117">Correct Example:</span></span>
  ```powershell
  Get-Process
  ```
  * <span data-ttu-id="36b4d-118">잘못된 예제:</span><span class="sxs-lookup"><span data-stu-id="36b4d-118">Incorrect Example:</span></span>
  ```powershell
  PS C:\> Get-Process
  ```
* <span data-ttu-id="36b4d-119">PowerShell 명령을 사용하여 내보낸 출력은 구문 강조를 받지 않도록 주석 처리</span><span class="sxs-lookup"><span data-stu-id="36b4d-119">Output emitted by PowerShell commands should be commented to prevent it from recieving syntax highlighting</span></span>
* <span data-ttu-id="36b4d-120">속성 이름 및 매개 변수 이름은 **굵게** 표시</span><span class="sxs-lookup"><span data-stu-id="36b4d-120">Property names and parameter names should be in **bold**</span></span>
* <span data-ttu-id="36b4d-121">PowerShell cmdlet은 "[파스칼식 대/소문자로 지정](https://en.wikipedia.org/wiki/PascalCase)"됩니다.</span><span class="sxs-lookup"><span data-stu-id="36b4d-121">PowerShell cmdlets are "[Pascal Cased](https://en.wikipedia.org/wiki/PascalCase)".</span></span> <span data-ttu-id="36b4d-122">동사와 명사는 하이픈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="36b4d-122">Verbs are seperated from nouns by a hyphen.</span></span>

## <a name="lists"></a><span data-ttu-id="36b4d-123">목록</span><span class="sxs-lookup"><span data-stu-id="36b4d-123">Lists</span></span>

* <span data-ttu-id="36b4d-124">목록 항목의 끝에 마침표를 사용하지 않음 (여러 문장이 있는 경우만 허용)</span><span class="sxs-lookup"><span data-stu-id="36b4d-124">Do not end list items with a period (unless they contain multiple sentences)</span></span>
* <span data-ttu-id="36b4d-125">목록에 여러 문장이 있을 경우 기본 아이디어 아래에 헤더 3/4/5를 적절하게 사용할 것을 고려</span><span class="sxs-lookup"><span data-stu-id="36b4d-125">If your list contains multiple sentences, consider using a header 3/4/5 (as applicable) underneath your primary idea</span></span>

## <a name="links"></a><span data-ttu-id="36b4d-126">링크</span><span class="sxs-lookup"><span data-stu-id="36b4d-126">Links</span></span>

* <span data-ttu-id="36b4d-127">링크는 항상 MarkDown 구문 `[friendlyname](url)`을 사용하여 마크업</span><span class="sxs-lookup"><span data-stu-id="36b4d-127">Links are always marked up using MarkDown syntax `[friendlyname](url)`</span></span>
* <span data-ttu-id="36b4d-128">링크에는 가능한 한 친숙한 이름 사용(대개는 링크된 페이지의 제목)</span><span class="sxs-lookup"><span data-stu-id="36b4d-128">Links should have a a friendly name when applicable, most likely the title of the linked page</span></span>
  * <span data-ttu-id="36b4d-129">**예외**: Microsoft 이외 사이트로 이동하는 링크는 URL만 사용</span><span class="sxs-lookup"><span data-stu-id="36b4d-129">**Exception**: Links going towards non-Microsoft sites should only have a URL</span></span>
* <span data-ttu-id="36b4d-130">맨 아래의 "관련 링크" 섹션에 있는 항목은 모두 하이퍼링크로 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36b4d-130">All items in the "related links" section at the bottom should be hyperlinked.</span></span> 

## <a name="line-breaks"></a><span data-ttu-id="36b4d-131">줄 바꿈</span><span class="sxs-lookup"><span data-stu-id="36b4d-131">Line breaks</span></span>

* <span data-ttu-id="36b4d-132">유의적 줄 바꿈을 반드시 포함</span><span class="sxs-lookup"><span data-stu-id="36b4d-132">You must include semantic line breaks</span></span>
* <span data-ttu-id="36b4d-133">한 줄은 100자로 제한(항목 열기: 확인에 도움이 되는 도구 사용)</span><span class="sxs-lookup"><span data-stu-id="36b4d-133">You should limit lines to 100char (Open item: tooling to help us validate this)</span></span>
* <span data-ttu-id="36b4d-134">PS4+에서는 추가 줄 바꿈을 제거할 수 있으나 ps3에서는 불가(유효성 검사 필요)</span><span class="sxs-lookup"><span data-stu-id="36b4d-134">You CAN remove additional line breaks for PS4+, NOT ps3 (needs validation)</span></span>
