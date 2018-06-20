---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217994"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="eaf28-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="eaf28-102">New-TemporaryFile</span></span>
<span data-ttu-id="eaf28-103">경우에 따라 스크립트에서 임시 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf28-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="eaf28-104">**New-TemporaryFile** cmdlet을 사용하면 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf28-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="eaf28-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="eaf28-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="eaf28-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="eaf28-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="eaf28-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="eaf28-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
