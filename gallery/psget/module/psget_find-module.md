---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: "psget_find 모듈"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 67542f54cd350bd1d9512eae0a2355b47943c2f2

---

# Find-Module
온라인 갤러리에서 지정된 조건과 일치하는 모듈을 찾습니다.

## 설명
Find-Module은 등록된 리포지토리에서 지정된 조건과 일치하는 모듈을 검색합니다.
찾은 각 모듈에 대해 Find-Module은 PSRepositoryItemInfo 개체를 반환하며, 필요에 따라 이 개체를 Install-Module에 파이프하여 모듈을 설치할 수 있습니다.

- Find-Module은 -Command, -DscResource, -RoleCapability 및 -Includes 매개 변수를 사용하여 모듈 콘텐츠를 기준으로 필터링할 수 있습니다.
- Find-Module은 버전 매개 변수(MinimumVersion, MaximumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.
  - 이러한 매개 변수는 MinmimumVersion 및 MaximumVersion을 제외하고 함께 사용할 수 없습니다.
  - 이 버전 매개 변수는 와일드카드 없이 단일 모듈 이름과 함께 사용해야 합니다.
  - RequiredVersion 매개 변수를 지정하지 않으면 Find-Module은 지정된 최소 버전과 같거나 그 이상인 최신 버전의 모듈 또는 최소 버전이 지정되지 않은 경우 최신 버전의 모듈을 반환합니다. 
  - RequiredVersion 매개 변수를 지정하면 Find-Module은 지정된 버전과 정확하게 일치하는 버전의 모듈만 반환합니다.
- Find-Module은 -Tag 매개 변수를 사용하여 모듈 메타데이터를 필터링할 수 있습니다.
- Find-Module은 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.
- Find-Module은 등록된 모든 또는 일부 리포지토리의 모듈을 필터링할 수 있습니다.

## Cmdlet 구문
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## Cmdlet 온라인 도움말 참조

[Find-Module](http://go.microsoft.com/fwlink/?LinkID=398574)

## 예제 명령
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion. 
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```




<!--HONumber=Oct16_HO2-->


