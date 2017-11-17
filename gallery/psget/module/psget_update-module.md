---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Update-Module
ms.openlocfilehash: 343c296dad2a3df35f13393b3796a1d484f5f535
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="update-module"></a><span data-ttu-id="3fe9a-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="3fe9a-103">Update-Module</span></span>

<span data-ttu-id="3fe9a-104">온라인 갤러리에서 지정된 모듈의 최신 버전을 로컬 컴퓨터에 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="3fe9a-105">설명</span><span class="sxs-lookup"><span data-stu-id="3fe9a-105">Description</span></span>

<span data-ttu-id="3fe9a-106">Update-Module cmdlet은 로컬 컴퓨터에서 Install-Module을 실행하여 온라인 갤러리에서 설치된 Windows PowerShell 모듈의 최신 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="3fe9a-107">필요한 버전을 지정하지 않으면 기본적으로 온라인 갤러리에서 사용할 수 있는 지정된 모듈의 최신 버전이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="3fe9a-108">모듈 이름을 지정하여 설치된 기존 모듈을 업데이트할 수 있습니다. Update-Module은 $env:PSModulePath에서 업데이트할 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="3fe9a-109">Name 매개 변수 없이 Update-Module을 실행하면 로컬 컴퓨터에서 업데이트할 수 있는 모든 모듈이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="3fe9a-110">참고</span><span class="sxs-lookup"><span data-stu-id="3fe9a-110">Notes</span></span>

- <span data-ttu-id="3fe9a-111">이 cmdlet은 Windows PowerShell 3.0 이상 버전의 Windows PowerShell, Windows 7 또는 Windows 2008 R2 이상 버전의 Windows에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="3fe9a-112">Name 매개 변수를 사용하여 지정한 모듈이 Install-Module을 통해 설치되지 않은 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="3fe9a-113">Install-Module을 실행하여 온라인 갤러리에서 설치한 모듈에서만 Update-Module을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="3fe9a-114">Update-Module이 사용 중인 이진 파일을 업데이트하려고 하면 Update-Module에서 문제 프로세스를 식별하고, 프로세스를 중지한 후 Update-Module을 다시 시도하도록 사용자에게 알리는 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="3fe9a-115">PowerShell 5.0 이상 버전에서 Update-Module은 모듈을 업데이트할 때 최신(또는 지정된) 버전의 모듈을 추가하므로 이제 이전 버전과 최신 버전이 동일한 디렉터리에 나란히 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="3fe9a-116">해당 메시지를 표시하고 이러한 명령의 출력 예를 보여 주는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="3fe9a-117">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="3fe9a-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="3fe9a-118">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="3fe9a-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="3fe9a-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="3fe9a-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="3fe9a-120">예제 명령</span><span class="sxs-lookup"><span data-stu-id="3fe9a-120">Example commands</span></span>

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="3fe9a-121">종속성이 있는 TestDepWithNestedRequiredModules1 모듈을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe9a-121">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

