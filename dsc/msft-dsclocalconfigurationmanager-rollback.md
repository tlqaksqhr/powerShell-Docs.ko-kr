---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 RollBack 메서드"
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="74c82-103">MSFT_DSCLocalConfigurationManager 클래스의 RollBack 메서드</span><span class="sxs-lookup"><span data-stu-id="74c82-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="74c82-104">이전 버전으로 구성을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="74c82-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="74c82-105">구문</span><span class="sxs-lookup"><span data-stu-id="74c82-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="74c82-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="74c82-106">Parameters</span></span>
----------

<span data-ttu-id="74c82-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="74c82-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="74c82-108">요청한 구성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74c82-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="74c82-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="74c82-109">Return value</span></span>
------------

<span data-ttu-id="74c82-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="74c82-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="74c82-111">설명</span><span class="sxs-lookup"><span data-stu-id="74c82-111">Remarks</span></span>

<span data-ttu-id="74c82-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="74c82-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="74c82-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="74c82-113">Requirements</span></span>
------------
><span data-ttu-id="74c82-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="74c82-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="74c82-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="74c82-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="74c82-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74c82-116">See also</span></span>


[<span data-ttu-id="74c82-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="74c82-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



