---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드"
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d62cc-103">MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="d62cc-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d62cc-104">진행 중인 구성 변경을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d62cc-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="d62cc-105">구문</span><span class="sxs-lookup"><span data-stu-id="d62cc-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="d62cc-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d62cc-106">Parameters</span></span>
----------

<span data-ttu-id="d62cc-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d62cc-107">*force* \[in\]</span></span>  
<span data-ttu-id="d62cc-108">**true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d62cc-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d62cc-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="d62cc-109">Return value</span></span>
------------

<span data-ttu-id="d62cc-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d62cc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d62cc-111">설명</span><span class="sxs-lookup"><span data-stu-id="d62cc-111">Remarks</span></span>

<span data-ttu-id="d62cc-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="d62cc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d62cc-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d62cc-113">Requirements</span></span>
------------
><span data-ttu-id="d62cc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d62cc-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d62cc-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d62cc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d62cc-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d62cc-116">See also</span></span>


[<span data-ttu-id="d62cc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d62cc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



