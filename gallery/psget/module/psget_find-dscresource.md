---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 6c5713f122d48e9c9d5e0aa45dc14047afc56102
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2018
---
# <a name="find-dscresource"></a>Find-DscResource

모듈에서 DSC 리소스를 찾습니다.

## <a name="description"></a>설명

Find-DscResource cmdlet은 등록된 리포지토리에서 지정된 조건과 일치하는, 모듈에 포함된 [DSC(필요한 상태 구성)](https://msdn.microsoft.com/PowerShell/dsc/overview) 리소스를 찾습니다.
이 cmdlet이 찾는 각 모듈에 대해 Find-DscResource는 PSGetDscResourceInfo 개체를 반환하며, 이 개체를 Install-Module에 파이프하면 이 cmdlet이 반환하는 리소스가 포함된 모듈을 설치할 수 있습니다.

DSC는 소프트웨어 서비스에 대한 구성 데이터를 배포 및 관리하고 이러한 서비스가 실행되는 환경을 관리할 수 있도록 해주는 Windows PowerShell의 새로운 관리 플랫폼입니다.

DSC(필요한 상태 구성) 리소스에서는 DSC 구성에 대한 구성 요소를 제공합니다. 리소스는 구성할 수 있는 속성(스키마)을 노출하고 LCM(로컬 구성 관리자)이 "그대로 수행"하기 위해 호출하는 PowerShell 스크립트 함수를 포함합니다.

리소스는 파일만큼 일반적이거나 IIS 서버만큼 특별한 것을 모델링할 수 있습니다. 같은 리소스들의 그룹은 모든 필수 파일을 이식 가능한 구조로 정리하고, 리소스를 사용하려고 한 방법을 식별하는 메타데이터를 포함하는 DSC 모듈에 결합됩니다.

- Find-DscResource는 버전 매개 변수(MinimumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.
  - 이러한 매개 변수는 함께 사용할 수 없습니다.
  - 이 버전 매개 변수는 와일드카드 없이 단일 모듈 이름과 함께 사용해야 합니다.
  - RequiredVersion 매개 변수를 지정하지 않으면 Find-DscResource는 지정된 최소 버전과 같거나 그 이상인 최신 버전의 모듈 또는 최소 버전이 지정되지 않은 경우 최신 버전의 모듈을 반환합니다.
  - RequiredVersion 매개 변수를 지정하면 Find-DscResource는 지정된 버전과 정확하게 일치하는 버전의 모듈만 반환합니다.
- Find-DscResource는 -Tag 매개 변수를 사용하여 모듈 메타데이터를 필터링할 수 있습니다.
- Find-DscResource는 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.
- Find-DscResource는 등록된 모든 또는 일부 리포지토리의 모듈을 필터링할 수 있습니다.

## <a name="cmdlet-syntax"></a>Cmdlet 구문
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet 온라인 도움말 참조

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a>예제 명령
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

