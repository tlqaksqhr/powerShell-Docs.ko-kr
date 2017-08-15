---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: WinRMSecurity
ms.openlocfilehash: a6adf61517708661e31a7387df5141f3c4f2c020
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="powershell-remoting-security-considerations"></a><span data-ttu-id="08c4d-103">PowerShell Remoting 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="08c4d-103">PowerShell Remoting Security Considerations</span></span>

<span data-ttu-id="08c4d-104">PowerShell Remoting을 사용해 Windows 시스템을 관리하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-104">PowerShell Remoting is the recommended way to manage Windows systems.</span></span> <span data-ttu-id="08c4d-105">Windows Server 2012 R2에서는 PowerShell Remoting이 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-105">PowerShell Remoting is enabled by default in Windows Server 2012 R2.</span></span> <span data-ttu-id="08c4d-106">이 문서에서는 PowerShell 원격을 사용할 때의 보안 문제, 권장 사항, 모범 사례 등을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-106">This document covers security concerns, recommendations, and best practices when using PowerShell Remoting.</span></span>

## <a name="what-is-powershell-remoting"></a><span data-ttu-id="08c4d-107">PowerShell Remoting이란?</span><span class="sxs-lookup"><span data-stu-id="08c4d-107">What is PowerShell Remoting?</span></span>

