---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "웹 액세스 cmdlet"
ms.technology: powershell
ms.openlocfilehash: 54821c318b165461ec613678a39c4e3b500dfd0e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="eaced-103">Windows PowerShell 웹 액세스 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eaced-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="eaced-104">이 참조는 모든 Windows PowerShell® 웹 액세스 특정 cmdlet에 대한 cmdlet 설명 및 구문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="eaced-105">cmdlet은 cmdlet의 시작 부분에 있는 동사에 따라 사전순으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="eaced-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="eaced-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="eaced-107">새로운 권한 부여 규칙을 Windows PowerShell® 웹 액세스 권한 부여 규칙 집합에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="eaced-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="eaced-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="eaced-109">일련의 Windows PowerShell 웹 액세스 권한 부여 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="eaced-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="eaced-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="eaced-111">IIS에서 Windows PowerShell 웹 액세스 웹 응용 프로그램을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="eaced-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="eaced-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="eaced-113">지정된 권한 부여 규칙을 Windows PowerShell 웹 액세스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="eaced-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="eaced-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="eaced-115">권한 부여 규칙을 테스트하여 특정 사용자, 컴퓨터, 끝점 액세스 요청이 인증되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="eaced-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="eaced-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="eaced-117">IIS에서 Windows PowerShell 웹 응용 프로그램을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="eaced-118">**참고**:</span><span class="sxs-lookup"><span data-stu-id="eaced-118">**Note**:</span></span>
>
><span data-ttu-id="eaced-119">사용 가능한 모든 cmdlet을 나열하려면 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="eaced-120">`Get-Command –Module PowerShellWebAccess` cmdlet</span><span class="sxs-lookup"><span data-stu-id="eaced-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="eaced-121">cmdlet 또는 해당 구문에 대한 자세한 내용을 보려면 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-121">For more information about, or for the syntax of, any of the cmdlets, use:</span></span>  
<span data-ttu-id="eaced-122">`Get-Help `*&lt;cmdlet name&gt;*</span><span class="sxs-lookup"><span data-stu-id="eaced-122">`Get-Help `*&lt;cmdlet name&gt;*</span></span>  
<span data-ttu-id="eaced-123">여기서 *&lt;cmdlet name&gt;*은 알아보려는 cmdlet의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-123">where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="eaced-124">자세한 내용을 보려면 다음 cmdlet 중 하나를 실행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaced-124">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="eaced-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="eaced-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="eaced-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="eaced-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="eaced-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="eaced-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="eaced-128">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="eaced-128">More Information</span></span>

<span data-ttu-id="eaced-129">PowerShell 웹 액세스에 대한 자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eaced-129">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="eaced-130">Windows PowerShell 웹 액세스 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="eaced-130">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)

