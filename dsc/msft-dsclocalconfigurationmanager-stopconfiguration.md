---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cc7c7-103">MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="cc7c7-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cc7c7-104">진행 중인 구성 변경을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="cc7c7-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="cc7c7-105">구문</span><span class="sxs-lookup"><span data-stu-id="cc7c7-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="cc7c7-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cc7c7-106">Parameters</span></span>
----------

<span data-ttu-id="cc7c7-107">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="cc7c7-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="cc7c7-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="cc7c7-108">Return value</span></span>
------------

<span data-ttu-id="cc7c7-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cc7c7-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc7c7-110">설명</span><span class="sxs-lookup"><span data-stu-id="cc7c7-110">Remarks</span></span>

<span data-ttu-id="cc7c7-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="cc7c7-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc7c7-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="cc7c7-112">Requirements</span></span>
------------
><span data-ttu-id="cc7c7-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cc7c7-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cc7c7-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc7c7-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cc7c7-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc7c7-115">See also</span></span>


[<span data-ttu-id="cc7c7-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cc7c7-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)