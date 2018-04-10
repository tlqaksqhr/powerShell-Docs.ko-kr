---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC 리소스
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="1ffb4-103">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="1ffb4-103">DSC Resources</span></span>

><span data-ttu-id="1ffb4-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1ffb4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1ffb4-105">DSC(필요한 상태 구성) 리소스에서는 DSC 구성에 대한 구성 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffb4-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="1ffb4-106">리소스는 구성할 수 있는 속성(스키마)을 노출하고 LCM(로컬 구성 관리자)이 "그대로 수행"하기 위해 호출하는 PowerShell 스크립트 함수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffb4-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="1ffb4-107">리소스는 파일만큼 일반적이거나 IIS 서버만큼 특별한 것을 모델링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ffb4-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="1ffb4-108">같은 리소스들의 그룹은 모든 필수 파일을 이식 가능한 구조로 정리하고, 리소스를 사용하려고 한 방법을 식별하는 메타데이터를 포함하는 DSC 모듈에 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ffb4-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="1ffb4-109">다음 항목에서는 DSC 리소스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ffb4-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="1ffb4-110">기본 제공 DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="1ffb4-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="1ffb4-111">사용자 지정 DSC 리소스 빌드</span><span class="sxs-lookup"><span data-stu-id="1ffb4-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="1ffb4-112">기본 제공 Linux용 DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="1ffb4-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)