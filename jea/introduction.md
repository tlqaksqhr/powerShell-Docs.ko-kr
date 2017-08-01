---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "소개"
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="introduction"></a><span data-ttu-id="7adb6-103">소개</span><span class="sxs-lookup"><span data-stu-id="7adb6-103">Introduction</span></span>

##  <a name="motivation"></a><span data-ttu-id="7adb6-104">**동기**</span><span class="sxs-lookup"><span data-stu-id="7adb6-104">**Motivation**</span></span>  
<span data-ttu-id="7adb6-105">누군가에게 시스템에 대한 액세스 권한을 부여하는 경우 해당 사용자에게 신뢰 경계를 확장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-105">When you grant someone privileged access to your systems, you extend your trust boundary to that person.</span></span>
<span data-ttu-id="7adb6-106">이는 위험하며 관리자가 공격 노출 영역이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-106">This is a risk -- administrators are an attack surface.</span></span>
<span data-ttu-id="7adb6-107">내부자 공격과 자격 증명 도난은 실제로 흔하게 벌어지는 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-107">Insider attacks and stolen credentials are both real and common.</span></span>

##  <a name="not-a-new-problem"></a><span data-ttu-id="7adb6-108">**새로운 문제가 아닙니다.**</span><span class="sxs-lookup"><span data-stu-id="7adb6-108">**Not a new problem**</span></span>  
<span data-ttu-id="7adb6-109">최소 권한의 원칙에 아주 익숙할 수도 있고, 특정 형태의 RBAC(역할 기반 액세스 제어)를 제공하는 응용 프로그램과 함께 RBAC를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-109">You are probably very familiar with the principle of least privilege, and you might use some form of role-based access control (RBAC) with applications that provide it.</span></span>
<span data-ttu-id="7adb6-110">그러나 이러한 솔루션의 유효성과 관리 효율성은 해당 솔루션의 넓은 범위와 부정확성에 따라 흔히 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-110">However, the effectiveness and manageability of these solutions are often limited by their broad scope and imprecision.</span></span>
<span data-ttu-id="7adb6-111">또한 RBAC 적용 범위에는 간격이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-111">Furthermore, there are gaps in RBAC coverage.</span></span>
<span data-ttu-id="7adb6-112">예를 들어 Windows에서 권한 있는 액세스는 주로 이진 스위치인데 Administrators 그룹에 사용자를 추가할 때 불필요한 권한을 부여할 수밖에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-112">For example, in Windows, privileged access is largely a binary switch, forcing you to give unnecessary permissions when adding users to the Administrators group.</span></span>

##  <a name="just-enough-administration-jea"></a><span data-ttu-id="7adb6-113">**JEA(Just Enough Administration)**</span><span class="sxs-lookup"><span data-stu-id="7adb6-113">**Just Enough Administration (JEA)**</span></span> 
<span data-ttu-id="7adb6-114">PowerShell 원격 기능을 통해 RBAC(역할 기반 액세스 제어) 플랫폼을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-114">Provides a role-based access control (RBAC) platform through PowerShell Remoting.</span></span>
<span data-ttu-id="7adb6-115">*JEA를 사용하면 관리자 권한을 부여하지 않고 특정 사용자가 서버에서 특정 관리 작업을 수행하도록 허용할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="7adb6-115">*It allows specific users to perform specific administrative tasks on servers without giving them administrator rights.*</span></span>
<span data-ttu-id="7adb6-116">이에 따라 기존 RBAC 솔루션 간의 간격이 채워지고 해당 설정의 관리가 단순화됩니다.</span><span class="sxs-lookup"><span data-stu-id="7adb6-116">This allows you to fill in the gaps between your existing RBAC solutions, and simplifies management of those settings.</span></span>

