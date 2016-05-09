# DSC 스크립트 리소스

 
> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)의 **스크립트** 리소스에서는 대상 노드에서 Windows PowerShell 스크립트 블록을 실행하는 메커니즘을 제공합니다. `Script` 리소스에 `GetScript`, `SetScript`, 및 `TestScript` 속성이 있습니다. 이러한 속성은 각 대상 노드에서 실행될 스크립트 블록에 설정되어야 합니다. 

`GetScript` 스크립트 블록은 현재 노드의 상태를 나타내는 해시 테이블을 반환해야 합니다. 아무것도 반환할 필요가 없습니다. DSC는 스크립트 블록의 출력을 사용해 아무런 작업도 하지 않습니다.

`TestScript` 스크립트 블록이 현재 노드를 수정해야 하는지 결정해야 합니다. 노드 최신 상태이면 `$true`를 반환해야 합니다. 노드의 구성이 최신 상태가 아니면 `$false`를 반환하고 `SetScript` 스크립트 블록으로 업데이트해야 합니다. `TestScript` 스크립트 블록이 DSC에 의해 호출됩니다.

`SetScript` 스크립트 블록에서 노드를 수정해야 합니다. `TestScript` 블록이 `$false`를 차단하는 경우 DSC에 의해 호출됩니다.

`GetScript`, `TestScript` 또는 `SetScript` 스크립트 블록에서 구성 스크립트의 변수를 사용해야 하는 경우 `$using:` 범위를 사용하세요(아래 예제 참조).


## 구문

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## 속성

|  속성  |  설명   | 
|---|---| 
| GetScript| [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet을 호출할 때 실행되는 Windows PowerShell 스크립트 블록을 제공합니다. 이 블록은 해시 테이블을 반환해야 합니다.| 
| SetScript| Windows PowerShell 스크립트 블록을 제공합니다. [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하면 **TestScript** 블록이 가장 먼저 실행됩니다. **TestScript** 블록에서 **$false**를 반환한다면, **SetScript** 블록이 실행됩니다. **TestScript** 블록에서 **$true**를 반환한다면, **SetScript** 블록이 실행되지 않습니다.| 
| TestScript| Windows PowerShell 스크립트 블록을 제공합니다. [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하면 이 블록이 실행됩니다. **$false**를 반환한다면, SetScript 블록이 실행됩니다. **$true**를 반환한다면, SetScript 블록이 실행되지 않습니다. [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet을 호출하면 **TestScript** 블록도 실행됩니다. 그러나 이 경우에서는 TestScript 블록이 어떤 값을 반환하는지 관계없이 **SetScript** 블록이 실행되지 않습니다. 실제 구성이 현재 필요한 상태 구성과 일치하는 경우 **TestScript** 블록은 True를 반환해야 하고, 일치하지 않는 경우에는 False를 반환해야 합니다. (현재 필요한 상태 구성은 DSC를 사용하는 노드에서 시행된 마지막 구성입니다.)| 
| 자격 증명| 자격 증명이 필요한 경우 이 스크립트를 실행하는 데 사용할 자격 증명을 나타냅니다.| 
| DependsOn| 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.

## 예제 1
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { <# This must return a hash table #> }          
}
```

## 예 2
```powershell
$version = Get-Content 'version.txt'
Script UpdateConfigurationVersion
{
    GetScript = { 
        $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        return @{ 'Version' = $currentVersion }
    }          
    TestScript = { 
        $state = GetScript
        if( $state['Version'] -eq $using:version )
        {
            Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
            return $true
        }
        Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
        return $false
    }
    SetScript = { 
        $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
    }
}
```

이 리소스는 텍스트 파일에 구성의 버전을 쓰는 중입니다. 이 버전은 클라이언트 컴퓨터에서 사용할 수 있지만, 어느 노드에도 없으므로 PowerShell의 `using` 범위를 가진 `Script` 리소스의 각 스크립트 블록에 전달해야 합니다. 노드의 MOF 파일을 생성할 때 `$version` 변수의 값을 클라이언트 컴퓨터의 텍스트 파일로부터 읽어옵니다. DSC는 각 스크립트 블록의 `$using:version` 변수를 `$version` 변수의 값으로 바꿉니다.



<!--HONumber=Apr16_HO2-->


