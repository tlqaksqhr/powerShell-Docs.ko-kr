---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: a8304b68a446de0be98aa732304c71302fb8389e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2017
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="2f5e0-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2f5e0-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="2f5e0-104">요약</span><span class="sxs-lookup"><span data-stu-id="2f5e0-104">SYNOPSIS</span></span>

<span data-ttu-id="2f5e0-105">지정된 권한 부여 규칙을 Windows PowerShell® 웹 액세스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f5e0-106">구문</span><span class="sxs-lookup"><span data-stu-id="2f5e0-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="2f5e0-107">Id</span><span class="sxs-lookup"><span data-stu-id="2f5e0-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="2f5e0-108">규칙</span><span class="sxs-lookup"><span data-stu-id="2f5e0-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="2f5e0-109">설명</span><span class="sxs-lookup"><span data-stu-id="2f5e0-109">DESCRIPTION</span></span>

<span data-ttu-id="2f5e0-110">지정된 권한 부여 규칙을 Windows PowerShell 웹 액세스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="2f5e0-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2f5e0-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="2f5e0-112">-Force</span><span class="sxs-lookup"><span data-stu-id="2f5e0-112">-Force</span></span>

<span data-ttu-id="2f5e0-113">확인 메시지를 표시하지 않고 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="2f5e0-114">기본적으로 cmdlet에서는 계속 진행하기 전에 확인하는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="2f5e0-115">별칭</span><span class="sxs-lookup"><span data-stu-id="2f5e0-115">Aliases</span></span>                              | <span data-ttu-id="2f5e0-116">없음</span><span class="sxs-lookup"><span data-stu-id="2f5e0-116">none</span></span>                                 |
| <span data-ttu-id="2f5e0-117">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-117">Required?</span></span>                            | <span data-ttu-id="2f5e0-118">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-118">false</span></span>                                |
| <span data-ttu-id="2f5e0-119">위치</span><span class="sxs-lookup"><span data-stu-id="2f5e0-119">Position?</span></span>                            | <span data-ttu-id="2f5e0-120">명명됨</span><span class="sxs-lookup"><span data-stu-id="2f5e0-120">named</span></span>                                |
| <span data-ttu-id="2f5e0-121">기본값</span><span class="sxs-lookup"><span data-stu-id="2f5e0-121">Default Value</span></span>                        | <span data-ttu-id="2f5e0-122">없음</span><span class="sxs-lookup"><span data-stu-id="2f5e0-122">none</span></span>                                 |
| <span data-ttu-id="2f5e0-123">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f5e0-124">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-124">false</span></span>                                |
| <span data-ttu-id="2f5e0-125">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f5e0-126">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="2f5e0-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2f5e0-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="2f5e0-128">제거할 규칙 하나 이상의 ID(식별자)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="2f5e0-129">별칭</span><span class="sxs-lookup"><span data-stu-id="2f5e0-129">Aliases</span></span>                              | <span data-ttu-id="2f5e0-130">없음</span><span class="sxs-lookup"><span data-stu-id="2f5e0-130">none</span></span>                                 |
| <span data-ttu-id="2f5e0-131">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-131">Required?</span></span>                            | <span data-ttu-id="2f5e0-132">true</span><span class="sxs-lookup"><span data-stu-id="2f5e0-132">true</span></span>                                 |
| <span data-ttu-id="2f5e0-133">위치</span><span class="sxs-lookup"><span data-stu-id="2f5e0-133">Position?</span></span>                            | <span data-ttu-id="2f5e0-134">2</span><span class="sxs-lookup"><span data-stu-id="2f5e0-134">2</span></span>                                    |
| <span data-ttu-id="2f5e0-135">기본값</span><span class="sxs-lookup"><span data-stu-id="2f5e0-135">Default Value</span></span>                        | <span data-ttu-id="2f5e0-136">없음</span><span class="sxs-lookup"><span data-stu-id="2f5e0-136">none</span></span>                                 |
| <span data-ttu-id="2f5e0-137">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f5e0-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2f5e0-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="2f5e0-139">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f5e0-140">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="2f5e0-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2f5e0-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="2f5e0-142">제거할 규칙을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="2f5e0-143">별칭</span><span class="sxs-lookup"><span data-stu-id="2f5e0-143">Aliases</span></span>                              | <span data-ttu-id="2f5e0-144">없음</span><span class="sxs-lookup"><span data-stu-id="2f5e0-144">none</span></span>                                 |
| <span data-ttu-id="2f5e0-145">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-145">Required?</span></span>                            | <span data-ttu-id="2f5e0-146">true</span><span class="sxs-lookup"><span data-stu-id="2f5e0-146">true</span></span>                                 |
| <span data-ttu-id="2f5e0-147">위치</span><span class="sxs-lookup"><span data-stu-id="2f5e0-147">Position?</span></span>                            | <span data-ttu-id="2f5e0-148">2</span><span class="sxs-lookup"><span data-stu-id="2f5e0-148">2</span></span>                                    |
| <span data-ttu-id="2f5e0-149">기본값</span><span class="sxs-lookup"><span data-stu-id="2f5e0-149">Default Value</span></span>                        | <span data-ttu-id="2f5e0-150">없음</span><span class="sxs-lookup"><span data-stu-id="2f5e0-150">none</span></span>                                 |
| <span data-ttu-id="2f5e0-151">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f5e0-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="2f5e0-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="2f5e0-153">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f5e0-154">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="2f5e0-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2f5e0-155">-Confirm</span></span>

