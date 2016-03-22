# 구성 및 환경 데이터 분리

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)에서는 구성 데이터를 구성의 논리에서 분리할 수 있습니다. 또한 구조적 구성(예를 들어 구성에 따라 IIS를 설치해야 할 수 있음)을 환경 구성에서 별도로 고려하는 것이 좋습니다(즉, 상황이 테스트 환경인지 프로덕션 환경인지 여부에 따라 노드 이름은 달라지겠지만 노드 이름에 적용되는 구성은 동일함). 이 방법의 이점은 다음과 같습니다.

* 다양한 리소스, 노드 및 구성에 구성 데이터를 다시 사용할 수 있습니다.
* 구성 논리는 하드 코드된 데이터를 포함하지 않을 경우 재사용률이 더 높습니다. 이것은 함수에 대한 좋은 스크립팅 지침과 비슷합니다.
* 일부 데이터를 변경해야 할 경우 한 곳에서 변경 작업을 수행할 수 있으므로 시간을 단축하고 오류를 줄일 수 있습니다.

## 기본 개념 및 예제

구성의 환경 부분을 지정하기 위해, DSC에서는 해시 테이블인 **ConfigurationData** 매개 변수 사용합니다(또는 해시 테이블을 포함하는 .psd1 파일을 사용할 수 있음). 이 해시 테이블에는 구조화된 값이 있는 하나 이상의 키 **AllNodes**가 있어야 합니다. 예:

```powershell
$MyData = 
@{
    AllNodes = @();
    NonNodeData = ""   
}
```

AllNodes 키에 주목하세요. 이 키의 값은 배열입니다. 이 배열의 각 요소는 키로서 NodeName을 필요로 하는 해시 테이블이기도 합니다.

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

AllNodes의 각 해시 테이블 항목은 구성에서 노드에 대한 구성 데이터에 해당합니다. 필수 NodeName 키 외에 다음과 같이 다른 키를 해시 테이블에 추가할 수도 있습니다.

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

DSC에서는 구성 스크립트에서 사용할 특별한 세 개의 변수를 제공합니다.

* **$AllNodes**: 모든 노드를 참조합니다. **.Where()** 및 **.ForEach()**를 사용할 수 있으므로 노드 이름을 하드 코드하여 작동시킬 특정 노드를 선택하는 대신 다음과 같은 것을 작성하여 위의 예에 있는 VM-1 및 VM-3을 선택할 수도 있습니다.

```powershell
configuration MyConfiguration
{
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
    }
}
```

* **$Node**: 노드 집합이 필터링되면 $Node를 사용하여 특정 항목을 참조할 수 있습니다. 예:

```powershell
configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }
    }
}
```

속성을 모든 노드에 적용하려면 NodeName = "*"를 설정하면 됩니다. 예를 들어 모든 노드에 LogPath 속성을 지정하기 위해 다음을 수행할 수 있습니다.

```
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );
}
```

* **$ConfigurationData**: 구성 내부에 이 변수를 사용하여 매개 변수로서 전달된 구성 데이터 해시 테이블에 액세스할 수 있습니다. 예:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },
 

        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );

    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 

configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

[xWebAdministration 모듈](https://powershellgallery.com/packages/xWebAdministration)에 포함된 전체 예제를 찾을 수 있습니다.
<!--HONumber=Feb16_HO4-->
