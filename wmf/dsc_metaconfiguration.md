# 새로운 메타 구성 특성으로 DSC LCM 구성

`DscLocalConfigurationManager` 특성은 DSC 로컬 구성 관리자를 구성하는 데 사용되는 구성 블록을 메타 구성으로 지정합니다. 이 특성은 DSC 로컬 구성 관리자를 구성하는 항목만 포함하도록 구성을 제한합니다. 처리하는 동안 이 구성은 `Set-DscLocalConfigurationManager` cmdlet을 사용하여 `*.meta.mof` 파일을 생성합니다. 그런 다음 이 파일은 적절한 대상 노드로 전송됩니다.

```powershell
[DscLocalConfigurationManager()]
configuration meta
{
    Node localhost
    {
        Settings
        {
            ConfigurationMode = "ApplyAndAutocorrect"
            ConfigurationID = "5603f952-d6c6-4971-88c4-948636bf5c3f"
            RefreshMode = "Pull"
        }
        ConfigurationRepositoryWeb PullServer
        {
            ServerURL = "https://corp.contoso.com/PSDSCPullServer/PSDSCPullServer.svc"
        }
    }
}
```

위 예제에서는 LCM에서 끌어오기 모드를 사용하도록 새로 고침 모드를 구성하고, 구성 모드를 ApplyAndAutocorrect로 변경하며, 끌어오기 서버의 유형과 위치를 정의합니다.

이 새로운 구성 특성은 PowerShell 4.0 LocalConfigurationManager 리소스의 기능을 대체하고 확장합니다. 이 LocalConfigurationManager는 이전 버전과의 호환성을 위해 이 특성이 없어도 구성에서 지원됩니다.

메타 리소스:

| **리소스 이름**            | **설명**                                |
|------------------------------|------------------------------------------------|
| LocalConfigurationManager    | DSC 엔진 실행에 대한 다양 한 설정      |
| PartialConfiguration         | 부분 구성 설정                 |
| ConfigurationRepositoryWeb   | 웹 기반 구성 리포지토리             |
| ConfigurationRepositoryShare | 파일 공유 기반 구성 리포지토리      |
| ResourceRepositoryWeb        | 웹 기반 리소스 리포지토리                  |
| ResourceRepositoryShare      | 파일 기반 리소스 리포지토리                 |
| ReportServerWeb              | 끌어오기 시나리오에 대한 웹 기반 보고 끝점 |
<!--HONumber=Mar16_HO2-->
