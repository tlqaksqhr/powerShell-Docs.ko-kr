# [WMF 릴리스 정보 개요](releasenotes.md)

# [설치 정보](requirements.md)

# [제품 호환성 상태](productincompat.md)

# [사용자 의견](feedback.md)

# [WMF 5.0에서 사용하도록 설정된 시나리오]()
## [JEA(Just Enough Administration)](jea_overview.md)
### [JEA 끝점 만들기 및 연결](jea_endpoint.md)
### [JEA에 대한 보고](jea_report.md)

## [PowerShell 클래스를 사용하여 사용자 지정 형식 만들기](class_overview.md)
### [사용자 지정 형식 정의](class_newtype.md)
### [기본 클래스 선언](class_base.md)
### [구현된 인터페이스 선언](class_interface.md)
### [기본 클래스 생성자 호출](class_baseconstructor.md)
### [기본 클래스 메서드 호출](class_basemethod.md)

## [PowerShell 스크립트 디버깅의 향상된 기능](debug_overview.md)

## [DSC(원하는 상태 구성)의 향상된 기능](dsc_improvements.md)
### [구성]()
#### [노든 간 종속성 지정](dsc_waitfor.md)
#### [암호화된 MOF](dsc_encryptedmof.md)
#### [DSC 구성에 대한 도움말 지원](dsc_confighelp.md)
#### [PowerShell ISE를 사용하여 작성 기능 향상](dsc_authoring.md)
#### [구성에서 동일한 중복 리소스에 대한 허용](dsc_identicalduplicate.md)
#### [Import-DscResource 키워드에서 -moduleversion 매개 변수 지원](dsc_importdscresource.md)
#### [WOW64에서 구성 키워드 지원](dsc_wow64.md)
### [리소스]()
#### [클래스 기반 DSC 리소스](dsc_classbasedresource.md)
#### [DSC 리소스 스크립트 디버깅](dsc_resourcedebugging.md)
#### [DSC 리소스의 자동 RunAs 지원](dsc_runas.md)
#### [DSC 리소스의 Side-by-side 버전 관리 지원](dsc_sxsresource.md)
#### [새로운 기본 제공 리소스](dsc_newresources.md)
### [로컬 구성 관리자]()
#### [여러 구성 조각을 사용하여 노드 구성](dsc_partialconfig.md)
##### [혼합 RefreshMode 지원](dsc_partialconfig_mixedmode.md)
#### [새 특성으로 DSC 엔진 구성](dsc_metaconfiguration.md)
#### [LCM 상태에 대한 자세한 정보](dsc_lcmstate.md)
#### [RefreshMode 및 ConfigurationMode의 빈도가 서로의 배수일 필요가 없음](dsc_freqnomultiple.md)
#### [RefreshMode 속성에 대한 추가 값](dsc_refreshmode.md)
### [Cmdlet]()
#### [구성 상태에 대한 세부 정보](dsc_getconfigurationstatus.md)
#### [Test-DscConfiguration cmdlet에서 참조 구성 지원](dsc_testconfiguration.md)
#### [DSC 리소스 메서드에 직접 액세스](dsc_directaccess.md)
#### [적용하지 않고 구성 문서 제공](dsc_publishconfig.md)
#### [DSC 문서 제거](dsc_removeconfigdoc.md)
#### [통합되고 일관된 상태 및 상태 표현](dsc_statestatus.md)
#### [Set-DscLocalConfigurationManager cmdlet에서 -force 매개 변수 지원](dsc_setdsclcm.md)
### [끌어오기 모드]()
#### [DSC 구성의 요청 시 끌어오기](dsc_updateconfig.md)
#### [노드 및 구성 ID의 분리](dsc_nodeid.md)
#### [구성, 리소스 및 보고서 리포지토리의 분리](dsc_repository.md)
#### [중앙 위치에 구성 상태 보고](dsc_reporting.md)

## [기록 및 로깅을 사용하여 PowerShell 사용 감사](audit_overview.md)
### [향상된 기록 옵션](audit_transcript.md)
### [스크립트 추적 및 로깅](audit_script.md)
### [암호화 메시지 구문(CMS) cmdlet](audit_cms.md)

## [PackageManagement를 사용하여 소프트웨어 검색, 설치 및 인벤토리에 추가](oneget_overview.md)
### [PackageManagement Cmdlet](oneget_cmdlets.md)

## [PowerShellGet을 사용하여 PowerShell 모듈 검색, 설치 및 인벤토리에 추가](psget_module_overview.md)
### [PowerShell 리포지토리 등록](psget_psrepository.md)
### [PowerShell 5.0 이상의 Side-by-Side 버전 지원](psget_modulesxsinstall.md)
### [모듈 종속성의 설치](psget_moduledependency.md)
### [모듈 관리를 위한 PowerShellGet Cmdlet](psget_modulecmdlets.md)

## [PowerShellGet을 사용하여 PowerShell 스크립트 검색, 설치 및 관리](psget_script_overview.md)
### [스크립트 관리를 위한 PowerShellGet Cmdlet](psget_scriptcmdlets.md)

## [커뮤니티 피드백에 따라 새로 제공되거나 업데이트된 cmdlet ](feedback_cmdlets.md)
### [Item cmdlet을 사용하는 기호화된 링크](feedback_symbolic.md)
### [보관 cmdlet](feedback_archive.md)
### [클립보드 cmdlet](feedback_clipboard.md)
### [Convert-String](feedback_convertstring.md)
### [문자열에서 구조화된 개체 추출 및 구문 분석](feedback_convertfromString.md)
### [Format-Hex](feedback_formathex.md)
### [NoNewLine 매개 변수](feedback_nonewline.md)
### [New-TemporaryFile](feedback_tempfile.md)
### [New-Guid](feedback_newguid.md)
### [Get-ChildItem의 -Depth 매개 변수](feedback_getchilditem.md)
### [FileInfo 개체에 대한 업데이트](feedback_fileinfo.md)
### [모듈의 버전 범위 선언(1.* 등) 지원](feedback_moduleversionranges.md)

## [정보 스트림](informationstream_overview.md)

## [OData 끝점에 따라 PowerShell Cmdlet 생성](odata_overview.md)

## [PowerShell을 사용하여 네트워크 스위치 관리](networkswitch_overview.md)

## [소프트웨어 인벤토리 로깅(SIL)](sil_overview.md)

# [알려진 문제 및 제한 사항](limitation_overview.md)
## [DSC(원하는 상태 구성)의 알려진 문제](limitation_dsc.md)


<!--HONumber=Jun16_HO4-->


