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
# <a name="using-dsc-on-microsoft-azure"></a>Microsoft Azure에서 DSC 사용

DSC(필요한 상태 구성)는 Microsoft Azure에서 [Azure 필요한 상태 구성 확장 처리기](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) 및 [Azure Automation DSC](/azure/automation/automation-dsc-overview)를 통해 지원됩니다.

## <a name="azure-desired-state-configuration-extension-handler"></a>Azure 필요한 상태 구성 확장 처리기

Azure DSC 확장을 사용하면 Microsoft Azure에서 호스트된 VM을 DSC로 관리할 수 있습니다.
자세한 내용은 아래 항목을 참조하세요.

- [Azure 필요한 상태 구성 확장 처리기](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [Azure Resource Manager 템플릿을 사용하는 Windows VMSS 및 필요한 상태 구성](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [Azure DSC 확장 처리기에 자격 증명 전달](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [Azure 필요한 상태 구성 확장 기록](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

[Azure Automation 서비스](https://azure.microsoft.com/services/automation/)를 사용하면 Azure 내에서 DSC 구성, 리소스 및 관리되는 노드를 관리할 수 있습니다. 자세한 내용은 아래 항목을 참조하세요.

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Azure Automation DSC 시작하기](/azure/automation/automation-dsc-getting-started)
- [Azure Automation DSC를 통한 관리를 위한 컴퓨터 온보드](/azure/automation/automation-dsc-onboarding)