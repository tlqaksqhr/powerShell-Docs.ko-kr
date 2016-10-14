---
title: "부분 구성 명명 규칙 끌어오기"
author: jaimeo
contributor: berheabrha
translationtype: Human Translation
ms.sourcegitcommit: dfa487a11528e26faf5b0e8637b75983abe0b1c8
ms.openlocfilehash: 368c26766961e760fd2de8c99057121bea076158

---

##부분 구성 명명 규칙 끌어오기
이전 릴리스에서는 부분 구성에 대한 명명 규칙에 따라 끌어오기 서버/서비스의 mof 파일 이름이 로컬 구성 관리자 설정에 지정된 부분 구성 이름과 일치하여 MOF 파일에 포함된 구성 이름과 일치해야 했습니다. 아래 스냅숏을 참조하세요.- •   노드가 수신할 수 있는 부분 구성을 정의하는 로컬 구성 설정입니다.

![샘플 메타 구성](../../images/MetaConfigPartialOne.png)

•   샘플 부분 구성 정의 

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

•   생성된 MOF 파일에 포함된 ‘ConfigurationName’

![샘플 생성된 mof 파일](../../images/PartialGeneratedMof.png)

•   끌어오기 구성 리포지토리의 FileName 

![구성 리포지토리의 FileName](../../images/PartialInConfigRepository.png)

Azure Automation 서비스 이름은 mof 파일을 ``<ConfigurationName>.<NodeName>.mof``로 생성했습니다. 따라서 아래 구성은 PartialOne.Localhost.mof로 컴파일됩니다.  
따라서 Azure Automation 서비스에서 부분 구성을 끌어올 수 없었습니다.

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

WMF 5.1에서는 끌어오기 서버/서비스의 부분 구성을 ``<ConfigurationName>.<NodeName>.mof``로 명명할 수 있습니다. 또한 컴퓨터가 끌어오기 서버/서비스에서 단일 구성을 끌어오는 경우 끌어오기 서버 구성 리포지토리의 구성 문서에 원하는 이름을 지정할 수 있습니다. 이러한 명명 유연성을 통해 온-프레미스 및 Azure Automation 끌어오기 서비스 둘 다를 사용하여 노드의 부분 구성을 관리할 수 있습니다. 예를 들어 로컬로 푸시되는 '기본' 부분 구성과 Azure Automation 서비스에서 끌어오는 다른 부분 구성을 사용할 수 있습니다.

아래 메타 구성에서는 노드를 로컬뿐 아니라 Azure 자동화 서비스에서 관리하도록 설정합니다.

```Powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30;
            RefreshMode = "PULL";            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation Service.
        PartialConfiguration PartialCOnfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   slcm -Path .\RegistrationMetaConfig -Verbose
 ```





<!--HONumber=Aug16_HO3-->


