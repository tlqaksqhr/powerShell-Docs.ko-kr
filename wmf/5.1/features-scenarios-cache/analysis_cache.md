# 모듈 분석 캐시 #

버전 5.1부터 PowerShell에서는 내보내는 명령과 같은 모듈에 대한 데이터를 캐시하는 데 사용되는 파일을 다음과 같이 제어할 수 있습니다.

기본적으로 이 캐시 파일은 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 파일에 저장됩니다.
일반적으로 이 캐시는 시작 시 명령을 검색할 때 읽으며 모듈을 가져오고 잠시 후에 백그라운드 스레드에서 기록됩니다.

캐시의 기본 위치를 변경하려면 PowerShell을 시작하기 전에 PSModuleAnalysisCachePath 환경 변수를 설정합니다. 이 환경 변수의 변경 내용은 자식 프로세스에만 적용됩니다.
PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다.
파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정할 수 있습니다.

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

이렇게 하면 잘못된 장치에 대한 경로가 설정됩니다. PowerShell에서 경로에 쓸 수 없는 경우 오류가 발생하지 않지만 추적 프로그램을 오류 보고가 표시될 수 있습니다.

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

캐시를 쓸 때 PowerShell에서는 캐시가 불필요하게 커지지 않도록 더 이상 없는 모듈을 확인합니다.
때론 이러한 확인이 필요하지 않을 수도 있으며, 이 경우 다음을 설정하여 확인을 끌 수 있습니다.

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

이 환경 변수를 설정하면 현재 프로세스에 즉시 적용됩니다.

<!--HONumber=Aug16_HO3-->


