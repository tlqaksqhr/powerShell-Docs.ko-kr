---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "레지스트리 키 작업"
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: efb2c016afa2212c2907c0740ad26c4e4cddd3af
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="75197-103">레지스트리 키 작업</span><span class="sxs-lookup"><span data-stu-id="75197-103">Working with Registry Keys</span></span>
<span data-ttu-id="75197-104">레지스트리 키는 Windows PowerShell 드라이브에 있는 항목이므로 레지스트리 키에 대한 작업 수행은 파일 및 폴더 작업과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="75197-105">한 가지 중요한 차이점은 레지스트리 기반 Windows PowerShell 드라이브의 모든 항목은 파일 시스템 드라이브의 폴더와 같이 컨테이너라는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="75197-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="75197-106">그러나 레지스트리 항목 및 연결된 값은 고유한 항목이 아니라 항목의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="75197-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="75197-107">레지스트리 키의 모든 하위 키 표시</span><span class="sxs-lookup"><span data-stu-id="75197-107">Listing All Subkeys of a Registry Key</span></span>
<span data-ttu-id="75197-108">**Get-ChildItem**을 사용하여 레지스트리 키 바로 아래에 있는 항목을 모두 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="75197-109">선택적 **Force** 매개 변수를 추가하면 숨겨진 항목이나 시스템 항목을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="75197-110">예를 들어 다음 명령은 HKEY_CURRENT_USER 레지스트리 하이브에 해당하는 Windows PowerShell 드라이브 HKCU: 바로 아래에 있는 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="75197-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="75197-111">이러한 키는 레지스트리 편집기(Regedit.exe)의 HKEY_CURRENT_USER에 표시되는 최상위 키입니다.</span><span class="sxs-lookup"><span data-stu-id="75197-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="75197-112">레지스트리 공급자 이름(뒤에 "**::**"이 옴)을 지정하여 레지스트리 경로를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="75197-113">레지스트리 공급자의 전체 이름은 **Microsoft.PowerShell.Core\\Registry**이지만 **Registry**로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="75197-114">다음 명령은 HKCU: 바로 아래에 있는 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="75197-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="75197-115">이 명령은 Cmd.exe의 **DIR** 명령이나 UNIX 셸의 **ls**를 사용하는 것과 매우 유사한 방법으로 바로 아래에 포함된 항목만 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="75197-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="75197-116">포함된 항목을 모두 보려면 **Recurse** 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="75197-117">HKCU에 있는 모든 레지스트리 키를 보려면 다음 명령을 사용합니다. 이 작업은 완료하는 데 시간이 많이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="75197-118">**Get-ChildItem**은 **Path**, **Filter**, **Include** 및 **Exclude** 매개 변수로 복잡한 필터링 기능을 수행할 수 있지만 이러한 변수는 일반적으로 이름을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="75197-119">**Where-Object** cmdlet을 사용하여 항목의 다른 속성을 기반으로 복잡한 필터링을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-119">You can perform complex filtering based on other properties of items by using the **Where-Object**cmdlet.</span></span> <span data-ttu-id="75197-120">다음 명령은 HKCU:\\Software 내에서 정확히 한 개의 하위 키와 네 개의 값을 갖는 모든 키를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="75197-121">키 복사</span><span class="sxs-lookup"><span data-stu-id="75197-121">Copying Keys</span></span>
<span data-ttu-id="75197-122">**Copy-Item**을 사용하여 복사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="75197-123">다음 명령은 "CurrentVersion"라는 새 키를 만들 때 HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion 및 모든 속성을 HKCU:\\에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="75197-124">레지스트리 편집기나 **Get-ChildItem**을 사용하여 새 키를 검사하면 포함된 하위 키가 새 위치에 복사되지 않은 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="75197-125">컨테이너의 내용을 모두 복사하려면 **Recurse** 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="75197-126">위의 복사 명령을 재귀적으로 실행하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-126">To make the preceding copy command recursive, you would use this command:</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="75197-127">파일 시스템 복사를 위해 이전부터 사용하던 다른 도구를 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="75197-128">예를 들어 reg.exe, regini.exe 및 regedit.exe 같은 레지스트리 편집 도구와 WScript.Shell 및 WMI의 StdRegProv 클래스와 같이 레지스트리 편집을 지원하는 COM 개체를 Windows PowerShell에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="75197-129">키 만들기</span><span class="sxs-lookup"><span data-stu-id="75197-129">Creating Keys</span></span>
<span data-ttu-id="75197-130">레지스트리에서 새 키를 만드는 것은 파일 시스템에서 새 항목을 만드는 것보다 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="75197-131">모든 레지스트리 키가 컨테이너이므로 항목 유형을 지정할 필요 없이 다음과 같이 명시적 경로만 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75197-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="75197-132">다음과 같이 공급자 기반 경로를 사용하여 키를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75197-132">You can also use a provider-based path to specify a key:</span></span>

```
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="75197-133">키 삭제</span><span class="sxs-lookup"><span data-stu-id="75197-133">Deleting Keys</span></span>
<span data-ttu-id="75197-134">기본적으로 항목 삭제는 모든 공급자에 대해 동일하게 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="75197-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="75197-135">다음 명령은 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-135">The following commands will silently remove items:</span></span>

```
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="75197-136">특정 키 아래에 있는 모든 키 제거</span><span class="sxs-lookup"><span data-stu-id="75197-136">Removing All Keys Under a Specific Key</span></span>
<span data-ttu-id="75197-137">**Remove-Item**을 사용하면 포함된 항목을 제거할 수 있지만 이 항목에 다른 항목이 들어 있는 경우 제거를 확인하는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="75197-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="75197-138">예를 들어 앞에서 만든 HKCU:\\CurrentVersion 하위 키를 삭제하려고 하면 다음과 같은 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="75197-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="75197-139">확인 메시지 없이 포함된 항목을 삭제하려면 다음과 같이 **-Recurse** 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="75197-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="75197-140">또한 HKCU:\\CurrentVersion은 제거하지 않고 HKCU:\\CurrentVersion 안에 들어 있는 항목만 모두 제거하려면 다음 명령을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75197-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
