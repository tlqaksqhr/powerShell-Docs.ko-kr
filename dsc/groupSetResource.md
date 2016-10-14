---
title: "DSC GroupSet 리소스"
ms.date: 2016-05-16
keywords: "powershell, DSC, 기본 제공, 리소스"
description: "대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다."
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: bf36abde6a3bfff4c2e49868465e089cc886d031
ms.openlocfilehash: 45fe96c43a834566d398820e3d94e3be923bb385

---

# DSC GroupSet 리소스

> 적용 대상: Windows Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)의 **GroupSet** 리소스에서는 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다. 이 리소스는 `GroupName` 매개 변수에 지정된 각 그룹에 대해 [그룹 리소스](groupResource.md)를 호출하는 [복합 리소스](authoringResourceComposite.md)입니다.

두 개 이상의 그룹에서 동일한 구성원 목록을 추가 및/또는 제거하거나 두 개 이상의 그룹을 제거하거나 구성원 목록이 동일한 두 개 이상의 그룹을 추가하려는 경우 이 리소스를 사용합니다.

##구문##
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## 속성

|  속성  |  설명   | 
|---|---| 
| GroupName| 상태를 확인하려는 그룹의 이름입니다.| 
| MembersToExclude| 그룹의 기존 구성원 자격에서 구성원을 제거하려면 이 속성을 사용합니다. 이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다. 구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요. 사용할 경우 오류가 발생합니다.| 
| 자격 증명| 원격 리소스에 액세스하는 데 필요한 자격 증명입니다. **참고**: 이 계정에 로컬이 아닌 모든 계정을 그룹에 추가할 수 있는 Active Directory 권한이 있어야 합니다. 그렇지 않으면 오류가 발생합니다.
| Ensure| 그룹이 있는지 여부를 나타냅니다. 그룹이 존재하지 않도록 하려면 이 속성을 "Absent"로 설정합니다. 그룹이 존재하도록 하려면 이 속성을 "Present"(기본값)로 설정합니다.| 
| 구성원| 현재 그룹 구성원 자격을 지정된 구성원으로 바꾸려면 이 속성을 사용합니다. 이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다. 구성에서 이 속성을 설정하는 경우 **MembersToExclude** 또는 **MembersToInclude** 속성을 사용하지 마세요. 사용할 경우 오류가 발생합니다.| 
| MembersToInclude| 그룹의 기존 구성원 자격에 구성원을 추가하려면 이 속성을 사용합니다. 이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다. 구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요. 사용할 경우 오류가 발생합니다.| 
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하는 구문은 `DependsOn = "[ResourceType]ResourceName"``입니다.| 

## 예제 1

다음 예제에서는 "myGroup" 및 "myOtherGroup"이라는 두 그룹이 있는지 확인하는 방법을 보여 줍니다. 

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}


GroupSetTest -ConfigurationData $cd
```

>**참고:** 이 예에서는 편의상 일반 텍스트 자격 증명을 사용합니다. 구성 MOF 파일에서 자격 증명을 암호화하는 방법에 대한 자세한 내용은 [MOF 파일 보안](secureMOF.md)을 참조하세요.





<!--HONumber=Aug16_HO3-->


