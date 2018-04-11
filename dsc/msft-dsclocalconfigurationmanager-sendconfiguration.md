---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드
ms.openlocfilehash: 07ae48dd456e68be4ad0b09127ba9801359fd101
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b383e-103">MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="b383e-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b383e-104">구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b383e-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="b383e-105">구문</span><span class="sxs-lookup"><span data-stu-id="b383e-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="b383e-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b383e-106">Parameters</span></span>
----------

<span data-ttu-id="b383e-107">*ConfigurationData* \[in\] 구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="b383e-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="b383e-108">*force* \[in\] **true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b383e-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b383e-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="b383e-109">Return value</span></span>
------------

<span data-ttu-id="b383e-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b383e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b383e-111">설명</span><span class="sxs-lookup"><span data-stu-id="b383e-111">Remarks</span></span>

<span data-ttu-id="b383e-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b383e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b383e-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b383e-113">Requirements</span></span>
------------
><span data-ttu-id="b383e-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b383e-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b383e-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b383e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b383e-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b383e-116">See also</span></span>


[<span data-ttu-id="b383e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b383e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)