# RefreshMode 및 ConfigurationMode의 빈도가 서로의 배수일 필요가 없음

이전 버전의 DSC에서 LCM은 블로그([여기](http://blogs.msdn.com/b/powershell/archive/2013/12/09/understanding-meta-configuration-in-windows-powershell-desired-state-configuration.aspx))에 설명된 대로 `RefreshFrequencyMins` 및 `ConfigurationModeFrequencyMins`를 서로의 배수로 처리합니다. WMF 5.0 RTM에서 이러한 속성은 서로 독립적으로 처리됩니다. 아래 표에서는 이 동작을 보여 줍니다.

**끌어오기** 모드의 동작: 

|                                  |**메타 구성의 값**|**메타 구성이 적용된 후의 값**|**끌어오기 발생 빈도(분)**|**구성이 적용되는 빈도(분)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |                                    |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |40                                  |                                                |

**밀어넣기** 모드의 동작:

|                                  |**메타 구성의 값**|**메타 구성이 적용된 후의 값**|**구성이 적용되는 빈도(분)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |                                                |
<!--HONumber=Mar16_HO2-->
