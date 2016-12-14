---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: psgallery_status
ms.technology: powershell
ms.openlocfilehash: 2e9eed63e0cc6fbf66543ea528581c2728e999c7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
<a name="powershell-gallery-status"></a>PowerShell 갤러리 상태
=========================


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>2016년 8월 10일 - 해결됨: cgadmin@microsoft.com으로 메일을 보낼 수 없음

__영향 요약__: 2016년 8월 5일에서 2016년 8월 10일 사이 고객이 cgadmin@microsoft.com,으로 메일을 보내거나 문의처 기능을 사용할 수 없었습니다.  
__근본 원인__: 엔지니어가 원인을 메일 계정의 구성 변경으로 식별했습니다.  
__해결 방법__: 엔지니어가 구성 문제를 해결하기 위해 노력했습니다.  
__다음 단계__: 이 시간 동안 문의처 링크를 사용하거나 cgadmin@microsoft.com으로 메일을 보내고 응답을 받지 못한 경우 다시 시도하세요. 기다려 주셔서 감사합니다.



## <a name="7132016---download-items-failed"></a>2016년 7월 13일 - 항목 다운로드 실패

__영향 요약__: 2016년 7월 11일에서 2016년 7월 13일 사이 일부 고객이 PowerShell 갤러리에서 항목을 다운로드할 때 문제가 발생했습니다. 문제는 Install-Module/Install-Script 및 Save-Module/Save-Script에서 반환된 다음 오류 메시지에서 명확해졌습니다.

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__임시 근본 원인__: 엔지니어가 2016년 7월 11일 PowerShell 갤러리에 배포된 Azure CDN(콘텐츠 배달 네트워크)에서 문제를 식별했습니다.  
__해결 방법__: 엔지니어가 PowerShell 갤러리에서 Azure CDN을 사용하지 않도록 설정했습니다.  
__다음 단계__: 근본 원인을 조사하고 이후에 다시 발생하지 않도록 해결 방법을 개발하고 있습니다.


## <a name="5192016---download-items-failed"></a>2016년 5월 19일 - 항목 다운로드 실패
__영향 요약__: 2016년 5월 17일에서 2016년 5월 19일 사이 일부 고객이 PowerShell 갤러리에서 항목을 다운로드할 때 문제가 발생했습니다. 문제는 Install-Module/Install-Script 및 Save-Module/Save-Script에서 반환된 다음 오류 메시지에서 명확해졌습니다.

```PowerShell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

__임시 근본 원인__: 엔지니어가 2016년 5월 17일 PowerShell 갤러리에 배포된 Azure CDN(콘텐츠 배달 네트워크)의 기본 공급자에서 중단을 식별했습니다.  
__해결 방법__: 엔지니어가 PowerShell 갤러리에서 Azure CDN을 사용하지 않도록 설정했습니다.  
__다음 단계__: 근본 원인을 조사하고 이후에 다시 발생하지 않도록 해결 방법을 개발하고 있습니다.

