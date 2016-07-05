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
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 38a6cb1b0402825b307652e6747ea65baafd1d8b

---

# 부록 1 - 호환성 별칭
Windows PowerShell에는 UNIX 및 Cmd 사용자가 Windows PowerShell에서 친숙한 명령 이름을 사용할 수 있게 해주는 여러 전환 별칭이 있습니다. 아래 표에는 가장 일반적인 별칭이 나와 있으며, 별칭 뒤에 Windows PowerShell 명령과 표준 Windows PowerShell 별칭(있는 경우)이 표시됩니다.

Get\-Alias cmdlet을 사용하면 Windows PowerShell 내에서 별칭이 가리키는 Windows PowerShell 명령을 찾을 수 있습니다. 예를 들어 **get\-alias cls**를 입력합니다.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD 명령|UNIX 명령|PS 명령|PS 별칭|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get\-ChildItem**|**gci**|
|**cls**|**clear**|**Clear\-Host**(함수)|해당 없음|
|**del, erase, rmdir**|**rm**|**Remove\-Item**|**ri**|
|**copy**|**cp**|**Copy\-Item**|**ci**|
|**move**|**mv**|**Move\-Item**|**mi**|
|**rename**|**mv**|**Rename\-Item**|**rni**|
|**형식**|**cat**|**Get\-Content**|**gc**|
|**cd**|**cd**|**Set\-Location**|**sl**|
|**md**|**mkdir**|**New\-Item**|**ni**|
|해당 없음|**pushd**|**Push\-Location**|해당 없음|
|해당 없음|**popd**|**Pop\-Location**|해당 없음|




<!--HONumber=Jun16_HO4-->


