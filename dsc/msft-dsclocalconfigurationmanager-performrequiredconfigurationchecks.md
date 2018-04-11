---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 PerformRequiredConfigurationChecks 메서드
ms.openlocfilehash: 9cc4384088fcc39b09979b8ae4d023fc46307b13
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="db403-103">MSFT_DSCLocalConfigurationManager 클래스의 PerformRequiredConfigurationChecks 메서드</span><span class="sxs-lookup"><span data-stu-id="db403-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="db403-104">작업 스케줄러를 사용해 일관성 확인을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="db403-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="db403-105">구문</span><span class="sxs-lookup"><span data-stu-id="db403-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="db403-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="db403-106">Parameters</span></span>
----------

<span data-ttu-id="db403-107">*Flags* \[in\] 실행할 일관성 확인 유형을 지정하는 비트 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="db403-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="db403-108">다음 값은 올바르며, 비트 **OR** 작업을 사용해 조합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db403-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="db403-109">Value</span><span class="sxs-lookup"><span data-stu-id="db403-109">Value</span></span> |<span data-ttu-id="db403-110">설명</span><span class="sxs-lookup"><span data-stu-id="db403-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="db403-111">**1**</span><span class="sxs-lookup"><span data-stu-id="db403-111">**1**</span></span> | <span data-ttu-id="db403-112">일반 일관성 확인입니다.</span><span class="sxs-lookup"><span data-stu-id="db403-112">A normal consistency check.</span></span> |
|<span data-ttu-id="db403-113">**2**</span><span class="sxs-lookup"><span data-stu-id="db403-113">**2**</span></span> | <span data-ttu-id="db403-114">다시 부팅한 후 일관성 확인의 연속입니다.</span><span class="sxs-lookup"><span data-stu-id="db403-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="db403-115">이 값은 다른 값과 결합하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db403-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="db403-116">**4**</span><span class="sxs-lookup"><span data-stu-id="db403-116">**4**</span></span> | <span data-ttu-id="db403-117">구성은 노드의 메타 구성에 지정된 끌어오기 서버에서 끌어와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db403-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="db403-118">**5** 값인 경우 이 값은 항상 **1**과 결합되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db403-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="db403-119">**8**</span><span class="sxs-lookup"><span data-stu-id="db403-119">**8**</span></span> | <span data-ttu-id="db403-120">보고서 서버에 상태를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="db403-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="db403-121">반환 값</span><span class="sxs-lookup"><span data-stu-id="db403-121">Return value</span></span>
------------

<span data-ttu-id="db403-122">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="db403-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="db403-123">설명</span><span class="sxs-lookup"><span data-stu-id="db403-123">Remarks</span></span>

<span data-ttu-id="db403-124">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="db403-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="db403-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="db403-125">Requirements</span></span>
------------
><span data-ttu-id="db403-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="db403-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="db403-127">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="db403-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="db403-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db403-128">See also</span></span>


[<span data-ttu-id="db403-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="db403-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)