---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Uninstall-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221921"
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="37cf1-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="37cf1-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="37cf1-104">요약</span><span class="sxs-lookup"><span data-stu-id="37cf1-104">SYNOPSIS</span></span>

<span data-ttu-id="37cf1-105">Windows PowerShell® 웹 응용 프로그램을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="37cf1-106">구문</span><span class="sxs-lookup"><span data-stu-id="37cf1-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="37cf1-107">Default</span><span class="sxs-lookup"><span data-stu-id="37cf1-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="37cf1-108">설명</span><span class="sxs-lookup"><span data-stu-id="37cf1-108">DESCRIPTION</span></span>

<span data-ttu-id="37cf1-109">**Uninstall-PswaWebApplication** cmdlet은 Windows PowerShell 웹 응용 프로그램을 제거하고 IIS에서 해당 웹 사이트를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="37cf1-110">이 cmdlet은 IIS나 Windows PowerShell 실행에 필요한 다른 설치된 기능은 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="37cf1-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="37cf1-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="37cf1-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="37cf1-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="37cf1-113">**Install\_PswaWebApplication** cmdlet(**UseTestCertificate** 매개 변수 사용)으로 만든 테스트 인증서를 삭제하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="37cf1-114">**Install-PswaWebApplication** cmdlet으로 만든 인증서와 이름이 같은 테스트 인증서만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="37cf1-115">별칭</span><span class="sxs-lookup"><span data-stu-id="37cf1-115">Aliases</span></span>                              | <span data-ttu-id="37cf1-116">없음</span><span class="sxs-lookup"><span data-stu-id="37cf1-116">none</span></span>                                 |
| <span data-ttu-id="37cf1-117">필수 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-117">Required?</span></span>                            | <span data-ttu-id="37cf1-118">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-118">false</span></span>                                |
| <span data-ttu-id="37cf1-119">위치</span><span class="sxs-lookup"><span data-stu-id="37cf1-119">Position?</span></span>                            | <span data-ttu-id="37cf1-120">명명됨</span><span class="sxs-lookup"><span data-stu-id="37cf1-120">named</span></span>                                |
| <span data-ttu-id="37cf1-121">기본값</span><span class="sxs-lookup"><span data-stu-id="37cf1-121">Default Value</span></span>                        | <span data-ttu-id="37cf1-122">true</span><span class="sxs-lookup"><span data-stu-id="37cf1-122">true</span></span>                                 |
| <span data-ttu-id="37cf1-123">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="37cf1-124">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-124">false</span></span>                                |
| <span data-ttu-id="37cf1-125">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="37cf1-126">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="37cf1-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="37cf1-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="37cf1-128">제거할 웹 응용 프로그램의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="37cf1-129">별칭</span><span class="sxs-lookup"><span data-stu-id="37cf1-129">Aliases</span></span>                              | <span data-ttu-id="37cf1-130">없음</span><span class="sxs-lookup"><span data-stu-id="37cf1-130">none</span></span>                                 |
| <span data-ttu-id="37cf1-131">필수 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-131">Required?</span></span>                            | <span data-ttu-id="37cf1-132">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-132">false</span></span>                                |
| <span data-ttu-id="37cf1-133">위치</span><span class="sxs-lookup"><span data-stu-id="37cf1-133">Position?</span></span>                            | <span data-ttu-id="37cf1-134">1</span><span class="sxs-lookup"><span data-stu-id="37cf1-134">1</span></span>                                    |
| <span data-ttu-id="37cf1-135">기본값</span><span class="sxs-lookup"><span data-stu-id="37cf1-135">Default Value</span></span>                        | <span data-ttu-id="37cf1-136">pswa</span><span class="sxs-lookup"><span data-stu-id="37cf1-136">pswa</span></span>                                 |
| <span data-ttu-id="37cf1-137">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="37cf1-138">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-138">false</span></span>                                |
| <span data-ttu-id="37cf1-139">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="37cf1-140">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="37cf1-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="37cf1-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="37cf1-142">웹 응용 프로그램이 설치되어 있는 웹 사이트의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="37cf1-143">별칭</span><span class="sxs-lookup"><span data-stu-id="37cf1-143">Aliases</span></span>                              | <span data-ttu-id="37cf1-144">없음</span><span class="sxs-lookup"><span data-stu-id="37cf1-144">none</span></span>                                 |
| <span data-ttu-id="37cf1-145">필수 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-145">Required?</span></span>                            | <span data-ttu-id="37cf1-146">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-146">false</span></span>                                |
| <span data-ttu-id="37cf1-147">위치</span><span class="sxs-lookup"><span data-stu-id="37cf1-147">Position?</span></span>                            | <span data-ttu-id="37cf1-148">명명됨</span><span class="sxs-lookup"><span data-stu-id="37cf1-148">named</span></span>                                |
| <span data-ttu-id="37cf1-149">기본값</span><span class="sxs-lookup"><span data-stu-id="37cf1-149">Default Value</span></span>                        | <span data-ttu-id="37cf1-150">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="37cf1-150">Default Web Site</span></span>                     |
| <span data-ttu-id="37cf1-151">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="37cf1-152">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-152">false</span></span>                                |
| <span data-ttu-id="37cf1-153">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="37cf1-154">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="37cf1-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="37cf1-155">-Confirm</span></span>

