---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="clipboard-cmdlets" class="xliff"></a>
# 클립보드 cmdlet
**Get-Clipboard** 및 **Set-Clipboard**를 사용하면 Windows PowerShell 세션 간에 콘텐츠를 더 쉽게 전송할 수 있습니다. 예를 들어, Windows 탐색기를 사용하여 세 개의 파일을 클립보드에 복사하는 경우(예: 파일을 선택한 후 `ctrl-c`를 누름) 클립보드의 내용을 파일 목록으로 손쉽게 액세스할 수 있습니다.

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


클립보드 cmdlet은 이미지, 오디오 파일, 파일 목록 및 텍스트를 지원합니다.

