---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: 8c325ce1c665181cff646eef6c5e7d55e9081e5e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="5bab9-103">PowerShell 갤러리 상태</span><span class="sxs-lookup"><span data-stu-id="5bab9-103">PowerShell Gallery Status</span></span>
=========================
## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="5bab9-104">2017년 6월 1일 - 현재 Azure Automation으로의 배포 사용 불가</span><span class="sxs-lookup"><span data-stu-id="5bab9-104">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="5bab9-105">__영향 요약__: Azure Automation에 대한 종속성이 포함된 항목을 현재 PowerShell 갤러리에서 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-105">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="5bab9-106">Azure Automation 내에서 PowerShell 갤러리의 항목을 가져오는 작업은 계속 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-106">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="5bab9-107">__근본 원인__: 다른 항목에 대한 종속성을 포함하며 이전에 Azure Automation에 배포했던 항목은 Azure Automation으로 배포되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-107">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="5bab9-108">Azure Automation으로 배포 기능용으로 종속성이 포함된 항목에 대해 ARM 템플릿이 생성되는 방식에서 문제가 확인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-108">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="5bab9-109">__해결 방법__: 현재 엔지니어들이 문제 해결을 위한 작업을 진행하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-109">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="5bab9-110">사용자가 현재 사용 가능한 해결 방법은 Azure Automation 내에서 PowerShell 갤러리의 항목을 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-110">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="5bab9-111">__다음 단계__: 조만간 픽스가 공개될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-111">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="5bab9-112">일단은 권장 해결 방법을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5bab9-112">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="5bab9-113">2017/04/11 - 사용자가 AAD(Azure Active Directory) 계정으로 로그인할 수 없음</span><span class="sxs-lookup"><span data-stu-id="5bab9-113">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="5bab9-114">__영향 요약__: 일부 사용자가 Azure AD 계정을 사용하여 PowerShell 갤러리에 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-114">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="5bab9-115">__근본 원인__: AAD와 보다 안전하게 상호 작용하도록 업데이트하는 동안 설정 변경이 누락되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-115">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="5bab9-116">변경 내용의 유효성을 검사하기 위해 수행한 테스트에 특정 유형의 AAD 계정이 포함되지 않았으며, 배포가 진행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-116">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="5bab9-117">__해결 방법__: 엔지니어가 누락된 설정을 확인하고 문제를 해결했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-117">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="5bab9-118">__다음 단계__: 광범위한 AAD 계정 유형 집합을 포함하도록 테스트를 수정할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-118">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="5bab9-119">2017/03/27 - 해결됨: 개별 모듈 및 스크립트 페이지를 볼 수 없음</span><span class="sxs-lookup"><span data-stu-id="5bab9-119">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="5bab9-120">__영향 요약__: https://www.powershellgallery.com에서 개별 모듈 및 스크립트 페이지로 연결되는 직접 링크가 끊어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-120">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="5bab9-121">이 문제는 모든 지역에서 보고되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-121">This was being reported across all the regions.</span></span> <span data-ttu-id="5bab9-122">이 문제는 Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt와 같은 PowerShellGet cmdlet이 계속 작동하는 데는 영향을 주지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-122">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="5bab9-123">__근본 원인__: 엔지니어들은 Facebook과 같은 소셜 미디어 단추를 페이지에 가져오는 과정에서 문제가 생긴 것을 알아냈습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-123">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="5bab9-124">__해결 방법__: 엔지니어가 Facebook 개수 정보를 사용하지 않도록 설정하여 문제를 해결했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-124">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="5bab9-125">__다음 단계__: Facebook API 사용 문제를 해결하기 위해 내부 추적 문제를 열었습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-125">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="5bab9-126">2016/12/15 - PowerShellGallery 웹 사이트를 통해 메일을 보낼 수 없음</span><span class="sxs-lookup"><span data-stu-id="5bab9-126">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="5bab9-127">__영향 요약__: 2016/12/13과 2016/12/15 사이에 소유자에게 문의, 소유자 관리, 고객 지원 또는 신고하기를 통해 전송된 모든 메시지는 PowerShell 갤러리 관리자가 받지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-127">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="5bab9-128">__근본 원인__: 엔지니어는 SMTP 서버와의 인증 문제를 원인으로 식별했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-128">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="5bab9-129">__해결 방법__: 엔지니어는 인증 문제를 해결하고 SMTP 서버에 대한 연결을 복원할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-129">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="5bab9-130">__다음 단계__: 이 시간 동안 소유자에게 문의, 소유자 관리, 고객 지원 또는 신고하기 링크를 사용하여 cgadmin@microsoft.com으로 메일을 보냈고 응답을 받지 못한 경우 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="5bab9-130">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="5bab9-131">불편을 드려 죄송합니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-131">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="5bab9-132">2016년 8월 10일 - 해결됨: cgadmin@microsoft.com으로 메일을 보낼 수 없음</span><span class="sxs-lookup"><span data-stu-id="5bab9-132">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="5bab9-133">__영향 요약__: 2016년 8월 5일에서 2016년 8월 10일 사이 고객이 cgadmin@microsoft.com으로 메일을 보내거나 문의처 기능을 사용할 수 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-133">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="5bab9-134">__근본 원인__: 엔지니어가 원인을 메일 계정의 구성 변경으로 식별했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-134">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="5bab9-135">__해결 방법__: 엔지니어가 구성 문제를 해결하기 위해 노력했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-135">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="5bab9-136">__다음 단계__: 이 시간 동안 문의처 링크를 사용하거나 cgadmin@microsoft.com으로 메일을 보내고 응답을 받지 못한 경우 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="5bab9-136">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="5bab9-137">기다려 주셔서 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-137">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="5bab9-138">2016년 7월 13일 - 항목 다운로드 실패</span><span class="sxs-lookup"><span data-stu-id="5bab9-138">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="5bab9-139">__영향 요약__: 2016년 7월 11일에서 2016년 7월 13일 사이 일부 고객이 PowerShell 갤러리에서 항목을 다운로드할 때 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-139">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="5bab9-140">문제는 Install-Module/Install-Script 및 Save-Module/Save-Script에서 반환된 다음 오류 메시지에서 명확해졌습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-140">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="5bab9-141">__임시 근본 원인__: 엔지니어가 2016년 7월 11일 PowerShell 갤러리에 배포된 Azure CDN(콘텐츠 배달 네트워크)에서 문제를 식별했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-141">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="5bab9-142">__해결 방법__: 엔지니어가 PowerShell 갤러리에서 Azure CDN을 사용하지 않도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-142">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="5bab9-143">__다음 단계__: 근본 원인을 조사하고 이후에 다시 발생하지 않도록 해결 방법을 개발하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-143">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="5bab9-144">2016년 5월 19일 - 항목 다운로드 실패</span><span class="sxs-lookup"><span data-stu-id="5bab9-144">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="5bab9-145">__영향 요약__: 2016년 5월 17일에서 2016년 5월 19일 사이 일부 고객이 PowerShell 갤러리에서 항목을 다운로드할 때 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-145">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="5bab9-146">문제는 Install-Module/Install-Script 및 Save-Module/Save-Script에서 반환된 다음 오류 메시지에서 명확해졌습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-146">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```PowerShell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="5bab9-147">__임시 근본 원인__: 엔지니어가 2016년 5월 17일 PowerShell 갤러리에 배포된 Azure CDN(콘텐츠 배달 네트워크)의 기본 공급자에서 중단을 식별했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-147">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="5bab9-148">__해결 방법__: 엔지니어가 PowerShell 갤러리에서 Azure CDN을 사용하지 않도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-148">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="5bab9-149">__다음 단계__: 근본 원인을 조사하고 이후에 다시 발생하지 않도록 해결 방법을 개발하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bab9-149">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

