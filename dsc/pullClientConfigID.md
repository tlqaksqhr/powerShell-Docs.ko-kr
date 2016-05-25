# 구성 ID를 사용하여 끌어오기 클라이언트 설정

> 적용 대상: Windows PowerShell 5.0

각 대상 노드는 끌어오기 모드를 사용하도록 지시 받고 끌어오기 서버에 연결하여 구성을 가져올 수 있는 URL을 받아야 합니다. 이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다. LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다. LCM을 구성에 대한 자세한 내용은 [LCM(로컬 구성 관리자) 구성](metaConfig.md)을 참조합니다..

> **참고**: 이 항목은 PowerShell 5.0에 적용됩니다. PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 것에 대해서는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.

다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }      
    }
}
PullClientConfigID
```

스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다. **ServerURL**

이 스크립트가 실행되면, **PullClientConfigID**라는 새 출력 폴더가 생성되고, 그 안에 메타 구성 MOF 파일이 생깁니다. 이 경우 메타 구성 MOF 파일의 이름은 다음과 같이 지정됩니다. `localhost.meta.mof`.

구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다. 예: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## 구성 ID

스크립트는 이전에 이 목적으로 만들어진 GUID에 LCM의 **ConfigurationID** 속성을 설정합니다(**New-Guid** cmdlet을 사용하여 GUID를 만들 수 있음). **ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다. 끌어오기 서버의 구성 MOF 파일의 이름은 _ConfigurationID_.mof로 지정해야 합니다. 여기서 _ConfigurationID_는 대상 노드 LCM의 **ConfigurationID** 속성 값입니다.

## SMB 끌어오기 서버

SMB 서버에서 구성을 끌어오도록 클라이언트를 설정하려면 **ConfigurationRepositoryShare** 블록을 사용합니다. **ConfigurationRepositoryShare** 블록에서 **SourcePath** 속성을 설정하여 서버 경로를 지정합니다. 다음 메타 구성은 **SMBPullServer**라는 SMB 끌어오기 서버에서 끌어오도록 대상 노드를 구성합니다..

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## 리소스 및 보고서 서버

앞의 예와 같이 LCM 구성에서 **ConfigurationRepositoryWeb** 또는 **ConfigurationRepositoryShare** 블록만 지정하는 경우 끌어오기 클라이언트가 
지정된 서버에서 리소스를 끌어오지만 서버에 보고서를 보내지 않습니다. 구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있지만 
**ReportRepositoryWeb** 블록을 만들어 보고를 설정해야 합니다. 

다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을
보여 줍니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

또한, 리소스 및 보고에 대해 다른 끌어오기 서버를 지정할 수도 있습니다. 리소스 서버를 지정하려면 **ResourceRepositoryWeb**(웹 끌어오기 서버용) 또는 
**ResourceRepositoryShare** 블록(SMB 끌어오기 서버용)을 사용합니다.
보고서 서버를 지정하려면 **ReportRepositoryWeb** 블록을 사용합니다. 보고서 서버는 SMB 서버일 수 없습니다.
해당 메타 구성은 **CONTOSO-PullSrv**에서 구성을 가져오고 **CONTOSO-ResourceSrv**에서 리소스를 가져오고, **CONTOSO-ReportSrv**에 상태 보고서를 보내도록 끌어오기 클라이언트를 구성합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## 참고 항목

* [구성 이름을 사용하여 끌어오기 클라이언트 설정](pullClientConfigNames.md)


<!--HONumber=May16_HO2-->


