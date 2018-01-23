---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC 사용자 리소스"
ms.openlocfilehash: c1b8487d9adc899950d185036ada3a2fa3747417
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
#<a name="dsc-user-resource"></a><span data-ttu-id="24153-103">DSC 사용자 리소스#</span><span class="sxs-lookup"><span data-stu-id="24153-103">DSC User Resource#</span></span>

 
><span data-ttu-id="24153-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="24153-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="24153-105">Windows PowerShell DSC(필요한 상태 구성)의 __사용자__ 리소스에서는 대상 노드에 있는 로컬 사용자 계정을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="24153-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="24153-106">구문##</span><span class="sxs-lookup"><span data-stu-id="24153-106">Syntax##</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="24153-107">속성</span><span class="sxs-lookup"><span data-stu-id="24153-107">Properties</span></span>
|  <span data-ttu-id="24153-108">속성</span><span class="sxs-lookup"><span data-stu-id="24153-108">Property</span></span>  |  <span data-ttu-id="24153-109">설명</span><span class="sxs-lookup"><span data-stu-id="24153-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="24153-110">UserName</span><span class="sxs-lookup"><span data-stu-id="24153-110">UserName</span></span>| <span data-ttu-id="24153-111">특정 상태를 확인하려는 계정 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-111">Indicates the account name for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="24153-112">설명</span><span class="sxs-lookup"><span data-stu-id="24153-112">Description</span></span>| <span data-ttu-id="24153-113">사용자 계정에 대해 사용할 설명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-113">Indicates the description you want to use for the user account.</span></span>| 
| <span data-ttu-id="24153-114">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="24153-114">Disabled</span></span>| <span data-ttu-id="24153-115">계정이 사용되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="24153-116">이 계정을 사용하지 않도록 하려면 이 속성을 __$true__로 설정하고, 사용하도록 하려면, __$false__로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24153-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>| 
| <span data-ttu-id="24153-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="24153-117">Ensure</span></span>| <span data-ttu-id="24153-118">계정이 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-118">Indicates if the account exists.</span></span> <span data-ttu-id="24153-119">계정이 존재하도록 하려면 이 속성을 "Present"으로 설정하고, 계정이 존재하지 않도록 하려면 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24153-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>| 
| <span data-ttu-id="24153-120">FullName</span><span class="sxs-lookup"><span data-stu-id="24153-120">FullName</span></span>| <span data-ttu-id="24153-121">사용자 계정에 대해 사용할 전체 이름으로 문자열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-121">Represents a string with the full name you want to use for the user account.</span></span>| 
| <span data-ttu-id="24153-122">암호</span><span class="sxs-lookup"><span data-stu-id="24153-122">Password</span></span>| <span data-ttu-id="24153-123">이 계정에 사용할 암호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-123">Indicates the password you want to use for this account.</span></span> | 
| <span data-ttu-id="24153-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="24153-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="24153-125">사용자가 암호를 변경할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="24153-126">사용자가 암호를 변경할 수 없도록 하려면 이 속성을 __$true__로 설정하고, 사용자가 암호를 변경할 수 있도록 하려면 __$false__로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24153-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="24153-127">기본값은 __$false__입니다.</span><span class="sxs-lookup"><span data-stu-id="24153-127">The default value is __$false__.</span></span>| 
| <span data-ttu-id="24153-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="24153-128">PasswordChangeRequired</span></span>| <span data-ttu-id="24153-129">사용자가 다음 로그인 시 암호를 변경해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="24153-130">사용자가 암호를 변경해야 하는 경우 이 속성을 __$true__로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24153-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="24153-131">기본값은 __$true__입니다.</span><span class="sxs-lookup"><span data-stu-id="24153-131">The default value is __$true__.</span></span>| 
| <span data-ttu-id="24153-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="24153-132">PasswordNeverExpires</span></span>| <span data-ttu-id="24153-133">암호가 만료될지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-133">Indicates if the password will expire.</span></span> <span data-ttu-id="24153-134">이 계정에 대한 암호가 절대로 만료되지 않도록 하려면, 이 속성을 __$true__로 설정하고, 암호가 만료될 것이라면 __$false__로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24153-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="24153-135">기본값은 __$false__입니다.</span><span class="sxs-lookup"><span data-stu-id="24153-135">The default value is __$false__.</span></span>| 
| <span data-ttu-id="24153-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="24153-136">DependsOn</span></span> | <span data-ttu-id="24153-137">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24153-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="24153-138">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="24153-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="24153-139">예제</span><span class="sxs-lookup"><span data-stu-id="24153-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

