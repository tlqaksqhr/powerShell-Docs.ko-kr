# 노드 및 구성 ID의 분리

## 개요

끌어오기 모드에서 DSC를 사용할 때 보다 유연하고 원활한 환경을 제공하기 위해 이번 릴리스에서 많은 기능을 추가했습니다. 이러한 기능은 각 노드에 대해 개별적으로 상태를 추적하고 정보를 보고하면서 여러 노드 간에 구성을 쉽게 설정하고 배포할 수 있는 유연성을 제공하기 위한 것입니다. 이러한 기능은 다음과 같습니다.

* 컴퓨터에 대한 구성을 식별하는 구성 이름. 이 이름은 여러 대상 노드에서 공유할 수 있습니다. 
* 단일 노드를 고유하게 식별하는 에이전트 ID
* 대상 노드가 끌어오기 서버에 처음으로 연결할 때만 수행되는 등록 단계

**참고:** 이러한 기능은 추가된 것이며 기존의 끌어오기 기능 및 개념을 대체하지 않습니다. 이번 릴리스에서 제공되는 새로운 끌어오기 서버에서는 이러한 새로운 기능이나 이전 기능을 사용할 수 있습니다.

## 에이전트 ID

이 기능은 각 대상 노드에 대해 고유 식별자를 설정하고 관리하지 않으려는 사용자를 위한 것입니다. 이제 더 이상 GUID를 기록할 필요가 없습니다. DSC에서 끌어오기 서버와 통신할 때 사용하는 에이전트 ID를 자동으로 생성합니다. 이 ID는 끌어오기 서버에서 지정된 노드에 대한 모든 정보를 고유하게 식별하는 데 사용됩니다. 또한 고유 ID를 포함하는 고유한 meta-configuation으로 각 대상 노드를 설정할 필요가 없으므로 많은 대상 노드에서 각 노드의 고유 ID를 유지하면서 단일 meta-configuation을 사용할 수 있습니다. 

## 구성 이름

구성 이름은 대상 노드에서 적용할 구성의 이름을 정의하는 식별 이름입니다. 이 기능과 관련된 변경 내용은 다음과 같습니다.  

### 식별 이름 지정

모든 문자열을 사용할 수 있습니다. GUID 형식일 필요가 없으므로 SQL server를 설정하는 구성의 경우 이름을 'SQL_Server'라고만 지정하면 됩니다. 따라서 특정 구성의 용도를 훨씬 더 쉽게 식별할 수 있습니다.

### 할당

대상 노드가 할당되는 구성은 끌어오기 서버의 중앙에서 관리됩니다. 이 기능은 메타 구성에서 ConfigrationName 속성을 정의하여 부트스트랩할 수 있지만 등록하는 동안에만 사용됩니다. 등록 후에는 서버가 가져올 구성을 대상 노드에 알립니다. 온-프레미스 끌어오기 서버의 경우 구성과 대상 노드 간의 이 매핑을 등록 중에만 수행할 수 있지만 Azure 자동화에서는 UI나 해당 cmdlet을 통해 쉽게 변경할 수 있습니다. 온-프레미스 끌어오기 서버의 경우 대상 노드에 할당된 구성을 변경하려면 등록을 다시 실행할 수 있습니다.

### 여러/부분 구성

여러 구성 이름이 대상 노드에 할당되는 경우 부분 구성으로 처리됩니다. 이 기능이 작동하려면 부분 구성을 허용하도록 대상 노드의 메타 구성을 구성해야 합니다. **참고:** 이 기능은 온-프레미스 끌어오기 서버에서만 지원됩니다. Azure 자동화에서는 부분 구성을 지원하지 않습니다.

## 등록

구성 이름이 더 이상 GUID가 아니고 식별 이름이므로 모든 사용자가 추측할 수 있습니다. 따라서 본질적으로 발생되는 보안 문제를 완하하기 위해 노드가 서버에서 구성 요청을 시작하기 이전의 등록 단계를 추가했습니다. 노드는 공유 암호(노드와 서버 둘 다 이미 알고 있음) 및 필요에 따라 요청될 구성의 이름을 사용하여 끌어오기 서버에 자신을 등록합니다. 이 공유 암호는 각 컴퓨터에 대해 고유할 필요가 없습니다. 가정: 공유 암호는 GUID 처럼 추측하기 어려운 식별자입니다. 이 공유 암호는 대상 노드 메타 구성의 **RegistrationKey** 속성으로 정의됩니다.

### 예제 메타 구성

```powershell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
        ConfigurationModeFrequencyMins = 60;
    }

    ConfigurationRepositoryWeb ConfigurationManager
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
        ConfigurationNames = @(“WebRole”)
    }
}

SampleMetaConfig
```

RegistrationKey 값은 끌어오기 서버에서 정의해야 합니다. 끌어오기 서버를 설정하는 동안 이 작업을 수행하려면 다음과 같이 이름이 **RegistrationKeys.txt**인 텍스트 파일을 특정 위치에 만든 다음 끌어오기 서버의 web.config에서 이 위치를 설정합니다.  

```XML
<add key="ConfigurationPath" value="C:\Program Files\WindowsPowerShell\DscService\Configuration">

<add key="ModulePath" value="C:\Program Files\WindowsPowerShell\DscService\Modules">

<add key="RegistrationKeyPath" value="C:\Program Files\WindowsPowerShell\DscService">
```

이 작업에 사용할 온-프레미스 끌어오기 서버를 완전히 배포하려면 최신 버전의 xDSCWebService DSC 리소스를 사용하세요. 전체 구성은 [Example Configuration(예제 구성)](https://github.com/grayzu/PSSummitEU2015/blob/master/PullServer/02%20-%20PullServer%20Config.ps1)을 참조하세요.

**참고:** 이 기능은 끌어오기 서버가 파일 공유로 설정된 경우 지원되지 않습니다. 웹 기반 끌어오기 서버에서만 지원됩니다.<!--HONumber=Mar16_HO2-->
