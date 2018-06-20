---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225592"
---
# <a name="new-guid"></a><span data-ttu-id="c39ed-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="c39ed-102">New-Guid</span></span>
<span data-ttu-id="c39ed-103">종종 스크립트(또는 DSC 리소스 작성)에는 고유 식별자가 필요했습니다.</span><span class="sxs-lookup"><span data-stu-id="c39ed-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="c39ed-104">GUID는 잘 작동하고 .NET Framework Guid 클래스를 호출하여 쉽게 생성할 수 있지만 cmdlet을 사용하면 .NET Framework 클래스에 익숙하지 않은 최종 사용자가 더 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c39ed-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="c39ed-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="c39ed-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="c39ed-106">Guid</span><span class="sxs-lookup"><span data-stu-id="c39ed-106">Guid</span></span>

----

<span data-ttu-id="c39ed-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="c39ed-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
