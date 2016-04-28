# DSC 웹 끌어오기 서버 설정

> 적용 대상: Windows PowerShell 5.0

DSC 웹 끌어오기 서버는 해당 노드에서 요청하면 OData 인터페이스를 사용하여 DSC 구성 파일을 대상 노드에 사용할 수 있도록 하는 IIS의 웹 서비스입니다.

끌어오기 서버 사용을 위한 요구 사항:

* 다음 항목을 실행 중인 서버:
  - WMF/PowerShell 5.0 이상
  - IIS 서버 역할
  - DSC 서비스
* 인증서를 생성하여 대상 노드에서 LCM(로컬 구성 관리자)에 전달된 자격 증명을 보호할 방법이 있으면 가장 좋습니다.

서버 관리자에서 역할 및 기능 추가 마법사를 사용하거나 PowerShell을 사용하여 IIS 서버 역할 및 DSC 서비스를 추가할 수 있습니다. 이 항목에 포함된 샘플 스크립트는 이 두 단계를 모두 처리하게 됩니다.

## xWebService 리소스 사용
웹 끌어오기 서버를 설정하는 가장 쉬운 방법은 xPSDesiredStateConfiguration 모듈에 포함된 xWebService 리소스를 사용하는 것입니다. 다음 단계에서는 웹 서비스를 설정하는 구성에서 리소스를 사용하는 방법에 대해 설명합니다.

