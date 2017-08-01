---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "이 가이드 전체에서 사용된 주요 개념"
ms.technology: powershell
ms.openlocfilehash: 873ab19fdf43ec4ac41cc546aa94b64fbc607984
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="key-concepts-used-throughout-this-guide"></a><span data-ttu-id="e99e0-103">이 가이드 전체에서 사용된 주요 개념</span><span class="sxs-lookup"><span data-stu-id="e99e0-103">Key Concepts Used Throughout This Guide</span></span>
<span data-ttu-id="e99e0-104">**JEA란 정확히 무엇인가요?**</span><span class="sxs-lookup"><span data-stu-id="e99e0-104">**What exactly is JEA?**</span></span>

<span data-ttu-id="e99e0-105">JEA는 역할 정의, 가상 계정 및 몇 가지 기타 개선 기능을 추가하여 관리 끝점을 잠그기 훨씬 쉽게 만드는 PowerShell [제한된 끝점](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx)의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-105">JEA is an extension of PowerShell [constrained endpoints](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) that adds in role definitions, virtual accounts, and several other improvements to make it even easier to lock down your management endpoints.</span></span>
<span data-ttu-id="e99e0-106">JEA 끝점은 PowerShell 세션 구성 파일과 하나 이상의 역할 기능 파일로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-106">A JEA endpoint consists of a PowerShell Session Configuration file and one or more Role Capability files.</span></span>

<span data-ttu-id="e99e0-107">**세션 구성 및 역할 기능 파일이란 무엇인가요?**</span><span class="sxs-lookup"><span data-stu-id="e99e0-107">**What are Session Configuration and Role Capability files?**</span></span>

<span data-ttu-id="e99e0-108">PowerShell 세션 구성 파일(.pssc)은 *누가* PowerShell 끝점에 연결할 수 있고 *어떻게* PowerShell 끝점이 구성되었는지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-108">PowerShell Session Configuration files (.pssc) define *who* can connect to a PowerShell endpoint and *how* it is configured.</span></span>
<span data-ttu-id="e99e0-109">이 파일에서 사용자 및 보안 그룹을 특정 관리 역할에 매핑하고 가상 계정 및 기록 정책과 같은 전역 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-109">This is where you would map users and security groups to specific management roles and configure global settings like virtual accounts and transcription policies.</span></span>
<span data-ttu-id="e99e0-110">세션 구성 파일은 각 컴퓨터에 한정되므로 원하는 경우 컴퓨터별로 액세스 권한을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-110">Session configuration files are specific to each machine, which allows you to control access on a per-machine basis if desired.</span></span>

<span data-ttu-id="e99e0-111">PowerShell 역할 기능 파일(.psrc)은 역할에 속한 사용자가 시스템에서 수행할 수 있는 *작업*을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-111">PowerShell Role Capability files (.psrc) define *what* users belonging to a role are able to do on the system.</span></span>
<span data-ttu-id="e99e0-112">여기서는 사용자가 JEA 세션에서 사용할 수 있는 cmdlet, 함수, 공급자 및 외부 프로그램을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-112">Here, you can restrict which cmdlets, functions, providers, and external programs a user may use in their JEA session.</span></span>
<span data-ttu-id="e99e0-113">역할 기능 파일은 처리되는 역할(DNS 관리자, 수준 1 지원 센터, 읽기 전용 인벤토리 감사 등)을 일반적으로 정의하며 PowerShell 모듈에 속하므로 사용자 환경과 다른 환경 간에 공유하기가 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-113">Role Capability files are often generic for the role being served (DNS admin, level 1 helpdesk, read-only inventory auditing, etc.) and belong to PowerShell modules, making it easy to share them across your environment and with others.</span></span>

<span data-ttu-id="e99e0-114">**JEA에서 가상 계정을 어떻게 활용하나요?**</span><span class="sxs-lookup"><span data-stu-id="e99e0-114">**How does JEA leverage virtual accounts?**</span></span>

