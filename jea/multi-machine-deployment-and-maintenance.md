---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "다중 컴퓨터 배포 및 유지 관리"
ms.technology: powershell
ms.openlocfilehash: 8117d0d12c062b460cb7117b54c138c8db5a1d0c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="multi-machine-deployment-and-maintenance"></a><span data-ttu-id="d4061-103">다중 컴퓨터 배포 및 유지 관리</span><span class="sxs-lookup"><span data-stu-id="d4061-103">Multi-machine Deployment and Maintenance</span></span>
<span data-ttu-id="d4061-104">이 시점에서 JEA를 로컬 시스템에 여러 번 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-104">At this point, you have deployed JEA to local systems several times.</span></span>
<span data-ttu-id="d4061-105">프로덕션 환경은 두 대 이상의 컴퓨터로 구성될 수 있으므로 각 컴퓨터에서 반복해야 하는 배포 프로세스의 중요 단계를 연습해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-105">Because your production environment probably consists of more than one machine, it's important to walk through the critical steps in the deployment process that must be repeated on each machine.</span></span>

## <a name="high-level-steps"></a><span data-ttu-id="d4061-106">상위 수준 단계:</span><span class="sxs-lookup"><span data-stu-id="d4061-106">High Level Steps:</span></span>
1.  <span data-ttu-id="d4061-107">역할 기능이 포함된 모듈을 각 노드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-107">Copy your modules (with Role Capabilities) to each node.</span></span>
2.  <span data-ttu-id="d4061-108">세션 구성 파일을 각 노드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-108">Copy your session configuration files to each node.</span></span>
3.  <span data-ttu-id="d4061-109">세션 구성과 함께 `Register-PSSessionConfiguration`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-109">Run `Register-PSSessionConfiguration` with your session configuration.</span></span>
4.  <span data-ttu-id="d4061-110">세션 구성과 도구 키트의 복사본을 안전한 위치에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-110">Keep a copy of your session configuration and toolkits in a secure location.</span></span>
<span data-ttu-id="d4061-111">수정 작업을 할 때 "단일 데이터 소스(single source of truth)"를 마련하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-111">As you make modifications, it's good to have a "single source of truth."</span></span>

## <a name="example-script"></a><span data-ttu-id="d4061-112">예제 스크립트</span><span class="sxs-lookup"><span data-stu-id="d4061-112">Example Script</span></span>
<span data-ttu-id="d4061-113">배포를 위한 예제 스크립트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-113">Here's an example script for deployment.</span></span>
<span data-ttu-id="d4061-114">해당 환경에서 이 스크립트를 사용하려면 실제 파일 공유 및 모듈의 이름/경로를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-114">To use it in your environment, you'll have to use the names/paths of real file shares and modules.</span></span>
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## <a name="modifying-capabilities"></a><span data-ttu-id="d4061-115">기능 수정</span><span class="sxs-lookup"><span data-stu-id="d4061-115">Modifying Capabilities</span></span>
<span data-ttu-id="d4061-116">많은 컴퓨터를 처리할 때 수정 내용을 일관된 방식으로 배포하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-116">When dealing with many machines, it's important that modifications are rolled out in a consistent manner.</span></span>
<span data-ttu-id="d4061-117">JEA에 DSC 리소스가 있으면 환경이 동기화되도록 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-117">Once JEA has a DSC Resource, this will help ensure your environment is in sync.</span></span>
<span data-ttu-id="d4061-118">그 전까지는 세션 구성의 마스터 복사본을 보관하고 수정할 때마다 다시 배포하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-118">Until that time, we highly recommend you keep a master copy of your session configurations and re-deploy each time you make a modification.</span></span>

## <a name="removing-capabilities"></a><span data-ttu-id="d4061-119">기능 제거</span><span class="sxs-lookup"><span data-stu-id="d4061-119">Removing Capabilities</span></span>
<span data-ttu-id="d4061-120">시스템에서 JEA 구성을 제거하려면 각 컴퓨터에서 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4061-120">To remove your JEA configuration from your systems, use the following command on each machine:</span></span>
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```

