---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Test-PswaAuthorizationRule
ms.openlocfilehash: 08248e65be229f9d0f4d606d6c0d039d86ced054
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="2f49b-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2f49b-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="2f49b-104">요약</span><span class="sxs-lookup"><span data-stu-id="2f49b-104">SYNOPSIS</span></span>

<span data-ttu-id="2f49b-105">지정된 사용자, 컴퓨터 또는 끝점에 대한 규칙이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f49b-106">구문</span><span class="sxs-lookup"><span data-stu-id="2f49b-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="2f49b-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="2f49b-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="2f49b-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="2f49b-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="2f49b-109">설명</span><span class="sxs-lookup"><span data-stu-id="2f49b-109">DESCRIPTION</span></span>

<span data-ttu-id="2f49b-110">**Test-pswaauthorizationrule** cmdlet은 지정된 사용자, 컴퓨터 또는 끝점에 대한 규칙이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="2f49b-111">권한 부여 규칙을 테스트하여 특정 사용자, 컴퓨터, 끝점 액세스 요청이 인증되었는지 확인하는 데에 이 cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="2f49b-112">기본적으로 이 cmdlet은 권한 부여 파일의 규칙을 모두 평가하지만,</span><span class="sxs-lookup"><span data-stu-id="2f49b-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="2f49b-113">규칙의 하위 집합을 지정하여 테스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="2f49b-114">이 cmdlet을 사용하여 인증 오류 문제를 해결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="2f49b-115">이 cmdlet의 매개 변수는 Windows PowerShell® 웹 액세스 로그온 페이지의 필드에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="2f49b-116">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2f49b-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="2f49b-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2f49b-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="2f49b-118">테스트할 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="2f49b-119">별칭</span><span class="sxs-lookup"><span data-stu-id="2f49b-119">Aliases</span></span>                              | <span data-ttu-id="2f49b-120">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-120">none</span></span>                                 |
| <span data-ttu-id="2f49b-121">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-121">Required?</span></span>                            | <span data-ttu-id="2f49b-122">true</span><span class="sxs-lookup"><span data-stu-id="2f49b-122">true</span></span>                                 |
| <span data-ttu-id="2f49b-123">위치</span><span class="sxs-lookup"><span data-stu-id="2f49b-123">Position?</span></span>                            | <span data-ttu-id="2f49b-124">2</span><span class="sxs-lookup"><span data-stu-id="2f49b-124">2</span></span>                                    |
| <span data-ttu-id="2f49b-125">기본값</span><span class="sxs-lookup"><span data-stu-id="2f49b-125">Default Value</span></span>                        | <span data-ttu-id="2f49b-126">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-126">none</span></span>                                 |
| <span data-ttu-id="2f49b-127">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f49b-128">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-128">false</span></span>                                |
| <span data-ttu-id="2f49b-129">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f49b-130">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="2f49b-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2f49b-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="2f49b-132">테스트할 Windows PowerShell 세션 구성(끝점 또는 runspace라고도 함)의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="2f49b-133">별칭</span><span class="sxs-lookup"><span data-stu-id="2f49b-133">Aliases</span></span>                              | <span data-ttu-id="2f49b-134">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-134">none</span></span>                                 |
| <span data-ttu-id="2f49b-135">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-135">Required?</span></span>                            | <span data-ttu-id="2f49b-136">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-136">false</span></span>                                |
| <span data-ttu-id="2f49b-137">위치</span><span class="sxs-lookup"><span data-stu-id="2f49b-137">Position?</span></span>                            | <span data-ttu-id="2f49b-138">3</span><span class="sxs-lookup"><span data-stu-id="2f49b-138">3</span></span>                                    |
| <span data-ttu-id="2f49b-139">기본값</span><span class="sxs-lookup"><span data-stu-id="2f49b-139">Default Value</span></span>                        | <span data-ttu-id="2f49b-140">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-140">none</span></span>                                 |
| <span data-ttu-id="2f49b-141">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f49b-142">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-142">false</span></span>                                |
| <span data-ttu-id="2f49b-143">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f49b-144">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="2f49b-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="2f49b-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="2f49b-146">테스트할 연결 URI를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="2f49b-147">별칭</span><span class="sxs-lookup"><span data-stu-id="2f49b-147">Aliases</span></span>                              | <span data-ttu-id="2f49b-148">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-148">none</span></span>                                 |
| <span data-ttu-id="2f49b-149">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-149">Required?</span></span>                            | <span data-ttu-id="2f49b-150">true</span><span class="sxs-lookup"><span data-stu-id="2f49b-150">true</span></span>                                 |
| <span data-ttu-id="2f49b-151">위치</span><span class="sxs-lookup"><span data-stu-id="2f49b-151">Position?</span></span>                            | <span data-ttu-id="2f49b-152">2</span><span class="sxs-lookup"><span data-stu-id="2f49b-152">2</span></span>                                    |
| <span data-ttu-id="2f49b-153">기본값</span><span class="sxs-lookup"><span data-stu-id="2f49b-153">Default Value</span></span>                        | <span data-ttu-id="2f49b-154">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-154">none</span></span>                                 |
| <span data-ttu-id="2f49b-155">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f49b-156">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-156">false</span></span>                                |
| <span data-ttu-id="2f49b-157">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f49b-158">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="2f49b-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="2f49b-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="2f49b-160">Windows PowerShell 웹 액세스 권한 부여 규칙을 테스트하는 데 사용할 사용자 계정에 대한 **PSCredential** 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="2f49b-161">이 매개 변수를 추가하지 않으면 현재 로그온한 사용자 계정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="2f49b-162">권한 부여 규칙을 원격으로 테스트하는 데 필요한 **PSCredential**을 가져오려면 [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="2f49b-163">별칭</span><span class="sxs-lookup"><span data-stu-id="2f49b-163">Aliases</span></span>                              | <span data-ttu-id="2f49b-164">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-164">none</span></span>                                 |
| <span data-ttu-id="2f49b-165">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-165">Required?</span></span>                            | <span data-ttu-id="2f49b-166">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-166">false</span></span>                                |
| <span data-ttu-id="2f49b-167">위치</span><span class="sxs-lookup"><span data-stu-id="2f49b-167">Position?</span></span>                            | <span data-ttu-id="2f49b-168">명명됨</span><span class="sxs-lookup"><span data-stu-id="2f49b-168">named</span></span>                                |
| <span data-ttu-id="2f49b-169">기본값</span><span class="sxs-lookup"><span data-stu-id="2f49b-169">Default Value</span></span>                        | <span data-ttu-id="2f49b-170">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-170">none</span></span>                                 |
| <span data-ttu-id="2f49b-171">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f49b-172">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-172">false</span></span>                                |
| <span data-ttu-id="2f49b-173">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f49b-174">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="2f49b-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2f49b-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="2f49b-176">테스트할 규칙의 하위 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="2f49b-177">이 매개 변수를 지정하지 않으면 이 cmdlet은 모든 권한 부여 규칙을 기준으로 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="2f49b-178">별칭</span><span class="sxs-lookup"><span data-stu-id="2f49b-178">Aliases</span></span>                              | <span data-ttu-id="2f49b-179">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-179">none</span></span>                                 |
| <span data-ttu-id="2f49b-180">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-180">Required?</span></span>                            | <span data-ttu-id="2f49b-181">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-181">false</span></span>                                |
| <span data-ttu-id="2f49b-182">위치</span><span class="sxs-lookup"><span data-stu-id="2f49b-182">Position?</span></span>                            | <span data-ttu-id="2f49b-183">명명됨</span><span class="sxs-lookup"><span data-stu-id="2f49b-183">named</span></span>                                |
| <span data-ttu-id="2f49b-184">기본값</span><span class="sxs-lookup"><span data-stu-id="2f49b-184">Default Value</span></span>                        | <span data-ttu-id="2f49b-185">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-185">none</span></span>                                 |
| <span data-ttu-id="2f49b-186">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f49b-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="2f49b-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="2f49b-188">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f49b-189">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="2f49b-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2f49b-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="2f49b-191">테스트할 사용자의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="2f49b-192">별칭</span><span class="sxs-lookup"><span data-stu-id="2f49b-192">Aliases</span></span>                              | <span data-ttu-id="2f49b-193">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-193">none</span></span>                                 |
| <span data-ttu-id="2f49b-194">필수 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-194">Required?</span></span>                            | <span data-ttu-id="2f49b-195">true</span><span class="sxs-lookup"><span data-stu-id="2f49b-195">true</span></span>                                 |
| <span data-ttu-id="2f49b-196">위치</span><span class="sxs-lookup"><span data-stu-id="2f49b-196">Position?</span></span>                            | <span data-ttu-id="2f49b-197">1</span><span class="sxs-lookup"><span data-stu-id="2f49b-197">1</span></span>                                    |
| <span data-ttu-id="2f49b-198">기본값</span><span class="sxs-lookup"><span data-stu-id="2f49b-198">Default Value</span></span>                        | <span data-ttu-id="2f49b-199">없음</span><span class="sxs-lookup"><span data-stu-id="2f49b-199">none</span></span>                                 |
| <span data-ttu-id="2f49b-200">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2f49b-201">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-201">false</span></span>                                |
| <span data-ttu-id="2f49b-202">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="2f49b-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2f49b-203">false</span><span class="sxs-lookup"><span data-stu-id="2f49b-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="2f49b-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2f49b-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="2f49b-205">이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="2f49b-206">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f49b-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="2f49b-207">입력</span><span class="sxs-lookup"><span data-stu-id="2f49b-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="2f49b-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="2f49b-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="2f49b-209">이 cmdlet은 PswaAuthorizationRule 개체 배열을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="2f49b-210">출력</span><span class="sxs-lookup"><span data-stu-id="2f49b-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="2f49b-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="2f49b-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="2f49b-212">이 cmdlet은 PswaAuthorizationRule 개체의 배열을 출력으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="2f49b-213">예제</span><span class="sxs-lookup"><span data-stu-id="2f49b-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="2f49b-214">예제 1</span><span class="sxs-lookup"><span data-stu-id="2f49b-214">EXAMPLE 1</span></span>

<span data-ttu-id="2f49b-215">이 예제에서는 *contoso\\mhanson* 사용자가 *srv2* 컴퓨터에 연결하고 *test*라는 Windows PowerShell 세션 구성을 사용할 수 있도록 허용하는 모든 규칙을 표시하기 위해 모든 권한 부여 규칙을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="2f49b-216">예제 2</span><span class="sxs-lookup"><span data-stu-id="2f49b-216">EXAMPLE 2</span></span>

<span data-ttu-id="2f49b-217">이 예제에서는 *contoso\\mhanson* 사용자에 적용되는 권한 부여 규칙을 확인하기 위해 모든 권한 부여 규칙을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="2f49b-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="2f49b-218">관련 항목</span><span class="sxs-lookup"><span data-stu-id="2f49b-218">Related topics</span></span>

- [<span data-ttu-id="2f49b-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2f49b-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="2f49b-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2f49b-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="2f49b-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="2f49b-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="2f49b-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2f49b-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)