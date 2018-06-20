---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Microsoft Azure에서 DSC 사용
ms.openlocfilehash: d35488c3f66895e930eaa84360f3d3ec9d74e9c7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221887"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="b9d99-103">Microsoft Azure에서 DSC 사용</span><span class="sxs-lookup"><span data-stu-id="b9d99-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="b9d99-104">DSC(필요한 상태 구성)는 Microsoft Azure에서 [Azure 필요한 상태 구성 확장 처리기](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) 및 [Azure Automation DSC](/azure/automation/automation-dsc-overview)를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9d99-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="b9d99-105">Azure 필요한 상태 구성 확장 처리기</span><span class="sxs-lookup"><span data-stu-id="b9d99-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="b9d99-106">Azure DSC 확장을 사용하면 Microsoft Azure에서 호스트된 VM을 DSC로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9d99-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="b9d99-107">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9d99-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="b9d99-108">Azure 필요한 상태 구성 확장 처리기</span><span class="sxs-lookup"><span data-stu-id="b9d99-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="b9d99-109">Azure Resource Manager 템플릿을 사용하는 Windows VMSS 및 필요한 상태 구성</span><span class="sxs-lookup"><span data-stu-id="b9d99-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="b9d99-110">Azure DSC 확장 처리기에 자격 증명 전달</span><span class="sxs-lookup"><span data-stu-id="b9d99-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [<span data-ttu-id="b9d99-111">Azure 필요한 상태 구성 확장 기록</span><span class="sxs-lookup"><span data-stu-id="b9d99-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="b9d99-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="b9d99-112">Azure Automation DSC</span></span>

<span data-ttu-id="b9d99-113">[Azure Automation 서비스](https://azure.microsoft.com/services/automation/)를 사용하면 Azure 내에서 DSC 구성, 리소스 및 관리되는 노드를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9d99-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="b9d99-114">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9d99-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="b9d99-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="b9d99-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="b9d99-116">Azure Automation DSC 시작하기</span><span class="sxs-lookup"><span data-stu-id="b9d99-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="b9d99-117">Azure Automation DSC를 통한 관리를 위한 컴퓨터 온보드</span><span class="sxs-lookup"><span data-stu-id="b9d99-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)