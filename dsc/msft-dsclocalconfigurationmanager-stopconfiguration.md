---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드"
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4f119-103">MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="4f119-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4f119-104">진행 중인 구성 변경을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="4f119-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="4f119-105">구문</span><span class="sxs-lookup"><span data-stu-id="4f119-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="4f119-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4f119-106">Parameters</span></span>
----------

<span data-ttu-id="4f119-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4f119-107">*force* \[in\]</span></span>  
<span data-ttu-id="4f119-108">**true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="4f119-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4f119-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="4f119-109">Return value</span></span>
------------

<span data-ttu-id="4f119-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4f119-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4f119-111">설명</span><span class="sxs-lookup"><span data-stu-id="4f119-111">Remarks</span></span>

<span data-ttu-id="4f119-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="4f119-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f119-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4f119-113">Requirements</span></span>
------------
><span data-ttu-id="4f119-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4f119-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4f119-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4f119-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4f119-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f119-116">See also</span></span>


[<span data-ttu-id="4f119-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4f119-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



