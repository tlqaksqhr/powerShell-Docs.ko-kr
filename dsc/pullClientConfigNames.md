---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "구성 이름을 사용하여 끌어오기 클라이언트 설정"
ms.openlocfilehash: 9bfcac87300d30a59b66e60ed24add32e2420e21
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="26bef-103">구성 이름을 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="26bef-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="26bef-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="26bef-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="26bef-105">각 대상 노드는 끌어오기 모드를 사용하도록 지시 받고 끌어오기 서버에 연결하여 구성을 가져올 수 있는 URL을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="26bef-106">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="26bef-107">LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="26bef-108">LCM을 구성에 대한 자세한 내용은 [LCM(로컬 구성 관리자) 구성](metaConfig.md)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="26bef-109">**참고**: 이 항목은 PowerShell 5.0에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="26bef-110">PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 것에 대해서는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26bef-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="26bef-111">다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="26bef-112">스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="26bef-113">**ServerURL** 속성은 끌어오기 서버에 대한 끝점을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="26bef-114">**RegistrationKey** 속성은 끌어오기 서버에 대한 모든 클라이언트 노드와 해당 끌어오기 서버 간의 공유 키입니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="26bef-115">동일한 값이 끌어오기 서버에 있는 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="26bef-116">**ConfigurationNames** 속성은 클라이언트 노드용으로 의도된 구성의 이름을 지정하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="26bef-117">끌어오기 서버에서 이 클라이언트 노드에 대한 구성 MOF 파일의 이름은 *ConfigurationNames*.mof로 지정해야 하며, 여기서 *ConfigurationNames*는 이 메타 구성에서 설정한 **ConfigurationNames** 속성의 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="26bef-118">**참고:** **ConfigurationNames**에 둘 이상의 값을 지정하는 경우 구성에서 **PartialConfiguration** 블록도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="26bef-119">부분 구성에 대한 자세한 내용은 [PowerShell 필요한 상태 구성 부분 구성](partialConfigs.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26bef-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="26bef-120">이 스크립트가 실행되면, **PullClientConfigNames**라는 새 출력 폴더가 생성되고, 그 안에 메타 구성 MOF 파일이 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="26bef-121">이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="26bef-122">구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="26bef-123">**참고**: 등록 키는 웹 끌어오기 서버에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="26bef-124">SMB 끌어오기 서버에는 여전히 **ConfigurationID**를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="26bef-125">**ConfigurationID**를 사용하여 끌어오기 서버를 구성하는 것에 대해서는 [구성 ID를 사용하여 끌어오기 클라이언트 설정](PullClientConfigNames.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26bef-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="26bef-126">리소스 및 보고서 서버</span><span class="sxs-lookup"><span data-stu-id="26bef-126">Resource and report servers</span></span>

<span data-ttu-id="26bef-127">앞의 예와 같이 LCM 구성에서 **ConfigurationRepositoryWeb** 또는 **ConfigurationRepositoryShare** 블록만 지정하는 경우 끌어오기 클라이언트가 지정된 서버에서 리소스를 끌어오지만 서버에 보고서를 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="26bef-128">구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있지만 **ReportRepositoryWeb** 블록을 만들어 보고를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="26bef-129">다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="26bef-130">또한, 리소스 및 보고에 대해 다른 끌어오기 서버를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="26bef-131">리소스 서버를 지정하려면, **ResourceRepositoryWeb**(웹 끌어오기 서버용) 및 **ResourceRepositoryShare**(SMB 끌어오기 서버용) 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="26bef-132">보고서 서버를 지정하려면 **ReportRepositoryWeb** 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="26bef-133">보고서 서버는 SMB 서버일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="26bef-134">해당 메타 구성은 **CONTOSO-PullSrv**에서 구성을 가져오고 **CONTOSO-ResourceSrv**에서 리소스를 가져오고, **CONTOSO-ReportSrv**에 상태 보고서를 보내도록 끌어오기 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="26bef-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="26bef-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26bef-135">See Also</span></span>

* [<span data-ttu-id="26bef-136">구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="26bef-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="26bef-137">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="26bef-137">Setting up a DSC web pull server</span></span>](pullServer.md)

