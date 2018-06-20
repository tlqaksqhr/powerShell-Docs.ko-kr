---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 RemoveConfiguration 메서드
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189740"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="308fe-103">MSFT_DSCLocalConfigurationManager 클래스의 RemoveConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="308fe-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="308fe-104">구성 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="308fe-105">구문</span><span class="sxs-lookup"><span data-stu-id="308fe-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="308fe-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="308fe-106">Parameters</span></span>
----------

<span data-ttu-id="308fe-107">*Stage* \[in\] 제거할 구성 문서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="308fe-108">다음은 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-108">The following values are valid:</span></span>

|<span data-ttu-id="308fe-109">Value</span><span class="sxs-lookup"><span data-stu-id="308fe-109">Value</span></span> |<span data-ttu-id="308fe-110">설명</span><span class="sxs-lookup"><span data-stu-id="308fe-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="308fe-111">**1**</span><span class="sxs-lookup"><span data-stu-id="308fe-111">**1**</span></span> | <span data-ttu-id="308fe-112">**현재** 구성 문서(current.mof)입니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="308fe-113">**2**</span><span class="sxs-lookup"><span data-stu-id="308fe-113">**2**</span></span> | <span data-ttu-id="308fe-114">**보류 중인** 구성 문서(pending.mof)입니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="308fe-115">**4**</span><span class="sxs-lookup"><span data-stu-id="308fe-115">**4**</span></span> | <span data-ttu-id="308fe-116">**이전** 구성 문서(previous.mof)입니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="308fe-117">*Force* \[in\] **true**이면 구성을 강제로 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="308fe-118">반환 값</span><span class="sxs-lookup"><span data-stu-id="308fe-118">Return value</span></span>
------------

<span data-ttu-id="308fe-119">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="308fe-120">설명</span><span class="sxs-lookup"><span data-stu-id="308fe-120">Remarks</span></span>

<span data-ttu-id="308fe-121">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="308fe-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="308fe-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="308fe-122">Requirements</span></span>
------------
><span data-ttu-id="308fe-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="308fe-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="308fe-124">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="308fe-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="308fe-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="308fe-125">See also</span></span>


[<span data-ttu-id="308fe-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="308fe-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)