---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: psget_get psrepository
ms.technology: powershell
ms.openlocfilehash: b1d5172232f0c2916382b6c35093a238f6b2cb4d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="get-psrepository"></a>Get-PSRepository

컴퓨터에 등록된 리포지토리를 가져옵니다.

## <a name="description"></a>설명

Get-PSRepository cmdlet은 컴퓨터에서 현재 사용자에 대해 등록된 PowerShell 모듈 리포지토리를 가져옵니다.

등록된 각 리포지토리에 대해 Get-PSRepository는 PSRepository 개체를 반환하며, 필요에 따라 이 개체를 Unregister-PSRepository에 파이프하여 등록된 리포지토리를 등록 취소할 수 있습니다.

## <a name="cmdlet-syntax"></a>Cmdlet 구문
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet 온라인 도움말 참조

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a>예제 명령

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```

