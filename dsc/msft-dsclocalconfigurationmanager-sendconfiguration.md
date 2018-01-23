---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드"
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0a079-103">MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="0a079-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0a079-104">구성 문서를 관리 노드로 보내고 보류 중인 변경으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0a079-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="0a079-105">구문</span><span class="sxs-lookup"><span data-stu-id="0a079-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="0a079-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a079-106">Parameters</span></span>
----------

<span data-ttu-id="0a079-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0a079-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="0a079-108">구성에 대한 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a079-108">The environment data for the configuration.</span></span>

<span data-ttu-id="0a079-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0a079-109">*force* \[in\]</span></span>  
<span data-ttu-id="0a079-110">**true**이면 구성을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0a079-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a079-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a079-111">Return value</span></span>
------------

<span data-ttu-id="0a079-112">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a079-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a079-113">설명</span><span class="sxs-lookup"><span data-stu-id="0a079-113">Remarks</span></span>

<span data-ttu-id="0a079-114">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="0a079-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a079-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0a079-115">Requirements</span></span>
------------
><span data-ttu-id="0a079-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0a079-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0a079-117">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0a079-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0a079-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a079-118">See also</span></span>


[<span data-ttu-id="0a079-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0a079-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



