---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="30245-103">MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드</span><span class="sxs-lookup"><span data-stu-id="30245-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="30245-104">구성 상태 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="30245-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="30245-105">구문</span><span class="sxs-lookup"><span data-stu-id="30245-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="30245-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="30245-106">Parameters</span></span>
----------

<span data-ttu-id="30245-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="30245-107">*All* \[in\]</span></span>  
<span data-ttu-id="30245-108">이 메서드가 구성 응용 프로그램 및 일관성 확인을 포함하여 컴퓨터에서 실행되는 모든 구성에 관한 정보를 반환하면 **true**입니다.</span><span class="sxs-lookup"><span data-stu-id="30245-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="30245-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="30245-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="30245-110">반환 시 설정을 정의하는 **MSFT_DSCConfigurationStatus** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30245-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="30245-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="30245-111">Return value</span></span>
------------

<span data-ttu-id="30245-112">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30245-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="30245-113">설명</span><span class="sxs-lookup"><span data-stu-id="30245-113">Remarks</span></span>

<span data-ttu-id="30245-114">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="30245-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="30245-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="30245-115">Requirements</span></span>
------------
><span data-ttu-id="30245-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="30245-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="30245-117">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="30245-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="30245-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30245-118">See also</span></span>


[<span data-ttu-id="30245-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="30245-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



