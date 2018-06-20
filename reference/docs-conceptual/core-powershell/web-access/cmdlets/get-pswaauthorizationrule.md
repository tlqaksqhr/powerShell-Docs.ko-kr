---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188911"
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="4afc0-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4afc0-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="4afc0-104">요약</span><span class="sxs-lookup"><span data-stu-id="4afc0-104">SYNOPSIS</span></span>

<span data-ttu-id="4afc0-105">일련의 Windows PowerShell® 웹 액세스 권한 부여 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="4afc0-106">구문</span><span class="sxs-lookup"><span data-stu-id="4afc0-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="4afc0-107">ID</span><span class="sxs-lookup"><span data-stu-id="4afc0-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="4afc0-108">이름</span><span class="sxs-lookup"><span data-stu-id="4afc0-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4afc0-109">설명</span><span class="sxs-lookup"><span data-stu-id="4afc0-109">DESCRIPTION</span></span>

<span data-ttu-id="4afc0-110">**Get-PswaAuthorizationRule** cmdlet은 Windows PowerShell® 웹 액세스 권한 부여 규칙의 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="4afc0-111">**Id** 매개 변수나 **RuleName** 매개 변수 중 아무것도 지정하지 않으면 모든 규칙이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="4afc0-112">**Id** 매개 변수를 사용하여 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="4afc0-113">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4afc0-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="4afc0-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4afc0-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="4afc0-115">이 cmdlet이 가져올 규칙의 ID(식별자)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="4afc0-116">ID를 지정하지 않으면 모든 권한 부여 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="4afc0-117">별칭</span><span class="sxs-lookup"><span data-stu-id="4afc0-117">Aliases</span></span>                              | <span data-ttu-id="4afc0-118">없음</span><span class="sxs-lookup"><span data-stu-id="4afc0-118">none</span></span>                                 |
| <span data-ttu-id="4afc0-119">필수 여부</span><span class="sxs-lookup"><span data-stu-id="4afc0-119">Required?</span></span>                            | <span data-ttu-id="4afc0-120">false</span><span class="sxs-lookup"><span data-stu-id="4afc0-120">false</span></span>                                |
| <span data-ttu-id="4afc0-121">위치</span><span class="sxs-lookup"><span data-stu-id="4afc0-121">Position?</span></span>                            | <span data-ttu-id="4afc0-122">2</span><span class="sxs-lookup"><span data-stu-id="4afc0-122">2</span></span>                                    |
| <span data-ttu-id="4afc0-123">기본값</span><span class="sxs-lookup"><span data-stu-id="4afc0-123">Default Value</span></span>                        | <span data-ttu-id="4afc0-124">없음</span><span class="sxs-lookup"><span data-stu-id="4afc0-124">none</span></span>                                 |
| <span data-ttu-id="4afc0-125">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="4afc0-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4afc0-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4afc0-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="4afc0-127">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="4afc0-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4afc0-128">false</span><span class="sxs-lookup"><span data-stu-id="4afc0-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="4afc0-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4afc0-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="4afc0-130">검색할 권한 부여 규칙의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="4afc0-131">이 매개 변수는 이 배열에 있는 문자열의 규칙 이름과 정확히 일치하는 모든 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="4afc0-132">별칭</span><span class="sxs-lookup"><span data-stu-id="4afc0-132">Aliases</span></span>                              | <span data-ttu-id="4afc0-133">없음</span><span class="sxs-lookup"><span data-stu-id="4afc0-133">none</span></span>                                 |
| <span data-ttu-id="4afc0-134">필수 여부</span><span class="sxs-lookup"><span data-stu-id="4afc0-134">Required?</span></span>                            | <span data-ttu-id="4afc0-135">true</span><span class="sxs-lookup"><span data-stu-id="4afc0-135">true</span></span>                                 |
| <span data-ttu-id="4afc0-136">위치</span><span class="sxs-lookup"><span data-stu-id="4afc0-136">Position?</span></span>                            | <span data-ttu-id="4afc0-137">2</span><span class="sxs-lookup"><span data-stu-id="4afc0-137">2</span></span>                                    |
| <span data-ttu-id="4afc0-138">기본값</span><span class="sxs-lookup"><span data-stu-id="4afc0-138">Default Value</span></span>                        | <span data-ttu-id="4afc0-139">없음</span><span class="sxs-lookup"><span data-stu-id="4afc0-139">none</span></span>                                 |
| <span data-ttu-id="4afc0-140">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="4afc0-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4afc0-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4afc0-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="4afc0-142">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="4afc0-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4afc0-143">false</span><span class="sxs-lookup"><span data-stu-id="4afc0-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="4afc0-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="4afc0-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="4afc0-145">이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4afc0-146">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4afc0-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="4afc0-147">입력</span><span class="sxs-lookup"><span data-stu-id="4afc0-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="4afc0-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="4afc0-148">int\[\]</span></span>

<span data-ttu-id="4afc0-149">이 cmdlet은 정수 배열 또는 문자열 값 배열을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="4afc0-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="4afc0-150">String\[\]</span></span>

<span data-ttu-id="4afc0-151">이 cmdlet은 정수 배열 또는 문자열 값 배열을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4afc0-152">출력</span><span class="sxs-lookup"><span data-stu-id="4afc0-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4afc0-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4afc0-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4afc0-154">이 cmdlet은 PswaAuthorizationRule 개체를 출력으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="4afc0-155">예제</span><span class="sxs-lookup"><span data-stu-id="4afc0-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4afc0-156">예제 1</span><span class="sxs-lookup"><span data-stu-id="4afc0-156">EXAMPLE 1</span></span>

<span data-ttu-id="4afc0-157">이 예제에서는 모든 규칙을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="4afc0-158">예제 2</span><span class="sxs-lookup"><span data-stu-id="4afc0-158">EXAMPLE 2</span></span>

<span data-ttu-id="4afc0-159">이 예제에서는 ID가 *2*인 규칙을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="4afc0-160">예제 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="4afc0-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="4afc0-161">이 예제에서는 cmdlet에서 파이프라인의 값을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="4afc0-162">이 cmdlet에서는 규칙 ID와 규칙 이름이 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="4afc0-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="4afc0-163">관련 항목</span><span class="sxs-lookup"><span data-stu-id="4afc0-163">Related topics</span></span>

- [<span data-ttu-id="4afc0-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4afc0-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="4afc0-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4afc0-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="4afc0-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4afc0-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="4afc0-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4afc0-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)