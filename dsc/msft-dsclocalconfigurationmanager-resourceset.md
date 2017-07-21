---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 ResourceSet 메서드"
ms.openlocfilehash: 9cd9c1b3f58a5862db6c4eea0488423b8dfe7310
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b1fd7-103">MSFT_DSCLocalConfigurationManager 클래스의 ResourceSet 메서드</span><span class="sxs-lookup"><span data-stu-id="b1fd7-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b1fd7-104">DSC 리소스의 **Set** 메서드를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b1fd7-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="b1fd7-105">구문</span><span class="sxs-lookup"><span data-stu-id="b1fd7-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="b1fd7-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b1fd7-106">Parameters</span></span>
----------

<span data-ttu-id="b1fd7-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b1fd7-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="b1fd7-108">호출할 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b1fd7-108">The name of the resource to call.</span></span>

<span data-ttu-id="b1fd7-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b1fd7-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="b1fd7-110">호출할 리소스를 포함하는 모듈의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b1fd7-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b1fd7-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b1fd7-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="b1fd7-112">해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1fd7-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b1fd7-113">[Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b1fd7-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b1fd7-114">*RebootRequired* \[out\]</span><span class="sxs-lookup"><span data-stu-id="b1fd7-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="b1fd7-115">반환 시, 대상 노드를 다시 부팅해야 하면 이 속성이 **true**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1fd7-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="b1fd7-116">반환 값</span><span class="sxs-lookup"><span data-stu-id="b1fd7-116">Return value</span></span>
------------

<span data-ttu-id="b1fd7-117">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b1fd7-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1fd7-118">설명</span><span class="sxs-lookup"><span data-stu-id="b1fd7-118">Remarks</span></span>

<span data-ttu-id="b1fd7-119">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b1fd7-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1fd7-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b1fd7-120">Requirements</span></span>
------------
><span data-ttu-id="b1fd7-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b1fd7-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b1fd7-122">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1fd7-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b1fd7-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1fd7-123">See also</span></span>


[<span data-ttu-id="b1fd7-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b1fd7-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



