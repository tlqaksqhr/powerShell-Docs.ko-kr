# 구성 상태에 대한 세부 정보

`Get-DscConfigurationStatus` cmdlet은 대상 노드에서 구성 상태에 대한 정보를 가져옵니다. 구성 실행의 성공 여부에 대한 상위 수준 정보를 포함하는 다양한 개체가 반환됩니다. 개체를 자세히 검토하면 다음과 같은 구성 실행에 대한 정보를 검색할 수 있습니다.

* 실패한 모든 리소스
* 다시 부팅을 요청한 모든 리소스
* 구성 실행 시 메타 구성 설정
* 기타

다음 매개 변수 집합은 마지막 구성 실행에 대한 상태 정보를 반환합니다.

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
다음 매개 변수 집합은 모든 이전 구성 실행에 대한 상태 정보를 반환합니다.

```powershell
Get-DscConfigurationStatus  -All 
                            [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```

## 예제

```powershell
PS C:\> $Status = Get-DscConfigurationStatus 

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :   
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :   
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :   
InDesiredState          :   False
InitialState            :   
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```<!--HONumber=Mar16_HO2-->
