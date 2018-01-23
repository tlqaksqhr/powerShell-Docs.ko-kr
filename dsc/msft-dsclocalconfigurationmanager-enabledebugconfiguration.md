---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드"
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="086a3-103">MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="086a3-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="086a3-104">DSC 리소스 디버깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="086a3-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="086a3-105">구문</span><span class="sxs-lookup"><span data-stu-id="086a3-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="086a3-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="086a3-106">Parameters</span></span>
----------

<span data-ttu-id="086a3-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="086a3-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="086a3-108">리소스 스크립트의 모든 줄에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="086a3-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="086a3-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="086a3-109">Return value</span></span>
------------

<span data-ttu-id="086a3-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="086a3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="086a3-111">설명</span><span class="sxs-lookup"><span data-stu-id="086a3-111">Remarks</span></span>

<span data-ttu-id="086a3-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="086a3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="086a3-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="086a3-113">Requirements</span></span>
------------
><span data-ttu-id="086a3-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="086a3-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="086a3-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="086a3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="086a3-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="086a3-116">See also</span></span>


[<span data-ttu-id="086a3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="086a3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