<span data-ttu-id="e99e0-115">PowerShell 세션 구성 파일에서 가상 "실행" 계정을 사용하도록 JEA 세션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-115">In the PowerShell Session Configuration file, you can configure JEA sessions to use virtual "run as" accounts.</span></span>
<span data-ttu-id="e99e0-116">가상 계정은 특정 세션에서 연결하는 사용자에 대해 생성된 일회성 권한 있는 계정입니다. 이 세션의 컨텍스트에서 사용자의 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-116">Virtual accounts are one-time privileged accounts spun up for the specific connecting user in that specific session under which context the user's commands are executed.</span></span>
<span data-ttu-id="e99e0-117">가상 계정은 기본적으로 로컬 "Administrators" 보안 그룹에 속하지만 필요에 따라 지정한 보안 그룹에만 속하도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-117">Virtual accounts belong to the local "Administrators" security group by default, but can optionally be configured to only belong to security groups you specify.</span></span>

<span data-ttu-id="e99e0-118">**PowerShell 원격**: PowerShell 원격을 사용하면 원격 컴퓨터에 대해 PowerShell 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-118">**PowerShell Remoting**: PowerShell remoting allows you to run PowerShell commands against remote machines.</span></span>
<span data-ttu-id="e99e0-119">한 대 이상의 컴퓨터를 대상으로 작업하고 임시 또는 영구 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-119">You can operate against one or many computers, and use either temporary or persistent connections.</span></span>
<span data-ttu-id="e99e0-120">이 데모에서는 대화형 세션으로 로컬 컴퓨터에 원격으로 연결했습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-120">In this demo, you remoted into your local machine with an interactive session.</span></span>
<span data-ttu-id="e99e0-121">JEA는 PowerShell 원격을 통해 사용할 수 있는 기능을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-121">JEA restricts the functionality available through PowerShell remoting.</span></span>
<span data-ttu-id="e99e0-122">PowerShell 원격에 대한 자세한 내용을 보려면 `Get-Help about_Remote`를 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="e99e0-122">For more information about PowerShell remoting, run `Get-Help about_Remote`.</span></span>

<span data-ttu-id="e99e0-123">**"실행" 사용자**: JEA를 사용할 때 관리자가 아닌 사용자가 권한 있는 "가상 계정으로 실행"합니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-123">**"RunAs" User**: When using JEA, a non-administrator "runs as" a privileged "Virtual Account."</span></span>
<span data-ttu-id="e99e0-124">가상 계정은 원격 세션의 기간 동안만 지속됩니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-124">The Virtual Account only lasts the duration of the remote session.</span></span>
<span data-ttu-id="e99e0-125">즉, 가상 계정은 사용자가 끝점에 연결할 때 만들어지고 사용자가 세션을 종료할 때 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-125">That is to say, it is created when a user connects to the endpoint, and destroyed when the user ends the session.</span></span>
<span data-ttu-id="e99e0-126">기본적으로 가상 계정은 로컬 Administrators 그룹의 구성원이고,</span><span class="sxs-lookup"><span data-stu-id="e99e0-126">By default, the Virtual Account is a member of the local Administrators group.</span></span>
<span data-ttu-id="e99e0-127">도메인 컨트롤러에서는 Domain Admins의 구성원입니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-127">On a domain controller, it is a member of Domain Admins.</span></span>
<span data-ttu-id="e99e0-128">가상 계정은 만들어진 컴퓨터에 로컬이며 해당 컴퓨터 외부에서는 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-128">Virtual Accounts are local to the machine on which they are created, and do not have permissions outside of that machine.</span></span>
<span data-ttu-id="e99e0-129">즉, Active Directory에서 등록되어 있지 않습니다(RID가 할당되지 않음).</span><span class="sxs-lookup"><span data-stu-id="e99e0-129">This means that they are not registered in Active Directory (no RID is assigned).</span></span>
<span data-ttu-id="e99e0-130">또한 허용되는 명령/스크립트가 로컬 컴퓨터 외부의 리소스에 액세스하려는 경우 가상 계정 ID가 아니라 컴퓨터의 ID로 해당 리소스에 액세스하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-130">Additionally, if an allowed command/script tries to access resources outside of the local machine, it will be accessing those resources under the machine's identity, not the Virtual Account identity.</span></span>

<span data-ttu-id="e99e0-131">**"연결된" 사용자**: JEA 끝점에 연결되고 역할이 할당된 관리자가 아닌 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-131">**"Connected" User**: The non-administrator user who connects to the JEA endpoint and to whom roles are assigned.</span></span>
<span data-ttu-id="e99e0-132">이 사용자가 실행하는 모든 명령은 실행 사용자 또는 가상 계정의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e99e0-132">Any commands this user runs are run under the context of the RunAs User or virtual account.</span></span>

