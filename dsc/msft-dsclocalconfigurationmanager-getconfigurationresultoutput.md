---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationResultOutput 메서드"
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="04df3-103">MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationResultOutput 메서드</span><span class="sxs-lookup"><span data-stu-id="04df3-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="04df3-104">특정 작업에 연결된 구성 에이전트 출력을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="04df3-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="04df3-105">구문</span><span class="sxs-lookup"><span data-stu-id="04df3-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="04df3-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="04df3-106">Parameters</span></span>
----------

<span data-ttu-id="04df3-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="04df3-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="04df3-108">출력 데이터를 가져올 작업의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="04df3-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="04df3-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="04df3-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="04df3-110">출력이 이전 책갈피의 연속이어야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04df3-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="04df3-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="04df3-111">*output* \[out\]</span></span>  
<span data-ttu-id="04df3-112">지정한 작업의 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="04df3-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="04df3-113">반환 값</span><span class="sxs-lookup"><span data-stu-id="04df3-113">Return value</span></span>
------------

<span data-ttu-id="04df3-114">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="04df3-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="04df3-115">설명</span><span class="sxs-lookup"><span data-stu-id="04df3-115">Remarks</span></span>

<span data-ttu-id="04df3-116">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="04df3-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="04df3-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="04df3-117">Requirements</span></span>
------------
><span data-ttu-id="04df3-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="04df3-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="04df3-119">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="04df3-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="04df3-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04df3-120">See also</span></span>


[<span data-ttu-id="04df3-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="04df3-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



