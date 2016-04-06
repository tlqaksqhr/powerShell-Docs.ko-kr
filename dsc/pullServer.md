# DSC 웹 끌어오기 서버 설정

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC 웹 끌어오기 서버는 해당 노드에서 요청하면 OData 인터페이스를 사용하여 DSC 구성 파일을 대상 노드에 사용할 수 있도록 하는 IIS의 웹 서비스입니다.

끌어오기 서버 사용을 위한 요구 사항:

* 다음 항목을 실행 중인 서버:
  - WMF/PowerShell 4.0 이상
  - IIS 서버 역할
  - DSC 서비스
* 인증서를 생성하여 대상 노드에서 LCM(로컬 구성 관리자)에 전달된 자격 증명을 보호할 방법이 있으면 가장 좋습니다.

서버 관리자에서 역할 및 기능 추가 마법사를 사용하거나 PowerShell을 사용하여 IIS 서버 역할 및 DSC 서비스를 추가할 수 있습니다. 이 항목에 포함된 샘플 스크립트는 이 두 단계를 모두 처리하게 됩니다.

## xWebService 리소스 사용
웹 끌어오기 서버를 설정하는 가장 쉬운 방법은 xPSDesiredStateConfiguration 모듈에 포함된 xWebService 리소스를 사용하는 것입니다. 다음 단계에서는 웹 서비스를 설정하는 구성에서 리소스를 사용하는 방법에 대해 설명합니다.

1. [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet을 호출하여 **xPSDesiredStateConfiguration** 모듈을 설치하세요. **참고**: **Install-Module**은 PowerShell 5.0에 포함된 **PowerShellGet** 모듈에 포함되어 있습니다. [PackageManagement PowerShell 모듈 미리 보기](https://www.microsoft.com/en-us/download/details.aspx?id=49186)에서 PowerShell 3.0 및 4.0용 **PowerShellGet** 모듈을 다운로드할 수 있습니다. 
1. `CERT:\LocalMachine\MY\` 스토어에서 주체 `"CN=PSDSCPullServerCert"`를 사용하여 자체 서명된 인증서를 만듭니다. 이 작업은 `New-SelfSignedCertificate  -CertStoreLocation 'CERT:\LocalMachine\MY' -DnsName "PSDSCPullServerCert"` 명령을 사용하여 수행할 수 있습니다.
1. PowerShell ISE에서 다음의 구성 스크립트(**xPSDesiredStateConfiguration** 모듈의 예제 폴더에 Sample_xDscWebService.ps1로 포함됨)를 시작합니다(F5). 이 스크립트는 끌어오기 서버와 준수 서버를 설정합니다.
  
```powershell
configuration Sample_xDscWebService 
6 { 
7     param  
8     ( 
9         [string[]]$NodeName = 'localhost', 
10 
 
11         [ValidateNotNullOrEmpty()] 
12         [string] $certificateThumbPrint 
13     ) 
14 
 
15     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 
16 
 
17     Node $NodeName 
18     { 
19         WindowsFeature DSCServiceFeature 
20         { 
21             Ensure = "Present" 
22             Name   = "DSC-Service"             
23         } 
24 
 
25         xDscWebService PSDSCPullServer 
26         { 
27             Ensure                  = "Present" 
28             EndpointName            = "PSDSCPullServer" 
29             Port                    = 8080 
30             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
31             CertificateThumbPrint   = $certificateThumbPrint          
32             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
33             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
34             State                   = "Started" 
35             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
36         } 
```

1. 구성을 실행하여, **certificateThumbPrint** 매개 변수로 만든 자체 서명된 인증서의 지문을 전달합니다.

```powershell
PS:\>$myCert = Get-ChildItem CERT:\LocalMachine\My | Where-Object {$_.Subject -eq 'CN=PSDSCPullServerCert'}
PS:\>Sample_xDSCService -certificateThumbprint $myCert.Thumbprint 
```

## 등록 키
구성 ID 대신 구성 이름을 사용할 수 있도록 클라이언트 노드가 서버에 등록할 수 있도록 하려면 등록 키(서버와 클라이언트 노드 모두에게 GUID로 알려짐)를 `RegistrationKeys.txt`라는 파일에 배치해야 합니다. 기본적으로 이 예제에서 만든 끌어오기 서버는 해당 파일이 `C:\Program Files\WindowsPowerShell\DscService`에 있을 것으로 예상합니다. 등록 키로 구성된 한 줄만 있는 텍스트 파일을 만들어 해당 폴더에 저장하세요.
> **참고**: PowerShell 4.0에서는 등록 키가 지원되지 않습니다. 

## 구성 및 리소스 배치
끌어오기 서버 설정이 완료되면 `$env:PROGRAMFILES\WindowsPowerShell` 아래에 "DscService"라는 새 폴더가 생깁니다. 해당 폴더에는 "Modules" 및 "Configuration"이라는 두 개의 폴더가 있습니다. 해당 노드가 이 서버에서 끌어올 구성에 필요한 모든 리소스를 "Modules" 폴더에 놓습니다. 노드가 끌어올 모든 구성에 대한 구성 MOF 파일을 "Configuration" 폴더에 놓습니다. MOF 파일의 이름은 끌어오기 클라이언트의 종류에 따라 달라집니다. 다음 항목에서는 끌어오기 클라이언트를 설정하는 것에 대해 자세히 설명합니다.

* [구성 ID를 사용하여 DSC 끌어오기 클라이언트 설정](pullClientConfigID.md)
* [구성 이름을 사용하여 DSC 끌어오기 클라이언트 설정](pullClientConfigNames.md)
* [부분 구성](partialConfigs.md)

## MOF 체크섬 만들기
구성 MOF 파일은 대상 노드의 LCM이 구성에 대한 유효성을 검사할 수 있도록 체크섬 파일과 함께 사용해야 합니다. 체크섬을 만들려면 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet을 호출합니다. 이 cmdlet은 구성 MOF가 있는 폴더를 지정하는 **Path** 매개 변수를 사용합니다. cmdlet은 `ConfigurationMOFName.mof.checksum`이라는 체크섬 파일을 만들며, 여기서 `ConfigurationMOFName`은 구성 mof 파일의 이름입니다. 지정된 폴더에 구성 MOF 파일이 두 개 이상 있는 경우, 폴더에 있는 각 구성에 대해 체크섬이 만들어집니다.

체크섬 파일은 구성 MOF 파일과 동일한 디렉터리에 있어야 하며(기본적으로 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`), 동일한 이름에 확장명으로 `.checksum`을 사용해야 합니다.

>**참고**: 어떤 식으로든 구성 MOF 파일을 변경하는 경우 체크섬 파일도 다시 만들어야 합니다.

## 참고 항목
* [Windows PowerShell 필요한 상태 구성 개요](overview.md)
* [구성 시행](enactingConfigurations.md)
* [DSC 끌어오기 서버에서 노드 정보를 검색하는 방법](retrieveNodeInfo.md)


<!--HONumber=Mar16_HO1-->


