---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApplyAsync 메서드"
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="10c44-103">MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApplyAsync 메서드</span><span class="sxs-lookup"><span data-stu-id="10c44-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="10c44-104">구성 문서를 비동기적으로 관리 노드로 보내고, 구성 에이전트를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="10c44-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="10c44-105">구문</span><span class="sxs-lookup"><span data-stu-id="10c44-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="10c44-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="10c44-106">Parameters</span></span>
----------

<span data-ttu-id="10c44-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="10c44-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="10c44-108">구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="10c44-108">The environment data for the configuration.</span></span>

<span data-ttu-id="10c44-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="10c44-109">*force* \[in\]</span></span>  
<span data-ttu-id="10c44-110">**true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="10c44-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="10c44-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="10c44-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="10c44-112">구성을 보낼 작업의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="10c44-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="10c44-113">반환 값</span><span class="sxs-lookup"><span data-stu-id="10c44-113">Return value</span></span>
------------

<span data-ttu-id="10c44-114">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="10c44-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="10c44-115">설명</span><span class="sxs-lookup"><span data-stu-id="10c44-115">Remarks</span></span>

<span data-ttu-id="10c44-116">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="10c44-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="10c44-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="10c44-117">Requirements</span></span>
------------
><span data-ttu-id="10c44-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="10c44-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="10c44-119">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="10c44-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="10c44-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10c44-120">See also</span></span>


[<span data-ttu-id="10c44-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="10c44-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



