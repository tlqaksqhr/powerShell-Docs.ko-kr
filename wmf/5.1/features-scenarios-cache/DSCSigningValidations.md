---
title: "DSC 모듈 및 구성 서명 유효성 검사"
author: jaimeo
contributor: berheabra
translationtype: Human Translation
ms.sourcegitcommit: 5c97ca6e93d31aaffc7e2207facc7658ee36dfb4
ms.openlocfilehash: 817fadb79716e41ce8cc8f4245dedc66347ac413

---

##DSC 모듈 및 구성 서명 유효성 검사
DSC에서는 구성 문서 및 모듈이 끌어오기 서버 또는 끌어오기 서비스(Azure Automation 끌어오기 서비스의 경우)에서 관리되는 컴퓨터로 배포됩니다. 끌어오기 서버/서비스가 손상되는 경우 공격자가 끌어오기 서버의 구성 및 모듈을 수정하고 모든 관리되는 컴퓨터에 배포하여 고객의 더 많은 컴퓨터를 손상시킬 수 있습니다. 

 이 위협은 WMF 5.1에서 해결되었습니다. DSC는 모듈 및 구성(.MOF) 파일에 있는 디지털 서명의 유효성 검사를 지원합니다. 이 기능은 노드에서 신뢰할 수 있는 서명자가 서명하지 않았거나 신뢰할 수 있는 서명자가 서명한 후 변조된 구성 또는 모듈 파일을 실행하지 못하게 합니다. 



###구성 및 모듈에 서명하는 방법 
***
1. 구성 파일(.MOFS): 기존 PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx)가 MOF 파일 서명을 지원하도록 확장되었습니다.  
2. 모듈: 다음 단계에 따라 해당 모듈 카탈로그에 서명하여 모듈 서명을 수행합니다. 
    * 카탈로그 파일을 만듭니다. 카탈로그 파일에는 암호화 해시 또는 지문의 컬렉션이 포함됩니다. 각 지문은 모듈에 포함된 파일에 해당합니다.  사용자가 모듈의 카탈로그 파일을 만들 수 있는 새로운 [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) cmdlet이 추가되었습니다. 카탈로그 파일을 만들려면 카탈로그 cmdlet [상대 링크](catalog-cmdlets.md)를 참조하세요. 
    * 카탈로그 파일에 서명합니다. [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx)를 사용하여 카탈로그 파일에 서명합니다.
    * 카탈로그 파일을 모듈 폴더 내에 배치합니다.
규칙에 따라 모듈 카탈로그 파일은 모듈과 이름이 같은 모듈 폴더에 배치해야 합니다.

###서명 유효성 검사를 사용하도록 설정하는 LocalConfigurationManager 설정

####끌어오기
노드의 LocalConfigurationManager는 현재 설정에 따라 모듈 및 구성의 서명 유효성 검사를 수행합니다. 기본적으로 서명 유효성 검사를 사용하지 않도록 설정되어 있습니다. 서명 유효성 검사를 사용하도록 설정하려면 아래와 같이 노드의 메타 구성 정의에 'SignatureValidation' 블록을 추가합니다.

```PowerShell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'        
    } 
    
    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default,LCM will use default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM will use this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType =  'Configuration','Module'         # Those are list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

노드에서 위의 메타 구성을 설정하면 다운로드된 구성 및 모듈에서 서명 유효성을 검사할 수 있습니다. Localconfigurationmanager는 다음 단계를 따라 디지털 서명을 확인합니다.
* 구성 파일(.MOF)의 서명이 유효한지 확인합니다. 5.1에서 MOF 서명 유효성 검사를 지원하도록 확장된 powershell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx)를 사용합니다.
* 서명자에게 권한을 부여한 인증 기관을 신뢰할 수 있는지 확인합니다.
* 구성의 모듈/리소스 종속성을 임시 위치로 다운로드합니다.
* 모듈 내에 포함된 카탈로그의 서명을 확인합니다.
    * <moduleName>.cat 파일을 찾고 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet을 사용하여 해당 서명을 확인합니다.
    * 서명자를 인증한 인증 기관을 신뢰할 수 있는지 확인합니다.
    * 새 [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) cmdlet을 사용하여 모듈의 콘텐츠가 변조되지 않았는지 확인합니다.
* 모듈을 $env:ProgramFiles\WindowsPowerShell\Modules\에 설치
* 구성을 처리합니다.

참고: - 모듈 카탈로그 및 구성의 서명 유효성 검사는 시스템에 구성을 처음으로 적용할 때나 모듈을 다운로드하여 설치할 때만 수행합니다. 일관성 실행에서는 Current.mof 또는 해당 모듈 종속성의 서명 유효성을 검사하지 않습니다.
끌어오기 서버에서 끌어온 구성에 서명이 되어 있지 않은 등 어느 단계에서든 유효성 검사가 실패하면 구성 처리가 종료되고 아래와 같은 오류가 표시되며 모든 임시 파일이 삭제됩니다.

![샘플 오류 출력 구성](../../images/PullUnsignedConfigFail.PNG)

마찬가지로 카탈로그에 서명이 되어 있지 않은 모듈을 끌어오면 다음 오류가 발생합니다.

![샘플 오류 출력 모듈](../../images/PullUnisgnedCatalog.PNG)

####푸시
푸시를 통해 전달된 구성은 노드로 전달되기 전에 해당 소스에서 변조될 수 있습니다. 로컬 구성 관리자는 푸시되거나 게시된 구성에 대해 비슷한 서명 유효성 검사 단계를 수행합니다.
다음은 푸시에 대한 서명 유효성 검사의 완전한 예제입니다.

* 노드에서 서명 유효성 검사를 사용하도록 설정합니다.

```Powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'        
    } 
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'   
        SignedItemType =  'Configuration','Module'             
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
``` 
* 샘플 구성 파일을 만듭니다.

```Powershell
# Sample configuration
Configuration Test{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* 서명되지 않은 구성 파일을 노드로 푸시해 봅니다. 

```Powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.PNG)

* 코드 서명 인증서를 사용하여 구성 파일에 서명합니다.

![SignMofFile](../../images/SignMofFile.PNG)

* 서명된 mof 파일을 푸시해 봅니다.

![SignMofFile](../../images/PushSignedMof.PNG)




<!--HONumber=Aug16_HO3-->