<span data-ttu-id="37cf1-156">cmdlet을 실행하기 전에 확인 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="37cf1-157">필수 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-157">Required?</span></span>                            | <span data-ttu-id="37cf1-158">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-158">false</span></span>                                |
| <span data-ttu-id="37cf1-159">위치</span><span class="sxs-lookup"><span data-stu-id="37cf1-159">Position?</span></span>                            | <span data-ttu-id="37cf1-160">명명됨</span><span class="sxs-lookup"><span data-stu-id="37cf1-160">named</span></span>                                |
| <span data-ttu-id="37cf1-161">기본값</span><span class="sxs-lookup"><span data-stu-id="37cf1-161">Default Value</span></span>                        | <span data-ttu-id="37cf1-162">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-162">false</span></span>                                |
| <span data-ttu-id="37cf1-163">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="37cf1-164">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-164">false</span></span>                                |
| <span data-ttu-id="37cf1-165">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="37cf1-166">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="37cf1-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="37cf1-167">-WhatIf</span></span>

<span data-ttu-id="37cf1-168">cmdlet이 실행될 경우 결과 동작을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="37cf1-169">cmdlet이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="37cf1-170">필수 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-170">Required?</span></span>                            | <span data-ttu-id="37cf1-171">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-171">false</span></span>                                |
| <span data-ttu-id="37cf1-172">위치</span><span class="sxs-lookup"><span data-stu-id="37cf1-172">Position?</span></span>                            | <span data-ttu-id="37cf1-173">명명됨</span><span class="sxs-lookup"><span data-stu-id="37cf1-173">named</span></span>                                |
| <span data-ttu-id="37cf1-174">기본값</span><span class="sxs-lookup"><span data-stu-id="37cf1-174">Default Value</span></span>                        | <span data-ttu-id="37cf1-175">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-175">false</span></span>                                |
| <span data-ttu-id="37cf1-176">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="37cf1-177">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-177">false</span></span>                                |
| <span data-ttu-id="37cf1-178">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="37cf1-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="37cf1-179">false</span><span class="sxs-lookup"><span data-stu-id="37cf1-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="37cf1-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="37cf1-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="37cf1-181">이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="37cf1-182">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37cf1-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="37cf1-183">입력</span><span class="sxs-lookup"><span data-stu-id="37cf1-183">INPUTS</span></span>

<span data-ttu-id="37cf1-184">이 cmdlet은 입력이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="37cf1-185">출력</span><span class="sxs-lookup"><span data-stu-id="37cf1-185">OUTPUTS</span></span>

<span data-ttu-id="37cf1-186">이 cmdlet은 출력을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="37cf1-187">예제</span><span class="sxs-lookup"><span data-stu-id="37cf1-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="37cf1-188">예제 1</span><span class="sxs-lookup"><span data-stu-id="37cf1-188">EXAMPLE 1</span></span>

<span data-ttu-id="37cf1-189">이 명령은 Windows PowerShell 웹 응용 프로그램을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="37cf1-190">Windows PowerShell 웹 응용 프로그램을 설치할 때 기본값을 사용한 경우 제거할 때 이 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="37cf1-191">예제 2</span><span class="sxs-lookup"><span data-stu-id="37cf1-191">EXAMPLE 2</span></span>

<span data-ttu-id="37cf1-192">이 명령은 Windows PowerShell 웹 응용 프로그램을 제거하고 응용 프로그램과 연결된 테스트 인증서를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="37cf1-193">Windows PowerShell 웹 응용 프로그램을 설치할 때 기본값을 사용하고 테스트 인증서를 만든 경우 제거할 때 이 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="37cf1-194">예제 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="37cf1-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="37cf1-195">Windows PowerShell 웹 응용 프로그램을 설치할 때 사용자 지정 웹 사이트 및 응용 프로그램을 지정한 경우 제거할 때 이 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="37cf1-196">이 명령은 *MySite*라는 웹 사이트와 *TestApplication*이라는 응용 프로그램을 제거하고 응용 프로그램과 연결된 테스트 인증서도 삭제하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37cf1-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="37cf1-197">관련 항목</span><span class="sxs-lookup"><span data-stu-id="37cf1-197">Related topics</span></span>

- [<span data-ttu-id="37cf1-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="37cf1-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="37cf1-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="37cf1-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="37cf1-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="37cf1-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="37cf1-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="37cf1-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="37cf1-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="37cf1-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)