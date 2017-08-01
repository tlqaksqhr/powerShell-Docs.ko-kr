---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "JEA에 대한 보고"
ms.technology: powershell
ms.openlocfilehash: 3e7bd2755281f491bba8a905df018fb2e1cac6ff
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="reporting-on-jea"></a><span data-ttu-id="0477c-103">JEA에 대한 보고</span><span class="sxs-lookup"><span data-stu-id="0477c-103">Reporting on JEA</span></span>
<span data-ttu-id="0477c-104">JEA는 권한 없는 사용자가 권한 있는 컨텍스트에서 실행하도록 허용하기 때문에 로깅과 감사가 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-104">Because JEA allows non-privileged users to run in a privileged context, logging and auditing are extremely important.</span></span>
<span data-ttu-id="0477c-105">이 섹션에서는 로깅과 보고에 유용하게 사용할 수 있는 도구를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-105">In this section, we'll run through the tools you can use to help you with logging and reporting.</span></span>

## <a name="reporting-on-jea-actions"></a><span data-ttu-id="0477c-106">JEA 작업에 대한 보고</span><span class="sxs-lookup"><span data-stu-id="0477c-106">Reporting on JEA Actions</span></span>
### <a name="over-the-shoulder-transcription"></a><span data-ttu-id="0477c-107">Over-the-Shoulder 기록</span><span class="sxs-lookup"><span data-stu-id="0477c-107">Over-the-Shoulder Transcription</span></span>
<span data-ttu-id="0477c-108">PowerShell 세션에서 발생하고 있는 상황을 대략적으로 파악하는 가장 빠른 방법은 입력하는 사용자의 어깨너머로 보는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-108">One of the quickest ways to get a summary of what's happening in a PowerShell session is to look over the shoulder of the person typing.</span></span>
<span data-ttu-id="0477c-109">입력한 명령, 해당 명령의 출력 및 모두 정상인지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-109">You see their commands, the output of those commands, and all is well.</span></span>
<span data-ttu-id="0477c-110">정상이 아닌 경우에는 적어도 문제 상황을 알게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-110">Or it's not, but at least you'll know.</span></span>
<span data-ttu-id="0477c-111">PowerShell 기록은 사건 뒤에 유사한 보기를 제공하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-111">PowerShell transcription is designed to give you a similar view after the fact.</span></span>

<span data-ttu-id="0477c-112">세션 구성에서 "TranscriptDirectory" 필드를 사용할 때 PowerShell에서는 주어진 세션에서 수행된 모든 작업의 기록을 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-112">When using the "TranscriptDirectory" field in your Session Configuration, PowerShell will automatically record a transcript of all actions taken in a given session.</span></span>
<span data-ttu-id="0477c-113">이 문서의 세션에서는 "$env:ProgramData\JEAConfiguration\Transcripts"에서 기록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-113">You can find transcripts from your sessions in this document here: "$env:ProgramData\JEAConfiguration\Transcripts"</span></span>

<span data-ttu-id="0477c-114">기록에는 "연결된" 사용자, "실행" 사용자, 세션에서 실행된 명령 등에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-114">As you can tell, the transcript records information about the "Connected" user, the "Run As" user, the commands run in the session, and more.</span></span>
<span data-ttu-id="0477c-115">PowerShell 기록에 대한 자세한 내용은 [이 블로그 게시물](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0477c-115">For more information about PowerShell transcription, check out [this blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>

### <a name="powershell-event-logs"></a><span data-ttu-id="0477c-116">PowerShell 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="0477c-116">PowerShell Event Logs</span></span>
<span data-ttu-id="0477c-117">모듈 로깅을 켠 경우 모든 PowerShell 작업은 일반 Windows 이벤트 로그에도 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-117">When you have module logging turned on, all PowerShell actions are also recorded in regular Windows Event logs.</span></span>
<span data-ttu-id="0477c-118">이벤트 로그는 기록과 비교할 때 다루기가 약간 더 복잡하지만 제공하는 세부 정보의 수준은 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-118">This is slightly messier to deal with when compared to transcripts, but the level of detail it gives you can be useful.</span></span>

<span data-ttu-id="0477c-119">"PowerShell" 작업 로그에서 이벤트 ID 4104는 모듈 로깅을 사용하도록 설정한 경우 호출된 각 명령을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-119">In the "PowerShell" operational log, Event ID 4104 will record each command invoked if you have enabled module logging.</span></span>

### <a name="other-event-logs"></a><span data-ttu-id="0477c-120">기타 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="0477c-120">Other Event Logs</span></span>
<span data-ttu-id="0477c-121">PowerShell 로그 및 기록과 달리, 다른 로깅 메커니즘은 "연결된 사용자"를 캡처하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-121">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the "Connected User".</span></span>
<span data-ttu-id="0477c-122">수행된 작업을 맞춰보기 위해 다른 로그와 PowerShell 로그 간의 상관 관계를 파악해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-122">You will need to do some correlation between other logs and PowerShell logs to match up actions taken.</span></span>

<span data-ttu-id="0477c-123">"Windows 원격 관리" 작업 로그에서 이벤트 ID 193은 이 상관 관계 파악에 도움을 주기 위해 연결하는 사용자의 SID 및 이름뿐만 아니라 실행 가상 계정의 SID를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-123">In the "Windows Remote Management" operational log, Event ID 193 will record the Connecting User's SID and Name, as well as the RunAs Virtual Account's SID to assist with this correlation.</span></span>
<span data-ttu-id="0477c-124">또한 실행 가상 계정 이름의 끝에 연결하는 사용자의 도메인 및 사용자 이름이 포함되어 있음을 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-124">You may have also noticed that the name of the RunAs Virtual Account includes the connecting user's domain and username at the end.</span></span>

## <a name="reporting-on-jea-configuration"></a><span data-ttu-id="0477c-125">JEA 구성에 대한 보고</span><span class="sxs-lookup"><span data-stu-id="0477c-125">Reporting on JEA Configuration</span></span>
### <a name="get-pssessionconfiguration"></a><span data-ttu-id="0477c-126">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0477c-126">Get-PSSessionConfiguration</span></span>
<span data-ttu-id="0477c-127">사용자 환경의 상태에 대해 정확하게 보고하기 위해 컴퓨터에서 설정한 JEA 끝점 수를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-127">In order to accurately report on the state of your environment, it's important to know how many JEA endpoints you have set up on your machine.</span></span>
<span data-ttu-id="0477c-128">`Get-PSSessionConfiguration`은 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-128">`Get-PSSessionConfiguration` does just that.</span></span>

### <a name="get-pssessioncapability"></a><span data-ttu-id="0477c-129">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="0477c-129">Get-PSSessionCapability</span></span>
<span data-ttu-id="0477c-130">JEA 끝점을 통한 지정된 사용자의 기능에 대해 수동으로 보고하는 것은 꽤 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-130">Manually reporting on the capabilities of any given user through a JEA endpoint can be quite complex.</span></span>
<span data-ttu-id="0477c-131">몇 가지 역할 기능을 검사해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-131">You would potentially need to inspect several role capabilities.</span></span>
<span data-ttu-id="0477c-132">다행히도 "Get-PSSessionCapability" cmdlet이 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-132">Fortunately, the "Get-PSSessionCapability" cmdlet does this.</span></span>

<span data-ttu-id="0477c-133">이를 테스트하려면 관리자 PowerShell 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0477c-133">To test this out, run the following command from an administrator PowerShell prompt:</span></span>
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```

