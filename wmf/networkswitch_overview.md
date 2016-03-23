# PowerShell을 사용하여 네트워크 스위치 관리

**Get-NetworkSwitchEthernetPort** cmdlet은 인스턴스와 함께 다음과 같은 추가 정보를 반환합니다.
-   IPAddress – 포트와 연결된 IP 주소
-   PortMode – 포트 모드: 액세스, 라우트 또는 트렁크
-   AccessVLAN – 액세스 모드에서 이 포트와 연결된 VLAN의 ID
-   TrunkedVLANList – 트렁크 모드에서 이 포트와 연결된 VLAN의 ID 목록

## Windows PowerShell을 사용한 기본적인 네트워크 스위치 관리
첫 번째 WMF 5.0 Preview에서 도입된 네트워크 스위치 cmdlet을 사용하면 스위치, VLAN(가상 LAN) 및 기본 계층 2 네트워크 스위치 포트 구성을 Windows Server 2012 R2 로고 인증 네트워크 스위치에 적용할 수 있습니다. Microsoft는 [DAL(데이터 센터 추상화 계층)](http://technet.microsoft.com/en-us/cloud/dal.aspx) 비전을 지원하고 이 공간에서 고객과 파트너에게 가치를 보여 주기 위해 최선을 다하고 있습니다. 이러한 cmdlet을 사용하여 다음을 수행할 수 있습니다.

-   다음과 같은 전역 스위치 구성:
    -   호스트 이름 설정
    -   스위치 배너 설정
    -   구성 유지
    -   기능을 사용하거나 사용하지 않도록 설정

-   VLAN 구성:
    -   VLAN 만들기 또는 제거
    -   VLAN을 사용하거나 사용하지 않도록 설정
    -   VLAN 열거
    -   VLAN의 식별 이름 설정

-   계층 2 포트 구성:
    -   포트 열거
    -   포트를 사용하거나 사용하지 않도록 설정
    -   포트 모드 및 속성 설정
    -   포트의 트렁크 또는 액세스에 VLAN 추가 또는 연결

모든 NetworkSwitch cmdlet을 검색하여 탐색을 시작하세요.

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

자세한 내용은 Jeffrey Snover의 WMF 5.0 Preview 공지 블로그 게시물에서 확인할 수 있습니다.<http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
<!--HONumber=Mar16_HO2-->
