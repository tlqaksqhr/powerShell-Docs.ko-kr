# PowerShell Remoting 보안 고려 사항

PowerShell Remoting을 사용해 Windows 시스템을 관리하는 것이 좋습니다. Windows Server 2012 R2에서는 PowerShell Remoting이 기본적으로 사용됩니다. 이 문서는 PowerShell Remoting 사용 시의 보안 우려 사항, 
권장 사항 및 모범 사례에 대해 다룹니다.

## PowerShell Remoting이란?

PowerShell Remoting은 [WS-Managment(Web Services for Managment)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx) 프로토콜의 Microsoft 구현인
[WinRM(Windows Remote Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) 프로토콜을 사용해 사용자가 원격 컴퓨터에서 PowerShell 명령을 실행하도록
허용합니다. PowerShell Remoting 사용에 관한 자세한 내용은 [원격 명령 실행](https://technet.microsoft.com/en-us/library/dd819505.aspx)에서 확인할 수 있습니다.

PowerShell Remoting은 원격 컴퓨터에서의 실행을 위해 cmdlet의 **ComputerName** 매개 변수를 사용하는 것과 다릅니다. 후자의 경우 RPC(Remote Procedure Call)를
기본 프로토콜로 사용합니다.

##  PowerShell Remoting 기본 설정

PowerShell Remoting 및 WinRM은 다음 포트에서 수신 대기합니다.

- HTTP: 5985
- HTTPS: 5986

기본적으로 PowerShell Remoting은 관리자 그룹 멤버의 연결만 허용합니다. 세션이 사용자의 컨텍스트에 따라 시작되므로,
PowerShell Remoting을 통해 연결되는 동안 개별 사용자 및 그룹에 적용된 모든 작동 시스템 엑세스 제어가 그대로 계속 적용됩니다.

개인 네트워크에서는 PowerShell Remoting용 기본 Windows 방화벽 규칙이 모든 연결을 수락합니다. 공용 네트워크에서는 기본 Windows 방화벽 규칙이 동일한 서브넷 내에서의
PowerShell Remoting 연결만 허용합니다. 공용 네트워크에서 모든 연결에 대해 PowerShell Remoting을 열려면 해당 규칙을 명시적으로 변경해야 합니다.

>**경고:** 공용 네트워크용 방화벽 규칙은 잠재적으로 악의적인 외부 연결 시도로부터 컴퓨터를 보호합니다. 이 규칙을 제거할 경우 
>주의하십시오.

## 프로세스 격리

PowerShell Remoting은 컴퓨터 간 통신을 위해 [WinRM(Windows Remote Management)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426)을 사용합니다. 
WinRM은 네트워크 서비스 계정 아래에서 서비스로 실행되며, 사용자 계정으로 실행되는 격리 프로세스를 생성해 PowerShell 인스턴스를 호스트합니다. 한 명의 사용자로 실행되는 PowerShell 인스턴스는
다른 사용자로 PowerShell 인스턴스를 실행하는 프로세스에 액세스할 수 없습니다.

## Powershell Remoting에서 생성된 이벤트 로그

FireEye는 Powershell Remoting 세션에서 생성된 이벤트 로그와 기타 보안 증명에 대한 훌륭한 요약  
([PowerShell 공격 조사](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)에서 이용 가능)을 제공했습니다.

## 암호화 및 전송 프로토콜

PowerShell Remoting 연결 보안은 초기 인증 및 지속적인 통신의 두 가지 관점으로 고려하는 것이 좋습니다. 

사용된 전송 프로토콜(HTTP 또는 HTTPS)에 관계 없이 PowerShell Remoting은 초기 인증 후 세션별 AES-256 대칭 키를 사용해 모든 통신을 항상 암호화합니다.
    
### 초기 인증

인증을 통해 클라이언트-서버, 그리고 이상적으로 서버-클라이언트의 ID를 확인합니다.
    
클라이언트가 컴퓨터 이름(예: server01 또는 server01.contoso.com)을 사용해 도메인 서버에 연결되는 경우 기본 인증 프로토콜은 
[Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx)입니다.
Kerberos는 모든 종류의 다시 사용할 수 있는 자격 증명을 보내지 않고 사용자 ID 및 서버 ID를 모두 보장합니다.

클라이언트가 IP 주소를 사용해 도메인 서버에 연결되는 경우 또는 작업 그룹 서버에 연결되는 경우 Kerberos 인증은 사용할 수 없습니다. 이 경우 PowerShell
Remoting은 [NTLM 인증 프로토콜](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx)을 사용합니다. NTLM 인증
프로토콜은 모든 종류의 위임할 수 자격 증명을 보내지 않고 사용자 ID를 보장합니다. 사용자 ID를 증명하기 위해 NTLM 프로토콜은 암호 자체를 교환하지 않고
클라이언트와 서버 모두에서 사용자 암호의 세션 키를 계산하도록 요구합니다. 서버는 보통 사용자의 암호를 모르기 때문에 사용자의 암호를 알고 있는 
도메인 컨트롤러로 통신해 서버의 세션 키를 계산합니다. 
      
그러나 NTLM 프로토콜 서버 ID를 보장하지 않습니다. 인증을 위해 NTLM을 사용하는 모든 프로토콜과 마찬가지로, 도메인 가입 컴퓨터의 컴퓨터 계정에 액세스할 수 있는 공격자가
도메인 컨트롤러를 호출해 NTLM 세션 키를 계산하여 서버를 가장할 수 있습니다.

NTLM 기반 인증은 기본적으로 사용하지 않도록 설정되어 있습니다. 하지만 대상 서버에 SSL을 구성하거나 WinRM TrustedHosts 설정을 구성해 허용할 수도 있습니다.
    
#### NTLM 기반 연결 동안 SSL 인증서를 사용해 서버 ID 유효성 검사

NTLM 인증 프로토콜은 대상 서버의 ID를 보장하지 않으므로 (사용자의 암호를 이미 아는 경우는 제외) 해 PowerShell Remoting에 SSL을 사용하도록
대상 서버를 구성할 수 있습니다. SSL 인증서를 대상 서버에 할당하면 (클라이언트도 신뢰하는 인증 기관에서 발급한 경우)
사용자 ID와 서버 ID를 모두 보장하는 NTLM 기반 인증을 수행할 수 있습니다.
    
#### NTLM 기반 서버 ID 오류 무시
      
NTLM 연결을 위해 서버에 SSL 인증서를 배포할 수 없는 경우 서버를 WinRM 
**TrustedHosts** 목록에 추가해 발생하는 ID 오류를 숨길 수 있습니다. 서버 이름을 TrustedHosts 목록에 추가하는 것은 호스트 자체의 신뢰도를 나타내는 것이 아닙니다.
이는 NTLM 인증 프로토콜이 사용자가 연결하려는 호스트에 실제로 연결되는 중인지 보장할 수 없기 때문입니다.
대신에 TrustedHosts 설정을 서버의 ID를 확인하지 못해 발생하는 오류를 숨기려는 호스트 목록으로 간주해야 합니다.
    
    
### 진행 중인 통신

초기 인증이 완료되면 [PowerShell Remoting 프로토콜](https://msdn.microsoft.com/en-us/library/dd357801.aspx)이 모든 진행 중인 통신을
세션별 AES-256 대칭 키를 사용해 암호화합니다.  


## 두 번째 홉 만들기

기본적으로 PowerShell Remoting은 인증을 위해 Kerberos(사용 가능한 경우) 또는 NTLM을 사용합니다. 이 두 프로토콜은 모두 자격 증명을 보내지 않고 원격 컴퓨터를 인증합니다.
이는 가장 안전한 인증 방법입니다. 하지만 원격 컴퓨터에 사용자의 자격 증명이 없으므로 사용자를 대신해 다른 컴퓨터나 서비스에 액세스할 수 없습니다. 
이를 "더블홉" 문제 라고 합니다.

이러한 문제를 방지하는 여러 가지 방법이 있습니다.

### Kerberos 제한 위임

매우 신뢰할 수 있는 서버의 경우 [Kerberos 제한 위임](https://technet.microsoft.com/en-us/library/cc995228.aspx)을 사용하도록 설정할 수 있습니다. 이를 통해 원격 서버가 인증된 사용자를 가장해
특정 컴퓨터 및 서비스 목록에 액세스할 수 있습니다.

### 원격 컴퓨터 간 트러스트

*Server1*에서 *Server2*의 리소스에 원격으로 연결된 사용자를 신뢰하는 경우 *Server1*에서 해당 리소스에 액세스하도록 명시적으로 권한을 부여할 수 있습니다.

### 원격 리소스에 액세스할 때 명시적 자격 증명 사용

cmdlet의 **Credential** 매개 변수를 사용해 자격 증명을 원격 리소스로 명시적으로 전달할 수 있습니다. 예:

```powershell
$myCredential = Get-Credential
New-PSDrive -Name Tools \\Server2\Shared\Tools -Credential $myCredential 
```

### CredSSP

[New-PSSession](https://technet.microsoft.com/en-us/library/hh849717.aspx) cmdlet 호출의 `Authentication` 매개 변수 값으로 "CredSSP"를 지정하여 
[CredSSP(Credential Security Support Provicer)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx)를 인증에 사용할 수 있습니다. CredSSP는 자격 증명을 일반 텍스트로 서버에 전달하므로,
이를 사용하면 자격 증명 도난 공격에 노출될 수 있습니다. 원격 컴퓨터의 보안이 손상되면 공격자가 사용자의 자격 증명에 액세스할 수 있습니다. 기본적으로 CredSSP는 클라이언트 및 서버 컴퓨터 모두에서 
사용하지 않도록 설정됩니다. 가장 신뢰할 수 있는 환경에서만 CredSSP를 사용하도록 설정해야 합니다. 예를 들어, 도메인 컨트롤러는 매우 신뢰할 수 있으므로 도메인 관리자는 도메인 컨트롤러에 
연결할 수 있습니다.

PowerShell Remoting에 CredSSP 사용 시의 보안 우려 사항에 대한 자세한 내용은 
[고의적 파괴: CredSSP 조심](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp)을 참조하세요.

자격 증명 도난 공격에 대한 자세한 내용은 [PtH(Pass-the-Hash) 공격 및 기타 자격 증명 도난 완화](https://www.microsoft.com/en-us/download/details.aspx?id=36036)를 참조하세요.










<!--HONumber=Apr16_HO4-->


