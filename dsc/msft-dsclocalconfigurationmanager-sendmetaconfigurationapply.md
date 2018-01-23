---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 SendMetaConfigurationApply 메서드"
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="aec8d-103">MSFT_DSCLocalConfigurationManager 클래스의 SendMetaConfigurationApply 메서드</span><span class="sxs-lookup"><span data-stu-id="aec8d-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="aec8d-104">구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aec8d-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="aec8d-105">구문</span><span class="sxs-lookup"><span data-stu-id="aec8d-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="aec8d-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="aec8d-106">Parameters</span></span>
----------

<span data-ttu-id="aec8d-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="aec8d-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="aec8d-108">구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="aec8d-108">The environment data for the configuration.</span></span>

<span data-ttu-id="aec8d-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="aec8d-109">*force* \[in\]</span></span>  
<span data-ttu-id="aec8d-110">**true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="aec8d-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="aec8d-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="aec8d-111">Return value</span></span>
------------

<span data-ttu-id="aec8d-112">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aec8d-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="aec8d-113">설명</span><span class="sxs-lookup"><span data-stu-id="aec8d-113">Remarks</span></span>

<span data-ttu-id="aec8d-114">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="aec8d-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aec8d-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="aec8d-115">Requirements</span></span>
------------
><span data-ttu-id="aec8d-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="aec8d-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="aec8d-117">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="aec8d-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="aec8d-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aec8d-118">See also</span></span>


[<span data-ttu-id="aec8d-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="aec8d-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