<span data-ttu-id="08c4d-108">PowerShell 원격은 [Web Services for Managment (WS-Managment)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf)(WS-Managment(Web Services for Managment))의 Microsoft 구현인 [Windows Remote Management (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx)(WinRM(Windows 원격 관리))를 사용하여 사용자가 원격 컴퓨터에서 PowerShell 명령을 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-108">PowerShell Remoting uses [Windows Remote Management (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx), which is the Microsoft implementation of the [Web Services for Management (WS-Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) protocol, to allow users to run PowerShell commands on remote computers.</span></span> <span data-ttu-id="08c4d-109">PowerShell Remoting 사용에 관한 자세한 내용은 [원격 명령 실행](https://technet.microsoft.com/en-us/library/dd819505.aspx)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-109">You can find more information about using PowerShell Remoting at [Running Remote Commands](https://technet.microsoft.com/en-us/library/dd819505.aspx).</span></span>

<span data-ttu-id="08c4d-110">PowerShell 원격은 원격 컴퓨터에서의 실행을 위해 cmdlet의 **ComputerName** 매개 변수를 사용하는 것과 다릅니다. 후자의 경우 RPC(원격 프로시저 호출)를 기본 프로토콜로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-110">PowerShell Remoting is not the same as using the **ComputerName** parameter of a cmdlet to run it on a remote computer, which uses Remote Procedure Call (RPC) as its underlying protocol.</span></span>

##  <a name="powershell-remoting-default-settings"></a><span data-ttu-id="08c4d-111">PowerShell Remoting 기본 설정</span><span class="sxs-lookup"><span data-stu-id="08c4d-111">PowerShell Remoting default settings</span></span>

<span data-ttu-id="08c4d-112">PowerShell Remoting 및 WinRM은 다음 포트에서 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-112">PowerShell Remoting (and WinRM) listen on the following ports:</span></span>

- <span data-ttu-id="08c4d-113">HTTP: 5985</span><span class="sxs-lookup"><span data-stu-id="08c4d-113">HTTP: 5985</span></span>
- <span data-ttu-id="08c4d-114">HTTPS: 5986</span><span class="sxs-lookup"><span data-stu-id="08c4d-114">HTTPS: 5986</span></span>

<span data-ttu-id="08c4d-115">기본적으로 PowerShell 원격은 Administrators 그룹 구성원의 연결만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-115">By default, PowerShell Remoting only allows connections from members of the Administrators group.</span></span> <span data-ttu-id="08c4d-116">세션은 사용자 컨텍스트에서 시작되므로 PowerShell 원격을 통해 연결된 상태에서는 개별 사용자 및 그룹에 적용된 모든 운영 체제 액세스 제어가 계속해서 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-116">Sessions are launched under the user's context, so all operating system access controls applied to individual users and groups continue to apply to them while connected over PowerShell Remoting.</span></span>

<span data-ttu-id="08c4d-117">개인 네트워크에서는 PowerShell Remoting용 기본 Windows 방화벽 규칙이 모든 연결을 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-117">On private networks, the default Windows Firewall rule for PowerShell Remoting accepts all connections.</span></span> <span data-ttu-id="08c4d-118">공용 네트워크에서는 기본 Windows 방화벽 규칙이 동일한 서브넷 내에서만 PowerShell 원격 연결을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-118">On public networks, the default Windows Firewall rule allows PowerShell Remoting connections only from within the same subnet.</span></span> <span data-ttu-id="08c4d-119">공용 네트워크에서 모든 연결에 대해 PowerShell Remoting을 열려면 해당 규칙을 명시적으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-119">You have to explicitly change that rule to open PowerShell Remoting to all connections on a public network.</span></span>

><span data-ttu-id="08c4d-120">**경고:** 공용 네트워크용 방화벽 규칙은 잠재적으로 악의적인 외부 연결 시도로부터 컴퓨터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-120">**Warning:** The firewall rule for public networks is meant to protect the computer from potentially malicious external connection attempts.</span></span> <span data-ttu-id="08c4d-121">이 규칙을 제거할 때는 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="08c4d-121">Use caution when removing this rule.</span></span>

## <a name="process-isolation"></a><span data-ttu-id="08c4d-122">프로세스 격리</span><span class="sxs-lookup"><span data-stu-id="08c4d-122">Process isolation</span></span>

<span data-ttu-id="08c4d-123">PowerShell Remoting은 컴퓨터 간 통신을 위해 [WinRM(Windows Remote Management)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-123">PowerShell Remoting uses [Windows Remote Management (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426) for communication between computers.</span></span> <span data-ttu-id="08c4d-124">WinRM은 네트워크 서비스 계정 아래에서 서비스로 실행되며, 사용자 계정으로 실행되는 격리 프로세스를 생성해 PowerShell 인스턴스를 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-124">WinRM runs as a service under the Network Service account, and spawns isolated processes running as user accounts to host PowerShell instances.</span></span> <span data-ttu-id="08c4d-125">한 명의 사용자로 실행하는 PowerShell의 인스턴스는 다른 사용자로 PowerShell 인스턴스를 실행하는 프로세스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-125">An instance of PowerShell running as one user has no access to a process running an instance of PowerShell as another user.</span></span>

## <a name="event-logs-generated-by-powershell-remoting"></a><span data-ttu-id="08c4d-126">PowerShell 원격에서 생성된 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="08c4d-126">Event logs generated by PowerShell Remoting</span></span>

<span data-ttu-id="08c4d-127">FireEye는 Powershell Remoting 세션에서 생성된 이벤트 로그와 기타 보안 증명에 대한 훌륭한 요약</span><span class="sxs-lookup"><span data-stu-id="08c4d-127">FireEye has provided a good summary of the event logs and other security evidence generated by PowerShell Remoting sessions, available at</span></span>  
<span data-ttu-id="08c4d-128">([PowerShell 공격 조사](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)에서 이용 가능)을 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-128">[Investigating PowerShell Attacks](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).</span></span>

## <a name="encryption-and-transport-protocols"></a><span data-ttu-id="08c4d-129">암호화 및 전송 프로토콜</span><span class="sxs-lookup"><span data-stu-id="08c4d-129">Encryption and transport protocols</span></span>

<span data-ttu-id="08c4d-130">PowerShell 원격 연결 보안은 초기 인증 및 지속적인 통신의 두 가지 관점으로 고려하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-130">It is helpful to consider the security of a PowerShell Remoting connection from two perspectives: initial authentication, and ongoing communication.</span></span> 

<span data-ttu-id="08c4d-131">사용된 전송 프로토콜(HTTP 또는 HTTPS)에 관계 없이 PowerShell Remoting은 초기 인증 후 세션별 AES-256 대칭 키를 사용해 모든 통신을 항상 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-131">Regardless of the transport protocol used (HTTP or HTTPS), PowerShell Remoting always encrypts all communication after initial authentication with a per-session AES-256 symmetric key.</span></span>
    
### <a name="initial-authentication"></a><span data-ttu-id="08c4d-132">초기 인증</span><span class="sxs-lookup"><span data-stu-id="08c4d-132">Initial authentication</span></span>

<span data-ttu-id="08c4d-133">인증을 통해 클라이언트-서버, 그리고 이상적으로 서버-클라이언트의 ID를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-133">Authentication confirms the identity of the client to the server - and ideally - the server to the client.</span></span>
    
<span data-ttu-id="08c4d-134">클라이언트가 컴퓨터 이름(server01 또는 server01.contoso.com)을 사용해 도메인 서버에 연결되는 경우 기본 인증 프로토콜은 [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx)입니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-134">When a client connects to a domain server using its computer name (i.e.: server01, or server01.contoso.com), the default authentication protocol is [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx).</span></span>
<span data-ttu-id="08c4d-135">Kerberos는 모든 종류의 다시 사용할 수 있는 자격 증명을 보내지 않고 사용자 ID 및 서버 ID를 모두 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-135">Kerberos guarantees both the user identity and server identity without sending any sort of reusable credential.</span></span>

<span data-ttu-id="08c4d-136">클라이언트가 IP 주소를 사용해 도메인 서버에 연결되는 경우 또는 작업 그룹 서버에 연결되는 경우 Kerberos 인증은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-136">When a client connects to a domain server using its IP address, or connects to a workgroup server, Kerberos authentication is not possible.</span></span> <span data-ttu-id="08c4d-137">이 경우 PowerShell 원격은 [NTLM authentication protocol(NTLM 인증 프로토콜)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-137">In that case, PowerShell Remoting relies on the [NTLM authentication protocol](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx).</span></span> <span data-ttu-id="08c4d-138">NTLM 인증 프로토콜은 어떠한 위임 가능 자격 증명도 보내지 않고 사용자 ID를 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-138">The NTLM authentication protocol guarantees the user identity without sending any sort of delegable credential.</span></span> <span data-ttu-id="08c4d-139">사용자 ID를 입증하기 위해 NTLM 프로토콜은 클라이언트와 서버 모두 암호 자체를 교환하지 않고 사용자 암호에서 세션 키를 계산하도록 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-139">To prove user identity, the NTLM protocol requires that both the client and server compute a session key from the user's password without ever exchanging the password itself.</span></span> <span data-ttu-id="08c4d-140">서버는 일반적으로 사용자 암호를 모르므로 사용자 암호를 알고 서버의 세션 키를 저장하는 도메인 컨트롤러와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-140">The server typically does not know the user's password, so it communicates with the domain controller, which does know the user's password and calculates the session key for the server.</span></span> 
      
<span data-ttu-id="08c4d-141">그러나 NTLM 프로토콜은 서버 ID를 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-141">The NTLM protocol does not, however, guarantee server identity.</span></span> <span data-ttu-id="08c4d-142">인증에 NTLM을 사용하는 모든 프로토콜에서와 마찬가지로 도메인에 가입된 컴퓨터의 컴퓨터 계정에 액세스할 수 있는 공격자는 도메인 컨트롤러의 호출하여 NTLM 세션 키를 계산하고 서버를 가장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-142">As with all protocols that use NTLM for authentication, an attacker with access to a domain-joined computer's machine account could invoke the domain controller to compute an NTLM session-key and thereby impersonate the server.</span></span>

<span data-ttu-id="08c4d-143">NTLM 기반 인증은 기본적으로 사용하지 않도록 설정되어 있습니다. 하지만 대상 서버에 SSL을 구성하거나 클라이언트에서 WinRM TrustedHosts 설정을 구성해 허용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-143">NTLM-based authentication is disabled by default, but may be permitted by either configuring SSL on the target server, or by configuring the WinRM TrustedHosts setting on the client.</span></span>
    
#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a><span data-ttu-id="08c4d-144">NTLM 기반 연결 동안 SSL 인증서를 사용해 서버 ID 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="08c4d-144">Using SSL certificates to validate server identity during NTLM-based connections</span></span>

<span data-ttu-id="08c4d-145">NTLM 인증 프로토콜은 대상 서버의 ID를 보장하지 않으므로(사용자의 암호를 이미 아는 경우는 제외) PowerShell Remoting에 SSL을 사용하도록 대상 서버를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-145">Since the NTLM authentication protocol cannot ensure the identity of the target server (only that it already knows your password), you can configure target servers to use SSL for PowerShell Remoting.</span></span> <span data-ttu-id="08c4d-146">대상 서버에 SSL 인증서를 할당하면(클라이언트도 신뢰하는 인증 기관에서 발급한 경우) 사용자 ID와 서버 ID를 모두 보장하는 NTLM 기반 인증을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-146">Assigning a SSL certificate to the target server (if issued by a Certificate Authority that the client also trusts) enables NTLM-based authentication that guarantees both the user identity and server identity.</span></span>
    
#### <a name="ignoring-ntlm-based-server-identity-errors"></a><span data-ttu-id="08c4d-147">NTLM 기반 서버 ID 오류 무시</span><span class="sxs-lookup"><span data-stu-id="08c4d-147">Ignoring NTLM-based server identity errors</span></span>
      
<span data-ttu-id="08c4d-148">NTLM 연결을 위해 서버에 SSL 인증서를 배포할 수 없는 경우 서버를 WinRM **TrustedHosts** 목록에 추가하여 결과 ID 오류를 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-148">If deploying a SSL certificate to a server for NTLM connections is infeasible, you may suppress the resulting identity errors by adding the server to the WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="08c4d-149">서버 이름을 TrustedHosts 목록에 추가한다고 호스트 자체를 신뢰할 수 있음을 나타내는 것은 아닙니다. NTLM 인증 프로토콜이 사용자가 연결하려는 호스트에 실제로 연결하는 중인지 보장할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-149">Please note that adding a server name to the TrustedHosts list should not be considered as any form of statement of the trustworthiness of the hosts themselves - as the NTLM authentication protocol cannot guarantee that you are in fact connecting to the host you are intending to connect to.</span></span>
<span data-ttu-id="08c4d-150">대신에 TrustedHosts 설정을 서버의 ID를 확인하지 못해 발생하는 오류를 숨기려는 호스트 목록으로 간주해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-150">Instead, you should consider the TrustedHosts setting to be the list of hosts for which you wish to suppress the error generated by being unable to verify the server's identity.</span></span>
    
    
### <a name="ongoing-communication"></a><span data-ttu-id="08c4d-151">진행 중인 통신</span><span class="sxs-lookup"><span data-stu-id="08c4d-151">Ongoing Communication</span></span>

<span data-ttu-id="08c4d-152">초기 인증이 완료되면 [PowerShell Remoting Protocol(PowerShell 원격 프로토콜)](https://msdn.microsoft.com/en-us/library/dd357801.aspx)이 모든 진행 중인 통신을 세션별 AES-256 대칭 키를 사용해 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-152">Once initial authentication is complete, the [PowerShell Remoting Protocol](https://msdn.microsoft.com/en-us/library/dd357801.aspx) encrypts all ongoing communication with a per-session AES-256 symmetric key.</span></span>  


## <a name="making-the-second-hop"></a><span data-ttu-id="08c4d-153">두 번째 홉 만들기</span><span class="sxs-lookup"><span data-stu-id="08c4d-153">Making the second hop</span></span>

<span data-ttu-id="08c4d-154">기본적으로 PowerShell Remoting은 인증을 위해 Kerberos(사용 가능한 경우) 또는 NTLM을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-154">By default, PowerShell Remoting uses Kerberos (if available) or NTLM for authentication.</span></span> <span data-ttu-id="08c4d-155">이 두 프로토콜은 모두 자격 증명을 보내지 않고 원격 컴퓨터를 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-155">Both of these protocols authenticate to the remote machine without sending credentials to it.</span></span>
<span data-ttu-id="08c4d-156">이는 가장 안전한 인증 방법입니다. 하지만 원격 컴퓨터에 사용자의 자격 증명이 없으므로 사용자를 대신해 다른 컴퓨터나 서비스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-156">This is the most secure way to authenticate, but because the remote machine does not have the user's credentials, it cannot access other computers and services on the user's behalf.</span></span> <span data-ttu-id="08c4d-157">이를 "두 번째 홉 문제"라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-157">This is known as the "second hop problem".</span></span>

<span data-ttu-id="08c4d-158">이 문제를 방지하는 방법은 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c4d-158">There are several ways to avoid this problem.</span></span> <span data-ttu-id="08c4d-159">이러한 방법에 대한 설명과 각 방법의 장점과 단점은 [PowerShell 원격에서 두 번째 홉 만들기](PS-remoting-second-hop.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c4d-159">For descriptions of these methods, and the pros and cons of each, see [Making the second hop in PowerShell Remoting](PS-remoting-second-hop.md).</span></span>









