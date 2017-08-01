---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC PackageManagementSource 리소스"
ms.openlocfilehash: 80d157aff5bf7685a797baaf6a26215f02473096
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)의 **PackageManagementSource** 리소스는 대상 노드에서 패키지 관리 원본을 등록하거나 등록 취소하는 메커니즘을 제공합니다. **이 방법으로 등록된 패키지 관리 원본은 시스템 계정이나 DSC 엔진에서 사용할 수 있는 시스템 컨텍스트에서 등록됩니다.** 이 리소스를 사용하려면 http://PowerShellGallery.com에서 제공하는 **PackageManagement** 모듈이 필요합니다.

## <a name="syntax"></a>구문

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성
|  속성  |  설명   | 
|---|---| 
| 이름| 시스템에서 등록하거나 등록 취소할 패키지 원본의 이름을 지정합니다.| 
| Ensure| 패키지 원본을 등록할지 또는 등록 취소할지를 결정합니다.| 
| InstallationPolicy| 패키지 원본을 신뢰할 수 있는지를 결정합니다. "Untrusted"와 "Trusted" 중 하나입니다.| 
| ProviderName| 패키지 원본과 상호 운용할 수 있는 OneGet 공급자의 이름을 지정합니다.| 
| SourceUri| 패키지 원본의 URI를 지정합니다.| 
| SourceCredential| 원격 소스에 있는 패키지에 액세스할 수 있도록 합니다.| 

## <a name="example"></a>예제

이 예제에서는 **PackageManagementSource** DSC 리소스를 사용하여 http://nuget.org 패키지 원본을 등록합니다.

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

