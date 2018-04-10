---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: ada4fcc0beb3eb74b099f221762341abbf2c3b4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
경우에 따라 스크립트에서 임시 파일을 만들어야 합니다. **New-TemporaryFile** cmdlet을 사용하면 쉽게 만들 수 있습니다.

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp