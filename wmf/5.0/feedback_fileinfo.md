---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225643"
---
# <a name="updates-to-fileinfo-object"></a>FileInfo 개체에 대한 업데이트
파일 버전 정보는 잘못될 수 있습니다. 특히 파일이 패치된 경우는 더욱 그렇습니다. 이 WMF Production Preview 릴리스에서는 새로운 **FileVersionRaw** 및 **ProductVersionRaw** 스크립트 속성을 FileInfo 개체에 추가합니다. 다음은 powershell.exe에 대해 표시되는 속성입니다($pid는 PowerShell 프로세스의 ID로 간주).

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
