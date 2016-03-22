# DSC 그룹 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)의 그룹 리소스에서는 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.

##구문##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## 속성

|  속성  |  설명   | 
|---|---| 
| GroupName| 특정 상태를 확인하려는 그룹의 이름을 나타냅니다.| 
| 자격 증명| 원격 리소스에 액세스하는 데 필요한 자격 증명을 나타냅니다. **참고**: 이 계정에 로컬이 아닌 모든 계정을 그룹에 추가할 수 있는 Active Directory 권한이 있어야 합니다. 그렇지 않으면 오류가 발생합니다.
| 설명| 그룹에 대한 설명을 나타냅니다.| 
| Ensure| 그룹이 존재하는지 여부를 나타냅니다. 그룹이 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다. 그룹이 존재하도록 하려면 이 속성을 "Present"(기본값)으로 설정합니다.| 
| 구성원| 이 구성원들이 그룹을 형성하도록 할 것임을 나타냅니다.| 
| MembersToExclude| 이 그룹의 구성원이 되지 않도록 할 사용자를 나타냅니다.| 
| MembersToInclude| 이 그룹의 구성원이 되도록 할 사용자를 나타냅니다.| 
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하는 구문은 `DependsOn = "[ResourceType]ResourceName"``입니다.| 

## 예제

다음 예제에서는 TestGroup이라는 그룹이 없음을 확인하는 방법을 보여 줍니다. 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
<!--HONumber=Feb16_HO4-->
