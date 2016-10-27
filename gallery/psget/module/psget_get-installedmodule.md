---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: psget_get installedmodule
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 40a79a74117f28407758367f4e27b7ae26917078

---

# Get-InstalledModule

컴퓨터에 설치된 모듈을 가져옵니다.

## 설명

Get-InstalledModule cmdlet은 Install-Module cmdlet을 사용하여 설치된 컴퓨터에 설치된 PowerShell 모듈을 가져옵니다.

설치된 각 모듈에 대해 Get-InstalledModule은 PSRepositoryItemInfo 개체를 반환하며, 필요에 따라 이 개체를 Uninstall-Module에 파이프하여 설치된 모듈을 제거할 수 있습니다.

- Get-InstalledModule은 이름, 버전 매개 변수에 따라 설치된 모듈을 필터링할 수 있습니다.
- Get-InstalledModule은 버전 매개 변수(MinimumVersion, MaximumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.
  - 이러한 매개 변수는 MinmimumVersion 및 MaximumVersion을 제외하고 함께 사용할 수 없습니다.
  - 이 버전 매개 변수는 와일드카드 없이 단일 모듈 이름과 함께 사용해야 합니다.
  - RequiredVersion 매개 변수를 지정하지 않으면 Get-InstalledModule은 지정된 최소 버전과 같거나 그 이상인 최신 버전의 설치된 모듈 또는 최소 버전이 지정되지 않은 경우 최신 버전의 모듈을 반환합니다. 
  - RequiredVersion 매개 변수를 지정하면 Get-InstalledModule은 지정된 버전과 정확하게 일치하는 버전의 설치된 모듈만 반환합니다.

## Cmdlet 구문
```powershell
Get-Command -Name Get-InstalledModule -Module PowerShellGet -Syntax
```

## Cmdlet 온라인 도움말 참조

[Get-InstalledModule](http://go.microsoft.com/fwlink/?LinkId=526863)

## 예제 명령

```powershell

# Get all modules installed using PowerShellGet cmdlets
Get-InstalledModule

# Get a specific installed module
Get-InstalledModule DJoin

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        DJoin                               PSGallery            This is a PowerShell frontend to the DJOIN.exe c...

# Get installed module with wildcards
Get-InstalledModule -Name AzureRM*

# Get all versions of an installed module
Get-InstalledModule -Name AzureRM.Automation -AllVersions

# Get installed module with MinimumVersion
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0

# Get installed module with MaximumVersion
Get-InstalledModule -Name AzureRM.Automation -MaximumVersion 1.0.8

# Get installed module with version range
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0 -MaximumVersion 1.0.8

# Get installed module with RequiredVersion
Get-InstalledScript -Name AzureRM.Automation -RequiredVersion 1.0.3

# Properties of Get-InstalledModule returned object
Get-InstalledModule DJoin | Format-List * -Force

Name                       : DJoin
Version                    : 1.0
Type                       : Module
Description                : This is a PowerShell frontend to the DJOIN.exe command which provides better
                             discoverability and usability.
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 7:12:37 PM
InstalledDate              : 4/5/2016 4:13:39 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Modules\DJoin\1.0

```



## PSGetRepositoryItemInfo 개체의 InstalledDate 및 UpdatedDate 속성

    During the install operation:
        InstalledDate: current DateTime (Get-Date) value
        UpdatedDate: null

    During the Update operation:
        InstalledDate: InstalledDate from the previous installation otherwise current DateTime (Get-Date) value
        UpdatedDate: current DateTime (Get-Date) value

```powershell
Install-Module -Name ContosoServer -RequiredVersion 1.0 -Repository INT
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM


\Update-Module -Name ContosoServer
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM 2/29/2016 12:00:15 PM
```




<!--HONumber=Oct16_HO2-->


