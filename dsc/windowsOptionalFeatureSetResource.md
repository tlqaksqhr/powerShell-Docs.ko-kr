---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC WindowsOptionalFeatureSet 리소스
ms.openlocfilehash: 3329e0d0f1988a2ee20eb848da943ff1b22bd4df
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="22d26-103">DSC WindowsOptionalFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="22d26-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="22d26-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="22d26-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="22d26-105">Windows PowerShell DSC(필요한 상태 구성)의 **WindowsOptionalFeatureSet** 리소스에서는 대상 노드에서 선택적 기능을 사용할 수 있도록 설정하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="22d26-106">이 리소스는 `Name` 속성에 지정된 각 기능에 대해 [WindowsOptionalFeature 리소스](windowsOptionalFeatureResource.md)를 호출하는 [복합 리소스](authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="22d26-107">여러 선택적 Windows 기능을 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="22d26-108">구문</span><span class="sxs-lookup"><span data-stu-id="22d26-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="22d26-109">속성</span><span class="sxs-lookup"><span data-stu-id="22d26-109">Properties</span></span>

|  <span data-ttu-id="22d26-110">속성</span><span class="sxs-lookup"><span data-stu-id="22d26-110">Property</span></span>  |  <span data-ttu-id="22d26-111">설명</span><span class="sxs-lookup"><span data-stu-id="22d26-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="22d26-112">이름</span><span class="sxs-lookup"><span data-stu-id="22d26-112">Name</span></span>| <span data-ttu-id="22d26-113">사용 또는 사용하지 않도록 설정하려는 기능의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="22d26-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="22d26-114">Ensure</span></span>| <span data-ttu-id="22d26-115">기능을 사용하도록 설정할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="22d26-116">기능을 사용하도록 설정하려면 이 속성을 "Enable"로 설정하고 기능을 사용하지 않도록 설정하려면 속성을 "Disable"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="22d26-117">원본</span><span class="sxs-lookup"><span data-stu-id="22d26-117">Source</span></span>| <span data-ttu-id="22d26-118">구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-118">Not implemented.</span></span>|
| <span data-ttu-id="22d26-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="22d26-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="22d26-120">기능을 사용하도록 설정하기 위해 원본 파일을 검색할 때 DISM에서 WU(Windows 업데이트)에 연결하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="22d26-121">$true이면 DISM에서 WU에 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="22d26-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="22d26-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="22d26-123">기능을 사용하지 않도록 설정할 때(즉, **Ensure**를 "Absent"로 설정할 때) 기능과 연결된 파일을 모두 제거하려면 **$true**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="22d26-124">로그 수준</span><span class="sxs-lookup"><span data-stu-id="22d26-124">LogLevel</span></span>| <span data-ttu-id="22d26-125">로그에 표시되는 최대 출력 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="22d26-126">사용 가능한 값은 "ErrorsOnly"(오류만 기록), "ErrorsAndWarning"(오류와 경고 기록) 및 "ErrorsAndWarningAndInformation"(오류, 경고 및 디버그 정보 기록)입니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="22d26-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="22d26-127">LogPath</span></span>| <span data-ttu-id="22d26-128">리소스 공급자가 작업을 기록할 로그 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="22d26-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="22d26-129">DependsOn</span></span>| <span data-ttu-id="22d26-130">이 리소스를 구성하기 전에 다른 리소스의 구성을 실행해야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="22d26-131">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="22d26-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|