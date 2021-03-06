---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: 라이선스 동의가 필요한 모듈
ms.openlocfilehash: fe197ea271e18580a221ad4d5245b685bd81775b
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048475"
---
# <a name="modules-requiring-license-acceptance"></a>라이선스 동의가 필요한 모듈

## <a name="synopsis"></a>요약

일부 모듈 게시자의 법률 부서에서는 고객이 PowerShell 갤러리에서 모듈을 설치하기 전에 명시적으로 라이선스에 동의하도록 요구합니다. 직접적이든 다른 항목에 대한 종속성으로서든, 사용자가 PowerShellGet을 사용하여 모듈을 설치, 업데이트 또는 저장하고 해당 모듈에서 사용자가 라이선스에 동의할 것을 요구하는 경우 사용자는 라이선스에 동의함을 나타내야 합니다. 그러하지 않으면 작업에 실패합니다.

## <a name="publish-requirements-for-modules"></a>모듈에 요구 사항 게시

사용자에게 라이선스 동의를 요구하는 모듈은 다음 요구 사항을 충족해야 합니다.

- 모듈 매니페스트의 PSData 섹션에 RequireLicenseAcceptance = $True가 포함되어야 합니다.
- 모듈의 루트 디렉터리에 license.txt 파일이 포함되어야 합니다.
- 모듈 매니페스트에 라이선스 URI가 포함되어야 합니다.
- 모듈은 PowerShellGet 형식 버전 2.0 이상으로 게시되어야 합니다.

## <a name="impact-on-installsaveupdate-module"></a>Install/Save/Update-Module에 미치는 영향

- Install/Save/Update cmdlet은 사용자가 라이선스를 확인한 것처럼 동작하는 새 매개 변수 –AcceptLicense를 지원합니다.
- RequiredLicenseAcceptance가 True이고 –AcceptLicense가 지정되지 않은 경우 사용자에게 license.txt가 표시되고 &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;(이 라이선스 조건에 동의하시나요(예/아니요/모두 예/모두 아니요))가 표시됩니다.
  - 라이선스에 동의하는 경우
    - **Save-Module:** 모듈이 사용자의 시스템에 복사됩니다.
    - **Install-Module:** 모듈이 사용자의 시스템에서 적절한 폴더(범위 기준)에 복사됩니다.
    - **Update-Module:** 모듈이 업데이트됩니다.
  - 라이선스에 동의하지 않는 경우
    - 작업이 취소됩니다.
- 모든 cmdlet은 라이선스 동의가 필요한 메타데이터(requireLicenseAcceptance 및 형식 버전)를 확인합니다.
  - 클라이언트의 형식 버전이 2.0보다 이전 버전인 경우 작업에 실패하고 사용자에게 클라이언트를 업데이트하도록 요청합니다.
  - 모듈이 2.0보다 이전인 형식 버전으로 게시된 경우 requireLicenseAcceptance 플래그가 무시됩니다.


 ## <a name="module-dependencies"></a>모듈 종속성
- 설치/저장/업데이트 작업 중 종속 모듈(모듈에 종속되는 작업)에 라이선스 동의가 필요한 경우 라이선스 동의 동작(위)이 필요합니다.
- 시스템에 설치되면서 모듈 버전이 로컬 카탈로그에 이미 나열되어 있는 경우 라이선스 확인을 무시합니다.
- 설치/저장/업데이트 작업 중 종속 모듈에 라이선스가 필요한데 라이선스 동의가 발생하지 않는 경우 작업에 실패하고 항목 설치/저장/업데이트 실패에 대한 일반적인 프로세스를 따릅니다.

 ## <a name="impact-on--force"></a>-Force에 대한 영향

-Force를 지정하여 라이선스에 동의할 수 없습니다. 설치 권한에 대해 –AcceptLicense가 필요합니다. –Force가 지정되고 RequiredLicenseAcceptance가 True이고 –AcceptLicense가 지정되지 않으면 작업에 실패합니다.

## <a name="examples"></a>예제

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>예제 1: 모듈 매니페스트를 업데이트하여 라이선스 동의 요구

```PowerShell
PS> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

이 명령은 매니페스트 파일을 업데이트하고 RequireLicenseAcceptance 플래그를 true로 설정합니다.

### <a name="example-2-install-module-requiring-license-acceptance"></a>예제 2: 라이선스 동의가 필요한 모듈 설치

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):

```

이 명령은 license.txt 파일의 라이선스를 표시하고 사용자에게 라이선스에 동의하라는 메시지를 표시합니다.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>예제 3: -AcceptLicense로 라이선스 동의가 필요한 모듈 설치

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

라이선스에 동의하라는 메시지가 표시되지 않고 모듈이 설치됩니다.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>예제 4: -Force로 라이선스 동의가 필요한 모듈 설치

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>예제 5: 라이선스 동의가 필요한 종속성이 있는 모듈 설치

모듈 ‘ModuleWithDependency’는 모듈 'ModuleRequireLicenseAcceptance'에 종속됩니다. 사용자에게 라이선스에 동의하라는 메시지가 표시됩니다.

```PowerShell
PS> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>예제 6: 라이선스 동의 및 -AcceptLicense가 필요한 종속성이 있는 모듈 설치

모듈 ‘ModuleWithDependency’는 모듈 'ModuleRequireLicenseAcceptance'에 종속됩니다. -AcceptLicense가 지정되면 사용자에게 라이선스에 동의하라는 메시지가 표시되지 않습니다.

```PowerShell
PS>  Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>예제 7: PSGetFormatVersion 2.0 이전의 클라이언트에서 라이선스 동의가 필요한 모듈 설치

```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```

### <a name="example-8-save-module-requiring-license-acceptance"></a>예제 8: 라이선스 동의가 필요한 모듈 저장

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

이 명령은 license.txt 파일의 라이선스를 표시하고 사용자에게 라이선스에 동의하라는 메시지를 표시합니다.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>예제 9: -AcceptLicense로 라이선스 동의가 필요한 모듈 저장

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

라이선스에 동의하라는 메시지가 표시되지 않고 모듈이 저장됩니다.

### <a name="example-10-update-module-requiring-license-acceptance"></a>예제 10: 라이선스 동의가 필요한 모듈 업데이트

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

이 명령은 license.txt 파일의 라이선스를 표시하고 사용자에게 라이선스에 동의하라는 메시지를 표시합니다.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>예제 11: -AcceptLicense로 라이선스 동의가 필요한 모듈 업데이트

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

라이선스에 동의하라는 메시지가 표시되지 않고 모듈이 업데이트됩니다.

## <a name="more-details"></a>자세한 내용

### <a name="require-license-acceptance-for-scriptsscript-license-acceptancemd"></a>[스크립트에 대한 라이선스 동의 필요](./script-license-acceptance.md)

### <a name="require-license-acceptance-support-on-powershellgalleryhow-toworking-with-itemsitems-that-require-license-acceptancemd"></a>[PowerShellGallery에서 라이선스 동의 지원 필요](../how-to/working-with-items/items-that-require-license-acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationhow-toworking-with-itemsdeploy-to-azure-automationmd"></a>[Azure Automation에 배포에 대한 라이선스 동의 필요](../how-to/working-with-items/deploy-to-azure-automation.md)