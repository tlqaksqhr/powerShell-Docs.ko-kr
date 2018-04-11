---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a61ec-103">MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="a61ec-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a61ec-104">DSC 리소스 디버깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a61ec-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="a61ec-105">구문</span><span class="sxs-lookup"><span data-stu-id="a61ec-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="a61ec-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a61ec-106">Parameters</span></span>
----------

<span data-ttu-id="a61ec-107">*BreakAll* \[in\] 리소스 스크립트의 모든 줄에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a61ec-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="a61ec-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="a61ec-108">Return value</span></span>
------------

<span data-ttu-id="a61ec-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a61ec-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a61ec-110">설명</span><span class="sxs-lookup"><span data-stu-id="a61ec-110">Remarks</span></span>

<span data-ttu-id="a61ec-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="a61ec-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a61ec-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a61ec-112">Requirements</span></span>
------------
><span data-ttu-id="a61ec-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a61ec-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a61ec-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a61ec-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a61ec-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a61ec-115">See also</span></span>


[<span data-ttu-id="a61ec-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a61ec-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)