# 여러 구성 조각을 사용하여 노드 구성(부분 구성)

WMF 5.0에서는 구성 문서를 조작으로 노드에 제공할 수 있습니다. 노드에서 여러 조각의 구성 문서를 받으려면 다음 예제와 같이 예상 조각을 지정하도록 LCM(로컬 구성 관리자)을 설정해야 합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration SQLServerDSCSettings
{
    Node localhost
    {
        Settings
        {
            ConfigurationModeFrequencyMins = 30
        }

        ConfigurationRepositoryWeb OSConfigServer
        {
            ServerURL = "https://corp.contoso.com/OSConfigServer/PSDSCPullServer.svc"
        }

        ConfigurationRepositoryWeb SQLConfigServer
        {
            ServerURL = "https://corp.contoso.com/SQLConfigServer/PSDSCPullServer.svc"
        }

        PartialConfiguration OSConfig
        {
            Description = 'Configuration for the Base OS'
            ExclusiveResources = 'PSDesiredStateConfiguration\*'
            ConfigurationSource = '[ConfigurationRepositoryWeb]OSConfigServer'
        }

        PartialConfiguration SQLConfig
        {
            Description = 'Configuration for the SQL Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]SQLConfigServer'
            DependsOn = '[PartialConfiguration]OSConfig'
        }
    }
}
```

부분 구성에서는 구성 이름이 LCM에 정의된 이름과 일치해야 합니다. 위 예제에서 구성 이름은 `OSConfig`와 `SQLConfig`여여 합니다.

LCM을 부분 구성으로 설정하면 구성을 조정할 수 있지만 보안 기능은 제공하지 않습니다.<!--HONumber=Mar16_HO2-->
