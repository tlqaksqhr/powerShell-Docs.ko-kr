---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Unregister-PSRepository
ms.openlocfilehash: 91380210f262208fce39d596bd6c2ad05a819fbf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="unregister-psrepository"></a><span data-ttu-id="9cb4d-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="9cb4d-103">Unregister-PSRepository</span></span>

<span data-ttu-id="9cb4d-104">리포지토리 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9cb4d-104">Unregisters a repository.</span></span>

## <a name="description"></a><span data-ttu-id="9cb4d-105">설명</span><span class="sxs-lookup"><span data-stu-id="9cb4d-105">Description</span></span>

<span data-ttu-id="9cb4d-106">Unregister-PSRepository cmdlet은 현재 사용자에 대해 리포지토리 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9cb4d-106">The Unregister-PSRepository cmdlet unregisters a repository for the current user.</span></span>
- <span data-ttu-id="9cb4d-107">엔터프라이즈 및 연결이 끊긴 시나리오의 경우 PSGallery 리포지토리를 등록 취소하고 다시 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cb4d-107">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
- <span data-ttu-id="9cb4d-108">사용자는 다음을 실행하기만 하면 PSGallery를 다시 등록할 수 있습니다. `Register-PSRepository -Default`</span><span class="sxs-lookup"><span data-stu-id="9cb4d-108">Users can re-register the PSGallery by simply running `Register-PSRepository -Default`</span></span>
- <span data-ttu-id="9cb4d-109">PSGallery는 Publish-Module 및 Publish-Script cmdlet의 기본 게시 리포지토리이므로 등록된 리포지토리 목록에서 PSGallery를 사용할 수 없는 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9cb4d-109">Since PSGallery is the default publish repository in Publish-Module and Publish-Script cmdlets, an error will be thrown if PSGallery is not available in the registered repository list.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="9cb4d-110">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="9cb4d-110">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="9cb4d-111">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="9cb4d-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="9cb4d-112">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="9cb4d-112">Unregister-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a><span data-ttu-id="9cb4d-113">예제 명령</span><span class="sxs-lookup"><span data-stu-id="9cb4d-113">Example commands</span></span>

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a><span data-ttu-id="9cb4d-114">엔터프라이즈 및 연결이 끊긴 시나리오의 경우 PSGallery 리포지토리를 등록 취소하고 다시 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cb4d-114">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

