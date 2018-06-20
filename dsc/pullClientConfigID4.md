---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187769"
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="45eb9-103">PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="45eb9-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="45eb9-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="45eb9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="45eb9-105">각 대상 노드는 끌어오기 모드를 사용하도록 지시 받고 끌어오기 서버에 연결하여 구성을 가져올 수 있는 URL을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="45eb9-106">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="45eb9-107">LCM을 구성하려면 "메타 구성"으로 알려진 특수한 형식의 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="45eb9-108">LCM 구성에 대한 자세한 내용은 [Windows PowerShell 4.0 필요한 상태 구성 로컬 구성 관리자](metaConfig4.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45eb9-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="45eb9-109">다음 스크립트는 "PullServer"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="45eb9-110">스크립트에서 **DownloadManagerCustomData**는 끌어오기 서버의 URL을 전달하고, (이 예제의 경우) 보안되지 않은 연결을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span>

<span data-ttu-id="45eb9-111">이 스크립트가 실행되면, **SimpleMetaConfigurationForPull**이라는 새 출력 폴더가 생성되고, 그 안에 메타 구성 MOF 파일이 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="45eb9-112">구성을 적용하려면 **ComputerName**("localhost" 사용) 및 **Path**(대상 노드의 localhost.meta.mof 파일의 위치 경로)에 대한 매개 변수와 함께 **Set-DscLocalConfigurationManager**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="45eb9-113">예:</span><span class="sxs-lookup"><span data-stu-id="45eb9-113">For example:</span></span>
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="45eb9-114">구성 ID</span><span class="sxs-lookup"><span data-stu-id="45eb9-114">Configuration ID</span></span>
<span data-ttu-id="45eb9-115">스크립트는 이전에 이 목적으로 만들어진 GUID에 LCM의 **ConfigurationID** 속성을 설정합니다(**New-Guid** cmdlet을 사용하여 GUID를 만들 수 있음).</span><span class="sxs-lookup"><span data-stu-id="45eb9-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="45eb9-116">**ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="45eb9-117">끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="45eb9-118">SMB 서버에서 끌어오기</span><span class="sxs-lookup"><span data-stu-id="45eb9-118">Pulling from an SMB server</span></span>

<span data-ttu-id="45eb9-119">끌어오기 서버가 웹 서비스가 아닌 SMB 파일 공유로 설정된 경우 **WebDownLoadManager** 대신 **DscFileDownloadManager**를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="45eb9-120">**DscFileDownloadManager**는 **ServerUrl** 대신 **SourcePath** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="45eb9-121">다음 스크립트는 "CONTOSO-SERVER"라는 서버에서 "SmbDscShare"라는 SMB 공유의 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="45eb9-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="45eb9-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45eb9-122">See Also</span></span>

- [<span data-ttu-id="45eb9-123">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="45eb9-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="45eb9-124">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="45eb9-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)