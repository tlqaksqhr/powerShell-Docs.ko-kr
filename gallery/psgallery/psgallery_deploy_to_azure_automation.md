---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="6da35-103">Azure 자동화에 배포</span><span class="sxs-lookup"><span data-stu-id="6da35-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="6da35-104">항목 세부 정보 페이지의 Azure Automation에 배포 단추를 클릭하면 PowerShell 갤러리의 항목이 Azure Automation에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="6da35-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Azure Automation에 배포](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="6da35-106">클릭하면 Azure 관리 포털로 리디렉션되며, 여기서 Azure 계정 자격 증명을 사용하여 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="6da35-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="6da35-107">항목에 종속성이 포함된 경우 모든 종속성도 Azure Automation에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="6da35-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="6da35-108">경고: Automation 계정에 동일한 항목과 버전이 이미 있는 경우 PowerShell 갤러리에서 다시 배포하면 Automation 계정의 항목을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="6da35-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="6da35-109">모듈을 배포하는 경우 Azure Automation의 Modules 섹션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6da35-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="6da35-110">스크립트를 배포하는 경우 Azure Automation의 Runbook 섹션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6da35-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="6da35-111">항목 메타데이터에 AzureAutomationNotSupported 태그를 추가하면 Azure Automation에 배포 단추를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6da35-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="6da35-112">Azure Automation에 대한 자세한 내용은 Azure Automation 웹 사이트 [Azure Automation 웹 사이트](http://azure.microsoft.com/en-us/services/automation/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6da35-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

