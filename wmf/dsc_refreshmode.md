# RefreshMode 속성에 대한 추가 값

이번 릴리스에서는 새 `RefreshMode` 값 **Disabled**가 도입되었습니다. 이 모드를 설정하면 LCM에서 문서 관리를 수행하지 않습니다. 이 모드는 `Invoke-DscResource` cmdlet에서 DSC 리소스를 활용하면서 DSC 대신 타사 구성 관리 도구를 사용하는 경우나 어떤 이유로든 DSC 처리를 중지해야 하는 경우에 사용할 수 있습니다.

```powershell
Configuration LCMSettings
{
    Node localhost
    {
        LocalConfigurationManager
        {
           RefreshMode = 'Disabled'
        }
    }
}

LCMSettings -OutputPath .\LCMSettings
Set-DscLocalConfigurationManager -Path .\LCMSettings -Verbose -ComputerName localhost
```
<!--HONumber=Mar16_HO2-->
