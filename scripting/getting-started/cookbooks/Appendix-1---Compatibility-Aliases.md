---
title: "부록 1 - 호환성 별칭"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: fc715f9ba2a1dc61d2549d5370371fe2b29fa063
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="appendix-1---compatibility-aliases"></a>부록 1 - 호환성 별칭
Windows PowerShell에는 UNIX 및 Cmd 사용자가 Windows PowerShell에서 친숙한 명령 이름을 사용할 수 있게 해주는 여러 전환 별칭이 있습니다. 아래 표에는 가장 일반적인 별칭이 나와 있으며, 별칭 뒤에 Windows PowerShell 명령과 표준 Windows PowerShell 별칭(있는 경우)이 표시됩니다.

Get-Alias cmdlet을 사용하면 Windows PowerShell 내에서 별칭이 가리키는 Windows PowerShell 명령을 찾을 수 있습니다. 예를 들어 **get-alias cls**를 입력합니다.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD 명령|UNIX 명령|PS 명령|PS 별칭|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host**(함수)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|

