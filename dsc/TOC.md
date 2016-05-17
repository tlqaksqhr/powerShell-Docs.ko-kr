# [개요](overview.md)

# [구성](configurations.md)
## [구성 시행](enactingConfigurations.md)
## [여러 버전의 리소스 사용](sxsResource.md)
## [사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md)
## [노드 간 종속성 지정](crossNodeDependencies.md)
## [구성 데이터](configData.md)
### [구성 데이터의 자격 증명 옵션](configDataCredentials.md)
## [구성 MOF 파일 보안](secureMOF.md)
## [부분 구성](partialConfigs.md)
## [DSC 구성에 대한 도움말 작성](configHelp.md)

# [리소스](resources.md)
## [기본 제공 리소스](builtInResource.md)
### [보관 리소스](archiveResource.md)
### [환경 리소스](environmentResource.md)
### [파일 리소스](fileResource.md)
### [그룹 리소스](groupResource.md)
### [로그 리소스](logResource.md)
### [패키지 리소스](packageResource.md)
### [레지스트리 리소스](registryResource.md)
### [스크립트 리소스](scriptResource.md)
### [서비스 리소스](serviceResource.md)
### [사용자 리소스](userResource.md)
### [WindowsFeature 리소스](windowsfeatureResource.md)
### [WindowsProcess 리소스](windowsProcessResource.md)
## [사용자 지정 리소스 작성](authoringResource.md) 
### [MOF 기반 사용자 지정 리소스](authoringResourceMOF.md)
#### [C의 MOF 기반 리소스#](authoringResourceMofCS.md)
### [클래스 기반 사용자 지정 리소스](authoringResourceClass.md)
### [복합 리소스](authoringResourceComposite.md)
### [DSC 리소스 디버그](debugResource.md)
### [DSC 리소스 메서드를 직접 호출](directCallResource.md)
### [단일 인스턴스 DSC 리소스 작성(모범 사례)](singleInstance.md)
### [리소스 작성 검사 목록](resourceAuthoringChecklist.md)

# [LCM(로컬 구성 관리자) 구성](metaConfig.md)
## [PowerShell 4.0에서 LCM 구성](metaConfig4.md)

# DSC 끌어오기 모델
## [웹 끌어오기 서버 설정](pullServer.md)
## [DSC SMB 끌어오기 서버 설정](pullServerSMB.md)
## [끌어오기 클라이언트 설정](pullClient.md)
### [구성 이름을 사용하여 끌어오기 클라이언트 설정](pullClientConfigNames.md)
### [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)
## [DSC 보고서 서버 사용](reportServer.md)
## [끌어오기 서버 모범 사례](secureServer.md)

# [DSC 문제 해결](troubleshooting.md)

# [DSC on Nano Server 사용](nanoDsc.md)

# Linux의 DSC
## [Linux용 DSC 시작](lnxGettingStarted.md)
## [Linux용 기본 제공 리소스](lnxBuiltInResources.md)
### [nxArchive 리소스](lnxArchiveResource.md)
### [nxEnvironment 리소스](lnxEnvironmentResource.md)
### [nxFile 리소스](lnxFileResource.md)
### [nxFileLine 리소스](lnxFileLineResource.md)
### [nxGroup 리소스](lnxGroupResource.md)
### [nxPackage 리소스](lnxPackageResource.md)
### [nxService 리소스](lnxServiceResource.md)
### [nxSshAuthorizedKeys 리소스](lnxSshAuthorizedKeysResource.md)
### [nxUser 리소스](lnxUserResource.md)

# DSC MOF 참조
## [MSFT_DSCLocalConfigurationManager 클래스](msft-dsclocalconfigurationmanager.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 ApplyConfiguration 메서드](msft-dsclocalconfigurationmanager-applyconfiguration.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 DisableDebugConfiguration 메서드](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 EnableDebugConfiguration 메서드](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 GetConfiguration 메서드](msft-dsclocalconfigurationmanager-getconfiguration.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationResultOutput 메서드](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 GetConfigurationStatus 메서드](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 GetMetaConfiguration 메서드](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 PerformRequiredConfigurationChecks 메서드](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 RemoveConfiguration 메서드](msft-dsclocalconfigurationmanager-removeconfiguration.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 ResourceGet 메서드](msft-dsclocalconfigurationmanager-resourceget.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 ResourceSet 메서드](msft-dsclocalconfigurationmanager-resourceset.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 ResourceTest 메서드](msft-dsclocalconfigurationmanager-resourcetest.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 RollBack 메서드](msft-dsclocalconfigurationmanager-rollback.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 SendConfiguration 메서드](msft-dsclocalconfigurationmanager-sendconfiguration.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApply 메서드](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 SendConfigurationApplyAsync 메서드](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 SendMetaConfigurationApply 메서드](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 StopConfiguration 메서드](msft-dsclocalconfigurationmanager-stopconfiguration.md)
### [MSFT_DSCLocalConfigurationManager 클래스의 TestConfiguration 메서드](msft-dsclocalconfigurationmanager-testconfiguration.md)

# 기타 참고 자료
## [백서](whitepapers.md)



<!--HONumber=May16_HO3-->


