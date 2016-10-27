
DSC에서는 <b>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System</b> 아래의 <b>DSCAutomationHostEnabled</b> 레지스트리 키를 사용하여 초기 부팅 시 컴퓨터를 자동으로 구성합니다.
DSCAutomationHostEnabled는 다음의 세 가지 모드를 지원합니다.

|  DSCAutomationHostEnabled 값  |  설명   | 
|---|---| 
0 | 부팅 시 컴퓨터를 구성하지 않도록 설정합니다. |
1 | 부팅 시 컴퓨터를 구성하도록 설정합니다. |
2 | DSC가 보류 중 또는 현재 상태인 경우에만 컴퓨터를 구성하도록 설정합니다. 기본값입니다. |




<!--HONumber=Oct16_HO2-->


