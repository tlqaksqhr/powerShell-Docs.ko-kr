---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: install pswawebapplication
ms.technology: powershell
ms.openlocfilehash: ce4d01fbe8a83924e7023d792c68c903a32e07d4
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="a278f-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="a278f-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="a278f-104">요약</span><span class="sxs-lookup"><span data-stu-id="a278f-104">SYNOPSIS</span></span>

<span data-ttu-id="a278f-105">IIS에서 Windows PowerShell® 웹 액세스 웹 응용 프로그램을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="a278f-106">구문</span><span class="sxs-lookup"><span data-stu-id="a278f-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="a278f-107">Default</span><span class="sxs-lookup"><span data-stu-id="a278f-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="a278f-108">설명</span><span class="sxs-lookup"><span data-stu-id="a278f-108">DESCRIPTION</span></span>

<span data-ttu-id="a278f-109">**Install-PswaWebApplication** cmdlet은 Windows PowerShell 웹 액세스 웹 응용 프로그램을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="a278f-110">이 cmdlet은 웹 응용 프로그램을 설치하고, 웹 사이트와 연결하고, 선택적으로 **useTestCertificate** 매개 변수를 사용하여 테스트 SSL 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="a278f-111">보안을 위해 웹 관리자는 테스트 인증서는 프로덕션 환경에서만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="a278f-112">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a278f-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="a278f-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="a278f-113">-UseTestCertificate</span></span>

<span data-ttu-id="a278f-114">테스트 인증서를 만들도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="a278f-115">이 매개 변수를 true로 설정하면 이 cmdlet은 테스트 인증서를 만들고 HTTPS 요청에 이 인증서를 사용하도록 Windows PowerShell 웹 액세스 웹 응용 프로그램을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="a278f-116">이 매개 변수를 false로 설정하면 인증서나 바인딩을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="a278f-117">Windows PowerShell 웹 액세스에 다른 인증서를 사용하는 경우 이 값을 false로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="a278f-118">별칭</span><span class="sxs-lookup"><span data-stu-id="a278f-118">Aliases</span></span>                              | <span data-ttu-id="a278f-119">없음</span><span class="sxs-lookup"><span data-stu-id="a278f-119">none</span></span>                                 |
| <span data-ttu-id="a278f-120">필수 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-120">Required?</span></span>                            | <span data-ttu-id="a278f-121">false</span><span class="sxs-lookup"><span data-stu-id="a278f-121">false</span></span>                                |
| <span data-ttu-id="a278f-122">위치</span><span class="sxs-lookup"><span data-stu-id="a278f-122">Position?</span></span>                            | <span data-ttu-id="a278f-123">명명됨</span><span class="sxs-lookup"><span data-stu-id="a278f-123">named</span></span>                                |
| <span data-ttu-id="a278f-124">기본값</span><span class="sxs-lookup"><span data-stu-id="a278f-124">Default Value</span></span>                        | <span data-ttu-id="a278f-125">true</span><span class="sxs-lookup"><span data-stu-id="a278f-125">true</span></span>                                 |
| <span data-ttu-id="a278f-126">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a278f-127">false</span><span class="sxs-lookup"><span data-stu-id="a278f-127">false</span></span>                                |
| <span data-ttu-id="a278f-128">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a278f-129">false</span><span class="sxs-lookup"><span data-stu-id="a278f-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="a278f-130">-WebApplicationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="a278f-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="a278f-131">웹 응용 프로그램 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-131">Specifies the name for your web application.</span></span> <span data-ttu-id="a278f-132">Windows PowerShell 웹 액세스 URL의 마지막 부분으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="a278f-133">별칭</span><span class="sxs-lookup"><span data-stu-id="a278f-133">Aliases</span></span>                              | <span data-ttu-id="a278f-134">없음</span><span class="sxs-lookup"><span data-stu-id="a278f-134">none</span></span>                                 |
| <span data-ttu-id="a278f-135">필수 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-135">Required?</span></span>                            | <span data-ttu-id="a278f-136">false</span><span class="sxs-lookup"><span data-stu-id="a278f-136">false</span></span>                                |
| <span data-ttu-id="a278f-137">위치</span><span class="sxs-lookup"><span data-stu-id="a278f-137">Position?</span></span>                            | <span data-ttu-id="a278f-138">1</span><span class="sxs-lookup"><span data-stu-id="a278f-138">1</span></span>                                    |
| <span data-ttu-id="a278f-139">기본값</span><span class="sxs-lookup"><span data-stu-id="a278f-139">Default Value</span></span>                        | <span data-ttu-id="a278f-140">pswa</span><span class="sxs-lookup"><span data-stu-id="a278f-140">pswa</span></span>                                 |
| <span data-ttu-id="a278f-141">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a278f-142">false</span><span class="sxs-lookup"><span data-stu-id="a278f-142">false</span></span>                                |
| <span data-ttu-id="a278f-143">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a278f-144">false</span><span class="sxs-lookup"><span data-stu-id="a278f-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="a278f-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="a278f-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="a278f-146">이 Windows PowerShell 웹 액세스 웹 응용 프로그램 설치할 웹 서버(IIS) 웹 사이트의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="a278f-147">별칭</span><span class="sxs-lookup"><span data-stu-id="a278f-147">Aliases</span></span>                              | <span data-ttu-id="a278f-148">없음</span><span class="sxs-lookup"><span data-stu-id="a278f-148">none</span></span>                                 |
| <span data-ttu-id="a278f-149">필수 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-149">Required?</span></span>                            | <span data-ttu-id="a278f-150">false</span><span class="sxs-lookup"><span data-stu-id="a278f-150">false</span></span>                                |
| <span data-ttu-id="a278f-151">위치</span><span class="sxs-lookup"><span data-stu-id="a278f-151">Position?</span></span>                            | <span data-ttu-id="a278f-152">명명됨</span><span class="sxs-lookup"><span data-stu-id="a278f-152">named</span></span>                                |
| <span data-ttu-id="a278f-153">기본값</span><span class="sxs-lookup"><span data-stu-id="a278f-153">Default Value</span></span>                        | <span data-ttu-id="a278f-154">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="a278f-154">Default Web Site</span></span>                     |
| <span data-ttu-id="a278f-155">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a278f-156">false</span><span class="sxs-lookup"><span data-stu-id="a278f-156">false</span></span>                                |
| <span data-ttu-id="a278f-157">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a278f-158">false</span><span class="sxs-lookup"><span data-stu-id="a278f-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="a278f-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a278f-159">-Confirm</span></span>

