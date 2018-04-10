---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="7a9f5-102">PowerShell 리포지토리 등록</span><span class="sxs-lookup"><span data-stu-id="7a9f5-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="7a9f5-103">내부 리포지토리에 대해 작동하도록 PowerShellGet을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9f5-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="7a9f5-104">이렇게 구성하려면 다음과 같은 추가 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9f5-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="7a9f5-105">Register-PSRepository: 현재 사용자에 대해 리포지토리를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9f5-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="7a9f5-106">Unregister-PSRepository: 현재 사용자에 대해 등록된 리포지토리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9f5-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="7a9f5-107">Set-PSRepository: 등록된 리포지토리에 대해 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9f5-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="7a9f5-108">Get-PSRepository: 현재 사용자에 대해 등록된 리포지토리를 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a9f5-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="7a9f5-109">리포지토리를 등록한 후에는 Find-Module 및 Install-Module을 사용하여 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9f5-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```