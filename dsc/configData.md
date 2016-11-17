---
title: "구성 및 환경 데이터 분리"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 3038854786edaa9f24b6cf39b7c0c49b3d5206e3
ms.openlocfilehash: 448cddf17a67ace9d228d1d8a9dc39109d0c91d5

---

# <a name="separating-configuration-and-environment-data"></a>구성 및 환경 데이터 분리

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

기본 제공 DSC**ConfigurationData** 매개 변수를 사용하여 구성 내에서 사용할 수 있는 데이터를 정의할 수 있습니다. 그러면 여러 노드 또는 다양한 환경에 사용할 수 있는 단일 구성을 만들 수 있습니다. 예를 들어 응용 프로그램을 개발할 경우 한 구성을 개발 및 프로덕션 환경 모두에 사용하고 구성 데이터를 사용하여 각 환경의 데이터를 지정할 수 있습니다.

간단한 예를 통해 이 과정을 알아보겠습니다. 일부 노드에 **IIS**가 있고 다른 노드에 **Hyper-V**가 있도록 하는 단일 구성을 만들려고 합니다. 

```powershell
Configuration MyDscConfiguration {
    
    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
        
    }
    Node $AllNodes.Where($_.Role -eq "VMHost").NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData = 
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

이 스크립트의 마지막 줄에서는 `$MyData`를 값 **ConfigurationData** 매개 변수로 전달하여 구성을 MOF 문서로 컴파일합니다. `$MyData`는 각각 `NodeName` 및 `Role`을 가진 서로 다른 두 노드를 지정합니다. 구성에서는 `$MyData` (특히 `$AllNodes`)로부터 받는 노드의 컬렉션을 받아 동적으로 **Node** 블록을 만들고 `Role` 속성을 기준으로 컬렉션을 필터링합니다.

이제 작동 원리를 더 자세히 살펴보겠습니다.

## <a name="the-configurationdata-parameter"></a>ConfigurationData 매개 변수

DSC 구성에서는 구성을 컴파일할 때 지정하는 **ConfigurationData**라는 이름의 매개 변수를 받습니다. 구성을 컴파일하는 방법에 대한 자세한 내용은 [DSC 구성](configurations.md)을 참조하세요.

**ConfigurationData** 매개 변수는 **AllNodes**라는 키가 하나 이상 있어야 하는 해시 테이블입니다. 다른 키도 있을 수 있습니다.

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

**AllNodes** 키의 값은 배열입니다. 이 배열의 각 요소도 **NodeName**이라는 키가 하나 이상 있어야 하는 해시 테이블입니다.

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

각 해시 테이블에도 다른 키를 추가할 수 있습니다.

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

모든 노드에 한 속성을 적용하려면 **AllNodes** 배열에 **NodeName**이 `*`인 원소를 만들 수 있습니다. 예를 들어 모든 노드에 `LogPath` 속성을 지정하기 위해 다음을 수행할 수 있습니다.

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

이 작업은 이름이 `LogPath`이고 값이 `"C:\Logs"`인 속성을 다른 블록 각각에(`VM-1`, `VM-2`, `VM-3`) 추가하는 것과 같습니다.

## <a name="defining-the-configurationdata-hashtable"></a>ConfigurationData 해시 테이블 정의

**ConfigurationData**를 방금의 예와 같이 구성과 같은 스크립트 파일에 포함된 변수로 정의할 수도 있고, 별도의 .psd1 파일에 정의할 수도 있습니다. **ConfigurationData**를 .psd1 파일에 정의하려면 구성 데이터를 나타내는 해시 테이블만 포함된 파일을 만듭니다.

예를 들어, 이름이 `MyData.psd1`이고 다음과 같은 내용이 있는 파일을 만들 수 있습니다.

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

.psd1 파일에 정의된 구성 데이터를 사용하려면 구성을 컴파일할 때 해당 파일의 경로와 이름을 **ConfigurationData** 매개 변수 값으로 전달합니다.

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>구성에 ConfigurationData 변수 사용

DSC에서는 구성 스크립트에 사용할 수 있는 세 가지 특수 변수 **$AllNodes**, **$Node**, **$ConfigurationData**를 제공합니다.

- **$AllNodes**는 **ConfigurationData**에 정의된 노드의 컬렉션 전체를 참조합니다. **AllNodes** 컬렉션은 **.Where()** 및 **.ForEach()**를 사용하여 필터링할 수 있습니다.
- **Node**는 **AllNodes** 컬렉션이 **.Where()** 또는 **.ForEach()**로 필터링된 후에 특정 항목을 참조합니다.
- **ConfigurationData**는 구성을 컴파일할 때 매개 변수로 전달된 해시 테이블 전체를 참조합니다.

## <a name="devops-example"></a>DevOps 예

단일 구성을 사용하여 웹 사이트의 개발 환경과 프로덕션 환경을 모두 설정하는 예 전체를 살펴보겠습니다. 개발 환경에서는 IIS와 SQL Server가 모두 단일 노드에 설치됩니다. 프로덕션 환경에서는 IIS와 SQL Server가 별도 노드에 설치됩니다. 구성 데이터 .psd1 파일을 사용하여 서로 다른 두 환경의 데이터를 지정하겠습니다.

### <a name="configuration-data-file"></a>구성 데이터 파일

`DevProdEnvData.psd1`이라는 파일에서 개발 및 프로덕션 환경 데이터를 다음과 같이 정의합니다.

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        }

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"

        }

    )

}

    )

}
```

### <a name="configuration-file"></a>구성 파일

이제 구성으로 가서 `DevProdEnvData.psd1`에 정의된 노드를 역할(`MSSQL`, `Dev` 또는 둘 모두, or both)에 따라 필터링하고 적절하게 구성합니다. 개발 환경은 SQL Server와 IIS가 모두 한 노드에 있고, 프로덕션 환경은 두 가지가 서로 다른 노드에 있습니다. `SiteContents` 속성으로 지정된 것처럼 사이트 내용도 서로 다릅니다.

구성 스크립트의 끝 부분에서 구성을 호출하며(MOF 문서로 컴파일) `DevProdEnvData.psd1`을 `$ConfigurationData` 매개 변수로 전달합니다.

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {            
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where($_.Role -contains "Web")
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite 
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }       


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

MyWebApp -ConfigurationData DevProdEnvData.psd1

}
```

## <a name="see-also"></a>참고 항목
- [구성 데이터의 자격 증명 옵션](configDataCredentials.md)
- [DSC 구성](configurations.md)


<!--HONumber=Nov16_HO1-->


