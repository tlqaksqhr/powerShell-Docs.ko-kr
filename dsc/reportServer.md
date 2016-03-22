# DSC 보고서 서버 사용

> 적용 대상: Windows PowerShell 5.0

> **참고:** 이 항목에 설명된 보고서 서버는 PowerShell 4.0에서 사용할 수 없습니다. PowerShell 4.0에서의 보고에 대해서는 DSC 준수 서버를 사용을 참조하세요.

노드의 LCM(로컬 구성 관리자)은 해당 구성 상태에 대한 보고서를 끌어오기 서버에 보내도록 구성할 수 있습니다. 이렇게 하면 해당 데이터를 검색하도록 쿼리할 수 있습니다. 노드는 구성을 확인하고 적용할 때마다
보고서를 보고서 서버에 보냅니다. 이러한 보고서는 서버의 데이터베이스에 저장되며, 보고 웹 서비스를 호출하여 검색할 수 있습니다. 각 보고서에는
적용된 구성, 성공 여부, 사용된 리소스, 발생한 모든 오류, 시작 및 완료 시간 등의 정보가 포함됩니다.

## 보고서를 보내도록 노드 구성

노드의 LCM 구성에서 **ReportServerWeb** 블록을 사용하여 서버에 보고서를 보내도록 노드에게 지시하세요(LCM 구성에 대해서는
 [로컬 구성 관리자 구성](metaConfig.md) 참조). 노드가 보내는 보고서를 받는 서버는 웹 끌어오기 서버로 설정되어 있어야 합니다(SMB 공유에는 보고서를
 보낼 수 없음). 끌어오기 서버 설정에 대한 내용은 [DSC 웹 끌어오기 서버 설정](pullServer.md)을 참조합니다. 보고서 서버는 노드가 구성을 끌어오고
 리소스를 가져오는 서비스와 동일한 서비스일 수도 있고, 또는 다른 서비스일 수 있습니다.
 
 **ReportServerWeb** 블록에서는 끌어오기 서비스의 URL과
 서버에 알려진 등록 키를 지정합니다.
 
  다음 구성은 한 서비스에서 구성을 끌어오고 다른 서버의 서비스에 보고서를 보내도록
 노드를 구성합니다. 
 
```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}
PullClientConfigID
```

## 보고서 데이터 가져오기

끌어오기 서버에 전송된 보고서는 서버의 데이터베이스에 입력됩니다. 보고서는 웹 서비스 호출을 통해 사용할 수 있습니다. 특정 노드에 대한 보고서를 검색하려면, 
보고서 웹 서비스에 다음 형식으로 HTTP 요청을 보냅니다.
`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentID = MyNodeAgentId)/Reports` 
여기서 `MyNodeAgentId`는 보고서를 가져올 노드의 에이전트 ID입니다. 해당 노드에서 [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)를 호출하여 노드에 대한 에이전트 ID를
가져올 수 있습니다.

보고서는 JSON 개체의 배열로 반환됩니다.

다음 스크립트는 스크립트가 실행되는 노드에 대한 보고서를 반환합니다.

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCReportServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## 보고서 데이터 보기

변수를 **GetReport** 함수의 결과로 설정하는 경우, 반환되는 배열의 요소에서 개별 필드를 볼 수 있습니다.

```powershell
$reports = GetReport
$reports[1]

JobId                : 71515ae8-7294-40a3-8137-fc85bf4b678f
OperationType        : Consistency
RefreshMode          : 
Status               : 
ReportFormatVersion  : 1.0
ConfigurationVersion : 2.0.0
StartTime            : 02/08/2016 01:28:54
EndTime              : 02/08/2016 01:28:57
RebootRequested      : False
Errors               : {}
StatusData           : {{"NumberOfResources":"2","Locale":"en-US","ResourcesInDesiredState":[{"ResourceId":"[WindowsFeature]MyFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::4::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"},{"ResourceId":"[WindowsFeature]My2ndFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::8::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"}]}}
```

**StatusData** 필드는 **NumberOfResources**, **Locale** 및 **ResourcesInDesiredState**, 이 세 가지 속성을 가진 개체입니다. **ResourcesInDesiredState** 속성은
각각 다양한 속성을 갖는 개체의 배열입니다. 다음 스크립트에서는 매개 변수로서 단일 보고서를 사용하고, 해당 **ResourcesInDesiredState**
배열을 통해 반복하고, 콘솔에 씁니다.
 
```powershell
function GetStatusData
{
    param ($Report)
    $statusData = $Report.StatusData | ConvertFrom-Json

    $Resources = $statusData.ResourcesInDesiredState

    Foreach ($Resource in $Resources)
    {
        Write-Host 'ResourceId: ' $Resource.ResourceId
        Write-Host 'SourceInfo: ' $Resource.SourceInfo
        Write-Host 'ModuleName: ' $Resource.ModuleName
        Write-Host 'ModuleVersion: ' $Resource.ModuleVersion
        Write-Host 'ConfigurationName: ' $Resource.ConfigurationName
        Write-Host 'ResourceName: ' $Resource.ResourceName
        Write-Host
    }
}
```

다음은 **GetStatusData** 함수를 호출한 후의 샘플 출력입니다.

```powershell
GetStatusData -Report $report[1]

ResourceId:  [WindowsFeature]MyFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::4::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature

ResourceId:  [WindowsFeature]My2ndFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::8::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature
```

이러한 예제는 보고서 데이터로 수행할 수 있는 작업에 대해 알 수 있도록 하기 위한 것입니다. PowerShell에서의 JSON 사용에 대한 소개 내용을 알려면
[Playing with JSON and PowerShell(JSON 및 PowerShell 사용)](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/)을 참조하세요.

## 참고 항목
>[로컬 구성 관리자 구성](metaConfig.md)
>[DSC 웹 끌어오기 서버 설정](pullServer.md)
>[구성 이름을 사용하여 끌어오기 클라이언트 설정](pullClientConfigNames.md)
<!--HONumber=Feb16_HO4-->
