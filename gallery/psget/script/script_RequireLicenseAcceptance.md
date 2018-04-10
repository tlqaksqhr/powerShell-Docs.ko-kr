---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 4a2dc39c2b6c380fb4ca94f9fd071ed9cdb35049
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="65601-103">스크립트에 대한 라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="65601-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="65601-104">스크립트에 대한 라이선스 동의가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65601-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="65601-105">그러나 라이선스 동의가 필요한 모듈에서 스크립트가 사용되는 시나리오는 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="65601-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="65601-106">스크립트 명령(Install-Script/Save-Script/Update-Script)은 새 매개 변수인 -AcceptLicense(사용자가 라이선스를 확인한 것처럼 동작)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="65601-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="65601-107">-AcceptLicense가 지정되지 않으면 종속 모듈에 대한 license.txt가 사용자에게 표시되고 라이선스에 동의하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65601-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="65601-108">예제</span><span class="sxs-lookup"><span data-stu-id="65601-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="65601-109">예제 1: 라이선스 동의가 필요한 종속성이 있는 스크립트 설치</span><span class="sxs-lookup"><span data-stu-id="65601-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="65601-110">‘ScriptRequireLicenseAcceptance’ 스크립트는 'ModuleRequireLicenseAcceptance' 모듈에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="65601-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="65601-111">사용자에게 라이선스에 동의하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65601-111">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="65601-112">예제 2: 라이선스 동의 및 -AcceptLicense가 필요한 종속성이 있는 스크립트 설치</span><span class="sxs-lookup"><span data-stu-id="65601-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="65601-113">‘ScriptRequireLicenseAcceptance’ 스크립트는 'ModuleRequireLicenseAcceptance' 모듈에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="65601-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="65601-114">-AcceptLicense가 지정되면 사용자에게 라이선스에 동의하라는 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65601-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="65601-115">자세한 내용</span><span class="sxs-lookup"><span data-stu-id="65601-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="65601-116">모듈에 대한 라이선스 동의 지원 필요</span><span class="sxs-lookup"><span data-stu-id="65601-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="65601-117">PowerShellGallery에서 라이선스 동의 지원 필요</span><span class="sxs-lookup"><span data-stu-id="65601-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="65601-118">Azure Automation에 배포에 대한 라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="65601-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)