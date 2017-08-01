---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "일반적인 역할 기능 문제"
ms.technology: powershell
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
### <a name="common-role-capability-pitfalls"></a><span data-ttu-id="c0d02-103">일반적인 역할 기능 문제</span><span class="sxs-lookup"><span data-stu-id="c0d02-103">Common Role Capability Pitfalls</span></span>
<span data-ttu-id="c0d02-104">이 프로세스를 직접 진행할 때 몇 가지 일반적인 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d02-104">You may run into a few common pitfalls if you go through this process yourself.</span></span>
<span data-ttu-id="c0d02-105">새 끝점을 수정하거나 만들 때 이러한 문제를 식별하고 수정하는 방법을 설명하는 간단한 지침은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d02-105">Here is a quick guide explaining how to identify and remediate these issues when modifying or creating a new endpoint:</span></span>

#### <a name="functions-vs-cmdlets"></a><span data-ttu-id="c0d02-106">함수와 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0d02-106">Functions vs. Cmdlets</span></span>
<span data-ttu-id="c0d02-107">PowerShell에서 작성된 PowerShell 명령이 PowerShell 함수이고,</span><span class="sxs-lookup"><span data-stu-id="c0d02-107">PowerShell commands written in PowerShell are PowerShell functions.</span></span>
<span data-ttu-id="c0d02-108">특수화된 .NET 클래스로 작성된 PowerShell 명령이 PowerShell cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d02-108">PowerShell commands written as specialized .NET classes are PowerShell cmdlets.</span></span>
<span data-ttu-id="c0d02-109">`Get-Command`를 실행하여 명령 유형을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d02-109">You can check the command type by running `Get-Command`.</span></span>

#### <a name="visibleproviders"></a><span data-ttu-id="c0d02-110">VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="c0d02-110">VisibleProviders</span></span>
<span data-ttu-id="c0d02-111">명령에 필요한 공급자를 노출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d02-111">You will need to expose any providers your commands need.</span></span>
<span data-ttu-id="c0d02-112">가장 일반적인 공급자는 FileSystem 공급자이지만 레지스트리 공급자 등의 다른 공급자도 노출해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d02-112">The most common is the FileSystem provider, but you may also need to expose others, like the Registry provider.</span></span>
<span data-ttu-id="c0d02-113">공급자에 대한 소개는 [Hey, Scripting Guy 블로그 게시물](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0d02-113">For an introduction to providers, check out this [Hey, Scripting Guy blog post](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span></span>
<span data-ttu-id="c0d02-114">공급자를 노출할 때 JEA 세션에서 공급자를 직접 노출하는 대신 기본 공급자와 작동하는 함수를 직접 정의하는 것이 효과적인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d02-114">Be careful when exposing providers -- often, it is better to define your own function that works with the underlying providers than to directly expose the provider in a JEA session.</span></span>
<span data-ttu-id="c0d02-115">이러한 방식으로 사용자가 파일, 레지스트리 키 등을 사용하여 작업하도록 계속 허용할 수 있지만 사용자 지정 유효성 검사 논리를 사용하여 작업할 수 있는 파일 및 레지스트리 키 **항목**에 대한 제어를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d02-115">This way, you can still allow users to work with files, registry keys, etc. but retain control over **which** files and registry keys they can work with using custom validation logic.</span></span>

