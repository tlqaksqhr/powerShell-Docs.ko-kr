---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 223acbcc2f6cd4f15e1ee55d3f2f68df851cd902
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2018
---
<a name="deploy-to-azure-automation"></a>Azure 자동화에 배포
===========================

항목 세부 정보 페이지의 Azure Automation에 배포 단추를 클릭하면 PowerShell 갤러리의 항목이 Azure Automation에 배포됩니다.

![Azure Automation에 배포](Images/DeployToAzureAutomationButton.png)

클릭하면 Azure 관리 포털로 리디렉션되며, 여기서 Azure 계정 자격 증명을 사용하여 로그인합니다.
항목에 종속성이 포함된 경우 모든 종속성도 Azure Automation에 배포됩니다.

경고: Automation 계정에 동일한 항목과 버전이 이미 있는 경우 PowerShell 갤러리에서 다시 배포하면 Automation 계정의 항목을 덮어씁니다.

모듈을 배포하는 경우 Azure Automation의 Modules 섹션에 표시됩니다.  스크립트를 배포하는 경우 Azure Automation의 Runbook 섹션에 표시됩니다.

항목 메타데이터에 AzureAutomationNotSupported 태그를 추가하면 Azure Automation에 배포 단추를 해제할 수 있습니다.

Azure Automation에 대한 자세한 내용은 Azure Automation 웹 사이트 [Azure Automation 웹 사이트](http://azure.microsoft.com/services/automation/)를 참조하세요.

