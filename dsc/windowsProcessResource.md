# DSC WindowsProcess 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(필요한 상태 구성)의 **WindowsProcess** 리소스에서는 대상 노드에서 프로세스를 구성하는 메커니즘을 제공 합니다.

## 구문

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## 속성
|  속성  |  설명   | 
|---|---| 
| 인수| 프로세스에 그대로 전달할 인수의 문자열을 나타냅니다. 몇 개의 인수를 전달해야 하는 경우 모두 이 문자열에 넣습니다.| 
| 경로| 프로세스 실행 파일의 경로를 나타냅니다. 이 속성을 실행 파일의 이름으로 설정하는 경우 DSC에서는 __Path__ 변수를 살펴 봅니다. 정규화된 도메인 이름을 지정한다면 이 경우 DSC는 __Path__ 변수를 확인하지 않을 것이므로 프로세스가 해당 위치에 존재해야 합니다.| 
| 자격 증명| 프로세스를 시작하기 위한 자격 증명을 나타냅니다.| 
| Ensure| 프로세스가 존재하는지 여부를 나타냅니다. 프로세스가 존재하도록 하려면 이 속성을 "Present"으로 설정합니다. 그렇지 않으면, "Absent"으로 설정합니다. 기본값은 "Present"입니다.| 
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"``입니다.| 
| StandardErrorPath| 표준 오류를 쓸 디렉터리 경로를 나타냅니다. 거기에 있던 기존 파일은 덮어씁니다.| 
| StandardInputPath| 표준 입력 위치를 나타냅니다.| 
| StandardOutputPath| 표준 출력을 쓸 위치를 나타냅니다. 거기에 있던 기존 파일은 덮어씁니다.| 
| WorkingDirectory| 프로세스에 대한 현재 작업 디렉터리로 사용할 위치를 나타냅니다.| 
<!--HONumber=Feb16_HO4-->
