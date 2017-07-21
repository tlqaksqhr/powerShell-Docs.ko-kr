---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드"
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="884dd-103">MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="884dd-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="884dd-104">구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="884dd-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="884dd-105">구문</span><span class="sxs-lookup"><span data-stu-id="884dd-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="884dd-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="884dd-106">Parameters</span></span>
----------

<span data-ttu-id="884dd-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="884dd-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="884dd-108">구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="884dd-108">The environment data for the configuration.</span></span>

<span data-ttu-id="884dd-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="884dd-109">*force* \[in\]</span></span>  
<span data-ttu-id="884dd-110">**true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="884dd-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="884dd-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="884dd-111">Return value</span></span>
------------

<span data-ttu-id="884dd-112">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="884dd-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="884dd-113">설명</span><span class="sxs-lookup"><span data-stu-id="884dd-113">Remarks</span></span>

<span data-ttu-id="884dd-114">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="884dd-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="884dd-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="884dd-115">Requirements</span></span>
------------
><span data-ttu-id="884dd-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="884dd-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="884dd-117">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="884dd-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="884dd-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="884dd-118">See also</span></span>


[<span data-ttu-id="884dd-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="884dd-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



