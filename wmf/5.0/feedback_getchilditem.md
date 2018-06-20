---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221904"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="f2e77-102">Get-ChildItem의 -Depth 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f2e77-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="f2e77-103">이제 **Get-ChildItem**은 **–Recurse**와 함께 사용되어 재귀를 제한하는 **–Depth** 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e77-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="f2e77-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="f2e77-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="f2e77-105">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="f2e77-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="f2e77-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="f2e77-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="f2e77-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="f2e77-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="f2e77-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="f2e77-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="f2e77-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="f2e77-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="f2e77-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="f2e77-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="f2e77-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="f2e77-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="f2e77-112">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="f2e77-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="f2e77-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="f2e77-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="f2e77-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="f2e77-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="f2e77-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="f2e77-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="f2e77-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="f2e77-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="f2e77-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="f2e77-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="f2e77-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="f2e77-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="f2e77-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="f2e77-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="f2e77-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="f2e77-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
