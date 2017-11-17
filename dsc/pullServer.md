---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC 웹 끌어오기 서버 설정"
ms.openlocfilehash: 03d4d148c87854b146091aa0e8d815b8c35def72
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2017
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="b1387-103">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="b1387-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="b1387-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b1387-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b1387-105">DSC 웹 끌어오기 서버는 해당 노드에서 요청하면 OData 인터페이스를 사용하여 DSC 구성 파일을 대상 노드에 사용할 수 있도록 하는 IIS의 웹 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b1387-106">끌어오기 서버 사용을 위한 요구 사항:</span><span class="sxs-lookup"><span data-stu-id="b1387-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="b1387-107">다음 항목을 실행 중인 서버:</span><span class="sxs-lookup"><span data-stu-id="b1387-107">A server running:</span></span>
  - <span data-ttu-id="b1387-108">WMF/PowerShell 5.0 이상</span><span class="sxs-lookup"><span data-stu-id="b1387-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="b1387-109">IIS 서버 역할</span><span class="sxs-lookup"><span data-stu-id="b1387-109">IIS server role</span></span>
  - <span data-ttu-id="b1387-110">DSC 서비스</span><span class="sxs-lookup"><span data-stu-id="b1387-110">DSC Service</span></span>
* <span data-ttu-id="b1387-111">인증서를 생성하여 대상 노드에서 LCM(로컬 구성 관리자)에 전달된 자격 증명을 보호할 방법이 있으면 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="b1387-112">서버 관리자에서 역할 및 기능 추가 마법사를 사용하거나 PowerShell을 사용하여 IIS 서버 역할 및 DSC 서비스를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="b1387-113">이 항목에 포함된 샘플 스크립트는 이 두 단계를 모두 처리하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="b1387-114">xDSCWebService 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="b1387-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="b1387-115">웹 끌어오기 서버를 설정하는 가장 쉬운 방법은 xPSDesiredStateConfiguration 모듈에 포함된 xWebService 리소스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="b1387-116">다음 단계에서는 웹 서비스를 설정하는 구성에서 리소스를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="b1387-117">[Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet을 호출하여 **xPSDesiredStateConfiguration** 모듈을 설치하세요.</span><span class="sxs-lookup"><span data-stu-id="b1387-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="b1387-118">**참고**: **Install-Module**은 PowerShell 5.0에 포함된 **PowerShellGet** 모듈에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b1387-119">[PackageManagement PowerShell 모듈 미리 보기](https://www.microsoft.com/en-us/download/details.aspx?id=49186)에서 PowerShell 3.0 및 4.0용 **PowerShellGet** 모듈을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="b1387-120">조직 내 또는 공공 기관 내의 신뢰할 수 있는 인증 기관에서 DSC 끌어오기 서버에 대한 SSL 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="b1387-121">기관에서 받은 인증서는 일반적으로 PFX 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="b1387-122">DSC 끌어오기 서버 역할을 할 노드에서 기본 위치 CERT:\LocalMachine\My에 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="b1387-123">인증서 지문을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="b1387-124">등록 키로 사용할 GUID를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="b1387-125">PowerShell을 사용하여 생성하려면 PS 프롬프트에 '``` [guid]::newGuid()```' 또는 '```New-Guid```'를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="b1387-126">이 키는 클라이언트 노드에서 등록할 때 인증할 공유 키로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="b1387-127">자세한 내용은 아래 등록 키 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1387-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="b1387-128">PowerShell ISE에서 다음의 구성 스크립트(**xPSDesiredStateConfiguration** 모듈의 예제 폴더에 Sample_xDscWebService.ps1로 포함됨)를 시작합니다(F5).</span><span class="sxs-lookup"><span data-stu-id="b1387-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="b1387-129">이 스크립트는 끌어오기 서버를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-129">This script sets up the pull server.</span></span>
  
    ```powershell
    configuration Sample_xDscPullServer
    { 
        param  
        ( 
                [string[]]$NodeName = 'localhost', 

                [ValidateNotNullOrEmpty()] 
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey 
         ) 
         
         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName 
         { 
             WindowsFeature DSCServiceFeature 
             { 
                 Ensure = 'Present'
                 Name   = 'DSC-Service'             
             } 

             xDscWebService PSDSCPullServer 
             { 
                 Ensure                   = 'Present' 
                 EndpointName             = 'PSDSCPullServer' 
                 Port                     = 8080 
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer" 
                 CertificateThumbPrint    = $certificateThumbPrint          
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration" 
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'     
                 UseSecurityBestPractices = $false
             } 

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }

    ```

