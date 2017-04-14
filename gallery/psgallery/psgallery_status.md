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
ms.openlocfilehash: 1886715c4b948e4bc59a51fb96d54b56b5b5afed
ms.sourcegitcommit: 809e4f1bdf218b283e84438151030bfa94ca956d
translationtype: HT
---
<a name="powershell-gallery-status"></a>PowerShell 갤러리 상태
=========================

## <a name="04112017---users-unable-to-log-in"></a>2017/04/11 - 사용자가 로그인 할 수 없음

__영향 요약__: 일부 사용자가 Azure AD 계정을 사용하여 PowerShell 갤러리에 로그인 할 수 없습니다. PowerShell 갤러리 운영 팀이 이 문제를 확인하고 있습니다. Microsoft 계정(Outlook.com, Live.com 등과 같은 도메인)을 지닌 사용자에게는 이 문제가 나타나지 않습니다. 
 
__근본 원인__: 미정  

__다음 단계__: Azure AD 팀과 함께 이 문제를 확인 중입니다. 

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017/03/27 - 해결됨: 개별 모듈 및 스크립트 페이지를 볼 수 없음

__영향 요약__: https://www.powershellgallery.com에서 개별 모듈 및 스크립트 페이지로 연결되는 직접 링크가 끊어졌습니다. 이 문제는 모든 지역에서 보고되었습니다. 이 문제는 Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt와 같은 PowerShellGet cmdlet이 계속 작동하는 데는 영향을 주지 않았습니다.

__근본 원인__: 엔지니어들은 Facebook과 같은 소셜 미디어 단추를 페이지에 가져오는 과정에서 문제가 생긴 것을 알아냈습니다.  

__해결 방법__: 엔지니어가 Facebook 개수 정보를 사용하지 않도록 설정하여 문제를 해결했습니다.

__다음 단계__: Facebook API 사용 문제를 해결하기 위해 내부 추적 문제를 열었습니다.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>2016/12/15 - PowerShellGallery 웹 사이트를 통해 메일을 보낼 수 없음

__영향 요약__: 2016/12/13과 2016/12/15 사이에 소유자에게 문의, 소유자 관리, 고객 지원 또는 신고하기를 통해 전송된 모든 메시지는 PowerShell 갤러리 관리자가 받지 못했습니다.  
__근본 원인__: 엔지니어는 SMTP 서버와의 인증 문제를 원인으로 식별했습니다.  
__해결 방법__: 엔지니어는 인증 문제를 해결하고 SMTP 서버에 대한 연결을 복원할 수 있었습니다.  
__다음 단계__: 이 시간 동안 소유자에게 문의, 소유자 관리, 고객 지원 또는 신고하기 링크를 사용하여 cgadmin@microsoft.com으로 메일을 보냈고 응답을 받지 못한 경우 다시 시도하세요. 불편을 드려 죄송합니다.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>2016년 8월 10일 - 해결됨: cgadmin@microsoft.com으로 메일을 보낼 수 없음

__영향 요약__: 2016년 8월 5일에서 2016년 8월 10일 사이 고객이 cgadmin@microsoft.com으로 메일을 보내거나 문의처 기능을 사용할 수 없었습니다.  
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

