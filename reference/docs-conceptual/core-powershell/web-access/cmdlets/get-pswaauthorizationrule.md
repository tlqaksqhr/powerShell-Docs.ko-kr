---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 43997320ec7ab779b2061a0af88f97db0b7e93d6
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2017
---
#  <a name="get-pswaauthorizationrule"></a><span data-ttu-id="ebefe-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ebefe-103">Get-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="ebefe-104">요약</span><span class="sxs-lookup"><span data-stu-id="ebefe-104">SYNOPSIS</span></span>

<span data-ttu-id="ebefe-105">일련의 Windows PowerShell® 웹 액세스 권한 부여 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

##  <a name="syntax"></a><span data-ttu-id="ebefe-106">구문</span><span class="sxs-lookup"><span data-stu-id="ebefe-106">Syntax</span></span>

###  <a name="id"></a><span data-ttu-id="ebefe-107">ID</span><span class="sxs-lookup"><span data-stu-id="ebefe-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

###  <a name="name"></a><span data-ttu-id="ebefe-108">이름</span><span class="sxs-lookup"><span data-stu-id="ebefe-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="ebefe-109">설명</span><span class="sxs-lookup"><span data-stu-id="ebefe-109">DESCRIPTION</span></span>

<span data-ttu-id="ebefe-110">**Get-PswaAuthorizationRule** cmdlet은 Windows PowerShell® 웹 액세스 권한 부여 규칙의 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="ebefe-111">**Id** 매개 변수나 **RuleName** 매개 변수 중 아무것도 지정하지 않으면 모든 규칙이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="ebefe-112">**Id** 매개 변수를 사용하여 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="ebefe-113">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ebefe-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="ebefe-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="ebefe-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="ebefe-115">이 cmdlet이 가져올 규칙의 ID(식별자)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="ebefe-116">ID를 지정하지 않으면 모든 권한 부여 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="ebefe-117">별칭</span><span class="sxs-lookup"><span data-stu-id="ebefe-117">Aliases</span></span>                              | <span data-ttu-id="ebefe-118">없음</span><span class="sxs-lookup"><span data-stu-id="ebefe-118">none</span></span>                                 |
| <span data-ttu-id="ebefe-119">필수 여부</span><span class="sxs-lookup"><span data-stu-id="ebefe-119">Required?</span></span>                            | <span data-ttu-id="ebefe-120">false</span><span class="sxs-lookup"><span data-stu-id="ebefe-120">false</span></span>                                |
| <span data-ttu-id="ebefe-121">위치</span><span class="sxs-lookup"><span data-stu-id="ebefe-121">Position?</span></span>                            | <span data-ttu-id="ebefe-122">2</span><span class="sxs-lookup"><span data-stu-id="ebefe-122">2</span></span>                                    |
| <span data-ttu-id="ebefe-123">기본값</span><span class="sxs-lookup"><span data-stu-id="ebefe-123">Default Value</span></span>                        | <span data-ttu-id="ebefe-124">없음</span><span class="sxs-lookup"><span data-stu-id="ebefe-124">none</span></span>                                 |
| <span data-ttu-id="ebefe-125">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="ebefe-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ebefe-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="ebefe-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="ebefe-127">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="ebefe-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ebefe-128">false</span><span class="sxs-lookup"><span data-stu-id="ebefe-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="ebefe-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="ebefe-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="ebefe-130">검색할 권한 부여 규칙의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="ebefe-131">이 매개 변수는 이 배열에 있는 문자열의 규칙 이름과 정확히 일치하는 모든 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="ebefe-132">별칭</span><span class="sxs-lookup"><span data-stu-id="ebefe-132">Aliases</span></span>                              | <span data-ttu-id="ebefe-133">없음</span><span class="sxs-lookup"><span data-stu-id="ebefe-133">none</span></span>                                 |
| <span data-ttu-id="ebefe-134">필수 여부</span><span class="sxs-lookup"><span data-stu-id="ebefe-134">Required?</span></span>                            | <span data-ttu-id="ebefe-135">true</span><span class="sxs-lookup"><span data-stu-id="ebefe-135">true</span></span>                                 |
| <span data-ttu-id="ebefe-136">위치</span><span class="sxs-lookup"><span data-stu-id="ebefe-136">Position?</span></span>                            | <span data-ttu-id="ebefe-137">2</span><span class="sxs-lookup"><span data-stu-id="ebefe-137">2</span></span>                                    |
| <span data-ttu-id="ebefe-138">기본값</span><span class="sxs-lookup"><span data-stu-id="ebefe-138">Default Value</span></span>                        | <span data-ttu-id="ebefe-139">없음</span><span class="sxs-lookup"><span data-stu-id="ebefe-139">none</span></span>                                 |
| <span data-ttu-id="ebefe-140">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="ebefe-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ebefe-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="ebefe-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="ebefe-142">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="ebefe-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ebefe-143">false</span><span class="sxs-lookup"><span data-stu-id="ebefe-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="ebefe-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ebefe-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="ebefe-145">이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="ebefe-146">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebefe-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="ebefe-147">입력</span><span class="sxs-lookup"><span data-stu-id="ebefe-147">INPUTS</span></span>

###  <a name="int"></a><span data-ttu-id="ebefe-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="ebefe-148">int\[\]</span></span>

<span data-ttu-id="ebefe-149">이 cmdlet은 정수 배열 또는 문자열 값 배열을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

###  <a name="string"></a><span data-ttu-id="ebefe-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="ebefe-150">String\[\]</span></span>

<span data-ttu-id="ebefe-151">이 cmdlet은 정수 배열 또는 문자열 값 배열을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="ebefe-152">출력</span><span class="sxs-lookup"><span data-stu-id="ebefe-152">OUTPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="ebefe-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="ebefe-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="ebefe-154">이 cmdlet은 PswaAuthorizationRule 개체를 출력으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="ebefe-155">예제</span><span class="sxs-lookup"><span data-stu-id="ebefe-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="ebefe-156">예제 1</span><span class="sxs-lookup"><span data-stu-id="ebefe-156">EXAMPLE 1</span></span>

<span data-ttu-id="ebefe-157">이 예제에서는 모든 규칙을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="ebefe-158">예제 2</span><span class="sxs-lookup"><span data-stu-id="ebefe-158">EXAMPLE 2</span></span>

<span data-ttu-id="ebefe-159">이 예제에서는 ID가 *2*인 규칙을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="ebefe-160">예제 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="ebefe-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="ebefe-161">이 예제에서는 cmdlet에서 파이프라인의 값을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="ebefe-162">이 cmdlet에서는 규칙 ID와 규칙 이름이 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebefe-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

##  <a name="related-topics"></a><span data-ttu-id="ebefe-163">관련 항목</span><span class="sxs-lookup"><span data-stu-id="ebefe-163">Related topics</span></span>

-  [<span data-ttu-id="ebefe-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ebefe-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="ebefe-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ebefe-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
-  [<span data-ttu-id="ebefe-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ebefe-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
-  [<span data-ttu-id="ebefe-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ebefe-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
