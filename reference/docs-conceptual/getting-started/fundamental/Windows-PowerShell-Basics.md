---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 기본 사항
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: b21c6cd84ea29d5e8085ccf8df2a5a9199e1d859
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950537"
---
# <a name="windows-powershell-basics"></a><span data-ttu-id="b8df7-103">Windows PowerShell 기본 사항</span><span class="sxs-lookup"><span data-stu-id="b8df7-103">Windows PowerShell Basics</span></span>
<span data-ttu-id="b8df7-104">그래픽 사용자 인터페이스는 대부분의 컴퓨터 사용자에게 잘 알려진 몇 가지 기본 개념을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-104">Graphical user interfaces use some basic concepts that are well known to most computer users.</span></span> <span data-ttu-id="b8df7-105">사용자는 이러한 친숙한 인터페이스를 사용하여 손쉽게 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-105">Users rely on the familiarity of those interfaces to accomplish tasks.</span></span> <span data-ttu-id="b8df7-106">운영 체제는 대개 특정 기능에 액세스하기 위한 드롭다운 메뉴와 특정 상황에 맞는 기능에 액세스하기 위한 상황에 맞는 메뉴를 사용하여 검색 가능한 항목을 그래픽 방식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-106">Operating systems present users with a graphical representation of items that can be browsed, usually with drop-down menus for accessing specific functionality and context menus for accessing context-specific functionality.</span></span>

<span data-ttu-id="b8df7-107">그러나 Windows PowerShell과 같은 CLI(명령줄 인터페이스)는 메뉴나 그래픽 시스템을 사용하지 않으므로 이와 다른 방식으로 정보를 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-107">A command-line interface (CLI), such as Windows PowerShell, must use a different approach to expose information, because it does not have menus or graphical systems to help the user.</span></span> <span data-ttu-id="b8df7-108">명령을 사용하려면 먼저 명령 이름을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-108">You need to know command names before you can use them.</span></span> <span data-ttu-id="b8df7-109">GUI 환경의 기능에 해당하는 복잡한 명령을 입력할 수 있더라도 일반적으로 사용되는 명령과 명령 매개 변수에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-109">Although you can type complex commands that are equivalent to the features in a GUI environment, you must become familiar with commonly-used commands and command parameters.</span></span>

<span data-ttu-id="b8df7-110">대부분의 CLI에는 인터페이스를 쉽게 익힐 수 있는 일정한 패턴이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-110">Most CLIs do not have patterns that can help the user to learn the interface.</span></span> <span data-ttu-id="b8df7-111">CLI는 최초 운영 체제 셸이기 때문에 많은 명령 이름과 매개 변수 이름이 임의로 선택되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-111">Because CLIs were the first operating system shells, many command names and parameter names were selected arbitrarily.</span></span> <span data-ttu-id="b8df7-112">대개 이러한 이름은 정확성보다는 간결성을 고려하여 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-112">Terse command names were generally chosen over clear ones.</span></span> <span data-ttu-id="b8df7-113">도움말 시스템 및 명령 설계 표준은 대부분의 CLI에 통합되어 있지만 대개 최초 명령과의 호환성을 고려해 설계되었으므로 명령 집합의 모양이 계속 이전에 결정된 모양을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-113">Although help systems and command design standards are integrated into most CLIs, they have been generally designed for compatibility with the earliest commands, so the command set is still shaped by decisions made decades ago.</span></span>

<span data-ttu-id="b8df7-114">Windows PowerShell은 사용자가 CLI에 대해 오랫동안 쌓은 지식을 활용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-114">Windows PowerShell was designed to take advantage of a user's historic knowledge of CLIs.</span></span> <span data-ttu-id="b8df7-115">이 장에서는 Windows PowerShell을 빠르게 익히는 데 사용할 수 있는 몇 가지 기본 도구와 개념에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-115">In this chapter, we will talk about some basic tools and concepts that you can use to learn Windows PowerShell quickly.</span></span> <span data-ttu-id="b8df7-116">해당 기능은 아래와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8df7-116">They include:</span></span>

- <span data-ttu-id="b8df7-117">[Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command) 사용</span><span class="sxs-lookup"><span data-stu-id="b8df7-117">Using [Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command)</span></span>

- <span data-ttu-id="b8df7-118">[Cmd.exe](/windows-server/administration/windows-commands/cmd) 및 [UNIX 명령](/windows/wsl/reference) 사용</span><span class="sxs-lookup"><span data-stu-id="b8df7-118">Using [Cmd.exe](/windows-server/administration/windows-commands/cmd) and [UNIX commands](/windows/wsl/reference)</span></span>

- [<span data-ttu-id="b8df7-119">탭 완성 기능 사용</span><span class="sxs-lookup"><span data-stu-id="b8df7-119">Using Tab-Completion</span></span>](../../core-powershell/console/using-tab-expansion.md)

- [<span data-ttu-id="b8df7-120">Get-Help 사용</span><span class="sxs-lookup"><span data-stu-id="b8df7-120">Using Get-Help</span></span>](./getting-detailed-help-information.md)