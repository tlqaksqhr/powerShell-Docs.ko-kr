---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApplyAsync 메서드"
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7a4bb-103">MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApplyAsync 메서드</span><span class="sxs-lookup"><span data-stu-id="7a4bb-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7a4bb-104">구성 문서를 비동기적으로 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="7a4bb-105">구문</span><span class="sxs-lookup"><span data-stu-id="7a4bb-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="7a4bb-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7a4bb-106">Parameters</span></span>
----------

<span data-ttu-id="7a4bb-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7a4bb-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="7a4bb-108">구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-108">The environment data for the configuration.</span></span>

<span data-ttu-id="7a4bb-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7a4bb-109">*force* \[in\]</span></span>  
<span data-ttu-id="7a4bb-110">**true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="7a4bb-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7a4bb-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="7a4bb-112">구성을 보낼 작업의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a4bb-113">반환 값</span><span class="sxs-lookup"><span data-stu-id="7a4bb-113">Return value</span></span>
------------

<span data-ttu-id="7a4bb-114">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a4bb-115">설명</span><span class="sxs-lookup"><span data-stu-id="7a4bb-115">Remarks</span></span>

<span data-ttu-id="7a4bb-116">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="7a4bb-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a4bb-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7a4bb-117">Requirements</span></span>
------------
><span data-ttu-id="7a4bb-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7a4bb-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7a4bb-119">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7a4bb-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7a4bb-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a4bb-120">See also</span></span>


[<span data-ttu-id="7a4bb-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7a4bb-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



