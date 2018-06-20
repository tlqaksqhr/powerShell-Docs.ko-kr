---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 갤러리에 대한 ScriptAnazlyer 규칙 프로필
ms.openlocfilehash: 54100f7a530cbc769e4a0e2dbff18dbc5de88fa6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225745"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="dee7f-103">갤러리에 대한 ScriptAnazlyer 규칙 프로필</span><span class="sxs-lookup"><span data-stu-id="dee7f-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="dee7f-104">PowerShell 갤러리에 게시된 항목의 품질을 보장하기 위해 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)제출된 스크립트에 위반 사항이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dee7f-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="dee7f-105">ScriptAnalyzer [GitHub 페이지](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)에서 실행하는 규칙의 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dee7f-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="dee7f-106">실행하는 규칙과 관련해서 질문이 있는 경우 PowerShell 갤러리 관리자에게 문의하거나 ScriptAnalzyer에 대한 문제를 개설합니다.</span><span class="sxs-lookup"><span data-stu-id="dee7f-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="dee7f-107">ScriptAnalyzer 결과는 향후 릴리스의 갤러리에 포함된 각 개별 항목 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dee7f-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="dee7f-108">항목 소유자는 해당 항목을 확인하여 게시된 항목에 심각한 오류가 없는지 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dee7f-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>
