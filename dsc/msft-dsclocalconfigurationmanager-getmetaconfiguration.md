---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 GetMetaConfiguration 메서드"
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="70bfb-103">MSFT_DSCLocalConfigurationManager 클래스의 GetMetaConfiguration 메서드</span><span class="sxs-lookup"><span data-stu-id="70bfb-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="70bfb-104">구성 에이전트를 제어하는 데 사용되는 로컬 구성 관리자 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70bfb-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="70bfb-105">구문</span><span class="sxs-lookup"><span data-stu-id="70bfb-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="70bfb-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70bfb-106">Parameters</span></span>
----------

<span data-ttu-id="70bfb-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="70bfb-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="70bfb-108">반환 시 설정을 정의하는 **MSFT_DSCMetaConfiguration** 클래스의 포함 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70bfb-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="70bfb-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="70bfb-109">Return value</span></span>
------------

<span data-ttu-id="70bfb-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="70bfb-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="70bfb-111">설명</span><span class="sxs-lookup"><span data-stu-id="70bfb-111">Remarks</span></span>

<span data-ttu-id="70bfb-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="70bfb-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="70bfb-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="70bfb-113">Requirements</span></span>
------------
><span data-ttu-id="70bfb-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="70bfb-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="70bfb-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="70bfb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="70bfb-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70bfb-116">See also</span></span>


[<span data-ttu-id="70bfb-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="70bfb-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



