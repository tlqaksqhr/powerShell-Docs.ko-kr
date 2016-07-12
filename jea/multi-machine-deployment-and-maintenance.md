---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "다중 컴퓨터 배포 및 유지 관리"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 784806197a64eb30af1ecea4af55575434ce7b87

---

# 다중 컴퓨터 배포 및 유지 관리
이 시점에서 JEA를 로컬 시스템에 여러 번 배포했습니다.
프로덕션 환경은 두 대 이상의 컴퓨터로 구성될 수 있으므로 각 컴퓨터에서 반복해야 하는 배포 프로세스의 중요 단계를 연습해야 합니다.

## 상위 수준 단계:
1.  역할 기능이 포함된 모듈을 각 노드에 복사합니다.
2.  세션 구성 파일을 각 노드에 복사합니다.
3.  세션 구성과 함께 `Register-PSSessionConfiguration`을 실행합니다.
4.  세션 구성과 도구 키트의 복사본을 안전한 위치에 보관합니다.
수정 작업을 할 때 "단일 데이터 소스(single source of truth)"를 마련하는 것이 좋습니다.

## 예제 스크립트
배포를 위한 예제 스크립트는 다음과 같습니다.
해당 환경에서 이 스크립트를 사용하려면 실제 파일 공유 및 모듈의 이름/경로를 사용해야 합니다.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## 기능 수정
많은 컴퓨터를 처리할 때 수정 내용을 일관된 방식으로 배포하는 것이 중요합니다.
JEA에 DSC 리소스가 있으면 환경이 동기화되도록 하는 데 도움이 됩니다.
그 전까지는 세션 구성의 마스터 복사본을 보관하고 수정할 때마다 다시 배포하는 것이 좋습니다.

## 기능 제거
시스템에서 JEA 구성을 제거하려면 각 컴퓨터에서 다음 명령을 사용합니다.
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```




<!--HONumber=Jul16_HO1-->


