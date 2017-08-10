---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 핵심 공급자"
ms.assetid: 6e24bf6d-4c70-4edf-956a-1e8e4779ba10
ms.openlocfilehash: fdfdfee86884d3ac18a33ac424828faa96ecd8bd
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-core-providers"></a><span data-ttu-id="0d0c3-103">Windows PowerShell 핵심 공급자</span><span class="sxs-lookup"><span data-stu-id="0d0c3-103">Windows PowerShell Core Providers</span></span>
<span data-ttu-id="0d0c3-104">이 섹션에는 **Microsoft.PowerShell.Core** 모듈의 Windows PowerShell 공급자에 대해 설명하는 도움말 항목이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-104">This section contains help topics that describe the Windows PowerShell providers in the **Microsoft.PowerShell.Core** module.</span></span>

<span data-ttu-id="0d0c3-105">Windows PowerShell 공급자는 특정 데이터 저장소에 있는 데이터를 쉽게 보고 관리하기 위해 Windows PowerShell에서 사용할 수 있도록 하는 .NET 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-105">Windows PowerShell providers are .NET programs that make the data in a specialized data store available in Windows PowerShell so that you can easily view and manage it.</span></span> <span data-ttu-id="0d0c3-106">공급자가 표시하는 데이터는 파일 시스템 드라이브와 매우 유사한 드라이브에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-106">The data that a provider exposes appears in a drive, much like a file system drive.</span></span> <span data-ttu-id="0d0c3-107">자세한 내용은 [about_Providers [v4]](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-107">For more information, see [about_Providers [v4]](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242).</span></span>

|<span data-ttu-id="0d0c3-108">공급자</span><span class="sxs-lookup"><span data-stu-id="0d0c3-108">Provider</span></span>|<span data-ttu-id="0d0c3-109">설명</span><span class="sxs-lookup"><span data-stu-id="0d0c3-109">Description</span></span>|
|------------|---------------|
|[<span data-ttu-id="0d0c3-110">별칭 공급자 [v3]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-110">Alias Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/dce3f872-aeff-4eb2-8b38-876cd612fc29)|<span data-ttu-id="0d0c3-111">Windows PowerShell 별칭 및 해당 값에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-111">Provides access to the Windows PowerShell aliases and their values.</span></span>|
|[<span data-ttu-id="0d0c3-112">환경 공급자 [v3]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-112">Environment Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/94fcd05d-e702-4706-9b7d-ad7e5fd0ec09)|<span data-ttu-id="0d0c3-113">Windows 환경 변수에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-113">Provides access to the Windows environment variables.</span></span>|
|[<span data-ttu-id="0d0c3-114">파일 시스템 공급자 [v3]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-114">FileSystem Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/0e494537-dfdf-437a-8b27-c21e30aa1f9f)|<span data-ttu-id="0d0c3-115">파일 및 디렉터리에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-115">Provides access to files and directories.</span></span>|
|[<span data-ttu-id="0d0c3-116">함수 공급자 [v3]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-116">Function Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/7dfc92f4-9a88-4399-978d-6d5d224b3e76)|<span data-ttu-id="0d0c3-117">Windows PowerShell에 정의된 함수에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-117">Provides access to the functions defined in Windows PowerShell.</span></span>|
|[<span data-ttu-id="0d0c3-118">레지스트리 공급자 [v3]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-118">Registry Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/d3c8013c-8caa-48d7-9feb-bfef0d95926e)|<span data-ttu-id="0d0c3-119">시스템 레지스트리 키 및 값에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-119">Provides access to the system registry keys and values.</span></span>|
|[<span data-ttu-id="0d0c3-120">변수 공급자 [v3]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-120">Variable Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/78dbcbbd-7946-4b9b-b75b-146f247f821c)|<span data-ttu-id="0d0c3-121">Windows PowerShell 변수 및 해당 값에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0c3-121">Provides access to Windows PowerShell variables and their values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0d0c3-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d0c3-122">See Also</span></span>
- [<span data-ttu-id="0d0c3-123">인증서 공급자 [v3]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-123">Certificate Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/3f743541-d0c6-4670-809a-b16fb01f7c4d)
- [<span data-ttu-id="0d0c3-124">WSMan 공급자 [v3]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-124">WSMan Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/4c3d8d36-4f7a-4211-996f-64110e4b2eb7)
- [<span data-ttu-id="0d0c3-125">about_Providers [v4]</span><span class="sxs-lookup"><span data-stu-id="0d0c3-125">about_Providers [v4]</span></span>](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242)
- [<span data-ttu-id="0d0c3-126">Microsoft.PowerShell.Core 모듈</span><span class="sxs-lookup"><span data-stu-id="0d0c3-126">Microsoft.PowerShell.Core Module</span></span>](Microsoft.PowerShell.Core-Module.md)

