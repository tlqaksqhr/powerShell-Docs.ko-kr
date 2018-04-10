---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a><span data-ttu-id="4d4c5-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="4d4c5-102">New-Guid</span></span>
<span data-ttu-id="4d4c5-103">종종 스크립트(또는 DSC 리소스 작성)에는 고유 식별자가 필요했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d4c5-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="4d4c5-104">GUID는 잘 작동하고 .NET Framework Guid 클래스를 호출하여 쉽게 생성할 수 있지만 cmdlet을 사용하면 .NET Framework 클래스에 익숙하지 않은 최종 사용자가 더 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d4c5-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="4d4c5-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="4d4c5-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="4d4c5-106">Guid</span><span class="sxs-lookup"><span data-stu-id="4d4c5-106">Guid</span></span>

----

<span data-ttu-id="4d4c5-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="4d4c5-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>