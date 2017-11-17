---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="aeca7-103">PowerShell 갤러리 상태</span><span class="sxs-lookup"><span data-stu-id="aeca7-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="aeca7-104">2017/03/27 - 해결됨: 개별 모듈 및 스크립트 페이지를 볼 수 없음</span><span class="sxs-lookup"><span data-stu-id="aeca7-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="aeca7-105">__영향 요약__: https://www.powershellgallery.com에서 개별 모듈 및 스크립트 페이지로 연결되는 직접 링크가 끊어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="aeca7-106">이 문제는 모든 지역에서 보고되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-106">This was being reported across all the regions.</span></span> <span data-ttu-id="aeca7-107">이 문제는 Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt와 같은 PowerShellGet cmdlet이 계속 작동하는 데는 영향을 주지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="aeca7-108">__근본 원인__: 엔지니어들은 Facebook과 같은 소셜 미디어 단추를 페이지에 가져오는 과정에서 문제가 생긴 것을 알아냈습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="aeca7-109">__해결 방법__: 엔지니어가 Facebook 개수 정보를 사용하지 않도록 설정하여 문제를 해결했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="aeca7-110">__다음 단계__: Facebook API 사용 문제를 해결하기 위해 내부 추적 문제를 열었습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="aeca7-111">2016/12/15 - PowerShellGallery 웹 사이트를 통해 메일을 보낼 수 없음</span><span class="sxs-lookup"><span data-stu-id="aeca7-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="aeca7-112">__영향 요약__: 2016/12/13과 2016/12/15 사이에 소유자에게 문의, 소유자 관리, 고객 지원 또는 신고하기를 통해 전송된 모든 메시지는 PowerShell 갤러리 관리자가 받지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="aeca7-113">__근본 원인__: 엔지니어는 SMTP 서버와의 인증 문제를 원인으로 식별했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="aeca7-114">__해결 방법__: 엔지니어는 인증 문제를 해결하고 SMTP 서버에 대한 연결을 복원할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="aeca7-115">__다음 단계__: 이 시간 동안 소유자에게 문의, 소유자 관리, 고객 지원 또는 신고하기 링크를 사용하여 cgadmin@microsoft.com으로 메일을 보냈고 응답을 받지 못한 경우 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="aeca7-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="aeca7-116">불편을 드려 죄송합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="aeca7-117">2016년 8월 10일 - 해결됨: cgadmin@microsoft.com으로 메일을 보낼 수 없음</span><span class="sxs-lookup"><span data-stu-id="aeca7-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="aeca7-118">__영향 요약__: 2016년 8월 5일에서 2016년 8월 10일 사이 고객이 cgadmin@microsoft.com으로 메일을 보내거나 문의처 기능을 사용할 수 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="aeca7-119">__근본 원인__: 엔지니어가 원인을 메일 계정의 구성 변경으로 식별했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="aeca7-120">__해결 방법__: 엔지니어가 구성 문제를 해결하기 위해 노력했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="aeca7-121">__다음 단계__: 이 시간 동안 문의처 링크를 사용하거나 cgadmin@microsoft.com으로 메일을 보내고 응답을 받지 못한 경우 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="aeca7-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="aeca7-122">기다려 주셔서 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="aeca7-122">Thank you for your patience.</span></span>