<span data-ttu-id="a278f-160">cmdlet을 실행하기 전에 확인 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="a278f-161">필수 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-161">Required?</span></span>                            | <span data-ttu-id="a278f-162">false</span><span class="sxs-lookup"><span data-stu-id="a278f-162">false</span></span>                                |
| <span data-ttu-id="a278f-163">위치</span><span class="sxs-lookup"><span data-stu-id="a278f-163">Position?</span></span>                            | <span data-ttu-id="a278f-164">명명됨</span><span class="sxs-lookup"><span data-stu-id="a278f-164">named</span></span>                                |
| <span data-ttu-id="a278f-165">기본값</span><span class="sxs-lookup"><span data-stu-id="a278f-165">Default Value</span></span>                        | <span data-ttu-id="a278f-166">false</span><span class="sxs-lookup"><span data-stu-id="a278f-166">false</span></span>                                |
| <span data-ttu-id="a278f-167">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a278f-168">false</span><span class="sxs-lookup"><span data-stu-id="a278f-168">false</span></span>                                |
| <span data-ttu-id="a278f-169">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a278f-170">false</span><span class="sxs-lookup"><span data-stu-id="a278f-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="a278f-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a278f-171">-WhatIf</span></span>

<span data-ttu-id="a278f-172">cmdlet이 실행될 경우 결과 동작을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a278f-173">cmdlet이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="a278f-174">필수 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-174">Required?</span></span>                            | <span data-ttu-id="a278f-175">false</span><span class="sxs-lookup"><span data-stu-id="a278f-175">false</span></span>                                |
| <span data-ttu-id="a278f-176">위치</span><span class="sxs-lookup"><span data-stu-id="a278f-176">Position?</span></span>                            | <span data-ttu-id="a278f-177">명명됨</span><span class="sxs-lookup"><span data-stu-id="a278f-177">named</span></span>                                |
| <span data-ttu-id="a278f-178">기본값</span><span class="sxs-lookup"><span data-stu-id="a278f-178">Default Value</span></span>                        | <span data-ttu-id="a278f-179">false</span><span class="sxs-lookup"><span data-stu-id="a278f-179">false</span></span>                                |
| <span data-ttu-id="a278f-180">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a278f-181">false</span><span class="sxs-lookup"><span data-stu-id="a278f-181">false</span></span>                                |
| <span data-ttu-id="a278f-182">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="a278f-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a278f-183">false</span><span class="sxs-lookup"><span data-stu-id="a278f-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="a278f-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="a278f-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="a278f-185">이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="a278f-186">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a278f-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="a278f-187">입력</span><span class="sxs-lookup"><span data-stu-id="a278f-187">INPUTS</span></span>

<span data-ttu-id="a278f-188">이 cmdlet은 입력이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="a278f-189">출력</span><span class="sxs-lookup"><span data-stu-id="a278f-189">OUTPUTS</span></span>

<span data-ttu-id="a278f-190">이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="a278f-191">예제</span><span class="sxs-lookup"><span data-stu-id="a278f-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="a278f-192">예제 1</span><span class="sxs-lookup"><span data-stu-id="a278f-192">EXAMPLE 1</span></span>

<span data-ttu-id="a278f-193">이 예제에서는 **WebApplicationName**(*pswa*) 및 **WebSiteName**(*Default Web Site*) 매개 변수의 기본값을 사용하여 PSWA 웹 응용 프로그램을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="a278f-194">예제 2</span><span class="sxs-lookup"><span data-stu-id="a278f-194">EXAMPLE 2</span></span>

<span data-ttu-id="a278f-195">이 예제에서는 **WebApplicationName** 및 **WebSiteName** 매개 변수의 기본값을 사용하고 테스트 인증서를 사용하여 PSWA 웹 응용 프로그램을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a278f-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="a278f-196">관련 항목</span><span class="sxs-lookup"><span data-stu-id="a278f-196">Related topics</span></span>

- [<span data-ttu-id="a278f-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a278f-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="a278f-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a278f-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="a278f-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a278f-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="a278f-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a278f-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
