---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Update-ModuleManifest
ms.openlocfilehash: ce3f6f173535d98648eb51adb1dbf84764e4f434
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="update-modulemanifest"></a><span data-ttu-id="d46de-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="d46de-103">Update-ModuleManifest</span></span>
<span data-ttu-id="d46de-104">모듈 매니페스트 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-104">Updates a module manifest file.</span></span>

## <a name="description"></a><span data-ttu-id="d46de-105">설명</span><span class="sxs-lookup"><span data-stu-id="d46de-105">Description</span></span>

<span data-ttu-id="d46de-106">Update-ModuleManifest cmdlet은 모듈 매니페스트(.psd1) 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-106">The Update-ModuleManifest cmdlet updates a module manifest (.psd1) file.</span></span>

### <a name="notes"></a><span data-ttu-id="d46de-107">참고</span><span class="sxs-lookup"><span data-stu-id="d46de-107">Notes</span></span>
    - <span data-ttu-id="d46de-108">DscResourcesToExport는 최신 PowerShell 버전 5.0에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-108">DscResourcesToExport is only supported on the latest PowerShell version 5.0.</span></span> <span data-ttu-id="d46de-109">더 낮은 버전의 PowerShell에서 실행하고 있는 경우 필드를 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-109">We won’t be able to update the field if you are running on lower versions of PowerShell.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="d46de-110">Cmdlet 구문</span><span class="sxs-lookup"><span data-stu-id="d46de-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="d46de-111">Cmdlet 온라인 도움말 참조</span><span class="sxs-lookup"><span data-stu-id="d46de-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="d46de-112">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="d46de-112">Update-ModuleManifest</span></span>](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a><span data-ttu-id="d46de-113">예제 명령</span><span class="sxs-lookup"><span data-stu-id="d46de-113">Example commands</span></span>

<span data-ttu-id="d46de-114">이 새로운 cmdlet을 사용하여 입력 속성 값으로 매니페스트 파일을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-114">This new cmdlet is used to help update manifest file with input property values.</span></span> <span data-ttu-id="d46de-115">이 cmdlet은 New-ModuleManifest에서 사용하는 모든 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-115">It takes all parameters that New-ModuleManifest does.</span></span>

<span data-ttu-id="d46de-116">많은 모듈 작성자가 FunctionsToExport, CmdletsToExport 등의 내보낸 값에 “\*”를 지정하려고 함을 알 수 있습니다. PowerShell 갤러리에 모듈을 게시하는 동안 지정되지 않은 함수 및 명령은 갤러리에 제대로 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-116">We notice that a lot of module authors would like to specify “\*” in exported values such as FunctionsToExport, CmdletsToExport, etc. During module publishing to PowerShell Gallery, unspecified functions and commands will not be populated properly onto the Gallery.</span></span> <span data-ttu-id="d46de-117">따라서 모듈 작성자가 적절한 값으로 매니페스트를 업데이트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-117">Therefore, we suggest module authors update their manifests with proper values.</span></span>

<span data-ttu-id="d46de-118">속성을 내보낸 모듈이 있는 경우 Update-ModuleManifest에서 내보낸 함수, cmdlet, 변수 등의 정보로 지정된 매니페스트 파일을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-118">If you have modules that have exported properties, Update-ModuleManifest will fill the specified manifest file with information from exported functions, cmdlets, variables etc:</span></span>
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

<span data-ttu-id="d46de-119">Update-ModuleManifest 후:</span><span class="sxs-lookup"><span data-stu-id="d46de-119">After Update-ModuleManifest:</span></span>
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

<span data-ttu-id="d46de-120">각 모듈의 경우 연결된 메타데이터 필드도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-120">For each module, there are also metadata fields associated with it.</span></span> <span data-ttu-id="d46de-121">PowrShell 갤러리에 메타데이터를 올바르게 표시하려면 Update-ModuleManifest를 사용하여 PrivateData 아래의 해당 필드를 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-121">In order to display metadata properly on PowrShell Gallery, you can use Update-ModuleManifest to populate those fields under PrivateData.</span></span>

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

<span data-ttu-id="d46de-122">매니페스트 파일 템플릿의 PrivateData 해시 테이블에는 다음과 같은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d46de-122">PrivateData hashtable from the manifest file template has the following properties</span></span>

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''
    
        # A URL to the main website for this project.
        # ProjectUri = ''
        
        # A URL to an icon representing this module.
        # IconUri = ''
        
        # ReleaseNotes of this module
        # ReleaseNotes = ''
        
        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```

