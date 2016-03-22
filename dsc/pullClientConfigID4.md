# PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

각 대상 노드는 끌어오기 모드를 사용하도록 지시 받고 끌어오기 서버에 연결하여 구성을 가져올 수 있는 URL을 받아야 합니다. 이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다. LCM을 구성하려면 "메타 구성"으로 알려진 특수한 형식의 구성을 만듭니다. LCM 구성에 대한 자세한 내용은 [Windows PowerShell 4.0 필요한 상태 구성 로컬 구성 관리자](metaConfig4.md)를 참조하세요.

다음 스크립트는 "PullServer"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 15;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

스크립트에서 **DownloadManagerCustomData**는 끌어오기 서버의 URL을 전달하고, (이 예제의 경우) 보안되지 않은 연결을 허용합니다. 

이 스크립트가 실행되면, **SimpleMetaConfigurationForPull**이라는 새 출력 폴더가 생성되고, 그 안에 메타 구성 MOF 파일이 생깁니다.

구성을 적용하려면 **ComputerName**("localhost" 사용) 및 **Path**(대상 노드의 localhost.meta.mof 파일의 위치 경로)에 대한 매개 변수와 함께 **Set-DscLocalConfigurationManager**를 사용합니다. 예: 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## 구성 ID
스크립트는 이전에 이 목적으로 만들어진 GUID에 LCM의 **ConfigurationID** 속성을 설정합니다(**New-Guid** cmdlet을 사용하여 GUID를 만들 수 있음). **ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다. 끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다.
<!--HONumber=Feb16_HO4-->
