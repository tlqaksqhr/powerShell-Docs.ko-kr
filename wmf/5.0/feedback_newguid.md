---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a><span data-ttu-id="5fb79-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="5fb79-102">New-Guid</span></span>
<span data-ttu-id="5fb79-103">종종 스크립트(또는 DSC 리소스 작성)에는 고유 식별자가 필요했습니다.</span><span class="sxs-lookup"><span data-stu-id="5fb79-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="5fb79-104">GUID는 잘 작동하고 .NET Framework Guid 클래스를 호출하여 쉽게 생성할 수 있지만 cmdlet을 사용하면 .NET Framework 클래스에 익숙하지 않은 최종 사용자가 더 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fb79-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="5fb79-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="5fb79-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="5fb79-106">Guid</span><span class="sxs-lookup"><span data-stu-id="5fb79-106">Guid</span></span>

----

<span data-ttu-id="5fb79-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="5fb79-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

