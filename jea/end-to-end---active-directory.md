---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "종단 간 - Active Directory"
ms.technology: powershell
ms.openlocfilehash: 3108f5dad96ef54feb3cf559fae38812ed46849c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="end-to-end---active-directory"></a><span data-ttu-id="7d76d-103">종단 간 - Active Directory</span><span class="sxs-lookup"><span data-stu-id="7d76d-103">End to End - Active Directory</span></span>
<span data-ttu-id="7d76d-104">프로그램의 범위가 증가했다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-104">Imagine the scope of your program has increased.</span></span>
<span data-ttu-id="7d76d-105">이제 Active Directory 작업을 수행하기 위해 JEA를 도메인 컨트롤러에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-105">You are now responsible for adding JEA to Domain Controllers to perform Active Directory actions.</span></span>
<span data-ttu-id="7d76d-106">지원 센터 직원들이 JEA를 사용하여 계정의 잠금을 해제하고, 암호를 다시 설정하고, 다른 유사한 작업을 수행하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-106">The help desk people are going to use JEA to unlock accounts, reset passwords, and do other similar actions.</span></span>

<span data-ttu-id="7d76d-107">다른 사용자 그룹에 완전히 새로운 명령 집합을 노출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-107">You need to expose a completely new set of commands to a different group of people.</span></span>
<span data-ttu-id="7d76d-108">뿐만 아니라 노출해야 하는 기존 Active Directory 스크립트 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-108">On top of that, you have a bunch of existing Active Directory scripts you need to expose.</span></span>
<span data-ttu-id="7d76d-109">이 섹션에서는 이 작업에 대한 세션 구성과 역할 기능을 작성하는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-109">This section will walk through authoring a Session Configuration and Role Capability for this task.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7d76d-110">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="7d76d-110">Prerequisites</span></span>
<span data-ttu-id="7d76d-111">이 섹션을 단계별로 수행하려면 도메인 컨트롤러에서 작업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-111">To follow this section step-by-step, you'll need to be operating on a domain controller.</span></span>
<span data-ttu-id="7d76d-112">도메인 컨트롤러에 액세스할 수 없는 경우 걱정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7d76d-112">If you don't have access to your domain controller, don't worry.</span></span>
<span data-ttu-id="7d76d-113">익숙한 다른 시나리오나 역할을 대상으로 작업하여 이 섹션의 내용을 파악해 보세요.</span><span class="sxs-lookup"><span data-stu-id="7d76d-113">Try to follow along with by working against some other scenario or role with which you are familiar.</span></span>
<span data-ttu-id="7d76d-114">새 도메인 컨트롤러를 신속하게 설정하려면 [도메인 컨트롤러 만들기 부록](.\creating-a-domain-controller.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d76d-114">If you want to quickly set up a new domain controller, check out the [Creating a Domain Controller appendix](.\creating-a-domain-controller.md).</span></span>

## <a name="steps-to-make-a-new-role-capability-and-session-configuration"></a><span data-ttu-id="7d76d-115">새로운 역할 기능 및 세션 구성을 만드는 단계</span><span class="sxs-lookup"><span data-stu-id="7d76d-115">Steps to Make a new Role Capability and Session Configuration</span></span>

<span data-ttu-id="7d76d-116">새로운 역할 기능을 만드는 작업은 처음에는 어렵게 느껴질 수 있지만 매우 간단한 단계로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-116">Making a new role capability can seem daunting at first, but it can be broken into fairly simple steps:</span></span>

1.  <span data-ttu-id="7d76d-117">사용하도록 설정해야 하는 작업 식별</span><span class="sxs-lookup"><span data-stu-id="7d76d-117">Identify the tasks you need to enable</span></span>
2.  <span data-ttu-id="7d76d-118">필요에 따라 해당 작업 제한</span><span class="sxs-lookup"><span data-stu-id="7d76d-118">Restrict those tasks as necessary</span></span>
3.  <span data-ttu-id="7d76d-119">해당 작업이 JEA와 작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="7d76d-119">Confirm they work with JEA</span></span>
4.  <span data-ttu-id="7d76d-120">해당 작업을 역할 기능 파일에 배치</span><span class="sxs-lookup"><span data-stu-id="7d76d-120">Put them in a Role Capability file</span></span>
5.  <span data-ttu-id="7d76d-121">해당 역할 기능을 노출하는 세션 구성 등록</span><span class="sxs-lookup"><span data-stu-id="7d76d-121">Register a Session Configuration that exposes that Role Capability</span></span>

## <a name="step-1-identify-what-needs-to-be-exposed"></a><span data-ttu-id="7d76d-122">1단계: 노출해야 하는 작업 식별</span><span class="sxs-lookup"><span data-stu-id="7d76d-122">Step 1: Identify What Needs to Be Exposed</span></span>
<span data-ttu-id="7d76d-123">새로운 역할 기능이나 세션 구성을 만들기 전에 사용자가 JEA 끝점을 통해 수행해야 하는 모든 작업과 PowerShell을 통해 해당 작업을 수행하는 방법을 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-123">Before you make a new Role Capability or Session Configuration, you need to identify all of the things users will need to do through the JEA endpoint, as well as how to do them through PowerShell.</span></span>
<span data-ttu-id="7d76d-124">여기에는 상당한 양의 요구 사항 수집과 연구가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-124">This will involve a fair amount of requirement gathering and research.</span></span>
<span data-ttu-id="7d76d-125">이 프로세스에 착수하는 방법은 조직과 목표에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-125">How you go about this process will depend on your organization and goals.</span></span>
<span data-ttu-id="7d76d-126">요구 사항 수집과 연구를 실제 프로세스의 중요한 부분으로 요구해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-126">It is important to call out requirement gathering and research as a critical part of the real world process.</span></span>
<span data-ttu-id="7d76d-127">이는 JEA 채택 프로세스의 가장 어려운 단계일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-127">This may be the most difficult step in the process of adopting JEA.</span></span>

### <a name="find-resources"></a><span data-ttu-id="7d76d-128">리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="7d76d-128">Find Resources</span></span>
<span data-ttu-id="7d76d-129">Active Directory 관리 끝점을 만드는 방법에 대한 연구에서 발견했을 수도 있는 온라인 리소스 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-129">Here is a set of online resources that might have come up in your research on creating an Active Directory management endpoint:</span></span>
-   [<span data-ttu-id="7d76d-130">Active Directory PowerShell 개요</span><span class="sxs-lookup"><span data-stu-id="7d76d-130">Active Directory PowerShell Overview</span></span>](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [<span data-ttu-id="7d76d-131">Active Directory에 대한 PowerShell CMD 가이드</span><span class="sxs-lookup"><span data-stu-id="7d76d-131">CMD to PowerShell Guide for Active Directory</span></span>](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### <a name="make-a-list"></a><span data-ttu-id="7d76d-132">목록 만들기</span><span class="sxs-lookup"><span data-stu-id="7d76d-132">Make a List</span></span>
<span data-ttu-id="7d76d-133">다음은 이 섹션의 나머지 부분에서 수행할 10가지 작업 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-133">Here is a set of ten actions that you will be working from in the remainder of this section.</span></span>
<span data-ttu-id="7d76d-134">이는 예일 뿐이라는 점을 명심하세요. 조직 요구 사항은 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-134">Keep in mind this is simply an example, your organizations requirements may be different:</span></span>

|<span data-ttu-id="7d76d-135">작업</span><span class="sxs-lookup"><span data-stu-id="7d76d-135">Action</span></span>                                                         |<span data-ttu-id="7d76d-136">PowerShell 명령</span><span class="sxs-lookup"><span data-stu-id="7d76d-136">PowerShell Command</span></span>                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|<span data-ttu-id="7d76d-137">계정 잠금 해제</span><span class="sxs-lookup"><span data-stu-id="7d76d-137">Account Unlock</span></span>                                                 |`Unlock-ADAccount`                                             |
|<span data-ttu-id="7d76d-138">암호 다시 설정</span><span class="sxs-lookup"><span data-stu-id="7d76d-138">Password Reset</span></span>                                                 |<span data-ttu-id="7d76d-139">`Set-ADAccountPassword` 및 `Set-ADUser -ChangePasswordAtLogon`</span><span class="sxs-lookup"><span data-stu-id="7d76d-139">`Set-ADAccountPassword` and `Set-ADUser -ChangePasswordAtLogon`</span></span>|
|<span data-ttu-id="7d76d-140">사용자의 직함 변경</span><span class="sxs-lookup"><span data-stu-id="7d76d-140">Change a User's Title</span></span>                                          |`Set-ADUser -Title`                                            |  
|<span data-ttu-id="7d76d-141">잠겨 있거나, 사용하지 않도록 설정되거나, 비활성 상태 등인 AD 계정 찾기</span><span class="sxs-lookup"><span data-stu-id="7d76d-141">Find AD Accounts that are locked out, disabled, inactive, etc.</span></span> |`Search-ADAccount`                                             |
|<span data-ttu-id="7d76d-142">그룹에 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="7d76d-142">Add User to Group</span></span>                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|<span data-ttu-id="7d76d-143">그룹에서 사용자 제거</span><span class="sxs-lookup"><span data-stu-id="7d76d-143">Remove User from Group</span></span>                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|<span data-ttu-id="7d76d-144">사용자 계정 사용</span><span class="sxs-lookup"><span data-stu-id="7d76d-144">Enable a user account</span></span>                                          |`Enable-ADAccount`                                             |
|<span data-ttu-id="7d76d-145">사용자 계정 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="7d76d-145">Disable a user account</span></span>                                         |`Disable-ADAccount`                                            |

## <a name="step-2-restrict-tasks-as-necessary"></a><span data-ttu-id="7d76d-146">2단계: 필요에 따라 작업 제한</span><span class="sxs-lookup"><span data-stu-id="7d76d-146">Step 2: Restrict Tasks as Necessary</span></span>

<span data-ttu-id="7d76d-147">이제 작업 목록이 있으므로 각 명령의 기능에 대해 자세히 알아봐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-147">Now that you have your list of actions, you need to think through the capabilities of each command.</span></span>
<span data-ttu-id="7d76d-148">이렇게 하는 데는 두 가지 중요한 이유가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-148">There are two important reasons to do this:</span></span>

1.  <span data-ttu-id="7d76d-149">의도한 것보다 많은 기능을 사용자에게 제공하기가 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-149">It is easy to give users more capabilities than you intend.</span></span>
<span data-ttu-id="7d76d-150">예를 들어 `Set-ADUser`는 매우 강력하고 유연한 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-150">For example, `Set-ADUser` is an incredibly powerful and flexible command.</span></span>
<span data-ttu-id="7d76d-151">이 명령으로 수행할 수 있는 모든 작업을 지원 센터 사용자에게 노출하는 것을 원하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-151">You may not want to expose everything it can do to help desk users.</span></span>  

2.  <span data-ttu-id="7d76d-152">훨씬 나쁜 경우로, JEA의 제한을 빠져나가도록 사용자에게 허용하는 명령을 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-152">Even worse, it's possible to expose commands that allow users to escape JEA's restrictions.</span></span>
<span data-ttu-id="7d76d-153">이 경우 JEA는 보안 경계로 기능하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-153">If this happens, JEA ceases to function as a security boundary.</span></span>
<span data-ttu-id="7d76d-154">명령을 선택할 때 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="7d76d-154">Please be careful when selecting commands.</span></span>
<span data-ttu-id="7d76d-155">예를 들어 Invoke-Expression은 사용자가 제한 없는 코드를 실행하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-155">For example, Invoke-Expression will allow users to run unrestricted code.</span></span>
<span data-ttu-id="7d76d-156">이 주제에 대한 자세한 내용은 명령을 제한하는 경우의 고려 사항 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d76d-156">For more discussion on this topic, check out the Considerations When Restricting Commands section.</span></span>

<span data-ttu-id="7d76d-157">각 명령을 검토한 후 다음을 제한하도록 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-157">After reviewing each command, you decide to restrict the following:</span></span>

1.  <span data-ttu-id="7d76d-158">`Set-ADUser`는 -Title 매개 변수를 사용하는 경우에만 실행되도록 허용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-158">`Set-ADUser` should only be allowed to run with the -Title parameter</span></span>

2.  <span data-ttu-id="7d76d-159">`Add-ADGroupMember` 및 `Remove-ADGroupMember`는 특정 그룹에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-159">`Add-ADGroupMember` and `Remove-ADGroupMember` should only work with certain groups</span></span>

### <a name="step-3-confirm-the-tasks-work-with-jea"></a><span data-ttu-id="7d76d-160">3단계: 작업이 JEA와 작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="7d76d-160">Step 3: Confirm the Tasks Work with JEA</span></span>
<span data-ttu-id="7d76d-161">이러한 cmdlet을 실제로 사용하는 것은 제한된 JEA 환경에서 간단하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-161">Actually using those cmdlets may not be straightforward in the restricted JEA environment.</span></span>
<span data-ttu-id="7d76d-162">JEA는 특히 사용자가 변수를 사용하지 못하게 하는 *NoLanguage* 모드에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-162">JEA runs in *NoLanguage* mode which, among other things, prevents users from using variables.</span></span>
<span data-ttu-id="7d76d-163">최종 사용자에게 원활한 환경을 보장하기 위해 몇 가지 사항을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-163">In order to ensure that end users have a smooth experience, it's important to check for a few things.</span></span>

<span data-ttu-id="7d76d-164">예를 들어 `Set-ADAccountPassword`를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-164">As an example, consider `Set-ADAccountPassword`.</span></span>
<span data-ttu-id="7d76d-165">-NewPassword 매개 변수에는 보안 문자열이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-165">The -NewPassword parameter requires a secure string.</span></span>
<span data-ttu-id="7d76d-166">흔히 사용자는 보안 문자열을 만들어 변수로 전달합니다(아래 참조).</span><span class="sxs-lookup"><span data-stu-id="7d76d-166">Often, users create a secure string and pass it in as a variable (as below):</span></span>

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

<span data-ttu-id="7d76d-167">그러나 *NoLanguage* 모드에서는 변수를 사용하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-167">However, *NoLanguage* mode prevents the usage of variables.</span></span>
<span data-ttu-id="7d76d-168">두 가지 방법으로 이 제한을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-168">You can get around this restriction in two ways:</span></span>

1.  <span data-ttu-id="7d76d-169">사용자가 변수를 할당하지 않고 명령을 실행하도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-169">You can require users run the command without assigning variables.</span></span>
<span data-ttu-id="7d76d-170">이렇게 구성하기는 쉽지만 끝점을 사용하는 운영자에게 어려움을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-170">This is easy to configure, but can be painful for the operators using the endpoint.</span></span>
<span data-ttu-id="7d76d-171">암호를 다시 설정할 때마다 다음과 같이 입력하고 싶은 사람이 누가 있을까요?</span><span class="sxs-lookup"><span data-stu-id="7d76d-171">Who wants to type this out every time you reset a password?</span></span>
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  <span data-ttu-id="7d76d-172">최종 사용자에게 노출하는 스크립트나 함수에 복잡한 사항을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-172">You can wrap the complexity in a script or a function that you expose to end users.</span></span>
<span data-ttu-id="7d76d-173">노출하는 스크립트와 함수는 제한 없는 컨텍스트에서 실행됩니다. 어떠한 문제도 없이 변수를 사용하고 다른 명령을 호출하는 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-173">Scripts and functions that you expose run in an unrestricted context; you can write functions that use variables and call other commands without any issue.</span></span>
<span data-ttu-id="7d76d-174">이 방법은 최종 사용자 환경을 간소화하고, 오류를 방지하고, 필요한 PowerShell 지식을 줄이고, 실수로 노출하는 초과 기능을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-174">This approach simplifies the end user experience, prevents errors, reduces required PowerShell knowledge, and reduces unintentionally exposing excess functionality.</span></span>
<span data-ttu-id="7d76d-175">유일한 단점은 함수 작성 및 유지 관리의 비용입니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-175">The only downside is the cost of authoring and maintaining the function.</span></span>

### <a name="aside-adding-a-function-to-your-module"></a><span data-ttu-id="7d76d-176">참고: 모듈에 함수 추가</span><span class="sxs-lookup"><span data-stu-id="7d76d-176">Aside: Adding a Function to your Module</span></span>
<span data-ttu-id="7d76d-177">두 번째 방법을 사용하는 경우 `Reset-ContosoUserPassword`라는 PowerShell 함수를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-177">Taking approach #2, you are going to write a PowerShell function called `Reset-ContosoUserPassword`.</span></span>
<span data-ttu-id="7d76d-178">이 함수는 사용자의 암호를 다시 설정할 때 발생해야 하는 모든 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-178">This function is going to do everything that needs to happen when you reset a user's password.</span></span>
<span data-ttu-id="7d76d-179">조직에서는 여기에 복잡한 고급 작업의 수행이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-179">In your organization, this may involve doing fancy and complicated things.</span></span>
<span data-ttu-id="7d76d-180">여기에서는 예를 보여 줄 뿐이므로 이 함수는 암호를 다시 설정하고 사용자가 로그온할 때 암호를 변경하도록 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-180">Because this is just an example, your command will just reset the password and require the user change the password at logon.</span></span>
<span data-ttu-id="7d76d-181">이 함수는 지난 섹션에서 만든 Contoso_AD_Module 모듈에 포함될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-181">We will put it in the Contoso_AD_Module module you made in the last section.</span></span>

1. <span data-ttu-id="7d76d-182">PowerShell ISE에서 "Contoso_AD_Module.psm1"을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-182">In PowerShell ISE, open "Contoso_AD_Module.psm1"</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. <span data-ttu-id="7d76d-183">Crtl+J를 눌러 코드 조각 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-183">Press Crtl+J to open the snippets menu.</span></span>

3. <span data-ttu-id="7d76d-184">"function"을 찾을 때까지 아래로 이동하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-184">Key down until you find "function" and press enter.</span></span>
<span data-ttu-id="7d76d-185">함수의 가장 기본적인 뼈대가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-185">This puts up a super basic skeleton of a function.</span></span>

4. <span data-ttu-id="7d76d-186">함수의 이름을 "Reset-ContosoUserPassword"로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-186">Rename the function "Reset-ContosoUserPassword".</span></span>  

5. <span data-ttu-id="7d76d-187">매개 변수 중 하나의 이름을 "Identity"로 변경하고 두 번째 매개 변수를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-187">Rename one of the parameters "Identity" and delete the second.</span></span>

6. <span data-ttu-id="7d76d-188">다음을 함수 본문에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-188">Copy the following into the body of the function.</span></span>
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. <span data-ttu-id="7d76d-189">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-189">Save the file.</span></span>
<span data-ttu-id="7d76d-190">최종적인 결과는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-190">You should end up with something that looks like this:</span></span>
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
<span data-ttu-id="7d76d-191">이제 사용자가 `Reset-ContosoUserPassword`를 호출하기만 하면 되고 보안 문자열을 인라인으로 만드는 구문을 기억할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-191">Now, your users can simply call `Reset-ContosoUserPassword` and not have to remember the syntax to create a secure string inline.</span></span>

## <a name="step-4-edit-the-role-capability-file"></a><span data-ttu-id="7d76d-192">4단계: 역할 기능 파일 편집</span><span class="sxs-lookup"><span data-stu-id="7d76d-192">Step 4: Edit the Role Capability File</span></span>
<span data-ttu-id="7d76d-193">[역할 기능 만들기](./role-capabilities.md#role-capability-creation) 섹션에서 비어 있는 역할 기능 파일을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-193">In the [Role Capability Creation](./role-capabilities.md#role-capability-creation) section, you created a blank Role Capability file.</span></span>
<span data-ttu-id="7d76d-194">이 섹션에서는 해당 파일에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-194">In this section, you will fill in the values in that file.</span></span>

<span data-ttu-id="7d76d-195">PowerShell ISE에서 역할 기능 파일을 열어 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-195">Start by opening the role capability file in PowerShell ISE.</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
<span data-ttu-id="7d76d-196">다음과 같이 변경하여 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-196">Update the file with the following changes:</span></span>
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

<span data-ttu-id="7d76d-197">위에서 몇 가지 사항에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-197">There are a few things to note about the above:</span></span>
1.  <span data-ttu-id="7d76d-198">PowerShell에서 역할 기능에 필요한 모듈을 자동으로 로드하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-198">PowerShell will attempt to auto-load the modules needed for your Role Capability.</span></span>
<span data-ttu-id="7d76d-199">모듈이 자동으로 로드되지 않는 문제가 발생하는 경우 "ModulesToImport" 필드에서 모듈 이름을 명시적으로 나열해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-199">You may need to explicitly list module names in the "ModulesToImport" field if you notice problems with a module not being autoloaded.</span></span>

2.  <span data-ttu-id="7d76d-200">명령이 cmdlet인지, 아니면 함수인지 모르겠는 경우 `Get-Command`를 실행하고 "CommandType" 속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-200">If you aren't sure if a command is a cmdlet or a function, run `Get-Command` and look at the "CommandType" property</span></span>

3.  <span data-ttu-id="7d76d-201">ValidatePattern은 허용 가능한 값 집합을 정의하기가 쉽지 않은 경우 정규식을 사용하여 매개 변수 인수를 제한할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-201">The ValidatePattern allows you to use a regular expression to restrict parameter arguments if it is not easy to define a set of allowable values.</span></span>
<span data-ttu-id="7d76d-202">단일 매개 변수에 대해 ValidatePattern과 ValidateSet을 둘 다 정의할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-202">You cannot define both a ValidatePattern and ValidateSet for a single parameter.</span></span>

## <a name="step-5-register-a-new-session-configuration"></a><span data-ttu-id="7d76d-203">5단계: 새 세션 구성 등록</span><span class="sxs-lookup"><span data-stu-id="7d76d-203">Step 5: Register a new Session Configuration</span></span>
<span data-ttu-id="7d76d-204">다음으로, "JEA_NonAdmin_HelpDesk" AD 그룹의 구성원에게 역할 기능을 노출할 새로운 세션 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-204">Next, you will create a new session configuration file that will expose your Role Capability to members of the "JEA_NonAdmin_HelpDesk" AD group.</span></span>

<span data-ttu-id="7d76d-205">PowerShell ISE에서 비어 있는 새 세션 구성 파일을 만들고 열어서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-205">Start by creating and opening a new blank Session Configuration file in PowerShell ISE.</span></span>
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
<span data-ttu-id="7d76d-206">PSSC 파일에서 다음 필드를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-206">Modify the following fields in the PSSC file.</span></span>
<span data-ttu-id="7d76d-207">자신의 환경에서 작업하는 경우 "CONTOSO\JEA_NonAdmins_Helpdesk"를 관리자가 아닌 자신의 사용자 또는 그룹으로 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-207">If you are working in your own environment, you should replace "CONTOSO\JEA_NonAdmins_Helpdesk" with your own non-administrator user or group.</span></span>
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
<span data-ttu-id="7d76d-208">세션 구성을 저장하고 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-208">Save and register the Session Configuration</span></span>
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## <a name="test-it-out"></a><span data-ttu-id="7d76d-209">테스트</span><span class="sxs-lookup"><span data-stu-id="7d76d-209">Test It Out!</span></span>
<span data-ttu-id="7d76d-210">관리자가 아닌 사용자의 자격 증명을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-210">Get your non-administrator user credentials:</span></span>
```PowerShell
$HelpDeskCred = Get-Credential
```
<span data-ttu-id="7d76d-211">[사용자 및 그룹 설정](creating-a-domain-controller.md#set-up-users-and-groups) 섹션을 따른 경우 자격 증명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-211">If you followed the [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) section, the credentials will be:</span></span>
-   <span data-ttu-id="7d76d-212">사용자 이름 = "HelpDeskUser"</span><span class="sxs-lookup"><span data-stu-id="7d76d-212">Username = "HelpDeskUser"</span></span>
-   <span data-ttu-id="7d76d-213">암호 = "pa$$w0rd"</span><span class="sxs-lookup"><span data-stu-id="7d76d-213">Password = "pa$$w0rd"</span></span>

<span data-ttu-id="7d76d-214">비관리자 자격 증명을 사용하여 ADHelpdesk 끝점에 원격으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-214">Remote into the ADHelpdesk endpoint using the non-admin credential:</span></span>
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
<span data-ttu-id="7d76d-215">Set-ADUser를 사용하여 사용자의 직함을 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-215">Use Set-ADUser to reset a user's title.</span></span>
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
<span data-ttu-id="7d76d-216">직함이 변경되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-216">Verify that the title has changed.</span></span>
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
<span data-ttu-id="7d76d-217">이제 Add-ADGroupMember를 사용하여 TestGroup에 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-217">Now, use Add-ADGroupMember to add a user to the TestGroup.</span></span>
<span data-ttu-id="7d76d-218">참고: TestGroup을 미리 만들어 놓아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-218">Note: make sure you've created the TestGroup beforehand.</span></span>
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
<span data-ttu-id="7d76d-219">세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-219">Exit the session:</span></span>
```PowerShell
Exit-PSSession
```
## <a name="key-concepts"></a><span data-ttu-id="7d76d-220">주요 개념</span><span class="sxs-lookup"><span data-stu-id="7d76d-220">Key Concepts</span></span>
<span data-ttu-id="7d76d-221">**NoLanguage 모드**: PowerShell이 "NoLanguage" 모드에 있는 경우 사용자는 명령을 실행할 수만 있고 언어 요소를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-221">**NoLanguage Mode**: When PowerShell is in "NoLanguage" mode, users may only run commands; they cannot use any language elements.</span></span>
<span data-ttu-id="7d76d-222">자세한 내용은 `Get-Help about_Language_Modes`를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d76d-222">For more information, run `Get-Help about_Language_Modes`.</span></span>

<span data-ttu-id="7d76d-223">**PowerShell 함수**: PowerShell 함수는 이름으로 호출할 수 있는 PowerShell 코드 조각입니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-223">**PowerShell Functions**: PowerShell functions are bits of PowerShell code that you can call by name.</span></span>
<span data-ttu-id="7d76d-224">자세한 내용은 `Get-Help about_Functions`를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d76d-224">For more information, run `Get-Help about_Functions`.</span></span>

<span data-ttu-id="7d76d-225">**ValidateSet/ValidatePattern**: 명령을 노출할 때 특정 매개 변수에 대한 유효한 인수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-225">**ValidateSet/ValidatePattern**: When exposing a command, you can restrict valid arguments for specific parameters.</span></span>
<span data-ttu-id="7d76d-226">ValidateSet은 유효한 인수의 특정 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-226">A ValidateSet is a specific list of valid arguments.</span></span>
<span data-ttu-id="7d76d-227">ValidatePattern은 해당 매개 변수에 대한 인수가 일치해야 하는 정규식입니다.</span><span class="sxs-lookup"><span data-stu-id="7d76d-227">A ValidatePattern is a regular expression that the arguments for that parameter must match.</span></span>

