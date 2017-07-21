---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Module
ms.openlocfilehash: 296c5c5ffc6f1e12da0162237e562b13b3679110
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="save-module"></a><span data-ttu-id="bdcbf-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="bdcbf-103">Save-Module</span></span>

<span data-ttu-id="bdcbf-104">모듈을 설치하지 않고 로컬에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bdcbf-104">Saves a module locally without installing it.</span></span>

## <a name="description"></a><span data-ttu-id="bdcbf-105">설명</span><span class="sxs-lookup"><span data-stu-id="bdcbf-105">Description</span></span>

<span data-ttu-id="bdcbf-106">Save-Module cmdlet은 검사를 위해 지정된 리포지토리의 모듈을 로컬에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bdcbf-106">The Save-Module cmdlet saves a module locally from the specified repository for inspection.</span></span> <span data-ttu-id="bdcbf-107">모듈이 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdcbf-107">The module is not installed.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="bdcbf-108">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="bdcbf-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Save-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="bdcbf-109">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="bdcbf-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="bdcbf-110">Save-Module</span><span class="sxs-lookup"><span data-stu-id="bdcbf-110">Save-Module</span></span>](http://go.microsoft.com/fwlink/?LinkId=531351)

## <a name="example-commands"></a><span data-ttu-id="bdcbf-111">예제 명령</span><span class="sxs-lookup"><span data-stu-id="bdcbf-111">Example commands</span></span>

```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3


# Find a command and save its module
# This command finds the specified command, and then passes it to Save-Module to save it to the C:\temp folder.
Find-Command -Name "Get-NestedRequiredModule4" -Repository "INT" | Save-Module -Path "C:\temp\" -Verbose


# Save the role capability modules by piping the Find-RoleCapability output to Save-Module cmdlet.
Find-RoleCapability -Name Maintenance,MyJeaRole | Save-Module -Path C:\MyModulesPath

```

