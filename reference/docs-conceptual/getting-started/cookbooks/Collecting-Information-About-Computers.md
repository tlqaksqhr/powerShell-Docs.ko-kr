---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 컴퓨터에 대한 정보 수집
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: c914a7133a1ac0a05346233db802175f7f29c6b2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="d0bfa-103">컴퓨터에 대한 정보 수집</span><span class="sxs-lookup"><span data-stu-id="d0bfa-103">Collecting Information About Computers</span></span>

<span data-ttu-id="d0bfa-104">**Get-WmiObject**는 일반적인 시스템 관리 작업에 사용되는 가장 중요한 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-104">**Get-WmiObject** is the most important cmdlet for general system management tasks.</span></span> <span data-ttu-id="d0bfa-105">모든 중요한 하위 시스템 설정은 WMI를 통해 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="d0bfa-106">또한 WMI는 하나 이상의 항목 컬렉션에 있는 개체로 데이터를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="d0bfa-107">Windows PowerShell은 개체에서도 작동하며 단일 또는 여러 개체를 동일한 방식으로 처리할 수 있게 해주는 파이프라인이 있기 때문에 일반적인 WMI 액세스를 통해 몇 가지 고급 작업을 매우 적은 노력으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="d0bfa-108">다음 예제에서는 임의 컴퓨터에 대해 **Get-WmiObject**를 사용하여 특정 정보를 수집하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-108">The following examples demonstrate how to collect specific information by using **Get-WmiObject** against an arbitrary computer.</span></span> <span data-ttu-id="d0bfa-109">로컬 컴퓨터를 나타내는 점 값(**.**)과 함께 **ComputerName** 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span> <span data-ttu-id="d0bfa-110">WMI를 통해 연결할 수 있는 컴퓨터와 연관된 이름 또는 IP 주소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span> <span data-ttu-id="d0bfa-111">로컬 컴퓨터에 대한 정보를 검색하려면 **-ComputerName**을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-111">To retrieve information about the local computer, you could omit the **-ComputerName.**</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="d0bfa-112">데스크톱 설정 표시</span><span class="sxs-lookup"><span data-stu-id="d0bfa-112">Listing Desktop Settings</span></span>

<span data-ttu-id="d0bfa-113">먼저 로컬 컴퓨터에서 데스크톱 정보를 수집하는 명령을 실행하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

<span data-ttu-id="d0bfa-114">이렇게 하면 사용 여부에 관계없이 모든 데스크톱에 대한 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="d0bfa-115">일부 WMI 클래스에서 반환되는 정보는 매우 자세할 수 있으며, WMI 클래스에 대한 메타데이터가 포함된 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span> <span data-ttu-id="d0bfa-116">이러한 메타데이터 속성에는 대부분 이중 밑줄로 시작하는 이름이 있으므로 Select-Object를 사용하여 속성을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-116">Because most of these metadata properties have names that begin with a double underscore, you can filter the properties using Select-Object.</span></span> <span data-ttu-id="d0bfa-117">\*\*[a-z]\*\*\*를 속성 값으로 사용하여 알파벳 문자로 시작하는 속성만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-117">Specify only properties that begin with alphabetic characters by using **[a-z]**\* as the Property value.</span></span> <span data-ttu-id="d0bfa-118">예:</span><span class="sxs-lookup"><span data-stu-id="d0bfa-118">For example:</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="d0bfa-119">메타데이터를 필터링하려면 파이프라인 연산자(|)를 사용하여 Get-WmiObject 명령의 결과를 \*\*Select-Object -Property [a-z]\*\*\*로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-119">To filter out the metadata, use a pipeline operator (|) to send the results of the Get-WmiObject command to \*\*Select-Object -Property [a-z]\*\*\*.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="d0bfa-120">BIOS 정보 표시</span><span class="sxs-lookup"><span data-stu-id="d0bfa-120">Listing BIOS Information</span></span>

<span data-ttu-id="d0bfa-121">WMI Win32_BIOS 클래스는 로컬 컴퓨터의 시스템 BIOS에 대한 전체 정보를 비교적 간결하게 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-121">The WMI Win32_BIOS class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="d0bfa-122">프로세서 정보 표시</span><span class="sxs-lookup"><span data-stu-id="d0bfa-122">Listing Processor Information</span></span>

<span data-ttu-id="d0bfa-123">정보를 필터링하려는 경우가 많지만 WMI의 **Win32_Processor** 클래스를 사용하여 일반적인 프로세서 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="d0bfa-124">프로세서 제품군에 대한 일반적인 설명 문자열을 위해 **SystemType** 속성을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="d0bfa-125">컴퓨터 제조업체 및 모델 표시</span><span class="sxs-lookup"><span data-stu-id="d0bfa-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="d0bfa-126">**Win32_ComputerSystem**을 통해 컴퓨터 모델 정보를 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="d0bfa-127">OEM 데이터를 제공하기 위해 표시되는 표준 출력을 필터링하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem

Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

<span data-ttu-id="d0bfa-128">일부 하드웨어의 정보를 직접 반환하는 이러한 명령의 출력 품질은 보유한 데이터에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="d0bfa-129">일부 정보는 하드웨어 제조업체에서 제대로 구성하지 않아 제공되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="d0bfa-130">설치된 핫픽스 표시</span><span class="sxs-lookup"><span data-stu-id="d0bfa-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="d0bfa-131">**Win32_QuickFixEngineering**을 사용하여 설치된 모든 핫픽스를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="d0bfa-132">이 클래스는 다음과 같은 핫픽스 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

