---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Get-PSRepository
ms.openlocfilehash: 97279a8ed0087c835fb924991484959cd7237016
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="get-psrepository"></a><span data-ttu-id="7ff92-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="7ff92-103">Get-PSRepository</span></span>

<span data-ttu-id="7ff92-104">컴퓨터에 등록된 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7ff92-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="7ff92-105">설명</span><span class="sxs-lookup"><span data-stu-id="7ff92-105">Description</span></span>

<span data-ttu-id="7ff92-106">Get-PSRepository cmdlet은 컴퓨터에서 현재 사용자에 대해 등록된 PowerShell 모듈 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7ff92-106">The Get-PSRepository cmdlet gets PowerShell module repositories that are registered for the current user on a computer.</span></span>

<span data-ttu-id="7ff92-107">등록된 각 리포지토리에 대해 Get-PSRepository는 PSRepository 개체를 반환하며, 필요에 따라 이 개체를 Unregister-PSRepository에 파이프하여 등록된 리포지토리를 등록 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ff92-107">For each registered repository, Get-PSRepository returns a PSRepository object which can optionally be piped to Unregister-PSRepository for unregistering a registered repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="7ff92-108">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="7ff92-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="7ff92-109">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="7ff92-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="7ff92-110">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="7ff92-110">Get-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a><span data-ttu-id="7ff92-111">예제 명령</span><span class="sxs-lookup"><span data-stu-id="7ff92-111">Example commands</span></span>

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```