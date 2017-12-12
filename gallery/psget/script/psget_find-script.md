---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Script
ms.openlocfilehash: df62a9934d8013d37bd0083c03f90fa7fa05ac0c
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2017
---
# <a name="find-script"></a>Find-Script

온라인 갤러리에서 지정된 조건과 일치하는 PowerShell 스크립트 파일을 찾습니다.

## <a name="description"></a>설명

Find-Script는 등록된 리포지토리에서 지정된 조건과 일치하는 스크립트 파일을 검색합니다.
찾은 각 스크립트에 대해 Find-Script는 PSRepositoryItemInfo 개체를 반환하며, 필요에 따라 이 개체를 Install-Script에 파이프하여 스크립트를 설치할 수 있습니다.
Find-Script cmdlet을 사용하면 종속성을 비롯한 이름, 태그, 필터, 명령 이름, 버전 범위, 정확한 버전, 모든 버전과 같은 다양한 검색 조건을 사용하여 스트립트 파일을 검색할 수 있으며 특정 또는 모든 등록된 리포지토리에서 검색할 수 있습니다.

- Find-Script는 -Command 및 -Includes 매개 변수를 사용하여 스크립트 콘텐츠를 기준으로 필터링할 수 있습니다.
- Find-Script는 버전 매개 변수(MinimumVersion, MaximumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.
  - 이러한 매개 변수는 MinmimumVersion 및 MaximumVersion을 제외하고 함께 사용할 수 없습니다.
  - 이 버전 매개 변수는 와일드카드 없이 단일 스크립트 이름과 함께 사용해야 합니다.
  - RequiredVersion 매개 변수를 지정하지 않으면 Find-Script는 지정된 최소 버전과 같거나 그 이상인 최신 버전의 스크립트 또는 최소 버전이 지정되지 않은 경우 최신 버전의 스크립트를 반환합니다. 
  - RequiredVersion 매개 변수를 지정하면 Find-Script는 지정된 버전과 정확하게 일치하는 버전의 스크립트만 반환합니다.
- Find-Script는 -Tag 매개 변수를 사용하여 스크립트 메타데이터를 필터링할 수 있습니다.
- Find-Script는 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.
- Find-Script는 등록된 모든 또는 일부 리포지토리의 스크립트를 필터링할 수 있습니다.

**참고:** 등록된 PSRepository에 유효한 ScriptSourceLocation이 있어야 합니다. Set-PSRepository를 사용하여 ScriptSourceLocation 값을 설정할 수 있습니다.

## <a name="cmdlet-syntax"></a>Cmdlet 구문

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet 온라인 도움말 참조

[Find-Script](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a>예제 명령

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script with a specific pre-release version
Find-Script -Name Connect-O365 -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
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
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```

