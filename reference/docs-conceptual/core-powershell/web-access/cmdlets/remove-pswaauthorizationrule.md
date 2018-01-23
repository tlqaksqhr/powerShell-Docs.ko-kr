---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="8cad6-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8cad6-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="8cad6-104">요약</span><span class="sxs-lookup"><span data-stu-id="8cad6-104">SYNOPSIS</span></span>

<span data-ttu-id="8cad6-105">지정된 권한 부여 규칙을 Windows PowerShell® 웹 액세스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="8cad6-106">구문</span><span class="sxs-lookup"><span data-stu-id="8cad6-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="8cad6-107">Id</span><span class="sxs-lookup"><span data-stu-id="8cad6-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="8cad6-108">규칙</span><span class="sxs-lookup"><span data-stu-id="8cad6-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="8cad6-109">설명</span><span class="sxs-lookup"><span data-stu-id="8cad6-109">DESCRIPTION</span></span>

<span data-ttu-id="8cad6-110">지정된 권한 부여 규칙을 Windows PowerShell 웹 액세스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="8cad6-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8cad6-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="8cad6-112">-Force</span><span class="sxs-lookup"><span data-stu-id="8cad6-112">-Force</span></span>

<span data-ttu-id="8cad6-113">확인 메시지를 표시하지 않고 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="8cad6-114">기본적으로 cmdlet에서는 계속 진행하기 전에 확인하는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="8cad6-115">별칭</span><span class="sxs-lookup"><span data-stu-id="8cad6-115">Aliases</span></span>                              | <span data-ttu-id="8cad6-116">없음</span><span class="sxs-lookup"><span data-stu-id="8cad6-116">none</span></span>                                 |
| <span data-ttu-id="8cad6-117">필수 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-117">Required?</span></span>                            | <span data-ttu-id="8cad6-118">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-118">false</span></span>                                |
| <span data-ttu-id="8cad6-119">위치</span><span class="sxs-lookup"><span data-stu-id="8cad6-119">Position?</span></span>                            | <span data-ttu-id="8cad6-120">명명됨</span><span class="sxs-lookup"><span data-stu-id="8cad6-120">named</span></span>                                |
| <span data-ttu-id="8cad6-121">기본값</span><span class="sxs-lookup"><span data-stu-id="8cad6-121">Default Value</span></span>                        | <span data-ttu-id="8cad6-122">없음</span><span class="sxs-lookup"><span data-stu-id="8cad6-122">none</span></span>                                 |
| <span data-ttu-id="8cad6-123">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8cad6-124">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-124">false</span></span>                                |
| <span data-ttu-id="8cad6-125">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8cad6-126">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="8cad6-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="8cad6-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="8cad6-128">제거할 규칙 하나 이상의 ID(식별자)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="8cad6-129">별칭</span><span class="sxs-lookup"><span data-stu-id="8cad6-129">Aliases</span></span>                              | <span data-ttu-id="8cad6-130">없음</span><span class="sxs-lookup"><span data-stu-id="8cad6-130">none</span></span>                                 |
| <span data-ttu-id="8cad6-131">필수 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-131">Required?</span></span>                            | <span data-ttu-id="8cad6-132">true</span><span class="sxs-lookup"><span data-stu-id="8cad6-132">true</span></span>                                 |
| <span data-ttu-id="8cad6-133">위치</span><span class="sxs-lookup"><span data-stu-id="8cad6-133">Position?</span></span>                            | <span data-ttu-id="8cad6-134">2</span><span class="sxs-lookup"><span data-stu-id="8cad6-134">2</span></span>                                    |
| <span data-ttu-id="8cad6-135">기본값</span><span class="sxs-lookup"><span data-stu-id="8cad6-135">Default Value</span></span>                        | <span data-ttu-id="8cad6-136">없음</span><span class="sxs-lookup"><span data-stu-id="8cad6-136">none</span></span>                                 |
| <span data-ttu-id="8cad6-137">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8cad6-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="8cad6-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="8cad6-139">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8cad6-140">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="8cad6-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="8cad6-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="8cad6-142">제거할 규칙을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="8cad6-143">별칭</span><span class="sxs-lookup"><span data-stu-id="8cad6-143">Aliases</span></span>                              | <span data-ttu-id="8cad6-144">없음</span><span class="sxs-lookup"><span data-stu-id="8cad6-144">none</span></span>                                 |
| <span data-ttu-id="8cad6-145">필수 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-145">Required?</span></span>                            | <span data-ttu-id="8cad6-146">true</span><span class="sxs-lookup"><span data-stu-id="8cad6-146">true</span></span>                                 |
| <span data-ttu-id="8cad6-147">위치</span><span class="sxs-lookup"><span data-stu-id="8cad6-147">Position?</span></span>                            | <span data-ttu-id="8cad6-148">2</span><span class="sxs-lookup"><span data-stu-id="8cad6-148">2</span></span>                                    |
| <span data-ttu-id="8cad6-149">기본값</span><span class="sxs-lookup"><span data-stu-id="8cad6-149">Default Value</span></span>                        | <span data-ttu-id="8cad6-150">없음</span><span class="sxs-lookup"><span data-stu-id="8cad6-150">none</span></span>                                 |
| <span data-ttu-id="8cad6-151">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8cad6-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="8cad6-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="8cad6-153">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8cad6-154">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="8cad6-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8cad6-155">-Confirm</span></span>

