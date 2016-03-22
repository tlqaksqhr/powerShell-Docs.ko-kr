# DSC 리소스 디버그

> 적용 대상: Windows PowerShell 5.0

PowerShell 5.0에서는 구성이 적용됨에 따라 DSC 리소스를 디버그할 수 있도록 해주는 새로운 기능이 DSC(필요한 상태 구성)에 도입되었습니다.

## DSC 디버그 사용
리소스를 디버그할 수 있으려면 먼저, [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx) cmdlet을 호출하여 디버그할 수 있도록 해야 합니다. 이 cmdlet은 필수 매개 변수인 **BreakAll**을 사용합니다. [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)를 호출한 결과를 보면 디버그할 수 있도록 되어 있는지 확인할 수 있습니다. 다음의 PowerShell 출력은 디버그 사용의 결과를 보여 줍니다.


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## 디버그를 사용하도록 설정된 구성 시작
DSC 리소스를 디버그하려면 해당 리소스를 호출하는 구성을 시작합니다. 예를 들어 [WindowsFeature](windowsfeatureResource.md)를 호출하여 "WindowsPowerShellWebAccess" 기능이 설치되어 있는지 확인하는 간단한 구성을 살펴보겠습니다.

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
구성을 컴파일한 후에는 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)을 호출하여 구성을 시작합니다. 이 구성은
LCM(로컬 구성 관리자)가 구성에서 첫 번째 리소스를 호출하면 중지됩니다. `-Verbose` 및 `-Wait` 매개 변수를 사용하는 경우, 출력에 디버그를 시작하려면 입력해야 하는
줄이 표시됩니다.

```powershell
PS C:\DebugTest> Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will 
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.  Use the follow
ing commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
이 시점에서 LCM은 리소스를 호출하고 첫 번째 중단점으로 이동했습니다. 출력의 마지막 세 줄에는 프로세스에 연결하여 리소스 스크립트의 디버그를 시작하는 방법이 나옵니다.

## 리소스 스크립트 디버그

PowerShell ISE의 새 인스턴스를 시작합니다. 콘솔 창에서 `Start-DscConifiguration` 출력으로부터 나온 결과의 마지막 세 줄을 명령으로 입력하여 `<credentials>`를
올바른 사용자 자격 증명으로 바꿉니다. 결과 출력은 다음과 같습니다.



<!--HONumber=Feb16_HO4-->
