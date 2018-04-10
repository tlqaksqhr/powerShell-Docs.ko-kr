---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC 끌어오기 클라이언트 설정
ms.openlocfilehash: e6d73187566db2756ae24dabe0a825fffb5ecce0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="f99e8-103">DSC 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="f99e8-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="f99e8-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f99e8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f99e8-105">각 대상 노드는 끌어오기 모드를 사용하도록 지시받고 끌어오기 서버에 연결하여 구성 및 리소스를 가져올 수 있는 URL 또는 파일 위치와 보고서 데이터를 보내야 하는 URL 또는 파일 위치를 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99e8-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="f99e8-106">다음 항목에서는 끌어오기 클라이언트를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f99e8-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="f99e8-107">구성 이름을 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="f99e8-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="f99e8-108">구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="f99e8-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="f99e8-109">**참고**: 이 항목은 PowerShell 5.0에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f99e8-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="f99e8-110">PowerShell 4.0에서 끌어오기 클라이언트를 설정하려면 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="f99e8-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>