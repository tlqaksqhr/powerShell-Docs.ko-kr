---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f66f9-103">MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="f66f9-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f66f9-104">DSC 리소스 디버깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f66f9-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="f66f9-105">구문</span><span class="sxs-lookup"><span data-stu-id="f66f9-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="f66f9-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f66f9-106">Parameters</span></span>
----------

<span data-ttu-id="f66f9-107">*BreakAll* \[in\] 리소스 스크립트의 모든 줄에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f66f9-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="f66f9-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="f66f9-108">Return value</span></span>
------------

<span data-ttu-id="f66f9-109">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f66f9-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f66f9-110">설명</span><span class="sxs-lookup"><span data-stu-id="f66f9-110">Remarks</span></span>

<span data-ttu-id="f66f9-111">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="f66f9-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f66f9-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f66f9-112">Requirements</span></span>
------------
><span data-ttu-id="f66f9-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f66f9-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f66f9-114">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f66f9-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f66f9-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f66f9-115">See also</span></span>


[<span data-ttu-id="f66f9-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f66f9-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)