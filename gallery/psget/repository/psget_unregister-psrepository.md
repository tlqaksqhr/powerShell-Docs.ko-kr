---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: psget_unregister psrepository
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 7d9c24ebb20756a2f7852692532ac6ec7e558ca9

---

# Unregister-PSRepository

리포지토리 등록을 취소합니다.

## 설명

Unregister-PSRepository cmdlet은 현재 사용자에 대해 리포지토리 등록을 취소합니다.
- 엔터프라이즈 및 연결이 끊긴 시나리오의 경우 PSGallery 리포지토리를 등록 취소하고 다시 등록할 수 있습니다.
- 사용자는 다음을 실행하기만 하면 PSGallery를 다시 등록할 수 있습니다. `Register-PSRepository -Default`
- PSGallery는 Publish-Module 및 Publish-Script cmdlet의 기본 게시 리포지토리이므로 등록된 리포지토리 목록에서 PSGallery를 사용할 수 없는 경우 오류가 발생합니다.

## Cmdlet 구문

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## Cmdlet 온라인 도움말 참조

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## 예제 명령

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### 엔터프라이즈 및 연결이 끊긴 시나리오의 경우 PSGallery 리포지토리를 등록 취소하고 다시 등록할 수 있습니다.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```




<!--HONumber=Oct16_HO2-->


