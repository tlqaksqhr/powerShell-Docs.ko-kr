---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "블랙리스트에 올리기"
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
### <a name="on-blacklisting"></a><span data-ttu-id="7c37f-103">블랙리스트에 올리기</span><span class="sxs-lookup"><span data-stu-id="7c37f-103">On Blacklisting</span></span>
<span data-ttu-id="7c37f-104">JEA를 사용하여 작업해 본 후 명령을 블랙리스트에 올리는 것이 가능한지 궁금할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-104">After playing around with JEA, you may be wondering if it is possible to blacklist commands.</span></span>
<span data-ttu-id="7c37f-105">이는 이해할 수 있는 요청이지만 블랙리스트에 올리는 기능은 다음과 같은 이유로 JEA에 대해 현재 계획되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-105">This is an understandable request, but it is not currently planned for JEA for the following reasons:</span></span>

1.  <span data-ttu-id="7c37f-106">수행해야 하는 작업으로만 운영자를 제한하도록 JEA를 설계했습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-106">We designed JEA to limit operators to only the actions they need to do.</span></span>
<span data-ttu-id="7c37f-107">블랙 리스트는 이와 반대입니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-107">A blacklist is the opposite.</span></span>

2.  <span data-ttu-id="7c37f-108">PowerShell 명령 작성자는 JEA를 염두에 두고 PowerShell 명령을 설계하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-108">PowerShell command authors did not design PowerShell commands with the JEA in mind.</span></span>
<span data-ttu-id="7c37f-109">Windows Server 2016을 새로 설치한 경우 약 1520개의 명령을 즉시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-109">On a fresh install of Windows Server 2016, there are about 1520 commands immediately available.</span></span>
<span data-ttu-id="7c37f-110">이러한 명령에 대한 위협 모델에는 사용자가 권한이 더 많은 계정으로 명령을 실행할 것이라는 가능성이 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-110">The threat models for these commands did not include the possibility that a user would be running commands as a more privileged account.</span></span>
<span data-ttu-id="7c37f-111">예를 들어 특정 명령은 설계상 코드 주입을 고려합니다(예: 핵심 PowerShell 모듈의 Add-Type 및 Invoke-Command).</span><span class="sxs-lookup"><span data-stu-id="7c37f-111">For example, certain commands allow for code injection by design (e.g. Add-Type and Invoke-Command in the core PowerShell module).</span></span>
<span data-ttu-id="7c37f-112">JEA는 Microsoft에서 알고 있는 특정 명령을 노출할 때 경고할 수 있지만, Microsoft에서는 새로운 위협 모델을 기초로 Windows의 다른 모든 명령을 다시 평가하지는 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-112">JEA can warn you when you expose the specific commands we know about, but we have not re-assessed every other command in Windows based on the new threat model.</span></span>
<span data-ttu-id="7c37f-113">JEA를 통해 노출하는 명령의 기능을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-113">You must understand the capabilities of the commands you exposing through JEA.</span></span>  

3.  <span data-ttu-id="7c37f-114">또한 JEA가 코드 주입에 취약한 모든 명령을 차단한다고 해도 악의적인 사용자가 블랙 리스트에 있는 작업을 다른 관련 명령으로 수행할 수 없다는 보장은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-114">Furthermore, even if JEA blocked all commands with code-injection vulnerabilities, there is no guarantee that a malicious user would not be able to carry out a blacklisted action with another related command.</span></span>
<span data-ttu-id="7c37f-115">노출할 명령을 모두 이해하지 않는 한 특정 작업이 가능하지 않다고 보장하는 것은 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-115">Unless you understand all of the commands that you are exposing, it is impossible for you to guarantee that a certain action is not possible.</span></span>
<span data-ttu-id="7c37f-116">허용 목록을 사용하든 블랙 리스트를 사용하든 간에 노출할 명령을 이해하는 것은 사용자의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-116">The burden is on you to understand what commands you are exposing, whether they are using a whitelist or a blacklist.</span></span>
<span data-ttu-id="7c37f-117">블랙 리스트로 노출할 명령 수는 관리할 수 없으므로 JEA는 대신 허용 목록을 사용하여 구현되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7c37f-117">The number of commands a blacklist would expose is unmanageable, so JEA is implemented using whitelists instead.</span></span>

