---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetCollection 개체
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="7c175-103">ISESnippetCollection 개체</span><span class="sxs-lookup"><span data-stu-id="7c175-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="7c175-104">**ISESnippetCollection** 개체는 **ISESnippet** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="7c175-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="7c175-105">**PowerShellTab** 개체와 연결되어 있는 파일 컬렉션이 이 클래스의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="7c175-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="7c175-106">예제는 **$psISE.CurrentPowerShellTab.Files** 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="7c175-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="7c175-107">메서드</span><span class="sxs-lookup"><span data-stu-id="7c175-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="7c175-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="7c175-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="7c175-109">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c175-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7c175-110">사용자가 정의한 코드 조각을 포함하는 .snippets.ps1xml 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="7c175-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="7c175-111">코드 조각을 만드는 가장 쉬운 방법은 New-IseSnippet cmdlet을 사용하는 것입니다. 이 cmdlet은 Windows PowerShell ISE를 시작할 때마다 코드 조각이 로드되도록 코드 조각을 프로필 폴더에 자동으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7c175-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="7c175-112">**FilePathName** – 문자열. 코드 조각 정의를 포함하는 .snippets.ps1xml 파일의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7c175-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="7c175-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c175-113">See Also</span></span>

- [<span data-ttu-id="7c175-114">ISESnippet 개체</span><span class="sxs-lookup"><span data-stu-id="7c175-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="7c175-115">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="7c175-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7c175-116">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="7c175-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)