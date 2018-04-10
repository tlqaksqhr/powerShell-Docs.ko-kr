---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Set-PSRepository
ms.openlocfilehash: 0b555f31241bad15c5e99f3db0136d88ff7ab717
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="set-psrepository"></a>Set-PSRepository

Set-PSRepository는 등록된 리포지토리에 대한 값을 설정합니다.

## <a name="description"></a>설명

Set-PSRepository cmdlet은 등록된 모듈 리포지토리에 대한 값을 설정합니다.

## <a name="cmdlet-syntax"></a>Cmdlet 구문

```powershell
Get-Command -Name Set-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet 온라인 도움말 참조

[Set-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517128)

## <a name="example-commands"></a>예제 명령

```powershell
PS C:\> Register-PSRepository -Name myRepository -SourceLocation "https://www.myget.org/F/powershellgetdemo/api/v2" -InstallationPolicy Trusted
PS C:\> Get-PSRepository
Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Trusted              https://www.myget.org/F/powershellgetdemo/api/v2

# Set installation Policy for a repository
PS C:\> Set-PSRepository -Name myRepository -InstallationPolicy Untrusted
PS C:\> Get-PSRepository

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Untrusted            https://www.myget.org/F/powershellgetdemo/api/v2
```


### <a name="set-psrepository-cmdlet-with-script-sharing-support"></a>스크립트 공유를 지원하는 Set-PSRepository cmdlet

Set-PSRepository cmdlet을 사용하여 **ScriptSourceLocation** 및 **ScriptPublishLocation**을 PSRepository에 추가합니다.
```powershell
# Add script sharing locations to an existing PSRepository using Set-PSRepository object.
Set-PSRepository -Name MyGallery `
                 -ScriptSourceLocation https://MyGallery.com/api/v2/items/psscript/ `
                 -ScriptPublishLocation https://MyGallery.com/api/v2/package/

Get-PSRepository -Name GalleryINT | Format-List * -Force

Name : GalleryINT
SourceLocation : https://MyGallery.com/api/v2/
Trusted : True
Registered : True
InstallationPolicy : Trusted
PackageManagementProvider : NuGet
PublishLocation : https://MyGallery.com/api/v2/package/
ScriptSourceLocation : https://MyGallery.com/api/v2/items/psscript/
ScriptPublishLocation : https://MyGallery.com/api/v2/package/
ProviderOptions : {}

```