<span data-ttu-id="8cad6-156">cmdlet을 실행하기 전에 확인 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="8cad6-157">필수 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-157">Required?</span></span>                            | <span data-ttu-id="8cad6-158">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-158">false</span></span>                                |
| <span data-ttu-id="8cad6-159">위치</span><span class="sxs-lookup"><span data-stu-id="8cad6-159">Position?</span></span>                            | <span data-ttu-id="8cad6-160">명명됨</span><span class="sxs-lookup"><span data-stu-id="8cad6-160">named</span></span>                                |
| <span data-ttu-id="8cad6-161">기본값</span><span class="sxs-lookup"><span data-stu-id="8cad6-161">Default Value</span></span>                        | <span data-ttu-id="8cad6-162">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-162">false</span></span>                                |
| <span data-ttu-id="8cad6-163">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8cad6-164">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-164">false</span></span>                                |
| <span data-ttu-id="8cad6-165">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8cad6-166">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="8cad6-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8cad6-167">-WhatIf</span></span>

<span data-ttu-id="8cad6-168">cmdlet이 실행될 경우 결과 동작을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8cad6-169">cmdlet이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="8cad6-170">필수 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-170">Required?</span></span>                            | <span data-ttu-id="8cad6-171">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-171">false</span></span>                                |
| <span data-ttu-id="8cad6-172">위치</span><span class="sxs-lookup"><span data-stu-id="8cad6-172">Position?</span></span>                            | <span data-ttu-id="8cad6-173">명명됨</span><span class="sxs-lookup"><span data-stu-id="8cad6-173">named</span></span>                                |
| <span data-ttu-id="8cad6-174">기본값</span><span class="sxs-lookup"><span data-stu-id="8cad6-174">Default Value</span></span>                        | <span data-ttu-id="8cad6-175">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-175">false</span></span>                                |
| <span data-ttu-id="8cad6-176">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8cad6-177">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-177">false</span></span>                                |
| <span data-ttu-id="8cad6-178">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="8cad6-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8cad6-179">false</span><span class="sxs-lookup"><span data-stu-id="8cad6-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="8cad6-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="8cad6-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="8cad6-181">이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="8cad6-182">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8cad6-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="8cad6-183">입력</span><span class="sxs-lookup"><span data-stu-id="8cad6-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="8cad6-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="8cad6-184">int\[\]</span></span>

<span data-ttu-id="8cad6-185">이 cmdlet은 정수 배열 또는 PswaAuthorizationRule 개체의 배열을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="8cad6-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8cad6-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8cad6-187">이 cmdlet은 정수 배열 또는 PswaAuthorizationRule 개체의 배열을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="8cad6-188">출력</span><span class="sxs-lookup"><span data-stu-id="8cad6-188">OUTPUTS</span></span>

<span data-ttu-id="8cad6-189">이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="8cad6-190">예제</span><span class="sxs-lookup"><span data-stu-id="8cad6-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="8cad6-191">예제 1</span><span class="sxs-lookup"><span data-stu-id="8cad6-191">EXAMPLE 1</span></span>

<span data-ttu-id="8cad6-192">이 예제에서는 ID가 *2*인 권한 부여 규칙을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="8cad6-193">예제 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="8cad6-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="8cad6-194">이 예제에서는 권한 부여 규칙을 모두 제거하고 사용자의 확인도 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8cad6-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="8cad6-195">관련 항목</span><span class="sxs-lookup"><span data-stu-id="8cad6-195">Related topics</span></span>

- [<span data-ttu-id="8cad6-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8cad6-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="8cad6-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8cad6-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="8cad6-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8cad6-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="8cad6-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8cad6-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
