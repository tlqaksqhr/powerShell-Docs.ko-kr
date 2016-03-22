# 구성 이름을 사용하여 끌어오기 클라이언트 설정

> 적용 대상: Windows PowerShell 5.0

각 대상 노드는 끌어오기 모드를 사용하도록 지시 받고 끌어오기 서버에 연결하여 구성을 가져올 수 있는 URL을 받아야 합니다. 이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다. LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다. LCM을 구성에 대한 자세한 내용은 [LCM(로컬 구성 관리자) 구성](metaConfig.md)을 참조합니다.

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
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
            
        }      
    }
}
PullClientConfigID
```

스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다. **ServerURL** 속성은 끌어오기 서버에 대한 끝점을 지정합니다.

**RegistrationKey** 속성은 끌어오기 서버에 대한 모든 클라이언트 노드와 해당 끌어오기 서버 간의 공유 키입니다. 동일한 값이 끌어오기 서버에 있는 파일에 저장됩니다. **ConfigurationNames** 속성은 클라이언트 노드용으로 의도된 구성의 이름을 지정합니다. 끌어오기 서버에서 이 클라이언트 노드에 대한 구성 MOF 파일의 이름은 *ConfigurationNames*.mof로 지정해야 하며, 여기서 *ConfigurationNames*는 이 메타 구성에서 설정한 **ConfigurationNames** 속성의 값과 일치해야 합니다.

이 스크립트가 실행되면, **PullClientConfigID**라는 새 출력 폴더가 생성되고, 그 안에 메타 구성 MOF 파일이 생깁니다. 이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.

구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다. 예를 들면 다음과 같습니다. `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

> **참고**: 등록 키는 웹 끌어오기 서버에만 작동합니다. SMB 끌어오기 서버에는 여전히 **ConfigurationID**를 사용해야 합니다. **ConfigurationID**를 사용하여 끌어오기 서버를 구성하는 것에 대해서는 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)을 참조하세요.

## 리소스 및 보고서 서버

기본적으로 클라이언트 노드는 구성 끌어오기 서버에서 필수 리소스를 가져오고 상태를 보고합니다. 그러나 리소스 및 보고에 대해 다른 끌어오기 서버를 지정할 수 있습니다.
리소스 서버를 지정하려면, **ResourceRepositoryWeb**(웹 끌어오기 서버용) 및 **ResourceRepositoryShare**(SMB 끌어오기 서버용) 블록을 사용합니다.
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
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
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

* [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)
* [DSC 웹 끌어오기 서버 설정](pullServer.md)
<!--HONumber=Feb16_HO4-->
