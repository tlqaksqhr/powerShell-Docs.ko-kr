---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "MSFT_DSCLocalConfigurationManager 클래스의 RollBack 메서드"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="44cd2-103">MSFT_DSCLocalConfigurationManager 클래스의 RollBack 메서드</span><span class="sxs-lookup"><span data-stu-id="44cd2-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="44cd2-104">이전 버전으로 구성을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="44cd2-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="44cd2-105">구문</span><span class="sxs-lookup"><span data-stu-id="44cd2-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="44cd2-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="44cd2-106">Parameters</span></span>
----------

<span data-ttu-id="44cd2-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="44cd2-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="44cd2-108">요청한 구성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44cd2-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="44cd2-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="44cd2-109">Return value</span></span>
------------

<span data-ttu-id="44cd2-110">성공하면 0을 반환하고 그렇지 않으면 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="44cd2-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="44cd2-111">설명</span><span class="sxs-lookup"><span data-stu-id="44cd2-111">Remarks</span></span>

<span data-ttu-id="44cd2-112">정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="44cd2-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="44cd2-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="44cd2-113">Requirements</span></span>
------------
><span data-ttu-id="44cd2-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="44cd2-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="44cd2-115">**네임스페이스**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="44cd2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="44cd2-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44cd2-116">See also</span></span>


[<span data-ttu-id="44cd2-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="44cd2-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



