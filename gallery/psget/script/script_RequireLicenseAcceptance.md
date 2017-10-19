---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 7092fb2e63b9e2b1eca59cd418317631bff8b172
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2017
---
# <a name="requiring-license-acceptance-for-scripts"></a>스크립트에 대한 라이선스 동의 필요

스크립트에 대한 라이선스 동의가 지원되지 않습니다. 그러나 라이선스 동의가 필요한 모듈에서 스크립트가 사용되는 시나리오는 지원됩니다.

스크립트 명령(Install-Script/Save-Script/Update-Script)은 새 매개 변수인 -AcceptLicense(사용자가 라이선스를 확인한 것처럼 동작)를 지원합니다. -AcceptLicense가 지정되지 않으면 종속 모듈에 대한 license.txt가 사용자에게 표시되고 라이선스에 동의하라는 메시지가 표시됩니다.

## <a name="examples"></a>예제

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>예제 1: 라이선스 동의가 필요한 종속성이 있는 스크립트 설치
‘ScriptRequireLicenseAcceptance’ 스크립트는 'ModuleRequireLicenseAcceptance' 모듈에 종속됩니다. 사용자에게 라이선스에 동의하라는 메시지가 표시됩니다.
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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>예제 2: 라이선스 동의 및 -AcceptLicense가 필요한 종속성이 있는 스크립트 설치
‘ScriptRequireLicenseAcceptance’ 스크립트는 'ModuleRequireLicenseAcceptance' 모듈에 종속됩니다. -AcceptLicense가 지정되면 사용자에게 라이선스에 동의하라는 메시지가 표시되지 않습니다.
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>자세한 내용
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[모듈에 대한 라이선스 동의 지원 필요](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[PowerShellGallery에서 라이선스 동의 지원 필요](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[Azure Automation에 배포에 대한 라이선스 동의 필요](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
