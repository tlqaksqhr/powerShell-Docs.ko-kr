---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: f3c218fc668e35fa50047459d8031d77cdf985a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
# <a name="reporting-on-jea"></a><span data-ttu-id="eb4db-102">JEA에 대한 보고</span><span class="sxs-lookup"><span data-stu-id="eb4db-102">Reporting on JEA</span></span>
<span data-ttu-id="eb4db-103">JEA 구성의 상태를 보고하려면 다음을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb4db-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="eb4db-104">**Get-PSSessionConfiguration** - 지정된 컴퓨터에서 등록된 모든 끝점 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4db-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="eb4db-105">**Get-PSSessionCapability** - 특정 끝점에 대해 지정된 사용자에게 제공되는 기능을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4db-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="eb4db-106">다음은 **Get-PSSessionCapability**의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="eb4db-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

<span data-ttu-id="eb4db-107">JEA 세션 중 사용자가 수행한 _작업_을 보고하려면 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb4db-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="eb4db-108">해당 JEA 끝점에 대해 “자격 증명 입력” 기록을 사용하고 기록 디렉터리에서 각 사용자의 작업에 대한 전체 로그를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4db-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="eb4db-109">PowerShell 모듈 로깅을 켜고 PowerShell 이벤트 로그를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4db-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>

