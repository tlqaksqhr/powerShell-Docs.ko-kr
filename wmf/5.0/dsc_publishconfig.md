---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e921a5ead21f52b7e0d9efd9335c44b99d7d6802
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="16e9c-102">구성 문서를 적용하지 않고 제공</span><span class="sxs-lookup"><span data-stu-id="16e9c-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="16e9c-103">[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet은 구성 MOF 파일을 대상 노드에 복사하지만 구성을 적용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16e9c-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span> <span data-ttu-id="16e9c-104">이 구성은 다음 일관성 검사 중이나 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet을 실행할 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="16e9c-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>

