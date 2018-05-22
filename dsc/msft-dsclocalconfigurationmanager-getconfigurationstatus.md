---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="76ff7-103">MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드</span><span class="sxs-lookup"><span data-stu-id="76ff7-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="76ff7-104">구성 상태 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="76ff7-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="76ff7-105">구문</span><span class="sxs-lookup"><span data-stu-id="76ff7-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="76ff7-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="76ff7-106">Parameters</span></span>
----------

<span data-ttu-id="76ff7-107">*All* \[in\] 이 메서드가 구성 응용 프로그램 및 일관성 확인을 포함하여 컴퓨터에서 실행되는 모든 구성에 대한 정보를 반환하면 **true**입니다.</span><span class="sxs-lookup"><span data-stu-id="76ff7-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="76ff7-108">*configurationStatus* \[out\] 반환 시, 설정을 정의하는 **MSFT_DSCConfigurationStatus** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ff7-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="76ff7-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="76ff7-109">Return value</span></span>
------------

<span data-ttu-id="76ff7-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="76ff7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="76ff7-111">설명</span><span class="sxs-lookup"><span data-stu-id="76ff7-111">Remarks</span></span>

<span data-ttu-id="76ff7-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="76ff7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="76ff7-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="76ff7-113">Requirements</span></span>
------------
><span data-ttu-id="76ff7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="76ff7-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="76ff7-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="76ff7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="76ff7-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76ff7-116">See also</span></span>


[<span data-ttu-id="76ff7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="76ff7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)