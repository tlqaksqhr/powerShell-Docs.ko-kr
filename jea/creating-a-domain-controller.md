---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "도메인 컨트롤러 만들기"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 12fc529cfb21db260c9d1a2af87e2c3825d2ec4e

---

### 도메인 컨트롤러 만들기

이 문서에서는 컴퓨터가 도메인에 가입되어 있다고 가정합니다.
가입할 도메인이 현재 없는 경우 이 섹션은 DSC를 사용하여 도메인 컨트롤러를 신속하게 설정하는 데 도움이 될 수 있습니다.

#### 필수 구성 요소

1.  컴퓨터가 내부 네트워크에 있습니다.
2.  컴퓨터가 기존 도메인에 가입되어 있지 않습니다.
3.  컴퓨터에서 Windows Server 2016이 실행되고 있거나 WMF 5.0이 설치되어 있습니다.

#### xActiveDirectory 설치
컴퓨터가 인터넷에 연결되어 있는 경우 관리자 권한 PowerShell 창에서 다음 명령을 실행합니다.
```PowerShell
Install-Module xActiveDirectory -Force
```
인터넷에 연결되어 있지 않은 경우에는 xActiveDirectory를 다른 컴퓨터에 설치한 다음 xActiveDirectory 폴더를 컴퓨터의 "C:\Program Files\WindowsPowerShell\Modules" 폴더에 복사합니다.

설치에 성공했는지 확인하려면 다음 명령을 실행합니다.
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### DSC를 사용하여 도메인 설정
PowerShell에서 다음 스크립트를 복사하여 컴퓨터를 새 도메인의 도메인 컨트롤러로 만듭니다.
**작성자의 참고 사항: 사용 중이 아닌 자격 증명을 제공하는 경우 알려진 문제가 있습니다.  안전을 위해 로컬 관리자 암호를 잊어버리지 마세요.**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }

}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
컴퓨터가 몇 차례 다시 시작됩니다.
"Domain has been created."가 포함된 "C:\temp.txt"라는 파일이 표시되면 프로세스가 완료된 것입니다.

#### 사용자 및 그룹 설정
다음 명령은 도메인에서 Operator 및 Helpdesk 그룹과 해당 그룹의 구성원인 관리자가 아닌 사용자를 설정합니다.
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```




<!--HONumber=Jun16_HO4-->


