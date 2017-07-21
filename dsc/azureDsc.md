---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Microsoft Azure에서 DSC 사용"
ms.openlocfilehash: 9b7d301c3e011b8933b9ee49219e7f0949a5c886
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="b9b4b-103">Microsoft Azure에서 DSC 사용</span><span class="sxs-lookup"><span data-stu-id="b9b4b-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="b9b4b-104">DSC(필요한 상태 구성)는 Microsoft Azure에서 [Azure 필요한 상태 구성 확장 처리기](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) 및 [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview)를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9b4b-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="b9b4b-105">Azure 필요한 상태 구성 확장 처리기</span><span class="sxs-lookup"><span data-stu-id="b9b4b-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="b9b4b-106">Azure DSC 확장을 사용하면 Microsoft Azure에서 호스트된 VM을 DSC로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b4b-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="b9b4b-107">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9b4b-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="b9b4b-108">Azure 필요한 상태 구성 확장 처리기</span><span class="sxs-lookup"><span data-stu-id="b9b4b-108">Azure Desired State Configuration extension handler</span></span>](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="b9b4b-109">Azure Resource Manager 템플릿을 사용하는 Windows VMSS 및 필요한 상태 구성</span><span class="sxs-lookup"><span data-stu-id="b9b4b-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="b9b4b-110">Azure DSC 확장 처리기에 자격 증명 전달</span><span class="sxs-lookup"><span data-stu-id="b9b4b-110">Passing credentials to the Azure DSC extension handler</span></span>](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)

## <a name="azure-automation-dsc"></a><span data-ttu-id="b9b4b-111">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="b9b4b-111">Azure Automation DSC</span></span>

<span data-ttu-id="b9b4b-112">[Azure Automation 서비스](https://azure.microsoft.com/services/automation/)를 사용하면 Azure 내에서 DSC 구성, 리소스 및 관리되는 노드를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b4b-112">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="b9b4b-113">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9b4b-113">For more information, see the following topics:</span></span>

- [<span data-ttu-id="b9b4b-114">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="b9b4b-114">Azure Automation DSC</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="b9b4b-115">Azure Automation DSC 시작하기</span><span class="sxs-lookup"><span data-stu-id="b9b4b-115">Getting started with Azure Automation DSC</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="b9b4b-116">Azure Automation DSC를 통한 관리를 위한 컴퓨터 온보드</span><span class="sxs-lookup"><span data-stu-id="b9b4b-116">Onboarding machines for management by Azure Automation DSC</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding)