<span data-ttu-id="d0bfa-133">더 간결한 출력을 위해 일부 속성을 제외할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-133">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="d0bfa-134">**Get-WmiObject's Property** 매개 변수를 사용하여 **HotFixID**만 선택할 수도 있지만, 이렇게 하면 기본적으로 모든 메타데이터가 표시되기 때문에 실제로 자세한 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-134">Although you can use the **Get-WmiObject's Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID

HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

<span data-ttu-id="d0bfa-135">**Get-WmiObject**의 Property 매개 변수는 Windows PowerShell로 반환되는 개체가 아니라 WMI 클래스 인스턴스에서 반환되는 속성을 제한하기 때문에 추가 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-135">The additional data is returned, because the Property parameter in **Get-WmiObject** restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span> <span data-ttu-id="d0bfa-136">출력을 줄이려면 **Select-Object**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-136">To reduce the output, use **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId

HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="d0bfa-137">운영 체제 버전 정보 표시</span><span class="sxs-lookup"><span data-stu-id="d0bfa-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="d0bfa-138">**Win32_OperatingSystem** 클래스 속성에는 버전 및 서비스 팩 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="d0bfa-139">이러한 속성만 명시적으로 선택하여 **Win32_OperatingSystem**에서 버전 정보 요약을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="d0bfa-140">**Select-Object 속성** 매개 변수와 함께 와일드카드를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-140">You can also use wildcards with the **Select-Object's Property** parameter.</span></span> <span data-ttu-id="d0bfa-141">**Build** 또는 **ServicePack**으로 시작하는 모든 속성을 여기서 사용하는 것이 중요하기 때문에 다음과 같은 형태로 축약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="d0bfa-142">로컬 사용자 및 소유자 표시</span><span class="sxs-lookup"><span data-stu-id="d0bfa-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="d0bfa-143">사용이 허가된 사용자 수, 현재 사용자 수, 소유자 이름 등의 로컬 일반 사용자 정보는 **Win32_OperatingSystem** 속성을 선택하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-143">Local general user information—number of licensed users, current number of users, and owner name—can be found with a selection of **Win32_OperatingSystem** properties.</span></span> <span data-ttu-id="d0bfa-144">다음과 같이 표시할 속성을 명시적으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="d0bfa-145">와일드카드를 사용하는 더 간결한 버전은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="d0bfa-146">사용 가능한 디스크 공간 가져오기</span><span class="sxs-lookup"><span data-stu-id="d0bfa-146">Getting Available Disk Space</span></span>

<span data-ttu-id="d0bfa-147">로컬 드라이브의 디스크 공간 및 여유 공간을 보려면 Win32_LogicalDisk WMI 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-147">To see the disk space and free space for local drives, you can use the WMI Win32_LogicalDisk class.</span></span> <span data-ttu-id="d0bfa-148">DriveType이 3(WMI에서 고정 하드 디스크에 사용하는 값)인 인스턴스만 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-148">You need to see only instances with a DriveType of 3—the value WMI uses for fixed hard disks.</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="d0bfa-149">로그온 세션 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="d0bfa-149">Getting Logon Session Information</span></span>

<span data-ttu-id="d0bfa-150">WMI Win32_LogonSession 클래스를 통해 사용자와 관련된 로그온 세션에 대한 일반적인 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-150">You can get general information about logon sessions associated with users through the WMI Win32_LogonSession class:</span></span>

```powershell
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="d0bfa-151">컴퓨터에 로그온한 사용자 가져오기</span><span class="sxs-lookup"><span data-stu-id="d0bfa-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="d0bfa-152">Win32_ComputerSystem을 사용하여 특정 컴퓨터 시스템에 로그온한 사용자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="d0bfa-153">이 명령은 시스템 데스크톱에 로그온한 사용자만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="d0bfa-154">컴퓨터에서 로컬 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="d0bfa-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="d0bfa-155">WMI Win32_LocalTime 클래스를 사용하여 특정 컴퓨터에서 현재 로컬 시간을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-155">You can retrieve the current local time on a specific computer by using the WMI Win32_LocalTime class.</span></span> <span data-ttu-id="d0bfa-156">기본적으로 이 클래스는 모든 메타데이터를 표시하기 때문에 **Select-Object**를 사용하여 필터링하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-156">Because this class by default displays all metadata, you may want to filter it using **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### <a name="displaying-service-status"></a><span data-ttu-id="d0bfa-157">서비스 상태 표시</span><span class="sxs-lookup"><span data-stu-id="d0bfa-157">Displaying Service Status</span></span>

<span data-ttu-id="d0bfa-158">특정 컴퓨터에서 모든 서비스의 상태를 보려면 앞에서 설명한 대로 **Get-Service** cmdlet을 로컬에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-158">To view the status of all services on a specific computer, you can locally use the **Get-Service** cmdlet as mentioned earlier.</span></span> <span data-ttu-id="d0bfa-159">원격 시스템의 경우 WMI Win32_Service 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-159">For remote systems, you can use the WMI Win32_Service class.</span></span> <span data-ttu-id="d0bfa-160">또한 **Select-Object**를 사용하여 결과를 **Status**, **Name** 및 **DisplayName**으로 필터링하는 경우 출력 형식이 **Get-Service**의 출력 형식과 거의 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-160">If you also use **Select-Object** to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from **Get-Service**:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="d0bfa-161">이름이 매우 긴, 가끔 발생하는 서비스의 이름을 전체 표시하려면 **AutoSize** 및 **Wrap** 매개 변수와 함께 **Format-Table**을 사용하여 열 너비를 최적화하고 긴 이름이 잘리는 대신 줄 바꿈되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bfa-161">To allow the complete display of names for the occasional services with extremely long names, you may want to use **Format-Table** with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```