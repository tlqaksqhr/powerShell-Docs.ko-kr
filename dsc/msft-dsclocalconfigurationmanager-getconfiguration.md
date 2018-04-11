---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 GetConfiguration 메서드
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1d881-103">MSFT_DSCLocalConfigurationManager 클래스의 GetConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="1d881-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1d881-104">구성 문서를 관리 노드로 보내고, 구성 에이전트의 **Get** 메서드를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="1d881-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="1d881-105">구문</span><span class="sxs-lookup"><span data-stu-id="1d881-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="1d881-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1d881-106">Parameters</span></span>
----------

<span data-ttu-id="1d881-107">*configurationData* \[in\] 보낼 구성 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d881-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="1d881-108">*configurations* \[out\] 반환 시, 구성의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d881-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="1d881-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="1d881-109">Return value</span></span>
------------

<span data-ttu-id="1d881-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d881-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d881-111">설명</span><span class="sxs-lookup"><span data-stu-id="1d881-111">Remarks</span></span>

<span data-ttu-id="1d881-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="1d881-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1d881-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1d881-113">Requirements</span></span>
------------
><span data-ttu-id="1d881-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1d881-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1d881-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d881-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1d881-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d881-116">See also</span></span>


[<span data-ttu-id="1d881-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1d881-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)