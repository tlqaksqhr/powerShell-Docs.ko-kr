---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드"
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9b5a8-103">MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="9b5a8-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9b5a8-104">DSC 리소스 디버깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b5a8-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="9b5a8-105">구문</span><span class="sxs-lookup"><span data-stu-id="9b5a8-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="9b5a8-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b5a8-106">Parameters</span></span>
----------

<span data-ttu-id="9b5a8-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9b5a8-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="9b5a8-108">리소스 스크립트의 모든 줄에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b5a8-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="9b5a8-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="9b5a8-109">Return value</span></span>
------------

<span data-ttu-id="9b5a8-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9b5a8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b5a8-111">설명</span><span class="sxs-lookup"><span data-stu-id="9b5a8-111">Remarks</span></span>

<span data-ttu-id="9b5a8-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="9b5a8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b5a8-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9b5a8-113">Requirements</span></span>
------------
><span data-ttu-id="9b5a8-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9b5a8-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9b5a8-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9b5a8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9b5a8-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b5a8-116">See also</span></span>


[<span data-ttu-id="9b5a8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9b5a8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



