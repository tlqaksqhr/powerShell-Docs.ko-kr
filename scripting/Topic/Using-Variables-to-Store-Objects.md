---
title: 변수를 사용하여 개체 저장
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
---
# 변수를 사용하여 개체 저장
Windows PowerShell에서는 개체에 대한 작업을 수행합니다. Windows PowerShell에서는 이름이 기본적으로 지정되는 개체인 변수를 만들어 출력을 나중에 사용하기 위해 저장할 수 있습니다. 다른 셸에서 변수에 대한 작업을 수행하는 데 익숙한 경우 Windows PowerShell 변수는 텍스트가 아닌 개체라는 사실에 주의해야 합니다.

변수 이름은 항상 $ 문자로 시작되며 모든 영숫자 문자와 밑줄을 사용할 수 있습니다.

### 변수 만들기
변수를 만들려면 다음과 같이 유효한 변수 이름을 입력해야 합니다.

```
PS> $loc
PS>
```

이 경우 **$loc**에 지정된 값이 없기 때문에 아무 결과도 표시되지 않습니다. 동일한 단계에서 변수를 만드는 작업과 변수에 값을 할당하는 작업을 수행할 수 있습니다. Windows PowerShell은 변수가 없으면 변수를 만들기만 하고, 변수가 있으면 기존 변수에 지정된 값을 할당합니다. **$loc** 변수에 현재 위치를 저장하려면 다음과 같이 입력합니다.

```
$loc = Get-Location
```

이 명령을 입력하면 출력이 $loc에 보내지기 때문에 아무 결과도 표시되지 않습니다. 출력이 표시된다면 이는 달리 리디렉션되지 않은 데이터가 항상 화면에 표시되기 때문에 발생하는 의도하지 않은 결과입니다. 다음과 같이 $loc를 입력하면 현재 위치가 표시됩니다.

```
PS> $loc

Path
----
C:\temp
```

**Get\-Member**를 사용하여 변수의 내용에 대한 정보를 표시할 수 있습니다. 다음과 같이 $loc를 Get\-Member에 파이프하면 Get\-Location을 입력한 것과 마찬가지로 변수에 **PathInfo** 개체가 포함되어 있는 것을 확인할 수 있습니다.

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### 변수 조작
Windows PowerShell에는 변수를 조작할 수 있는 여러 명령이 포함되어 있습니다. 다음과 같이 입력하면 이러한 명령의 전체 목록을 쉽게 확인할 수 있습니다.

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

현재 Windows PowerShell 세션에서 사용자가 직접 만든 변수 외에도 여러 시스템 정의 변수가 있습니다. **Remove\-Variable** cmdlet을 사용하여 Windows PowerShell에서 제어하지 않는 모든 변수를 지울 수 있습니다. 다음 명령을 입력하면 모든 변수를 지울 수 있습니다.

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

이 경우 다음과 같은 확인 메시지가 나타납니다.

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

**Get\-Variable** cmdlet을 실행하면 나머지 Windows PowerShell 변수를 볼 수 있습니다. 또한 변수 Windows PowerShell 드라이브도 있으므로 다음과 같이 입력하면 모든 Windows PowerShell 변수를 표시할 수도 있습니다.

```
Get-ChildItem variable:
```

### Cmd.exe 변수 사용
Windows PowerShell은 Cmd.exe가 아니지만 명령 셸 환경에서 실행되며 Windows 환경에서 사용할 수 있는 것과 동일한 변수를 사용할 수 있습니다. 이러한 변수는 **env**:라는 드라이브를 통해 표시됩니다. 다음과 같이 입력하면 이러한 변수를 볼 수 있습니다.

```
Get-ChildItem env:
```

표준 변수 cmdlet은 원래 **env:** 변수와 함께 사용하도록 설계되지 않았지만 **env:** 접두사를 지정하여 사용할 수도 있습니다. 예를 들어 운영 체제 루트 디렉터리를 보려면 다음과 같이 입력하여 Windows PowerShell에서 명령 셸 **%SystemRoot%** 변수를 사용하면 됩니다.

```
PS> $env:SystemRoot
C:\WINDOWS
```

또한 Windows PowerShell에서 환경 변수를 만들고 수정할 수도 있습니다. Windows PowerShell에서 액세스하는 환경 변수는 다른 Windows 환경 변수에 대한 일반적인 규칙을 따릅니다.



<!--HONumber=Apr16_HO1-->


