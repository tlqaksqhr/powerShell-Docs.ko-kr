---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Command
ms.openlocfilehash: 26ddf4824816db245131a0fc95b7d2a88bef8f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="find-command"></a><span data-ttu-id="80870-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="80870-103">Find-Command</span></span>

<span data-ttu-id="80870-104">모듈에서 PowerShell 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="80870-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="80870-105">설명</span><span class="sxs-lookup"><span data-stu-id="80870-105">Description</span></span>
<span data-ttu-id="80870-106">Find-Command cmdlet은 cmdlet, 별칭, 함수 및 워크플로와 같은 PowerShell 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="80870-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="80870-107">Find-Command는 등록된 리포지토리에서 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="80870-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="80870-108">이 cmdlet은 찾은 각 명령에 대해 PSGetCommandInfo 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80870-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="80870-109">명령이 포함된 모듈을 설치하려면 Install-Module cmdlet에 PSGetCommandInfo 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80870-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="80870-110">Find-Command는 버전 매개 변수(MinimumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80870-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="80870-111">이러한 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80870-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="80870-112">이 버전 매개 변수는 와일드카드 없이 단일 모듈 이름과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80870-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="80870-113">RequiredVersion 매개 변수를 지정하지 않으면 Find-Command는 지정된 최소 버전과 같거나 그 이상인 최신 버전의 모듈 또는 최소 버전이 지정되지 않은 경우 최신 버전의 모듈을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80870-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="80870-114">RequiredVersion 매개 변수를 지정하면 Find-Command는 지정된 버전과 정확하게 일치하는 버전의 모듈만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80870-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="80870-115">Find-Command는 -Tag 매개 변수를 사용하여 모듈 메타데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80870-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="80870-116">Find-Command는 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80870-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="80870-117">Find-Command는 등록된 모든 또는 일부 리포지토리의 모듈을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80870-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="80870-118">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="80870-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="80870-119">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="80870-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="80870-120">Find-Command</span><span class="sxs-lookup"><span data-stu-id="80870-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="80870-121">예제 명령</span><span class="sxs-lookup"><span data-stu-id="80870-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```