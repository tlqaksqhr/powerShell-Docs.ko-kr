# 구성, 리소스 및 보고서 리포지토리의 분리

이번 릴리스에서는 하나 이상의 DSC 끌어오기 서버로 끌어오고 보고해야 하는 모든 유연성을 허용합니다. 각 끝점을 개별적으로 정의하여 한 위치에서는 구성을, 다른 위치에서는 리소스를 끌어와 또 다른 위치에 보고할 수 있습니다. 다음 메타 구성만으로 수행할 수 있습니다.

```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
    }

    ConfigurationRepositoryWeb Configurations
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```

또한 이러한 기능을 조합하여 사용할 수 있습니다. 다음 메타 구성에서는 대상 노드를 밀어넣기 모드로 구성하지만 이 노드는 'DSC 끌어오기 서버'에서 설치하지 않은 리소스를 끌어오고 해당 상태를 다른 'DSC 끌어오기 서버'에 보고합니다.


```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "Push";
        RebootNodeIfNeeded = $true;
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```<!--HONumber=Mar16_HO2-->
