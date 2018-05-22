---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 리소스
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-resources"></a>DSC 리소스

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC(필요한 상태 구성) 리소스에서는 DSC 구성에 대한 구성 요소를 제공합니다. 리소스는 구성할 수 있는 속성(스키마)을 노출하고 LCM(로컬 구성 관리자)이 "그대로 수행"하기 위해 호출하는 PowerShell 스크립트 함수를 포함합니다.

리소스는 파일만큼 일반적이거나 IIS 서버만큼 특별한 것을 모델링할 수 있습니다.  같은 리소스들의 그룹은 모든 필수 파일을 이식 가능한 구조로 정리하고, 리소스를 사용하려고 한 방법을 식별하는 메타데이터를 포함하는 DSC 모듈에 결합됩니다.

다음 항목에서는 DSC 리소스에 대해 설명합니다.

- [기본 제공 DSC 리소스](builtInResource.md)
- [사용자 지정 DSC 리소스 빌드](authoringResource.md)
- [기본 제공 Linux용 DSC 리소스](lnxBuiltInResources.md)