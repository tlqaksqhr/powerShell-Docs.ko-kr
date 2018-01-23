---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 ResourceGet 메서드"
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1da13-103">MSFT_DSCLocalConfigurationManager 클래스의 ResourceGet 메서드</span><span class="sxs-lookup"><span data-stu-id="1da13-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1da13-104">DSC 리소스의 **Get** 메서드를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1da13-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="1da13-105">구문</span><span class="sxs-lookup"><span data-stu-id="1da13-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="1da13-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1da13-106">Parameters</span></span>
----------

<span data-ttu-id="1da13-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1da13-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="1da13-108">호출할 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1da13-108">The name of the resource to call.</span></span>

<span data-ttu-id="1da13-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1da13-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="1da13-110">호출할 리소스를 포함하는 모듈의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1da13-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="1da13-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1da13-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="1da13-112">해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1da13-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="1da13-113">[Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1da13-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="1da13-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="1da13-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="1da13-115">반환 시 구성의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1da13-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="1da13-116">반환 값</span><span class="sxs-lookup"><span data-stu-id="1da13-116">Return value</span></span>
------------

<span data-ttu-id="1da13-117">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1da13-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1da13-118">설명</span><span class="sxs-lookup"><span data-stu-id="1da13-118">Remarks</span></span>

<span data-ttu-id="1da13-119">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="1da13-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1da13-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1da13-120">Requirements</span></span>
------------
><span data-ttu-id="1da13-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1da13-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1da13-122">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1da13-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1da13-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1da13-123">See also</span></span>


[<span data-ttu-id="1da13-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1da13-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



