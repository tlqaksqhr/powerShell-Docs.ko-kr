---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드
ms.openlocfilehash: f1ac626c5ef18b7ed14f3754ab39139db2a2a2d7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="1bd61-103">사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드</span><span class="sxs-lookup"><span data-stu-id="1bd61-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="1bd61-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1bd61-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1bd61-105">Windows PowerShell DSC(필요한 상태 구성)은 환경을 구성하는 데 사용할 수 있는 기본 제공 리소스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd61-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="1bd61-106">(자세한 내용은 [Built-In Windows PowerShell Desired State Configuration Resources(기본 제공 Windows PowerShell 필요한 상태 구성 리소스)](builtInResource.md)를 참조하세요.) 이 항목에서는 리소스 개발에 대한 개요와 특정 정보 및 예제가 있는 항목에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd61-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="1bd61-107">DSC 리소스 구성 요소</span><span class="sxs-lookup"><span data-stu-id="1bd61-107">DSC resource components</span></span>

<span data-ttu-id="1bd61-108">DSC 리소스는 Windows PowerShell 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="1bd61-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="1bd61-109">모듈에는 리소스에 대한 스키마(구성 가능한 속성 정의)와 구현(구성으로 지정한 실제 작업을 수행하는 코드)이 모두 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bd61-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="1bd61-110">DSC 리소스 스키마는 MOF 파일에 정의할 수 있으며, 구현은 스크립트 모듈에 의해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bd61-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="1bd61-111">버전 5에 있는 PowerShell 클래스의 지원으로 시작하여, 스키마와 구현은 클래스에서 모두 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bd61-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="1bd61-112">다음 항목에서는 DSC 리소스를 만드는 방법을 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd61-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="1bd61-113">Writing a custom DSC resource with MOF(MOF를 사용하여 사용자 지정 DSC 리소스 작성)</span><span class="sxs-lookup"><span data-stu-id="1bd61-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="1bd61-114">Implementing a DSC resource in C#(C#에서 DSC 리소스 구현)</span><span class="sxs-lookup"><span data-stu-id="1bd61-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="1bd61-115">PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성</span><span class="sxs-lookup"><span data-stu-id="1bd61-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="1bd61-116">Composite resources: Using a DSC configuration as a resource(복합 리소스: DSC 구성을 리소스로 사용)</span><span class="sxs-lookup"><span data-stu-id="1bd61-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="1bd61-117">Using the Resource Designer tool(리소스 디자이너 도구 사용)</span><span class="sxs-lookup"><span data-stu-id="1bd61-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)