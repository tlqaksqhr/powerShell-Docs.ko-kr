---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "개체 파이프라인"
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="object-pipeline"></a><span data-ttu-id="445ec-103">개체 파이프라인</span><span class="sxs-lookup"><span data-stu-id="445ec-103">Object Pipeline</span></span>
<span data-ttu-id="445ec-104">파이프라인은 일련의 파이프 세그먼트가 연결된 것처럼 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="445ec-105">파이프라인을 따라 이동하는 항목은 각 세그먼트를 통과합니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="445ec-106">Windows PowerShell에서 파이프라인을 만들려면 여러 명령을 파이프 연산자 "|"로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-106">To create a pipeline in Windows PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="445ec-107">그러면 각 명령의 출력이 그 다음 명령의 입력으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="445ec-108">파이프라인은 명령줄 인터페이스에 사용되는 가장 중요한 개념이라고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-108">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="445ec-109">파이프라인을 올바로 사용하면 복잡한 명령을 보다 쉽게 입력할 수 있을 뿐 아니라 명령의 작업 흐름도 보다 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-109">Properly used, pipelines not only reduce the effort involved in entering complex commands, but also make it easier to see the flow of work in the commands.</span></span> <span data-ttu-id="445ec-110">또한 파이프라인은 각 항목에 대해 개별적으로 작동하기 때문에 파이프라인에 있는 항목 수에 따라 파이프라인을 수정하지 않아도 된다는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-110">A related useful characteristic of pipelines is that because they operate on each item separately, you do not have to modify them based on whether you will have zero, one, or many items in the pipeline.</span></span> <span data-ttu-id="445ec-111">게다가 파이프라인에 있는 각 명령(파이프라인 요소)은 해당 출력을 파이프라인에 있는 다음 명령에 항목 단위로 전달하므로</span><span class="sxs-lookup"><span data-stu-id="445ec-111">Furthermore, each command in a pipeline (called a pipeline element) usually passes its output to the next command in the pipeline item-by-item.</span></span> <span data-ttu-id="445ec-112">복잡한 명령의 리소스 수요를 줄이고 출력을 즉시 볼 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-112">This usually reduces the resource demand of complex commands and allows you to begin getting the output immediately.</span></span>

<span data-ttu-id="445ec-113">이 장에서는 Windows PowerShell 파이프라인과 가장 보편적으로 사용되는 셸 파이프라인의 차이점에 대해 설명한 다음 파이프라인 출력을 제어하고 파이프라인의 작동 방법을 확인하는 데 사용할 수 있는 몇 가지 기본 도구를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="445ec-113">In this chapter, we will describe how the Windows PowerShell pipeline differs from the pipelines of most popular shells, and then demonstrate some basic tools that you can use to help control pipeline output and also to see how the pipeline operates.</span></span>