<span data-ttu-id="2f5e0-156">cmdlet을 실행하기 전에 확인 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="2f5e0-157">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-157">Required?</span></span>                            | <span data-ttu-id="2f5e0-158">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-158">false</span></span>                                |
| <span data-ttu-id="2f5e0-159">위치</span><span class="sxs-lookup"><span data-stu-id="2f5e0-159">Position?</span></span>                            | <span data-ttu-id="2f5e0-160">명명됨</span><span class="sxs-lookup"><span data-stu-id="2f5e0-160">named</span></span>                                |
| <span data-ttu-id="2f5e0-161">기본값</span><span class="sxs-lookup"><span data-stu-id="2f5e0-161">Default Value</span></span>                        | <span data-ttu-id="2f5e0-162">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-162">false</span></span>                                |
| <span data-ttu-id="2f5e0-163">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f5e0-164">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-164">false</span></span>                                |
| <span data-ttu-id="2f5e0-165">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f5e0-166">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="2f5e0-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2f5e0-167">-WhatIf</span></span>

<span data-ttu-id="2f5e0-168">cmdlet이 실행될 경우 결과 동작을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2f5e0-169">cmdlet이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="2f5e0-170">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-170">Required?</span></span>                            | <span data-ttu-id="2f5e0-171">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-171">false</span></span>                                |
| <span data-ttu-id="2f5e0-172">위치</span><span class="sxs-lookup"><span data-stu-id="2f5e0-172">Position?</span></span>                            | <span data-ttu-id="2f5e0-173">명명됨</span><span class="sxs-lookup"><span data-stu-id="2f5e0-173">named</span></span>                                |
| <span data-ttu-id="2f5e0-174">기본값</span><span class="sxs-lookup"><span data-stu-id="2f5e0-174">Default Value</span></span>                        | <span data-ttu-id="2f5e0-175">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-175">false</span></span>                                |
| <span data-ttu-id="2f5e0-176">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f5e0-177">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-177">false</span></span>                                |
| <span data-ttu-id="2f5e0-178">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f5e0-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f5e0-179">false</span><span class="sxs-lookup"><span data-stu-id="2f5e0-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="2f5e0-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2f5e0-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="2f5e0-181">이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="2f5e0-182">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="2f5e0-183">입력</span><span class="sxs-lookup"><span data-stu-id="2f5e0-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="2f5e0-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="2f5e0-184">int\[\]</span></span>

<span data-ttu-id="2f5e0-185">이 cmdlet은 정수 배열 또는 PswaAuthorizationRule 개체의 배열을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="2f5e0-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="2f5e0-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="2f5e0-187">이 cmdlet은 정수 배열 또는 PswaAuthorizationRule 개체의 배열을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="2f5e0-188">출력</span><span class="sxs-lookup"><span data-stu-id="2f5e0-188">OUTPUTS</span></span>

<span data-ttu-id="2f5e0-189">이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="2f5e0-190">예제</span><span class="sxs-lookup"><span data-stu-id="2f5e0-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="2f5e0-191">예제 1</span><span class="sxs-lookup"><span data-stu-id="2f5e0-191">EXAMPLE 1</span></span>

<span data-ttu-id="2f5e0-192">이 예제에서는 ID가 *2*인 권한 부여 규칙을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="2f5e0-193">예제 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="2f5e0-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="2f5e0-194">이 예제에서는 권한 부여 규칙을 모두 제거하고 사용자의 확인도 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="2f5e0-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="2f5e0-195">관련 항목</span><span class="sxs-lookup"><span data-stu-id="2f5e0-195">Related topics</span></span>

- [<span data-ttu-id="2f5e0-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2f5e0-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="2f5e0-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2f5e0-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="2f5e0-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="2f5e0-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="2f5e0-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2f5e0-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
