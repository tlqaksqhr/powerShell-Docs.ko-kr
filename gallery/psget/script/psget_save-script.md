---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: "psget_save 스크립트"
ms.technology: powershell
ms.openlocfilehash: 58003350b991ca10b1d8bc65964bbfdd324334b5
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="save-script"></a>Save-Script

Save-Script cmdlet을 사용하면 스크립트 파일을 지정된 위치에 저장하여 검토할 수 있습니다.

## <a name="description"></a>설명

Save-Script cmdlet은 지정된 스크립트를 저장합니다.

## <a name="cmdlet-syntax"></a>Cmdlet 구문

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet 온라인 도움말 참조

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>예제 명령

### <a name="example-1-save-a-script-from-a-repository"></a>예제 1: 리포지토리의 스크립트 저장
이 명령은 GalleryINT 리포지토리에 있는 최신 버전의 스크립트 Fabrikam-ClientScript를 로컬 폴더 C:\ScriptSharingDemo에 저장합니다.

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>예제 2: Find-Script cmdlet에서 파이프하여 특정 버전의 스크립트 저장

첫 번째 명령은 GalleryINT 리포지토리에서 Fabrikam ClientScript 버전 1.5를 찾아서 C:\ScriptSharingDemo 폴더에 저장합니다.

두 번째 명령은 저장된 스크립트 메타데이터의 유효성을 검사합니다.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

