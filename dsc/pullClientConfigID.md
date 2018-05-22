---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 ID를 사용하여 끌어오기 클라이언트 설정
ms.openlocfilehash: b4a45c4d014b3c4fc0140ad492f81474b260065a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="a8cd2-103">구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="a8cd2-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="a8cd2-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a8cd2-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8cd2-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a8cd2-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a8cd2-107">각 대상 노드는 끌어오기 모드를 사용하도록 지시 받고 끌어오기 서버에 연결하여 구성을 가져올 수 있는 URL을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="a8cd2-108">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="a8cd2-109">LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="a8cd2-110">LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](metaConfig.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="a8cd2-111">**참고**: 이 항목은 PowerShell 5.0에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-111">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="a8cd2-112">PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 것에 대해서는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="a8cd2-113">다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="a8cd2-114">스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="a8cd2-115">**ServerURL**</span><span class="sxs-lookup"><span data-stu-id="a8cd2-115">The **ServerURL**</span></span>

<span data-ttu-id="a8cd2-116">이 스크립트가 실행되면, **PullClientConfigID**라는 새 출력 폴더가 생성되고, 그 안에 메타 구성 MOF 파일이 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-116">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="a8cd2-117">이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-117">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="a8cd2-118">구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-118">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="a8cd2-119">예를 들면 다음과 같습니다. `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="a8cd2-119">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="a8cd2-120">구성 ID</span><span class="sxs-lookup"><span data-stu-id="a8cd2-120">Configuration ID</span></span>

<span data-ttu-id="a8cd2-121">스크립트는 이전에 이 목적으로 만들어진 GUID에 LCM의 **ConfigurationID** 속성을 설정합니다(**New-Guid** cmdlet을 사용하여 GUID를 만들 수 있음).</span><span class="sxs-lookup"><span data-stu-id="a8cd2-121">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="a8cd2-122">**ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-122">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="a8cd2-123">끌어오기 서버의 구성 MOF 파일의 이름은 _ConfigurationID_.mof로 지정해야 합니다. 여기서 _ConfigurationID_는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-123">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="a8cd2-124">SMB 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="a8cd2-124">SMB pull server</span></span>

<span data-ttu-id="a8cd2-125">SMB 서버에서 구성을 끌어오도록 클라이언트를 설정하려면, **ConfigurationRepositoryShare** 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-125">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="a8cd2-126">**ConfigurationRepositoryShare** 블록에서 **SourcePath** 속성을 설정하여 서버 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-126">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="a8cd2-127">다음 메타 구성은 **SMBPullServer**라는 SMB 끌어오기 서버에서 끌어오도록 대상 노드를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-127">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="a8cd2-128">리소스 및 보고서 서버</span><span class="sxs-lookup"><span data-stu-id="a8cd2-128">Resource and report servers</span></span>

<span data-ttu-id="a8cd2-129">앞의 예와 같이 LCM 구성에서 **ConfigurationRepositoryWeb** 또는 **ConfigurationRepositoryShare** 블록만 지정하는 경우 끌어오기 클라이언트가 지정된 서버에서 리소스를 끌어오지만 서버에 보고서를 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="a8cd2-130">구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있지만 **ReportRepositoryWeb** 블록을 만들어 보고를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

<span data-ttu-id="a8cd2-131">다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }


        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="a8cd2-132">또한, 리소스 및 보고에 대해 다른 끌어오기 서버를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-132">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="a8cd2-133">리소스 서버를 지정하려면, **ResourceRepositoryWeb**(웹 끌어오기 서버용) 및 **ResourceRepositoryShare**(SMB 끌어오기 서버용) 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="a8cd2-134">보고서 서버를 지정하려면 **ReportRepositoryWeb** 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="a8cd2-135">보고서 서버는 SMB 서버일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="a8cd2-136">해당 메타 구성은 **CONTOSO-PullSrv**에서 구성을 가져오고 **CONTOSO-ResourceSrv**에서 리소스를 가져오고, **CONTOSO-ReportSrv**에 상태 보고서를 보내도록 끌어오기 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a8cd2-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a><span data-ttu-id="a8cd2-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8cd2-137">See Also</span></span>

* [<span data-ttu-id="a8cd2-138">Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)</span><span class="sxs-lookup"><span data-stu-id="a8cd2-138">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)