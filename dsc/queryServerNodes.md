---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "끌어오기 서버에서 노드 정보를 쿼리하는 DSC 함수"
ms.openlocfilehash: f97e1d62873fb9e23147ff137468a767455cd82c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a><span data-ttu-id="2e4e4-103">끌어오기 서버에서 노드 정보를 쿼리하는 DSC 함수</span><span class="sxs-lookup"><span data-stu-id="2e4e4-103">DSC function to query node information from pull server.</span></span>

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

<span data-ttu-id="2e4e4-104">`Uri` 매개 변수를 끌어오기 서버에 대한 URI로 바꾸세요.</span><span class="sxs-lookup"><span data-stu-id="2e4e4-104">Replace the `Uri` parameter with the URI for your pull server.</span></span> <span data-ttu-id="2e4e4-105">XML 형식의 노드 정보가 필요할 경우, `ContentType`을 `application/xml`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e4e4-105">If you want the node information in XML format, set `ContentType` to `application/xml`.</span></span>

<span data-ttu-id="2e4e4-106">`$json` 매개 변수에서 노드 정보를 검색하려면 다음을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="2e4e4-106">To retrieve the node information from the `$json` parameter, use the following:</span></span>

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status 

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```

