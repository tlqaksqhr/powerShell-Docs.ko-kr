---
title: 컴퓨터에 대한 정보 수집
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
---
# 컴퓨터에 대한 정보 수집
**Get\-WmiObject**는 일반적인 시스템 관리 작업에 사용되는 가장 중요한 cmdlet입니다. 모든 중요한 하위 시스템 설정은 WMI를 통해 노출됩니다. 또한 WMI는 하나 이상의 항목 컬렉션에 있는 개체로 데이터를 처리합니다. Windows PowerShell은 개체에서도 작동하며 단일 또는 여러 개체를 동일한 방식으로 처리할 수 있게 해주는 파이프라인이 있기 때문에 일반적인 WMI 액세스를 통해 몇 가지 고급 작업을 매우 적은 노력으로 수행할 수 있습니다.

다음 예제에서는 임의 컴퓨터에 대해 **Get\-WmiObject**를 사용하여 특정 정보를 수집하는 방법을 보여 줍니다. 로컬 컴퓨터를 나타내는 점 값(**.**)과 함께 **ComputerName** 매개 변수를 지정합니다. WMI를 통해 연결할 수 있는 컴퓨터와 연관된 이름 또는 IP 주소를 지정할 수 있습니다. 로컬 컴퓨터에 대한 정보를 검색하려면 **\-ComputerName**을 생략할 수 있습니다.

### 데스크톱 설정 표시
먼저 로컬 컴퓨터에서 데스크톱 정보를 수집하는 명령을 실행하겠습니다.

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

이렇게 하면 사용 여부에 관계없이 모든 데스크톱에 대한 정보가 반환됩니다.

> [!NOTE]
> 일부 WMI 클래스에서 반환되는 정보는 매우 자세할 수 있으며, WMI 클래스에 대한 메타데이터가 포함된 경우도 있습니다. 이러한 메타데이터 속성에는 대부분 이중 밑줄로 시작하는 이름이 있으므로 Select\-Object를 사용하여 속성을 필터링할 수 있습니다. **\[a\-z]\&#42;**를 속성 값으로 사용하여 알파벳 문자로 시작하는 속성만 지정합니다. 예:

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

메타데이터를 필터링하려면 파이프라인 연산자(|)를 사용하여 Get\-WmiObject 명령의 결과를 **Select\-Object \-Property \[a\-z]\&#42;**로 보냅니다.

### BIOS 정보 표시
WMI Win32\_BIOS 클래스는 로컬 컴퓨터의 시스템 BIOS에 대한 전체 정보를 비교적 간결하게 반환합니다.

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### 프로세서 정보 표시
정보를 필터링하려는 경우가 많지만 WMI의 **Win32\_Processor** 클래스를 사용하여 일반적인 프로세서 정보를 검색할 수 있습니다.

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

프로세서 제품군에 대한 일반적인 설명 문자열을 위해 **Win32\_ComputerSystemSystemType** 속성을 반환할 수 있습니다.

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### 컴퓨터 제조업체 및 모델 표시
**Win32\_ComputerSystem**을 통해 컴퓨터 모델 정보를 확인할 수도 있습니다. OEM 데이터를 제공하기 위해 표시되는 표준 출력을 필터링하지 않아도 됩니다.

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

일부 하드웨어의 정보를 직접 반환하는 이러한 명령의 출력 품질은 보유한 데이터에 따라 달라집니다. 일부 정보는 하드웨어 제조업체에서 제대로 구성하지 않아 제공되지 않을 수도 있습니다.

### 설치된 핫픽스 표시
**Win32\_QuickFixEngineering**을 사용하여 설치된 모든 핫픽스를 표시할 수 있습니다.

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

이 클래스는 다음과 같은 핫픽스 목록을 반환합니다.

```
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

더 간결한 출력을 위해 일부 속성을 제외할 수도 있습니다. **Get\-WmiObject 속성** 매개 변수를 사용하여 **HotFixID**만 선택할 수도 있지만, 이렇게 하면 기본적으로 모든 메타데이터가 표시되기 때문에 실제로 자세한 정보가 반환됩니다.

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId
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

**Get\-WmiObject**의 Property 매개 변수는 Windows PowerShell로 반환되는 개체가 아니라 WMI 클래스 인스턴스에서 반환되는 속성을 제한하기 때문에 추가 데이터가 반환됩니다. 출력을 줄이려면 **Select\-Object**를 사용합니다.

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### 운영 체제 버전 정보 표시
**Win32\_OperatingSystem** 클래스 속성에는 버전 및 서비스 팩 정보가 포함되어 있습니다. 이러한 속성만 명시적으로 선택하여 **Win32\_OperatingSystem**에서 버전 정보 요약을 가져올 수 있습니다.

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

**Select\-Object 속성** 매개 변수와 함께 와일드카드를 사용할 수도 있습니다. **Build** 또는 **ServicePack**으로 시작하는 모든 속성을 여기서 사용하는 것이 중요하기 때문에 다음과 같은 형태로 축약할 수 있습니다.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### 로컬 사용자 및 소유자 표시
사용이 허가된 사용자 수, 현재 사용자 수, 소유자 이름 등의 로컬 일반 사용자 정보는 **Win32\_OperatingSystem** 속성을 선택하여 확인할 수 있습니다. 다음과 같이 표시할 속성을 명시적으로 선택할 수 있습니다.

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

와일드카드를 사용하는 더 간결한 버전은 다음과 같습니다.

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### 사용 가능한 디스크 공간 가져오기
로컬 드라이브의 디스크 공간 및 여유 공간을 보려면 Win32\_LogicalDisk WMI 클래스를 사용할 수 있습니다. DriveType이 3(WMI에서 고정 하드 디스크에 사용하는 값)인 인스턴스만 표시해야 합니다.

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

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

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### 로그온 세션 정보 가져오기
WMI Win32\_LogonSession 클래스를 통해 사용자와 관련된 로그온 세션에 대한 일반적인 정보를 가져올 수 있습니다.

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### 컴퓨터에 로그온한 사용자 가져오기
Win32\_ComputerSystem을 사용하여 특정 컴퓨터 시스템에 로그온한 사용자를 표시할 수 있습니다. 이 명령은 시스템 데스크톱에 로그온한 사용자만 반환합니다.

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### 컴퓨터에서 로컬 시간 가져오기
WMI Win32\_LocalTime 클래스를 사용하여 특정 컴퓨터에서 현재 로컬 시간을 검색할 수 있습니다. 기본적으로 이 클래스는 모든 메타데이터를 표시하기 때문에 **Select\-Object**를 사용하여 필터링하는 것이 좋습니다.

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

### 서비스 상태 표시
특정 컴퓨터에서 모든 서비스의 상태를 보려면 앞에서 설명한 대로 **Get\-Service** cmdlet을 로컬에서 사용할 수 있습니다. 원격 시스템의 경우 WMI Win32\_Service 클래스를 사용할 수 있습니다. 또한 **Select\-Object**를 사용하여 결과를 **Status**, **Name** 및 **DisplayName**으로 필터링하는 경우 출력 형식이 **Get\-Service**의 출력 형식과 거의 동일합니다.

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

이름이 매우 긴, 가끔 발생하는 서비스의 이름을 전체 표시하려면 **AutoSize** 및 **Wrap** 매개 변수와 함께 **Format\-Table**을 사용하여 열 너비를 최적화하고 긴 이름이 잘리는 대신 줄 바꿈되도록 할 수 있습니다.

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```



<!--HONumber=Apr16_HO1-->


