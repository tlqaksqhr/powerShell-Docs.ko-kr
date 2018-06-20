---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: cmdlet 문제 해결
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219830"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="a8b5d-103">cmdlet 문제 해결</span><span class="sxs-lookup"><span data-stu-id="a8b5d-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="a8b5d-104">"경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법</span><span class="sxs-lookup"><span data-stu-id="a8b5d-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="a8b5d-105">Install-Module 또는 Update-Module이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5d-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="a8b5d-106">조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5d-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="a8b5d-107">최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5d-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="a8b5d-108">아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5d-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="a8b5d-109">아래에서는 'Azure' 모듈을 예로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5d-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```