---
title: "DSC 구성"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 29676d0bf51adf9176753d0056efe76687a40600

---

# DSC 구성

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC 구성은 특별한 형식의 함수를 정의하는 PowerShell 스크립트입니다. 구성을 정의하려면 PowerShell 키워드 __Configuration__을 사용합니다.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

스크립트를 .ps1 파일로 저장하세요.

## 구성 구문

구성 스크립트는 다음의 부분들로 구성됩니다.

- **Configuration** 블록. 가장 바깥쪽 스크립트 블록입니다. **Configuration** 키워드를 사용하고 이름을 제공하여 정의합니다. 이 경우 구성의 이름은 "MyDscConfiguration"입니다.
- 하나 이상의 **Node** 블록. 이 블록에서는 구성 중인 노드(컴퓨터 또는 VM)를 정의합니다. 위의 구성에는 "TEST-PC1"이라는 컴퓨터를 대상으로 하는 하나의 **Node** 블록이 있습니다.
- 하나 이상의 리소스 블록. 이 블록은 구성으로 구성 중인 리소스에 대한 속성을 설정하는 위치입니다. 이 경우 두 개의 리소스 블록이 있으며, 각각 "WindowsFeature" 리소스를 호출합니다.

**Configuration** 블록 내에서는 PoweShell 함수에서 일반적으로 수행할 수도 있는 모든 작업을 수행할 수 있습니다. 예를 들어 앞의 예에서는, 구성에서 대상 컴퓨터의 이름을 하드 코드하지 않으려는 경우 노드 이름에 대한 매개 변수를 추가할 수도 있습니다.

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

이 예제에서는 [구성을 컴파일](# Compiling the configuration)할 때 $ComputerName 매개 변수로 전달하여 노드의 이름을 지정합니다. 이름의 기본값은 "localhost"입니다.

## 구성 컴파일
구성을 시행할 수 있으려면 먼저 MOF 문서로 컴파일해야 합니다. PowerShell 함수에 대해 하는 것처럼 구성을 호출하여 이렇게 수행합니다.
>__참고:__ 구성을 호출하려면 (다른 PowerShell 함수에서 처럼) 함수가 전역 범위에 있어야 합니다. 스크립트를 "도트 소싱"하거나, F5 키를 사용하거나 ISE에서 __스크립트 실행__ 단추를 클릭하여 구성 스크립트를 실행하면 이렇게 할 수 있습니다. 스크립트를 도트 소싱하려면 명령을 `. .\myConfig.ps1`을 실행합니다. 여기서 `myConfig.ps1`은 구성을 포함하는 스크립트 파일의 이름입니다.

구성을 호출하면 다음 항목들이 생성됩니다.

- 구성과 같은 이름으로 현재 디렉터리에 폴더가 생성됩니다.
- 새 디렉터리에 _NodeName_.mof라는 파일이 생성됩니다. _NodeName_은 구성의 대상 노드 이름입니다. 노드가 두 개 이상 있을 경우에는 각 노드에 대해 MOF 파일이 생성됩니다.

>__참고__: MOF 파일은 대상 노드에 대한 모든 구성 정보를 포함합니다. 이 때문에 안전하게 유지해야 합니다. 자세한 내용은 [MOF 파일 보안](secureMOF.md)을 참조하세요.

위의 첫 번째 구성을 컴파일하면 다음 폴더 구조가 생성됩니다.

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

구성에서 매개 변수를 사용하는 경우, 두 번째 예제에서처럼 컴파일 시 제공해야 합니다. 다음과 같은 모습이 됩니다.

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration -ComputerName 'MyTestNode'
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## DependsOn 사용
유용한 DSC 키워드는 __DependsOn__입니다. 일반적으로(늘 반드시 그렇지는 않지만), DSC는 구성 내에서 나타나는 순서로 리소스를 적용합니다. 그러나 __DependsOn__은 다른 리소스에 종속되는 리소스를 지정하며, LCM은 이러한 리소스가 리소스 인스턴스가 정의된 순서에 관계없이 올바른 순서로 적용되도록 합니다. 예를 들어, 구성은 __User__ 리소스의 인스턴스가 __Group__ 인스턴스의 존재 여부에 따라 달라진다고 지정할 수 있습니다.

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}
```

## 구성에서 새 리소스 사용
앞의 예제를 실행했다면 명시적으로 가져오지 않고 리소스를 사용하고 있다는 경고가 표시된 것을 보았을 수 있습니다.
오늘, DSC는 PSDesiredStateConfiguration 모듈의 일부로서 12개의 리소스와 함께 제공됩니다. 외부 모듈의 다른 리소스는 LCM에서 인식할 수 있도록 `$env:PSModulePath`에 배치해야 합니다. 새 cmdlet인 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)는 시스템에 설치되어 있고 LCM에서 사용할 수 있는 리소스를 파악하는 데 사용할 수 있습니다. 이러한 모듈은 `$env:PSModulePath`에 배치되어 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)에 의해 제대로 인식된 후에도 여전히 구성 내에서 로드되어야 합니다. __Import-DscResource__는 __구성__ 블록 내에서만 인식될 수 있는 동적 키워드입니다(즉, cmdlet이 아님). __Import-DscResource__에서는 두 개의 매개 변수를 지원합니다.
* __ModuleName__은 __Import-DscResource__를 사용하는 권장 방법입니다. 가져올 리소스를 포함하는 모듈의 이름을 받습니다(모듈 이름으로 이루어진 문자열 배열도 받음). 
* __Name__은 가져올 리소스의 이름입니다. 이 이름은 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)에 의해 "Name"으로 반환한 친숙한 이름이 아니라, 리소스 스키마를 정의할 때 사용된 클래스 이름입니다([Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)에 의해 __ResourceType__으로 반환됨). 

## 참고 항목
* [Windows PowerShell 필요한 상태 구성 개요](overview.md)
* [DSC 리소스](resources.md)
* [로컬 구성 관리자 구성](metaConfig.md)




<!--HONumber=Jun16_HO4-->


