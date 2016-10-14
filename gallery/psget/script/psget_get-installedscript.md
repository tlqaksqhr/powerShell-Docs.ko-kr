# Get-InstalledScript

컴퓨터에 설치된 스크립트를 가져옵니다.

## 설명

Get-InstalledScript cmdlet은 컴퓨터에 설치된 PowerShell 스크립트를 가져옵니다.

설치된 각 스크립트에 대해 Get-InstalledScript는 PSRepositoryItemInfo 개체를 반환하며, 필요에 따라 이 개체를 Uninstall-Script에 파이프하여 설치된 스크립트를 제거할 수 있습니다.

- Get-InstalledScript는 이름, 버전 매개 변수에 따라 설치된 스크립트를 필터링할 수 있습니다.
- Get-InstalledScript는 버전 매개 변수(MinimumVersion, MaximumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.
  - 이러한 매개 변수는 MinmimumVersion 및 MaximumVersion을 제외하고 함께 사용할 수 없습니다.
  - 이 버전 매개 변수는 와일드카드 없이 단일 스크립트 이름과 함께 사용해야 합니다.
  - RequiredVersion 매개 변수를 지정하지 않으면 Get-InstalledScript는 지정된 최소 버전과 같거나 그 이상인 최신 버전의 설치된 스크립트 또는 최소 버전이 지정되지 않은 경우 최신 버전의 스크립트를 반환합니다. 
  - RequiredVersion 매개 변수를 지정하면 Get-InstalledScript는 지정된 버전과 정확하게 일치하는 버전의 설치된 스크립트만 반환합니다.

## Cmdlet 구문

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## Cmdlet 온라인 도움말 참조

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## 예제 명령

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

<!--HONumber=Aug16_HO3-->


