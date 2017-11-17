---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetConfiguration 메서드"
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9749f-103">MSFT_DSCLocalConfigurationManager 클래스의 GetConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="9749f-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9749f-104">구성 문서를 관리 노드로 보내고, 구성 에이전트의 **Get** 메서드를 사용해 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9749f-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="9749f-105">구문</span><span class="sxs-lookup"><span data-stu-id="9749f-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="9749f-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9749f-106">Parameters</span></span>
----------

<span data-ttu-id="9749f-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9749f-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="9749f-108">보낼 구성 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9749f-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="9749f-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="9749f-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="9749f-110">반환 시 구성의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9749f-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="9749f-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="9749f-111">Return value</span></span>
------------

<span data-ttu-id="9749f-112">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9749f-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9749f-113">설명</span><span class="sxs-lookup"><span data-stu-id="9749f-113">Remarks</span></span>

<span data-ttu-id="9749f-114">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="9749f-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9749f-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9749f-115">Requirements</span></span>
------------
><span data-ttu-id="9749f-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9749f-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9749f-117">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9749f-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9749f-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9749f-118">See also</span></span>


[<span data-ttu-id="9749f-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9749f-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



