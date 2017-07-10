---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC PackageManagement 리소스"
ms.openlocfilehash: a984fbf5db561a696d89b60dde8b92096c6e4924
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a id="dsc-packagemanagement-resource" class="xliff"></a>
# DSC PackageManagement 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)의 **PackageManagement** 리소스는 대상 노드에서 패키지 관리 패키지를 설치하거나 제거하는 메커니즘을 제공합니다. 이 리소스를 사용하려면 http://PowerShellGallery.com에서 제공하는 **PackageManagement** 모듈이 필요합니다.

<a id="syntax" class="xliff"></a>
## 구문

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

<a id="properties" class="xliff"></a>
## 속성
|  속성  |  설명   | 
|---|---| 
| 이름| 설치하거나 제거할 패키지의 이름을 지정합니다.| 
| 원본| 패키지를 찾을 수 있는 패키지 원본의 이름을 지정합니다. 이는 Register-PackageSource 또는 PackageManagementSource DSC 리소스에 등록된 원본 또는 URI일 수 있습니다. DSC 리소스 MSFT_PackageManagementSource도 패키지 원본을 등록할 수 있습니다.| 
| Ensure| 패키지를 설치할지 또는 제거할지를 결정합니다.| 
| RequiredVersion| 설치할 패키지의 정확한 버전을 지정합니다. 이 매개 변수를 지정하지 않으면 이 DSC 리소스는 MaximumVersion 매개 변수로 지정된 최대 버전도 만족하는 패키지의 사용 가능한 최신 버전을 설치합니다.| 
| MinimumVersion| 설치할 패키지의 최소 허용 버전을 지정합니다. 이 매개 변수를 추가하지 않으면 이 DSC 리소스는 MaximumVersion 매개 변수로 지정된 최대 지정 버전도 만족하는 패키지의 사용 가능한 가장 높은 버전을 설치합니다.| 
| MaximumVersion| 설치할 패키지의 최대 허용 버전을 지정합니다. 이 매개 변수를 지정하지 않으면 이 DSC 리소스는 패키지의 사용 가능한 가장 높은 번호가 지정된 버전을 설치합니다.| 
| SourceCredential | 지정된 패키지 공급자 또는 원본에 대한 패키지를 설치하는 권한이 있는 사용자 계정을 지정합니다.| 
| ProviderName| 패키지 검색 범위를 지정할 패키지 공급자 이름을 지정합니다. Get-PackageProvider cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.| 
| AdditionalParameters| Hashtable로 전달되는 공급자별 매개 변수입니다. 예를 들어 NuGet 공급자의 경우 DestinationPath와 같은 추가 매개 변수를 전달할 수 있습니다.| 

<a id="additional-parameters" class="xliff"></a>
## 추가 매개 변수
다음 표에는 AdditionalParameters 속성에 대한 옵션이 나와 있습니다.
|  매개 변수  | 설명   | 
|---|---|
| DestinationPath| 기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다. 패키지를 설치할 파일 위치를 지정합니다.|
| InstallationPolicy| 기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다. 패키지 원본을 신뢰할 수 있는지를 결정합니다. "Untrusted"와 "Trusted" 중 하나입니다.|

<a id="example" class="xliff"></a>
## 예제

이 예제에서는 **PackageManagement** DSC 리소스를 사용하여 **JQuery** NuGet 패키지 및 **GistProvider** PowerShell 모듈을 설치합니다. 이 예제에서는 먼저 필요한 패키지 원본을 사용할 수 있는지를 확인한 다음 **JQuery** 및 **GistProvider** 패키지(각각 NuGet 및 PowerShell)의 필요한 상태를 정의합니다.

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```

