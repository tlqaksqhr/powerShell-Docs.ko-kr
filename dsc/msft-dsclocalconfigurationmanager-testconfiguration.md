---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 TestConfiguration 메서드"
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="07e1f-103">MSFT_DSCLocalConfigurationManager 클래스의 TestConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="07e1f-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="07e1f-104">구성 문서를 관리 노드로 보내고, 문서에 대해 현재 구성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="07e1f-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="07e1f-105">구문</span><span class="sxs-lookup"><span data-stu-id="07e1f-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="07e1f-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="07e1f-106">Parameters</span></span>
----------

<span data-ttu-id="07e1f-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="07e1f-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="07e1f-108">구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="07e1f-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="07e1f-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="07e1f-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="07e1f-110">반환 시, 관리 노드가 구성 문서에서 지정한 상태인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07e1f-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="07e1f-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="07e1f-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="07e1f-112">반환 시, 원하는 상태인 리소스를 지정하는 **MSFT_ResourceInDesiredState** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07e1f-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="07e1f-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="07e1f-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="07e1f-114">반환 시, 원하는 상태가 아닌 리소스를 지정하는 **MSFT_ResourceNotInDesiredState** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07e1f-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="07e1f-115">반환 값</span><span class="sxs-lookup"><span data-stu-id="07e1f-115">Return value</span></span>
------------

<span data-ttu-id="07e1f-116">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="07e1f-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="07e1f-117">설명</span><span class="sxs-lookup"><span data-stu-id="07e1f-117">Remarks</span></span>

<span data-ttu-id="07e1f-118">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="07e1f-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="07e1f-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="07e1f-119">Requirements</span></span>
------------
><span data-ttu-id="07e1f-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="07e1f-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="07e1f-121">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="07e1f-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="07e1f-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07e1f-122">See also</span></span>


[<span data-ttu-id="07e1f-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="07e1f-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



