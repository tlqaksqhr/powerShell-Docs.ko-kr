# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="65331-101">PowerShell Core 지원 수명 주기</span><span class="sxs-lookup"><span data-stu-id="65331-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="65331-102">PowerShell Core는 Windows PowerShell과 별개로 제공, 설치 및 구성되는 도구 및 구성 요소의 고유 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="65331-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="65331-103">따라서 PowerShell Core는 Windows 7/8.1/10 또는 Windows Server 라이선싱 계약에 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="65331-104">그러나 PowerShell Core는 [프리미어][], [Microsoft 기업 계약][enterprise-agreement] 및 [Microsoft 소프트웨어 보증][assurance]을 포함한 기존의 Microsoft 지원 계약에서 지원받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="65331-105">또한, 문제가 있는 경우 지원 요청서를 작성하여 PowerShell Core에 대한 [보조 지원][]을 유료로 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="65331-106">또한 GitHub에 대한 [커뮤니티 지원][]도 제공하여 문제, 버그 또는 기능 요청을 취합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="65331-107">또는, [Microsoft 커뮤니티][] 또는 Microsoft [PowerShell 기술 커뮤니티][]와 같은 일반적인 커뮤니티에서 다양한 구성원들에게 도움을 받을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="65331-108">단, 문제가 제때 해결된다는 보장은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="65331-109">긴급하게 도움이 필요한 문제가 있는 경우 기존의 유료 지원 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="65331-110">PowerShell Core의 수명 주기</span><span class="sxs-lookup"><span data-stu-id="65331-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="65331-111">PowerShell Core는 [Microsoft 최신 수명 주기 정책][modern]을 채택합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="65331-112">이 지원 수명 주기는 고객이 항상 최신 버전을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="65331-113">약 6개월 단위로 PowerShell Core의 6.x 버전이 분기별로 업데이트 됩니다(예: 6.0, 6.1, 6.2 등).</span><span class="sxs-lookup"><span data-stu-id="65331-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65331-114">지원을 계속 받으려면 부 버전이 새로 릴리스될 때마다 6개월 이내에 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="65331-115">예를 들어 PowerShell Core 6.1이 2018년 7월 1일에 릴리스 되고, 계속해서 지원을 받고자 하는 경우 2019년 1월 1일까지 PowerShell Core 6.1로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core 분기 수명 주기][lifecycle-chart]

<span data-ttu-id="65331-117">최신 수명 주기 정책에 따라 Microsoft는 해당 제품(예: PowerShell Core)에 대한 지원을 중단하기 12개월 전에 고객 측에 공지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="65331-118">즉, PowerShell Core는 "장기 서비스"를 채택하여 6.x의 특정 분기/버전에 대한 지속적인 지원을 위해 서비스 및 보안 업데이트를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="65331-119">지원되는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="65331-119">Supported platforms</span></span>

<span data-ttu-id="65331-120">PowerShell Core는 공식적으로 다음 플랫폼에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="65331-121">Windows 7, 8.1 및 10</span><span class="sxs-lookup"><span data-stu-id="65331-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="65331-122">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="65331-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="65331-123">[Windows 서버 반기 채널][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="65331-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="65331-124">Ubuntu 14.04, 16.04, 17.04</span><span class="sxs-lookup"><span data-stu-id="65331-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="65331-125">Debian 8.7+, 9</span><span class="sxs-lookup"><span data-stu-id="65331-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="65331-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="65331-126">CentOS 7</span></span>
* <span data-ttu-id="65331-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="65331-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="65331-128">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="65331-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="65331-129">Fedora 27, 28</span><span class="sxs-lookup"><span data-stu-id="65331-129">Fedora 27, 28</span></span>
* <span data-ttu-id="65331-130">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="65331-130">macOS 10.12+</span></span>

<span data-ttu-id="65331-131">또한 커뮤니티에서 다음 플랫폼과 관련한 패키지를 제공하였으나 공식적으로 지원되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="65331-132">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="65331-132">Arch Linux</span></span>
* <span data-ttu-id="65331-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="65331-133">Kali Linux</span></span>
* <span data-ttu-id="65331-134">AppImage(여러 Linux 플랫폼에서 사용)</span><span class="sxs-lookup"><span data-stu-id="65331-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="65331-135">라이선싱에 대한 메모</span><span class="sxs-lookup"><span data-stu-id="65331-135">Notes on licensing</span></span>

<span data-ttu-id="65331-136">PowerShell Core는 [MIT 라이선스][]에서 릴리스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65331-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="65331-137">본 라이선스 및 유료 지원 계약이 안 된 경우 사용자는 [커뮤니티 지원][]으로 서비스가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="65331-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="65331-138">커뮤니티 지원을 이용하더라도 Microsoft는 문의 응답 및 해결 방안을 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="65331-139">Windows PowerShell 모듈</span><span class="sxs-lookup"><span data-stu-id="65331-139">Windows PowerShell Module</span></span>

<span data-ttu-id="65331-140">PowerShell Core에 대한 지원은 명시적으로 이 모듈이 PowerShell Core를 지원하지 않는 한 다른 제품 모듈로 확장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="65331-141">예를 들어, Windows Server에 부분적으로 제공되는 `ActiveDirectory` 모듈을 사용하는 경우 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="65331-142">그러나 PowerShell Core를 명시적으로 지원하지 않는 모듈은 경우에 따라 호환이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="65331-143">[`WindowsPSModulePath`][] 모듈을 설치하여 Windows PowerShell `PSModulePath` 를 PowerShell Core `PSModulePath`로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65331-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="65331-144">먼저, PowerShell 갤러리에서 `WindowsPSModulePath` 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="65331-145">이 모듈을 설치한 후에, `Add-WindowsPSModulePath` cmdlet을 실행하여 Windows PowerShell `PSModulePath`를 PowerShell Core에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="65331-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[프리미어]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[커뮤니티 지원]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft 커뮤니티]: https://answers.microsoft.com/
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell 기술 커뮤니티]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[보조 지원]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 라이선스]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
