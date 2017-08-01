---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "명령을 제한하는 경우의 고려 사항"
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
### <a name="considerations-when-limiting-commands"></a><span data-ttu-id="ff815-103">명령을 제한하는 경우의 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ff815-103">Considerations When Limiting Commands</span></span>
<span data-ttu-id="ff815-104">이 단계에 대해 유의할 한 가지 중요한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff815-104">There is one important point to make about this step.</span></span>
<span data-ttu-id="ff815-105">JEA를 통해 노출된 모든 기능이 관리자 제한 영역에 위치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff815-105">It is critical that all capabilities exposed through JEA are located in administrator-restricted areas.</span></span>
<span data-ttu-id="ff815-106">관리자가 아닌 사용자는 JEA 끝점을 통해 사용된 스크립트를 수정할 수 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff815-106">Non-administrator users should not have the capability to modify the scripts used through JEA endpoints.</span></span>

<span data-ttu-id="ff815-107">이와 관련하여 JEA 사용자에게 자신의 JEA 세션 내에서 JEA 구성 및 허용된 스크립트를 덮어쓰는 기능을 제공하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff815-107">On a related note, it is critical that you do not give JEA users the ability to overwrite JEA configurations and whitelisted scripts within their JEA sessions.</span></span>
<span data-ttu-id="ff815-108">`Copy-Item`과 같은 명령을 노출하는 경우에는 특히 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="ff815-108">Be extremely careful when exposing commands like `Copy-Item`!</span></span>

