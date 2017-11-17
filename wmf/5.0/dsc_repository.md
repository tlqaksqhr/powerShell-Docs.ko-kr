---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 48dc7c8c47b28b65117dbeb568e23a802a9b0a49
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-configuration-resource-and-report-repositories"></a><span data-ttu-id="ddd82-102">구성, 리소스 및 보고서 리포지토리의 분리</span><span class="sxs-lookup"><span data-stu-id="ddd82-102">Separation of Configuration, Resource and Report Repositories</span></span>

<span data-ttu-id="ddd82-103">이번 릴리스에서는 하나 이상의 DSC 끌어오기 서버로 끌어오고 보고해야 하는 모든 유연성을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd82-103">In this release we allow you all of the flexibility that you need to pull and report to one or more DSC Pull Servers.</span></span> <span data-ttu-id="ddd82-104">각 끝점을 개별적으로 정의하여 한 위치에서는 구성을, 다른 위치에서는 리소스를 끌어와 또 다른 위치에 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddd82-104">Each endpoint can be defined separately so that you can pull configurations from one location, resources from another and report to yet another location.</span></span> 

<span data-ttu-id="ddd82-105">자세한 내용은 [구성 ID를 사용하여 끌어오기 클라이언트 설정](https://msdn.microsoft.com/powershell/dsc/pullclientconfigid) 또는 [구성 이름을 사용하여 끌어오기 클라이언트 설정](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ddd82-105">For more information, see [Setting up a pull client using configuration ID](https://msdn.microsoft.com/powershell/dsc/pullclientconfigid) or [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>

