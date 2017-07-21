---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d23cfc2aaa680c247aaab91d8875c64c9d62187e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="a5265-102">보관 cmdlet</span><span class="sxs-lookup"><span data-stu-id="a5265-102">Archive cmdlets</span></span>

<span data-ttu-id="a5265-103">두 가지 새 cmdlet **Compress-Archive** 및 **Expand-Archive**를 사용하여 ZIP 파일을 압축하고 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5265-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="a5265-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="a5265-104">Compress-Archive</span></span>
<span data-ttu-id="a5265-105">**Compress-Archive** cmdlet은 지정된 파일에서 새로운 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a5265-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="a5265-106">보관 파일을 사용하면 여러 파일을 패키지하고 필요에 따라 단일 파일로 압축하여 더 쉽게 처리하고 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5265-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="a5265-107">보관 파일은 **-CompressionLevel** 매개 변수에 지정된 압축 알고리즘을 사용하여 압축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5265-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="a5265-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="a5265-108">Expand-Archive</span></span>
<span data-ttu-id="a5265-109">**Expand-Archive** cmdlet은 지정된 보관 파일에서 파일을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="a5265-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="a5265-110">보관 파일을 사용하면 여러 파일을 패키지하고 필요에 따라 단일 파일로 압축하여 더 쉽게 처리하고 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5265-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