1. [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet을 호출하여 **xPSDesiredStateConfiguration** 모듈을 설치하세요. **참고**: **Install-Module**은 PowerShell 5.0에 포함된 **PowerShellGet** 모듈에 포함되어 있습니다. [PackageManagement PowerShell 모듈 미리 보기](https://www.microsoft.com/en-us/download/details.aspx?id=49186)에서 PowerShell 3.0 및 4.0용 **PowerShellGet** 모듈을 다운로드할 수 있습니다. 
1. 조직 내 또는 공공 기관 내의 신뢰할 수 있는 인증 기관에서 DSC 끌어오기 서버에 대한 SSL 인증서를 가져옵니다. 기관에서 받은 인증서는 일반적으로 PFX 형식입니다. DSC 끌어오기 서버 역할을 할 노드에서 기본 위치 CERT:\LocalMachine\My에 인증서를 설치합니다. 인증서 지문을 기록해 둡니다.
1. 등록 키로 사용할 GUID를 선택합니다. PowerShell을 사용하여 생성하려면 PS 프롬프트에 '``` [guid]::newGuid()```'를 입력하고 Enter 키를 누릅니다. 이 키는 클라이언트 노드에서 등록할 때 인증할 공유 키로 사용됩니다. 자세한 내용은 아래의 [등록 키](#RegKey) 섹션을 참조하세요.
1. PowerShell ISE에서 다음의 구성 스크립트(**xPSDesiredStateConfiguration** 모듈의 예제 폴더에 Sample_xDscWebService.ps1로 포함됨)를 시작합니다(F5). 이 스크립트는 끌어오기 서버를 설정합니다.
  
```powershell
configuration Sample_xDscWebService 
{ 
    param  
    ( 
            [string[]]$NodeName = 'localhost', 
            
            [ValidateNotNullOrEmpty()] 
            [string] $certificateThumbPrint,
            
            [Parameter(Mandatory)]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey 
     ) 
 
 
     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 

     Node $NodeName 
     { 
         WindowsFeature DSCServiceFeature 
         { 
             Ensure = "Present" 
             Name   = "DSC-Service"             
         } 
 
 
         xDscWebService PSDSCPullServer 
         { 
             Ensure                  = "Present" 
             EndpointName            = "PSDSCPullServer" 
             Port                    = 8080 
             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
             CertificateThumbPrint   = $certificateThumbPrint          
             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
             State                   = "Started" 
             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
         } 

        File RegistrationKeyFile
        {
            Ensure          ='Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}

```

1. 구성을 실행합니다. 이때 SSL 인증서의 지문을 **certificateThumbPrint** 매개 변수로 전달하고 GUID 등록 키를 **RegistrationKey** 매개 변수로 전달합니다.

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certifcates in your local store 
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCService -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutpuPath c:\Configs\PullServer
```

## 등록 키
구성 ID 대신 구성 이름을 사용할 수 있도록 클라이언트 노드가 서버에 등록할 수 있도록 하려면 위 구성에서 만든 등록 키가 `C:\Program Files\WindowsPowerShell\DscService`에서 `RegistrationKeys.txt`라는 파일에 저장되어 있어야 합니다. 등록 키는 끌어오기 서버에 클라이언트를 처음 등록할 때 사용되는 공유 암호 역할을 합니다. 클라이언트는 등록이 완료되면 끌어오기 서버에 고유하게 인증하는 데 사용되는 자체 서명된 인증서를 생성합니다. 이 지문의 인증서는 로컬에 저장되고 끌어오기 서버의 URL에 연결됩니다.
> **참고**: PowerShell 4.0에서는 등록 키가 지원되지 않습니다. 

끌어오기 서버에 인증하도록 노드를 구성하려면 이 끌어오기 서버에 등록할 모든 대상 노드의 메타 구성에 등록 키가 있어야 합니다. 아래 메타 구성에서 **RegistrationKey**는 대상 컴퓨터가 등록된 후 제거되며 '140a952b-b9d6-406b-b416-e0f759c9c0e4' 값은 끌어오기 서버의 RegistrationKeys.txt 파일에 저장된 값과 일치해야 합니다. 등록 키 값을 알면 대상 컴퓨터가 끌어오기 서버에 등록할 수 있으므로 등록 키 값을 항상 안전하게 보관하세요.

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
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL         = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey   = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> **참고**: **ReportServerWeb** 섹션을 사용하면 보고 데이터를 끌어오기 서버로 보낼 수 있습니다. 

메타 구성 파일에 **ConfigurationID** 속성이 없으면 끌어오기 서버가 V2 버전의 끌어오기 서버 프로토콜을 지원하므로 초기 등록이 필요하다는 의미입니다. 반대로 **ConfigurationID**가 있으면 V1 버전의 끌어오기 서버 프로토콜이 사용되고 등록 처리가 없습니다.

>**참고**: 밀어넣기 시나리오에서 현재 릴리스에는 끌어오기 서버에 등록하지 않는 노드에 대한 ConfigurationID 속성을 메타 구성 파일에 정의해야 하는 버그가 있습니다. 따라서 V1 끌어오기 서버 프로토콜이 강제로 사용되고 등록 실패 메시지가 표시되지 않습니다.

## 구성 및 리소스 배치
끌어오기 서버 설정이 완료되면 끌어오기 서버 구성의 **ConfigurationPath** 및 **ModulePath** 속성에 정의된 폴더에 끌어올 대상 노드에 사용할 수 있는 모듈 및 구성을 배치합니다. 이러한 파일은 특정 형식이어야만 끌어오기 서버에서 올바로 처리할 수 있습니다. 

### DSC 리소스 모듈 패키지 형식
각 리소스 모듈은 압축해야 하며 **{모듈 이름}_{모듈 버전}.zip** 패턴으로 이름을 지정해야 합니다. 예를 들어 모듈 버전이 3.1.2.0인 xWebAdminstration이라는 모듈은 'xWebAdministration_3.2.1.0.zip'으로 이름이 지정됩니다. 모듈의 각 버전은 단일 zip 파일에 포함되어야 합니다. 각 zip 파일에 리소스의 단일 버전만 있으므로 단일 디렉터리에서 여러 모듈 버전을 지원하는 WMF 5.0에서 추가된 모듈 형식은 지원되지 않습니다. 따라서 끌어오기 서버에서 사용할 DSC 리소스 모듈을 패키징하기 전에 디렉터리 구조를 약간 변경해야 합니다. WMF 5.0에서 DSC 리소스를 포함하는 모듈의 기본 형식은 '{모듈 폴더}\{모듈 버전}\DscResources\{DSC 리소스 폴더}\'입니다. 끌어오기 서버에 대해 패키징하기 전에 **{모듈 버전}** 폴더를 제거하면 되므로 폴더는 '{모듈 폴더}\DscResources\{DSC 리소스 폴더}\'가 됩니다. 이렇게 변경하고 위에서 설명한 대로 폴더를 압축하여 이러한 zip 파일을 **ModulePath** 폴더에 배치합니다.

### 구성 MOF 형식 
구성 MOF 파일은 대상 노드의 LCM이 구성에 대한 유효성을 검사할 수 있도록 체크섬 파일과 함께 사용해야 합니다. 체크섬을 만들려면 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet을 호출합니다. 이 cmdlet은 구성 MOF가 있는 폴더를 지정하는 **Path** 매개 변수를 사용합니다. cmdlet은 `ConfigurationMOFName.mof.checksum`이라는 체크섬 파일을 만들며, 여기서 `ConfigurationMOFName`은 구성 mof 파일의 이름입니다. 지정된 폴더에 구성 MOF 파일이 두 개 이상 있는 경우, 폴더에 있는 각 구성에 대해 체크섬이 만들어집니다. MOF 파일 및 연관된 체크섬 파일을 **ConfigurationPath** 폴더에 배치합니다.

>**참고**: 어떤 식으로든 구성 MOF 파일을 변경하는 경우 체크섬 파일도 다시 만들어야 합니다.

## 도구
끌어오기 서버를 더 간단히 설정하고 유효성을 검사하고 관리할 수 있도록 xPSDesiredStateConfiguration 모듈의 최신 버전에는 다음 도구가 예제로 포함되어 있습니다.
1. 끌어오기 서버에서 사용할 DSC 리소스 모듈 및 구성 파일을 패키징하는 데 도움이 되는 모듈: [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). 다음은 예제입니다.

```powershell
    # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
     $moduleList = @("xWebAdministration", "xPhp") 
     Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 
     
     # Example 2 - Package modules and mof documents from c:\LocalDepot
     Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
```

1. 끌어오기 서버가 올바로 구성되었는지 확인하는 스크립트: [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/Examples/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## 끌어오기 클라이언트 구성 
다음 항목에서는 끌어오기 클라이언트를 설정하는 것에 대해 자세히 설명합니다.

* [구성 ID를 사용하여 DSC 끌어오기 클라이언트 설정](pullClientConfigID.md)
* [구성 이름을 사용하여 DSC 끌어오기 클라이언트 설정](pullClientConfigNames.md)
* [부분 구성](partialConfigs.md)


## 참고 항목
* [Windows PowerShell 필요한 상태 구성 개요](overview.md)
* [구성 시행](enactingConfigurations.md)
* [DSC 보고서 서버 사용](reportServer.md)


<!--HONumber=Mar16_HO5-->


