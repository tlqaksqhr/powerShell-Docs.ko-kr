---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: 끌어오기 서버에서 노드 정보를 쿼리하는 DSC 함수
ms.openlocfilehash: 5c10eefe9ded4fe6339c4e6252cc189bcd793978
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a><span data-ttu-id="bfe35-103">끌어오기 서버에서 노드 정보를 쿼리하는 DSC 함수</span><span class="sxs-lookup"><span data-stu-id="bfe35-103">DSC function to query node information from pull server.</span></span>

```powershell
function QueryNodeInformation
{
Param (
       [string] $Uri =
"http://localhost:7070/PSDSCComplianceServer.svc/Status",
       [string] $ContentType = "application/json"
     )

  Write-Host "Querying node information from pull server URI  = $Uri" -ForegroundColor Green

  Write-Host "Querying node status in content type  = $ContentType " -ForegroundColor Green

   $response = Invoke-WebRequest -Uri $Uri -Method Get -ContentType $ContentType -UseDefaultCredentials -Headers
    @{Accept = $ContentType}

   if($response.StatusCode -ne 200)
 {
     Write-Host "node information was not retrieved." -ForegroundColor Red
 }

 $jsonResponse = ConvertFrom-Json $response.Content

  return $jsonResponse
}
```

<span data-ttu-id="bfe35-104">`Uri` 매개 변수를 끌어오기 서버에 대한 URI로 바꾸세요.</span><span class="sxs-lookup"><span data-stu-id="bfe35-104">Replace the `Uri` parameter with the URI for your pull server.</span></span> <span data-ttu-id="bfe35-105">XML 형식의 노드 정보가 필요할 경우, `ContentType`을 `application/xml`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bfe35-105">If you want the node information in XML format, set `ContentType` to `application/xml`.</span></span>

<span data-ttu-id="bfe35-106">`$json` 매개 변수에서 노드 정보를 검색하려면 다음을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="bfe35-106">To retrieve the node information from the `$json` parameter, use the following:</span></span>

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```