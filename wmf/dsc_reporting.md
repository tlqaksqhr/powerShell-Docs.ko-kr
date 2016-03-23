# 중앙 위치에 구성 상태 보고

DSC 구성 상태에 대한 자세한 정보를 DSC 서비스를 실행하는 서버로 전송할 수 있습니다. Get-DscConfigurationStatus cmdlet에서 반환하는 동일한 정보는 DSC 서비스로 전송됩니다. 메타 구성에서 보고서 서버를 정의하면 이 상태는 오류가 발생하거나 구성이 완료될 때 서버로 전송됩니다. 이 정보는 노드가 끌어오기 또는 밀어넣기 모드로 구성되면 전송됩니다. 상태 정보는 DSC 서비스 데이터베이스에 저장됩니다.

## 상태 보고에 대한 샘플 메타 구성
```PowerShell
[DscLocalConfigurationManager()]
Configuration ReportingClientMetaConfig
{
    Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PUSH"
            ConfigurationModeFrequencyMins = 15
            AllowModuleOverwrite = $true
        }

        ReportServerWeb ReportManager
        {
            ServerUrL = "http://localhost:8080/PSDSCPullServer/PSDSCPullserver.svc"
            AllowUnsecureConnection  = $true
        }           
}
```
이 상태 정보를 노출하는 새 OData 끝점이 DSC 서비스에 생성됩니다. 구성 ID 또는 에이전트 ID {$guid}를 끝점에 전달하면 노드에 대한 모든 상태를 수집하고 구문 분석할 수 있습니다.

## 구성 상태를 수집하는 샘플 웹 요청 
```PowerShell
$statusReports = Invoke-WebRequest -Uri "[http://localhost:8080/PSDSCPullserver/PSDSCPullserver.svc/Node(ConfigurationId='$guid')/StatusReport](http://localhost:8080/PSDSCPullserver/psdscpullserver.svc/Node(ConfigurationId='$guid')/StatusReport)s" -UseBasicParsing -UseDefaultCredentials -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" -Headers @{Accept = "application/json"; ProtocolVersion = “1.1”}
```<!--HONumber=Mar16_HO2-->
