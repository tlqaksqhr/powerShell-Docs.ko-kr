# RefreshMode 및 ConfigurationMode의 빈도가 서로의 배수일 필요가 없음

이전 버전의 DSC에서 LCM은 `RefreshFrequencyMins` 및 `ConfigurationModeFrequencyMins`를 서로의 배수로 처리합니다. WMF 5.0 RTM에서 이러한 속성은 서로 독립적으로 처리됩니다. 

자세한 내용은 [로컬 구성 관리자 구성](../dsc/metaConfig.md)을 참조하세요.

<!--HONumber=Jun16_HO4-->


