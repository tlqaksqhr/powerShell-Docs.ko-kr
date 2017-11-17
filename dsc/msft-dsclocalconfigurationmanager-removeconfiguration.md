---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 RemoveConfiguration 메서드"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="39c23-103">MSFT_DSCLocalConfigurationManager 클래스의 RemoveConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="39c23-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="39c23-104">구성 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="39c23-105">구문</span><span class="sxs-lookup"><span data-stu-id="39c23-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="39c23-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="39c23-106">Parameters</span></span>
----------

<span data-ttu-id="39c23-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="39c23-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="39c23-108">제거할 구성 문서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="39c23-109">다음은 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-109">The following values are valid:</span></span>

|<span data-ttu-id="39c23-110">Value</span><span class="sxs-lookup"><span data-stu-id="39c23-110">Value</span></span> |<span data-ttu-id="39c23-111">설명</span><span class="sxs-lookup"><span data-stu-id="39c23-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="39c23-112">**1**</span><span class="sxs-lookup"><span data-stu-id="39c23-112">**1**</span></span> | <span data-ttu-id="39c23-113">**현재** 구성 문서(current.mof)입니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="39c23-114">**2**</span><span class="sxs-lookup"><span data-stu-id="39c23-114">**2**</span></span> | <span data-ttu-id="39c23-115">**보류 중인** 구성 문서(pending.mof)입니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="39c23-116">**4**</span><span class="sxs-lookup"><span data-stu-id="39c23-116">**4**</span></span> | <span data-ttu-id="39c23-117">**이전** 구성 문서(previous.mof)입니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="39c23-118">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="39c23-118">*Force* \[in\]</span></span>  
<span data-ttu-id="39c23-119">**true**이면 구성을 강제로 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="39c23-120">반환 값</span><span class="sxs-lookup"><span data-stu-id="39c23-120">Return value</span></span>
------------

<span data-ttu-id="39c23-121">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="39c23-122">설명</span><span class="sxs-lookup"><span data-stu-id="39c23-122">Remarks</span></span>

<span data-ttu-id="39c23-123">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="39c23-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="39c23-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="39c23-124">Requirements</span></span>
------------
><span data-ttu-id="39c23-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="39c23-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="39c23-126">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="39c23-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="39c23-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39c23-127">See also</span></span>


[<span data-ttu-id="39c23-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="39c23-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



