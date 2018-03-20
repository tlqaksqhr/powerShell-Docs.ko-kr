---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: "PowerShellGet 모듈 가져오기"
ms.openlocfilehash: 7224cf5d71b98d51ca22c47a00ca382d34864bfb
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2018
---
<a name="get-powershellget-module"></a><span data-ttu-id="0a036-103">PowerShellGet 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="0a036-103">Get PowerShellGet Module</span></span>
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="0a036-104">PowerShellGet은 다음 릴리스에서 제공되는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-104">PowerShellGet is an in-box module in the following releases</span></span>
- <span data-ttu-id="0a036-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) 이상</span><span class="sxs-lookup"><span data-stu-id="0a036-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="0a036-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) 이상</span><span class="sxs-lookup"><span data-stu-id="0a036-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="0a036-107">[WMF(Windows Management Framework) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 이상</span><span class="sxs-lookup"><span data-stu-id="0a036-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="0a036-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="0a036-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="0a036-109">PowerShell 버전 3.0 및 4.0용 PowerShellGet 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="0a036-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>
- [<span data-ttu-id="0a036-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="0a036-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="0a036-111">PowerShell 갤러리에서 최신 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="0a036-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="0a036-112">PowerShellGet을 업데이트하기 전에 항상 최신 Nuget 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="0a036-113">이렇게 하려면 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-113">To do that, run the following in an elevated PowerShell session.</span></span>
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="0a036-114">PowerShell 5.0 이상이 설치된 시스템에 최신 PowerShellGet을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span> 
- <span data-ttu-id="0a036-115">Windows 10, Windows Server 2016, WMF 5.0/5.1이 설치된 시스템 또는 PowerShell 6이 설치된 시스템에서 PowerShellGet을 설치하려면 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="0a036-116">Update-Module을 사용하여 최신 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-116">Use Update-Module to get newer versions.</span></span>
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="0a036-117">PowerShell 3 또는 PowerShell 4를 실행하며 [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)를 설치한 시스템</span><span class="sxs-lookup"><span data-stu-id="0a036-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="0a036-118">관리자 권한 PowerShell 세션에서 아래의 PowerShellGet cmdlet을 사용하여 로컬 디렉터리에 모듈을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="0a036-119">PowerShellGet 및 PackageManagment 모듈이 다른 프로세스에서 로드되지 않았음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="0a036-120">`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 및 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 폴더의 내용을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="0a036-121">관리자 권한으로 PS 콘솔을 다시 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0a036-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force