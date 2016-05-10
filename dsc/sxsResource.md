# 여러 버전의 리소스 사용

> 적용 대상: Windows PowerShell 5.0

PowerShell 5.0에서 DSC 리소스는 여러 버전이 있을 수 있으며, 이러한 버전들을 컴퓨터에 병렬로 설치할 수 있습니다. 이는 동일한 모듈 폴더에 포함된 여러 버전의
리소스 모듈에 의해 구현됩니다.

## 여러 리소스 버전을 병렬로 설치

[Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet의 **MinimumVersion**, **MaximumVersion** 및 **RequiredVersion**를 사용하여 설치할
모듈 버전을 지정할 수 있습니다. 버전을 지정하지 않고 **Install-Module**을 호출하면 가장 최근 버전이 설치됩니다.

예를 들어 **xFailOverCluster** 모듈의 여러 버전이 있고, 각 버전에는 **xCluster** 리소스가 포함되어 있습니다. 버전 번호를 지정하지 않고 **Install-Module**을 호출한
결과는 다음과 같습니다.

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

**Install-Module**을 다시 호출하고 **RequiredVersion** 1.1.0.0을 지정하면 그 결과는 다음과 같습니다.

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## 구성에서 리소스 버전 지정

컴퓨터에 여러 리소스가 설치되어 있으면, 해당 리소스의 버전을 지정한 후 구성에서 사용해야 합니다. 이 작업은 **Import-DscResource** 키워드의 
 **ModuleVersion** 매개 변수를 지정해 수행할 수 있습니다. 하나가 넘는 버전이 설치된 리소스의 리소스 모듈 버전을 지정하지 않으면 구성에서
오류가 발생 합니다.

다음 구성에서는 호출할 리소스의 버전을 지정하는 방법을 보여 줍니다.

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

>참고: Import-DscResource의 ModuleVersion 매개 변수는 PowerShell 4.0에서 사용할 수 없습니다. PowerShell 4.0에서는 모듈 사양 개체를 Import-DscResource의 ModuleName 매개 변수로 
>전달하여 모듈 버전을 지정할 수 있습니다. 모듈 사양 개체는 모듈 이름 및 RequiredVersion 키가 포함된 해시 테이블입니다. 예:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

이 작업은 PowerShell 5.0에서도 동작하지만, 이 경우 **ModuleVersion** 매개 변수를 사용하는 것이 좋습니다.

## 참고 항목
* [DSC 구성](configurations.md)
* [DSC 리소스](resources.md)

<!--HONumber=Apr16_HO4-->