1. <span data-ttu-id="b1387-130">구성을 실행합니다. 이때 SSL 인증서의 지문을 **certificateThumbPrint** 매개 변수로 전달하고 GUID 등록 키를 **RegistrationKey** 매개 변수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="b1387-131">등록 키</span><span class="sxs-lookup"><span data-stu-id="b1387-131">Registration Key</span></span>
<span data-ttu-id="b1387-132">구성 ID 대신 구성 이름을 사용할 수 있도록 클라이언트 노드가 서버에 등록할 수 있도록 하려면 위 구성에서 만든 등록 키가 `C:\Program Files\WindowsPowerShell\DscService`에서 `RegistrationKeys.txt`라는 파일에 저장되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="b1387-133">등록 키는 끌어오기 서버에 클라이언트를 처음 등록할 때 사용되는 공유 암호 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="b1387-134">클라이언트는 등록이 완료되면 끌어오기 서버에 고유하게 인증하는 데 사용되는 자체 서명된 인증서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="b1387-135">이 인증서의 지문은 로컬에 저장되고 끌어오기 서버의 URL과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="b1387-136">**참고**: PowerShell 4.0에서는 등록 키가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="b1387-137">끌어오기 서버에 인증하도록 노드를 구성하려면 이 끌어오기 서버에 등록할 모든 대상 노드의 메타 구성에 등록 키가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="b1387-138">아래 메타 구성에서 **RegistrationKey**는 대상 컴퓨터가 등록된 후 제거되며 '140a952b-b9d6-406b-b416-e0f759c9c0e4' 값은 끌어오기 서버의 RegistrationKeys.txt 파일에 저장된 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="b1387-139">등록 키 값을 알면 대상 컴퓨터가 끌어오기 서버에 등록할 수 있으므로 등록 키 값을 항상 안전하게 보관하세요.</span><span class="sxs-lookup"><span data-stu-id="b1387-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }
        
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }   
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> <span data-ttu-id="b1387-140">**참고**: **ReportServerWeb** 섹션을 사용하면 보고 데이터를 끌어오기 서버로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="b1387-141">메타 구성 파일에 **ConfigurationID** 속성이 없으면 끌어오기 서버가 V2 버전의 끌어오기 서버 프로토콜을 지원하므로 초기 등록이 필요하다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="b1387-142">반대로 **ConfigurationID**가 있으면 V1 버전의 끌어오기 서버 프로토콜이 사용되고 등록 처리가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="b1387-143">**참고**: 밀어넣기 시나리오에서 현재 릴리스에는 끌어오기 서버에 등록하지 않는 노드에 대한 ConfigurationID 속성을 메타 구성 파일에 정의해야 하는 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="b1387-144">따라서 V1 끌어오기 서버 프로토콜이 강제로 사용되고 등록 실패 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b1387-145">구성 및 리소스 배치</span><span class="sxs-lookup"><span data-stu-id="b1387-145">Placing configurations and resources</span></span>

<span data-ttu-id="b1387-146">끌어오기 서버 설정이 완료되면 끌어오기 서버 구성의 **ConfigurationPath** 및 **ModulePath** 속성에 정의된 폴더에 끌어올 대상 노드에 사용할 수 있는 모듈 및 구성을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="b1387-147">이러한 파일은 특정 형식이어야만 끌어오기 서버에서 올바로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="b1387-148">DSC 리소스 모듈 패키지 형식</span><span class="sxs-lookup"><span data-stu-id="b1387-148">DSC resource module package format</span></span>

