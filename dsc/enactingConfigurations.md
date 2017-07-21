---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "구성 시행"
ms.openlocfilehash: db82788650186eb82f67b30b24cd45b719bbe314
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="enacting-configurations"></a><span data-ttu-id="31e2d-103">구성 시행</span><span class="sxs-lookup"><span data-stu-id="31e2d-103">Enacting configurations</span></span>

><span data-ttu-id="31e2d-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="31e2d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="31e2d-105">PowerShell DSC(필요한 상태 구성) 구성을 시행하는 방법에는 밀어넣기 모드와 끌어오기 모드, 이렇게 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="31e2d-106">밀어넣기 모드</span><span class="sxs-lookup"><span data-stu-id="31e2d-106">Push mode</span></span>

<span data-ttu-id="31e2d-107">![밀어넣기 모드](images/Push.png "밀어넣기 모드 작동 방식")</span><span class="sxs-lookup"><span data-stu-id="31e2d-107">![Push mode](images/Push.png "How push mode works")</span></span>

<span data-ttu-id="31e2d-108">밀어넣기 모드는 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하여 대상 노드에 구성을 적극적으로 적용하는 사용자를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="31e2d-109">구성을 만들고 컴파일한 후에는 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하고 cmdlet의 -Path 매개 변수를 구성 MOF가 있는 경로로 설정하여 밀어넣기 모드에서 구성을 시행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span> <span data-ttu-id="31e2d-110">예를 들어 구성 MOF가 `C:\DSC\Configurations\localhost.mof`에 있으면, 다음 명령을 사용하여 로컬 컴퓨터에 적용합니다.`Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="31e2d-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="31e2d-111">__참고__: 기본적으로 DSC는 구성을 백그라운드 작업으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="31e2d-112">구성을 대화형으로 실행하려면 __-Wait__ 매개 변수로 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx)을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>


## <a name="pull-mode"></a><span data-ttu-id="31e2d-113">끌어오기 모드</span><span class="sxs-lookup"><span data-stu-id="31e2d-113">Pull mode</span></span>

<span data-ttu-id="31e2d-114">![끌어오기 모드](images/Pull.png "끌어오기 모드 작동 방식")</span><span class="sxs-lookup"><span data-stu-id="31e2d-114">![Pull Mode](images/Pull.png "How pull mode works")</span></span>

<span data-ttu-id="31e2d-115">끌어오기 모드에서는 끌어오기 클라이언트가 해당 클라이언트의 필요한 상태 구성을 원격 끌어오기 서버에서 가져오도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull server.</span></span> <span data-ttu-id="31e2d-116">마찬가지로, 끌어오기 서버는 DSC 서비스를 호스트하도록 설정되었으며 끌어오기 클라이언트에 필요한 구성과 리소스로 프로비전되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-116">Likewise, the pull server has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span> <span data-ttu-id="31e2d-117">각 끌어오기 클라이언트에는 노드의 구성에 대해 주기적인 준수 확인을 수행하는 예약된 작업이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-117">Each one of the pull clients has a scheduled task that performs a periodic compliance check on the configuration of the node.</span></span> <span data-ttu-id="31e2d-118">이벤트가 처음으로 트리거되면 끌어오기 클라이언트의 LCM(로컬 구성 관리자)이 LCM에 지정된 구성을 가져오기 위해 끌어오기 서버에 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-118">When the event is triggered the first time, it the Local Configuration Manager (LCM) on the pull client makes a request to the pull server to get the configuration specified in the LCM.</span></span> <span data-ttu-id="31e2d-119">해당 구성이 끌어오기 서버에 존재하고 초기 유효성 검사를 통과하면 이 구성은 끌어오기 클라이언트로 전송된 후 여기에서 LCM에 의해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-119">If that configuration exists on the pull server, and it passes initial validation checks, the configuration is transmitted to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="31e2d-120">LCM은 LCM의 **ConfigurationModeFrequencyMins** 속성으로 지정된 정기적인 간격에 따라 클라이언트가 구성을 준수하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="31e2d-121">LCM은 LCM의 **RefreshModeFrequency** 속성으로 지정된 정기적인 간격에 따라 끌어오기 서버의 업데이트된 구성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-121">The LCM checks for updated configurations on the pull server at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span> <span data-ttu-id="31e2d-122">LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](metaConfig.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31e2d-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="31e2d-123">DSC 끌어오기 서버 설정에 대한 자세한 내용은 [DSC 웹 끌어오기 서버 설정](pullServer.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31e2d-123">For more information on setting up a DSC Pull Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="31e2d-124">온라인 서비스를 활용하여 끌어오기 서버 기능을 호스트하려는 경우에는 [Azure 자동화 DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31e2d-124">If you would prefer to take advantage of an online service to host Pull Server functionality, see the [Azure Automation DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) service.</span></span>

<span data-ttu-id="31e2d-125">다음 항목에서는 끌어오기 서버 및 클라이언트를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="31e2d-125">The following topics explain how to set up pull servers and clients:</span></span>

- [<span data-ttu-id="31e2d-126">웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="31e2d-126">Setting up a web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="31e2d-127">Setting up an SMB pull server(SMB 끌어오기 서버 설정)</span><span class="sxs-lookup"><span data-stu-id="31e2d-127">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="31e2d-128">Configuring a pull client(끌어오기 클라이언트 구성)</span><span class="sxs-lookup"><span data-stu-id="31e2d-128">Configuring a pull client</span></span>](pullClientConfigID.md)

