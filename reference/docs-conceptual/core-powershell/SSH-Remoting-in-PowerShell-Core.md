# <a name="powershell-remoting-over-ssh"></a>SSH를 통한 PowerShell 원격

## <a name="overview"></a>개요

PowerShell 원격 기능은 일반적으로 연결 협상 및 데이터 전송에 WinRM을 사용합니다.
SSH는 이제 Linux 및 Windows 플랫폼에 모두 사용할 수 있고 진정한 다중 플랫폼 PowerShell 원격 기능을 허용하므로 이 원격 기능 구현에 선택되었습니다.
그러나 WinRM은 이 구현이 아직 지원하지 않는 PowerShell 원격 세션에 대한 강력한 호스팅 모델도 제공합니다.
그리고 이는 PowerShell 원격 엔드포인트 구성 및 JEA(Just Enough Administration)가 이 구현에서 아직 지원되지 않음을 의미합니다.

PowerShell SSH 원격 기능을 사용하면 Windows 및 Linux 컴퓨터 간에 기본적인 PowerShell 세션 원격 작업을 수행할 수 있습니다.
이러한 작업은 SSH 하위 시스템인 대상 컴퓨터에 PowerShell 호스팅 프로세스를 만드는 방식으로 수행됩니다.
결국 이는 엔드포인트 구성 및 JEA를 지원하기 위해 WinRM이 작동하는 방식과 유사한, 보다 일반적인 호스팅 모델로 변경됩니다.

New-PSSession, Enter-PSSession 및 Invoke-Command cmdlet에는 이제 이 새로운 원격 연결을 용이하게 하는 새로운 매개 변수가 설정됩니다.

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

이 새로운 매개 변수 집합은 변경될 가능성이 높지만 현재는 명령줄에서 상호 작용하거나 명령 및 스크립트를 호출할 수 있는 SSH PSSession을 만드는 데 사용할 수 있습니다.
HostName 매개 변수를 사용하여 대상 컴퓨터를 지정하고 UserName을 사용하여 사용자 이름을 제공합니다.
PowerShell 명령줄에서 대화형으로 cmdlet을 실행할 때는 암호를 묻는 메시지가 나타납니다.
하지만 SSH 키 인증을 사용하고 KeyFilePath 매개 변수를 사용하여 개인 키 파일 경로를 지정하는 옵션도 있습니다.

## <a name="general-setup-information"></a>일반적인 설치 정보

SSH는 모든 컴퓨터에 설치해야 합니다.
컴퓨터에서 들어오고 나가는 원격 작업을 실험할 수 있도록 클라이언트(ssh.exe) 및 서버(sshd.exe)를 설치해야 합니다.
Windows의 경우 [GitHub의 Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)를 설치해야 합니다.
Linux의 경우 플랫폼에 적합한 SSH(sshd 서버 포함)를 설치해야 합니다.
또한 GitHub에서 SSH 원격 기능이 있는 최신 PowerShell 빌드 또는 패키지를 설치해야 합니다.
SSH 하위 시스템은 원격 컴퓨터에 PowerShell 프로세스를 설정하는 데 사용되며, SSH 서버에 이를 구성해야 합니다.
또한 암호 인증을 활성화하고, 필요에 따라 키 기반 인증도 활성화해야 합니다.

## <a name="setup-on-windows-machine"></a>Windows 컴퓨터에 설치

1. 최신 버전의 [Windows용 PowerShell Core] 설치
    - New-PSSession의 매개 변수 집합을 확인하면 SSH 원격 기능이 지원되는지 알 수 있습니다.

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. [설치] 지침에 따라 GitHub에서 최신 [Win32 OpenSSH] 빌드를 설치합니다.
1. Win32 OpenSSH를 설치한 위치에서 sshd_config 파일을 편집합니다.
    - 암호 인증이 활성화되었는지 확인합니다.

    ```
    PasswordAuthentication yes
    ```

    - PowerShell 하위 시스템 항목을 추가하고 `c:/program files/powershell/6.0.0/pwsh.exe`를 사용하려는 버전에 대한 올바른 경로로 바꿉니다.

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - 필요에 따라 키 인증을 활성화합니다.

    ```
    PubkeyAuthentication yes
    ```

1. sshd 서비스를 다시 시작합니다.

    ```powershell
    Restart-Service sshd
    ```

1. Path Env 변수에 OpenSSH가 설치된 경로를 추가합니다.
    - 이는 `C:\Program Files\OpenSSH\` 줄에 있어야 합니다.
    - 그래야 시스템에서 ssh.exe를 찾을 수 있습니다.

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Linux(Ubuntu 14.04) 컴퓨터에 설치

1. GitHub에서 최신 [Linux용 PowerShell Core] 빌드를 설치합니다.
1. 필요에 따라 [Ubuntu SSH]를 설치합니다.

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. /etc/ssh 위치에서 sshd_config 파일을 편집합니다.
    - 암호 인증이 활성화되었는지 확인합니다.

    ```
    PasswordAuthentication yes
    ```

    - PowerShell 하위 시스템 항목을 추가합니다.

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - 필요에 따라 키 인증을 활성화합니다.

    ```
    PubkeyAuthentication yes
    ```

1. sshd 서비스를 다시 시작합니다.

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a>MacOS 컴퓨터에 설치

1. 최신 [MacOS용 PowerShell Core] 빌드를 설치합니다.
    - 다음 단계를 수행하여 SSH 원격 기능이 활성화되어 있는지 확인합니다.
      - `System Preferences`를 엽니다.
      - `Sharing`을 클릭합니다.
      - `Remote Login`을 확인합니다(`Remote Login: On`이어야 함).
      - 적절한 사용자에게 액세스를 허용합니다.
1. `/private/etc/ssh/sshd_config` 위치에서 `sshd_config` 파일을 편집합니다.
    - 선호하는 편집기를 사용합니다. 또는

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - 암호 인증이 활성화되었는지 확인합니다.

    ```
    PasswordAuthentication yes
    ```

    - PowerShell 하위 시스템 항목을 추가합니다.

    ```
    Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - 필요에 따라 키 인증을 활성화합니다.

    ```
    PubkeyAuthentication yes
    ```

1. sshd 서비스를 다시 시작합니다.

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a>PowerShell 원격 기능 예제

원격 기능을 테스트하는 가장 쉬운 방법은 단일 컴퓨터에서 사용해 보는 것입니다.
여기에서는 Linux 상자의 동일한 컴퓨터에 다시 원격 세션을 만들겠습니다.
암호 프롬프트뿐만 아니라 명령 프롬프트에서도 PowerShell cmdlet을 사용하므로 SSH에서 호스트 컴퓨터를 확인할지 묻는 메시지를 볼 수 있습니다.
또한 Windows 컴퓨터에서도 동일한 작업을 수행하여 원격 기능이 작동하는지 확인한 후 호스트 이름을 변경하여 컴퓨터 간에 원격 기능이 작동하는지 확인할 수 있습니다.

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a>알려진 문제

1. sudo 명령은 Linux 컴퓨터에 대한 원격 세션에서 작동하지 않습니다.

[Windows용 PowerShell Core]: ../setup/installing-powershell-core-on-windows.md#msi
[Linux용 PowerShell Core]: ../setup/installing-powershell-core-on-linux.md#ubuntu-1404
[MacOS용 PowerShell Core]: ../setup/installing-powershell-core-on-macos.md
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[설치]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