<span data-ttu-id="b1387-149">각 리소스 모듈은 압축해야 하며 `{Module Name}_{Module Version}.zip` 패턴으로 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="b1387-150">예를 들어 모듈 버전이 3.1.2.0인 xWebAdminstration이라는 모듈은 'xWebAdministration_3.2.1.0.zip'으로 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="b1387-151">모듈의 각 버전은 단일 zip 파일에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="b1387-152">각 zip 파일에 리소스의 단일 버전만 있으므로 단일 디렉터리에서 여러 모듈 버전을 지원하는 WMF 5.0에서 추가된 모듈 형식은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="b1387-153">따라서 끌어오기 서버에서 사용할 DSC 리소스 모듈을 패키징하기 전에 디렉터리 구조를 약간 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="b1387-154">WMF 5.0에서 DSC 리소스를 포함하는 모듈의 기본 형식은 '{모듈 폴더}\{모듈 버전}\DscResources\{DSC 리소스 폴더}\'입니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="b1387-155">끌어오기 서버에 대해 패키징하기 전에 **{모듈 버전}** 폴더를 제거하면 되므로 폴더는 '{모듈 폴더}\DscResources\{DSC 리소스 폴더}\'가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="b1387-156">이렇게 변경하고 위에서 설명한 대로 폴더를 압축하여 이러한 zip 파일을 **ModulePath** 폴더에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="b1387-157">`new-dscchecksum {module zip file}`을 사용하여 새로 추가된 모듈에 대한 체크섬 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="b1387-158">구성 MOF 형식</span><span class="sxs-lookup"><span data-stu-id="b1387-158">Configuration MOF format</span></span> 
<span data-ttu-id="b1387-159">구성 MOF 파일은 대상 노드의 LCM이 구성에 대한 유효성을 검사할 수 있도록 체크섬 파일과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="b1387-160">체크섬을 만들려면 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="b1387-161">이 cmdlet은 구성 MOF가 있는 폴더를 지정하는 **Path** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="b1387-162">cmdlet은 `ConfigurationMOFName.mof.checksum`이라는 체크섬 파일을 만들며, 여기서 `ConfigurationMOFName`은 구성 mof 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="b1387-163">지정된 폴더에 구성 MOF 파일이 두 개 이상 있는 경우, 폴더에 있는 각 구성에 대해 체크섬이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="b1387-164">MOF 파일 및 연관된 체크섬 파일을 **ConfigurationPath** 폴더에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="b1387-165">**참고**: 어떤 식으로든 구성 MOF 파일을 변경하는 경우 체크섬 파일도 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="b1387-166">도구</span><span class="sxs-lookup"><span data-stu-id="b1387-166">Tooling</span></span>
<span data-ttu-id="b1387-167">끌어오기 서버를 더 간단히 설정하고 유효성을 검사하고 관리할 수 있도록 xPSDesiredStateConfiguration 모듈의 최신 버전에는 다음 도구가 예제로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="b1387-168">끌어오기 서버에서 사용할 DSC 리소스 모듈 및 구성 파일을 패키징하는 데 도움이 되는 모듈:</span><span class="sxs-lookup"><span data-stu-id="b1387-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="b1387-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="b1387-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="b1387-170">다음은 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="b1387-171">끌어오기 서버가 올바로 구성되었는지 확인하는 스크립트:</span><span class="sxs-lookup"><span data-stu-id="b1387-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="b1387-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="b1387-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="b1387-173">끌어오기 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="b1387-173">Pull client configuration</span></span> 
<span data-ttu-id="b1387-174">다음 항목에서는 끌어오기 클라이언트를 설정하는 것에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b1387-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="b1387-175">구성 ID를 사용하여 DSC 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="b1387-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="b1387-176">구성 이름을 사용하여 DSC 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="b1387-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="b1387-177">부분 구성</span><span class="sxs-lookup"><span data-stu-id="b1387-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="b1387-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1387-178">See also</span></span>
* [<span data-ttu-id="b1387-179">Windows PowerShell 필요한 상태 구성 개요</span><span class="sxs-lookup"><span data-stu-id="b1387-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="b1387-180">구성 시행</span><span class="sxs-lookup"><span data-stu-id="b1387-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="b1387-181">DSC 보고서 서버 사용</span><span class="sxs-lookup"><span data-stu-id="b1387-181">Using a DSC report server</span></span>](reportServer.md)

