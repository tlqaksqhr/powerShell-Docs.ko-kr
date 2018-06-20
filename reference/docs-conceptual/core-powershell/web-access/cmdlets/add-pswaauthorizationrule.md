---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: b8020f8b034ab24d79a96da3908e9b63bf017cd9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190386"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="25948-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="25948-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="25948-104">요약</span><span class="sxs-lookup"><span data-stu-id="25948-104">SYNOPSIS</span></span>

<span data-ttu-id="25948-105">새로운 권한 부여 규칙을 Windows PowerShell® 웹 액세스 권한 부여 규칙 집합에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="25948-106">구문</span><span class="sxs-lookup"><span data-stu-id="25948-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="25948-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="25948-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="25948-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="25948-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="25948-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="25948-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="25948-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="25948-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="25948-111">설명</span><span class="sxs-lookup"><span data-stu-id="25948-111">DESCRIPTION</span></span>

<span data-ttu-id="25948-112">**Add-PswaAuthorizationRule** cmdlet은 새로운 권한 부여 규칙을 Windows PowerShell® 웹 액세스 권한 부여 규칙 집합에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="25948-113">이 규칙에 대한 사용자, 컴퓨터 및 Windows PowerShell 끝점을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="25948-114">개별 사용자 및 컴퓨터 이름을 지정하거나 그룹을 지정하여 사용자 및 컴퓨터를 모두 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25948-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="25948-115">Active Directory 도메인에 가입된 컴퓨터의 경우 이 cmdlet은 컴퓨터의 SID(보안 식별자)를 사용하여 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25948-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="25948-116">따라서 로그인 페이지의 **컴퓨터 이름** 필드에 약식 이름, FQDN(정규화된 도메인 이름 ) 또는 IP 주소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25948-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="25948-117">Active Directory 도메인에 가입되지 않은 컴퓨터의 경우 이 cmdlet은 관리자가 제공한 컴퓨터 이름을 사용하여 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25948-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="25948-118">이 컴퓨터에 연결하려면 최종 사용자는 컴퓨터 이름을 규칙에 표시된 대로 정확히 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="25948-119">네트워크에서 같은 이름의 컴퓨터가 여럿 있는 경우에는 약식 이름을 사용하여 둘 이상의 컴퓨터를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25948-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="25948-120">따라서 연결을 설정할 때 모호해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25948-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="25948-121">예를 들어 "*Server1*"이라는 작업 그룹 컴퓨터에 대한 규칙이 있고 *server1.contoso.com*이라는 새 컴퓨터가 네트워크에 가입된 경우 권한 부여 규칙을 사용한 유효성 검사가 성공하고 Windows PowerShell 웹 액세스가 "*Server1*"이라는 컴퓨터에 대한 연결을 설정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="25948-122">지정된 작업 그룹 컴퓨터와의 연결이 설정된다는 보장은 없으며, 작업 그룹 또는 "*Server1*"이라는 도메인 컴퓨터에 대해 연결이 시도될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25948-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="25948-123">모호성을 줄이기 위해 가능하면 대상 컴퓨터의 FQDN을 사용하여 권한 부여 규칙을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="25948-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="25948-124">권한 부여 규칙에서는 대체 자격 증명(로그인 페이지의 **옵션 연결 설정** 섹션에 있는 두 번째 자격 증명 집합)이 아니라 Windows PowerShell 웹 액세스 사용자의 기본 로그인 자격 증명을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="25948-125">관련 예제는 예제 6을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25948-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="25948-126">매개 변수</span><span class="sxs-lookup"><span data-stu-id="25948-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="25948-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="25948-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="25948-128">이 규칙이 액세스 권한을 부여하는 AD DS(Active Directory 도메인 서비스)의 컴퓨터 그룹 또는 로컬 그룹의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="25948-129">별칭</span><span class="sxs-lookup"><span data-stu-id="25948-129">Aliases</span></span>                              | <span data-ttu-id="25948-130">없음</span><span class="sxs-lookup"><span data-stu-id="25948-130">none</span></span>                                 |
| <span data-ttu-id="25948-131">필수 여부</span><span class="sxs-lookup"><span data-stu-id="25948-131">Required?</span></span>                            | <span data-ttu-id="25948-132">true</span><span class="sxs-lookup"><span data-stu-id="25948-132">true</span></span>                                 |
| <span data-ttu-id="25948-133">위치</span><span class="sxs-lookup"><span data-stu-id="25948-133">Position?</span></span>                            | <span data-ttu-id="25948-134">명명됨</span><span class="sxs-lookup"><span data-stu-id="25948-134">named</span></span>                                |
| <span data-ttu-id="25948-135">기본값</span><span class="sxs-lookup"><span data-stu-id="25948-135">Default Value</span></span>                        | <span data-ttu-id="25948-136">없음</span><span class="sxs-lookup"><span data-stu-id="25948-136">none</span></span>                                 |
| <span data-ttu-id="25948-137">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25948-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="25948-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="25948-139">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25948-140">false</span><span class="sxs-lookup"><span data-stu-id="25948-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="25948-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="25948-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="25948-142">이 규칙이 액세스 권한을 부여하는 컴퓨터 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="25948-143">별칭</span><span class="sxs-lookup"><span data-stu-id="25948-143">Aliases</span></span>                              | <span data-ttu-id="25948-144">없음</span><span class="sxs-lookup"><span data-stu-id="25948-144">none</span></span>                                 |
| <span data-ttu-id="25948-145">필수 여부</span><span class="sxs-lookup"><span data-stu-id="25948-145">Required?</span></span>                            | <span data-ttu-id="25948-146">true</span><span class="sxs-lookup"><span data-stu-id="25948-146">true</span></span>                                 |
| <span data-ttu-id="25948-147">위치</span><span class="sxs-lookup"><span data-stu-id="25948-147">Position?</span></span>                            | <span data-ttu-id="25948-148">명명됨</span><span class="sxs-lookup"><span data-stu-id="25948-148">named</span></span>                                |
| <span data-ttu-id="25948-149">기본값</span><span class="sxs-lookup"><span data-stu-id="25948-149">Default Value</span></span>                        | <span data-ttu-id="25948-150">없음</span><span class="sxs-lookup"><span data-stu-id="25948-150">none</span></span>                                 |
| <span data-ttu-id="25948-151">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25948-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="25948-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="25948-153">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25948-154">false</span><span class="sxs-lookup"><span data-stu-id="25948-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="25948-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="25948-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="25948-156">이 규칙이 액세스 권한을 부여하는 Windows PowerShell 세션 구성(runspace라고도 함)의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="25948-157">별칭</span><span class="sxs-lookup"><span data-stu-id="25948-157">Aliases</span></span>                              | <span data-ttu-id="25948-158">없음</span><span class="sxs-lookup"><span data-stu-id="25948-158">none</span></span>                                 |
| <span data-ttu-id="25948-159">필수 여부</span><span class="sxs-lookup"><span data-stu-id="25948-159">Required?</span></span>                            | <span data-ttu-id="25948-160">true</span><span class="sxs-lookup"><span data-stu-id="25948-160">true</span></span>                                 |
| <span data-ttu-id="25948-161">위치</span><span class="sxs-lookup"><span data-stu-id="25948-161">Position?</span></span>                            | <span data-ttu-id="25948-162">명명됨</span><span class="sxs-lookup"><span data-stu-id="25948-162">named</span></span>                                |
| <span data-ttu-id="25948-163">기본값</span><span class="sxs-lookup"><span data-stu-id="25948-163">Default Value</span></span>                        | <span data-ttu-id="25948-164">없음</span><span class="sxs-lookup"><span data-stu-id="25948-164">none</span></span>                                 |
| <span data-ttu-id="25948-165">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25948-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="25948-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="25948-167">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25948-168">false</span><span class="sxs-lookup"><span data-stu-id="25948-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="25948-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="25948-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="25948-170">Windows PowerShell 웹 액세스 권한 부여 규칙을 변경하는 데 사용할 사용자 계정에 대한 **PSCredential** 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="25948-171">이 매개 변수를 추가하지 않으면 현재 로그온한 사용자 계정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="25948-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="25948-172">권한 부여 규칙을 추가하는 데 필요한 **PSCredential**을 가져오려면 [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="25948-173">별칭</span><span class="sxs-lookup"><span data-stu-id="25948-173">Aliases</span></span>                              | <span data-ttu-id="25948-174">없음</span><span class="sxs-lookup"><span data-stu-id="25948-174">none</span></span>                                 |
| <span data-ttu-id="25948-175">필수 여부</span><span class="sxs-lookup"><span data-stu-id="25948-175">Required?</span></span>                            | <span data-ttu-id="25948-176">false</span><span class="sxs-lookup"><span data-stu-id="25948-176">false</span></span>                                |
| <span data-ttu-id="25948-177">위치</span><span class="sxs-lookup"><span data-stu-id="25948-177">Position?</span></span>                            | <span data-ttu-id="25948-178">명명됨</span><span class="sxs-lookup"><span data-stu-id="25948-178">named</span></span>                                |
| <span data-ttu-id="25948-179">기본값</span><span class="sxs-lookup"><span data-stu-id="25948-179">Default Value</span></span>                        | <span data-ttu-id="25948-180">없음</span><span class="sxs-lookup"><span data-stu-id="25948-180">none</span></span>                                 |
| <span data-ttu-id="25948-181">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25948-182">false</span><span class="sxs-lookup"><span data-stu-id="25948-182">false</span></span>                                |
| <span data-ttu-id="25948-183">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25948-184">false</span><span class="sxs-lookup"><span data-stu-id="25948-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="25948-185">-Force</span><span class="sxs-lookup"><span data-stu-id="25948-185">-Force</span></span>

<span data-ttu-id="25948-186">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.\\</span><span class="sxs-lookup"><span data-stu-id="25948-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="25948-187">또한, 단순하거나 짧은 컴퓨터 이름(예: 도메인 이름이 아니거나 정규화되지 않은 이름)을 입력할 경우 확인하는 메시지도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="25948-188">확인은 보안 때문에 필요하므로 컴퓨터가 작업 그룹에 있는 경우에만 단순 이름을 사용하여 컴퓨터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25948-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="25948-189">별칭</span><span class="sxs-lookup"><span data-stu-id="25948-189">Aliases</span></span>                              | <span data-ttu-id="25948-190">없음</span><span class="sxs-lookup"><span data-stu-id="25948-190">none</span></span>                                 |
| <span data-ttu-id="25948-191">필수 여부</span><span class="sxs-lookup"><span data-stu-id="25948-191">Required?</span></span>                            | <span data-ttu-id="25948-192">false</span><span class="sxs-lookup"><span data-stu-id="25948-192">false</span></span>                                |
| <span data-ttu-id="25948-193">위치</span><span class="sxs-lookup"><span data-stu-id="25948-193">Position?</span></span>                            | <span data-ttu-id="25948-194">명명됨</span><span class="sxs-lookup"><span data-stu-id="25948-194">named</span></span>                                |
| <span data-ttu-id="25948-195">기본값</span><span class="sxs-lookup"><span data-stu-id="25948-195">Default Value</span></span>                        | <span data-ttu-id="25948-196">없음</span><span class="sxs-lookup"><span data-stu-id="25948-196">none</span></span>                                 |
| <span data-ttu-id="25948-197">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25948-198">false</span><span class="sxs-lookup"><span data-stu-id="25948-198">false</span></span>                                |
| <span data-ttu-id="25948-199">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25948-200">false</span><span class="sxs-lookup"><span data-stu-id="25948-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="25948-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="25948-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="25948-202">이 규칙의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="25948-203">별칭</span><span class="sxs-lookup"><span data-stu-id="25948-203">Aliases</span></span>                              | <span data-ttu-id="25948-204">없음</span><span class="sxs-lookup"><span data-stu-id="25948-204">none</span></span>                                 |
| <span data-ttu-id="25948-205">필수 여부</span><span class="sxs-lookup"><span data-stu-id="25948-205">Required?</span></span>                            | <span data-ttu-id="25948-206">false</span><span class="sxs-lookup"><span data-stu-id="25948-206">false</span></span>                                |
| <span data-ttu-id="25948-207">위치</span><span class="sxs-lookup"><span data-stu-id="25948-207">Position?</span></span>                            | <span data-ttu-id="25948-208">명명됨</span><span class="sxs-lookup"><span data-stu-id="25948-208">named</span></span>                                |
| <span data-ttu-id="25948-209">기본값</span><span class="sxs-lookup"><span data-stu-id="25948-209">Default Value</span></span>                        | <span data-ttu-id="25948-210">없음</span><span class="sxs-lookup"><span data-stu-id="25948-210">none</span></span>                                 |
| <span data-ttu-id="25948-211">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25948-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="25948-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="25948-213">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25948-214">false</span><span class="sxs-lookup"><span data-stu-id="25948-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="25948-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="25948-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="25948-216">이 규칙이 액세스 권한을 부여하는 AD DS의 사용자 그룹 하나 이상 또는 로컬 그룹의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="25948-217">별칭</span><span class="sxs-lookup"><span data-stu-id="25948-217">Aliases</span></span>                              | <span data-ttu-id="25948-218">없음</span><span class="sxs-lookup"><span data-stu-id="25948-218">none</span></span>                                 |
| <span data-ttu-id="25948-219">필수 여부</span><span class="sxs-lookup"><span data-stu-id="25948-219">Required?</span></span>                            | <span data-ttu-id="25948-220">true</span><span class="sxs-lookup"><span data-stu-id="25948-220">true</span></span>                                 |
| <span data-ttu-id="25948-221">위치</span><span class="sxs-lookup"><span data-stu-id="25948-221">Position?</span></span>                            | <span data-ttu-id="25948-222">명명됨</span><span class="sxs-lookup"><span data-stu-id="25948-222">named</span></span>                                |
| <span data-ttu-id="25948-223">기본값</span><span class="sxs-lookup"><span data-stu-id="25948-223">Default Value</span></span>                        | <span data-ttu-id="25948-224">없음</span><span class="sxs-lookup"><span data-stu-id="25948-224">none</span></span>                                 |
| <span data-ttu-id="25948-225">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25948-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="25948-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="25948-227">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25948-228">false</span><span class="sxs-lookup"><span data-stu-id="25948-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="25948-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="25948-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="25948-230">이 규칙이 액세스 권한을 부여하는 하나 이상의 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="25948-231">사용자 이름은 게이트웨이 컴퓨터의 로컬 사용자 계정 또는 AD DS의 사용자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25948-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="25948-232">형식은 `domain\user` 또는 `computer\user`입니다.</span><span class="sxs-lookup"><span data-stu-id="25948-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="25948-233">별칭</span><span class="sxs-lookup"><span data-stu-id="25948-233">Aliases</span></span>                              | <span data-ttu-id="25948-234">없음</span><span class="sxs-lookup"><span data-stu-id="25948-234">none</span></span>                                 |
| <span data-ttu-id="25948-235">필수 여부</span><span class="sxs-lookup"><span data-stu-id="25948-235">Required?</span></span>                            | <span data-ttu-id="25948-236">true</span><span class="sxs-lookup"><span data-stu-id="25948-236">true</span></span>                                 |
| <span data-ttu-id="25948-237">위치</span><span class="sxs-lookup"><span data-stu-id="25948-237">Position?</span></span>                            | <span data-ttu-id="25948-238">1</span><span class="sxs-lookup"><span data-stu-id="25948-238">1</span></span>                                    |
| <span data-ttu-id="25948-239">기본값</span><span class="sxs-lookup"><span data-stu-id="25948-239">Default Value</span></span>                        | <span data-ttu-id="25948-240">없음</span><span class="sxs-lookup"><span data-stu-id="25948-240">none</span></span>                                 |
| <span data-ttu-id="25948-241">파이프라인 입력 적용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25948-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="25948-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="25948-243">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="25948-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25948-244">false</span><span class="sxs-lookup"><span data-stu-id="25948-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="25948-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="25948-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="25948-246">이 cmdlet은 -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, -OutVariable 등의 일반 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="25948-247">자세한 내용은 [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25948-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="25948-248">입력</span><span class="sxs-lookup"><span data-stu-id="25948-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="25948-249">문자열</span><span class="sxs-lookup"><span data-stu-id="25948-249">String</span></span>

<span data-ttu-id="25948-250">이 cmdlet은 문자열 또는 문자열 배열을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="25948-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="25948-251">String\[\]</span></span>

<span data-ttu-id="25948-252">이 cmdlet은 문자열 또는 문자열 배열을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="25948-253">출력</span><span class="sxs-lookup"><span data-stu-id="25948-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="25948-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="25948-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="25948-255">이 cmdlet은 권한 부여 규칙 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="25948-256">예제</span><span class="sxs-lookup"><span data-stu-id="25948-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="25948-257">예제 1</span><span class="sxs-lookup"><span data-stu-id="25948-257">EXAMPLE 1</span></span>

<span data-ttu-id="25948-258">이 예제에서는 *srv2*에서 *SMAdmins* 그룹의 사용자에게 세션 구성 *PSWAEndpoint*(제한된 runspace)에 대한 액세스 권한을 부여합니다.\\</span><span class="sxs-lookup"><span data-stu-id="25948-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="25948-259">**참고**: 컴퓨터 이름은 FQDN(정규화된 도메인 이름)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="25948-260">관리자는 최종 사용자가 실행할 수 있는 제한된 범위의 cmdlet 및 작업인 제한 세션 구성 또는 runspace를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="25948-261">제한된 runspace를 정의하면 사용자가 허용된 Windows PowerShell® runspace에 없는 다른 컴퓨터에 액세스하지 못하므로 더 안전한 연결을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="25948-262">세션 구성에 대한 자세한 내용은 [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) 또는 [Windows PowerShell 웹 액세스 설치 및 사용](../install-and-use-windows-powershell-web-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25948-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="25948-263">예제 2</span><span class="sxs-lookup"><span data-stu-id="25948-263">EXAMPLE 2</span></span>

<span data-ttu-id="25948-264">이 예제에서는 *srv2*에서 contoso\\user1, contoso\\user2 및 contoso\\user3이라는 사용자에게 기본 Windows PowerShell 세션 구성 `Microsoft.PowerShell`에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="25948-265">이 cmdlet은 세 개의 규칙(사용자당 1개)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25948-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="25948-266">예제 3</span><span class="sxs-lookup"><span data-stu-id="25948-266">EXAMPLE 3</span></span>

<span data-ttu-id="25948-267">이 예제에서는 파이프라인을 통해 사용자 이름 값을 입력하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25948-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="25948-268">예제 4</span><span class="sxs-lookup"><span data-stu-id="25948-268">EXAMPLE 4</span></span>

<span data-ttu-id="25948-269">이 예제에서는 모든 매개 변수의 값을 속성 이름별로 파이프라인에서 가져오는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="25948-270">예제 5</span><span class="sxs-lookup"><span data-stu-id="25948-270">EXAMPLE 5</span></span>

<span data-ttu-id="25948-271">이 예제에서는 *PswaServer\\ChrisLocal*이라는 로컬 사용자가 *srv1.contoso.com*이라는 서버에 액세스할 수 있도록 규칙을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="25948-272">이 예제에서는 게이트웨이가 작업 그룹에 있고 대상 컴퓨터가 도메인에 있는 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25948-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="25948-273">권한 부여 규칙은 게이트웨이의 로컬 사용자에게 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="25948-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="25948-274">Windows PowerShell 웹 액세스 로그인 페이지에서 인증하려면 사용자는 **옵션 연결 설정** 영역의 두 번째 자격 증명 집합을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="25948-275">게이트웨이 서버는 추가 자격 증명 집합을 사용하여 대상 컴퓨터인 *srv1.contoso.com*이라는 서버에서 사용자를 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="25948-276">예제 6</span><span class="sxs-lookup"><span data-stu-id="25948-276">EXAMPLE 6</span></span>

<span data-ttu-id="25948-277">이 예제에서는 모든 사용자가 모든 컴퓨터의 모든 끝점에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="25948-278">여기서는 기본적으로 권한 부여 규칙을 끕니다.\\</span><span class="sxs-lookup"><span data-stu-id="25948-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="25948-279">**참고**: `*` 와일드카드 문자는 보안이 중요한 배포에서는 사용하지 않는 것이 좋으며 테스트 환경에서나 보안을 완화할 수 있는 배포에서만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25948-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="25948-280">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25948-280">See Also</span></span>

- <span data-ttu-id="25948-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="25948-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="25948-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="25948-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="25948-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="25948-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="25948-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="25948-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="25948-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="25948-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="25948-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="25948-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="25948-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="25948-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)