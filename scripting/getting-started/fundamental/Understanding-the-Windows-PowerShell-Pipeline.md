---
title: "Windows PowerShell 파이프라인 이해"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 233ec6fafbf1e770190601750be3bdcef2337b7f

---

# Windows PowerShell 파이프라인 이해
파이프는 사실상 Windows PowerShell의 모든 영역에 사용됩니다. 화면에 텍스트가 표시되어 있는 경우에도 Windows PowerShell은 명령 사이에 있는 텍스트를 파이프하는 대신 개체를 파이프합니다.

파이프라인에 사용되는 표기법과 다른 셸에 사용되는 표기법이 유사하기 때문에 처음에는 Windows PowerShell에 새로 도입된 기능을 쉽게 확인하지 못할 수도 있습니다. 예를 들어 **Out\-Host** cmdlet을 사용하여 다른 명령의 출력을 페이지 단위로 표시하면 다음과 같이 일반 텍스트가 페이지 단위로 나뉘어져 화면에 표시된 것처럼 보입니다.

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

Out\-Host \-Paging 명령은 긴 출력을 천천히 표시하려는 경우에 유용한 파이프라인 요소로, 특히 CPU를 많이 사용하는 작업에 유용합니다. Out\-Host cmdlet이 전체 페이지를 표시할 준비가 되면 프로세스가 이 cmdlet에 전달되므로 파이프라인에서 이 cmdlet 앞에 있는 cmdlet은 다음 페이지를 출력할 수 있을 때까지 작업을 중지합니다. Windows 작업 관리자에서 Windows PowerShell이 사용하는 CPU와 메모리를 모니터링하면 이를 확인할 수 있습니다.

다음 명령을 실행합니다. **Get\-ChildItem C:\\Windows \-Recurse**. CPU 및 메모리 사용량을 다음 명령과 비교합니다. **Get\-ChildItem C:\\Windows \-Recurse | Out\-Host \-Paging**. 화면에 텍스트가 표시되지만 이것은 개체를 콘솔 창에 텍스트로 표시해야 하기 때문이며 Windows PowerShell에서 실제로 진행되고 있는 작업을 보여 주기 위한 것일 뿐입니다. Get\-Location cmdlet을 예로 들어 보겠습니다. 현재 위치가 C 드라이브의 루트일 때 **Get\-Location**을 입력하면 다음과 같은 내용이 출력됩니다.

```
PS> Get-Location

Path
----
C:\
```

Windows PowerShell에서 파이프라인으로 결합한 **Get\-Location | Out\-Host**와 같은 명령을 실행하면 일련의 문자가 화면에 표시되는 순서대로 **Get\-Location**에서 **Out\-Host**로 전달됩니다. 즉, 머리글 정보를 무시할 경우 **Out\-Host**에 '**C'** 문자, '**:'** 문자 및 '**\\'** 문자가 차례로 전달됩니다. **Out\-Host** cmdlet으로는 **Get\-Location** cmdlet이 출력하는 문자에 연결된 의미를 알 수 없습니다.

Windows PowerShell은 텍스트 대신 개체를 사용하여 파이프라인에 있는 명령과 통신합니다. 사용자의 관점에서 볼 때 개체는 관련 정보를 하나의 단위로 쉽게 조작할 수 있는 형식으로 패키징하고 필요한 특정 항목을 추출합니다.

**Get\-Location** 명령은 현재 경로가 포함된 텍스트를 반환하지 않고 현재 경로와 함께 몇 가지 다른 정보가 포함된 **PathInfo** 개체라는 정보 패키지를 반환합니다. 그러면 **Out\-Host** cmdlet이 이 **PathInfo** 개체를 화면에 보내고 Windows PowerShell은 형식 지정 규칙에 따라 표시할 정보와 이러한 정보의 표시 방법을 결정합니다.

사실 **Get\-Location** cmdlet이 출력하는 머리글 정보는 화면에 표시할 데이터의 형식을 지정하는 프로세스의 일부로 해당 프로세스의 끝에만 추가됩니다. 화면에는 출력 개체에 대한 전체 정보 대신 요약 정보가 표시됩니다.

Windows PowerShell 명령이 출력하는 정보가 콘솔 창에 표시되는 정보보다 많을 경우 콘솔 창에 표시되지 않는 요소를 검색하거나 추가 데이터를 표시할 수 있으며 특정 Windows PowerShell이 일반적으로 사용하는 것과 다른 형식으로 데이터를 표시할 수도 있습니다.

이 장의 나머지 부분에서는 특정 Windows PowerShell 개체의 구조를 검색하는 방법과 이러한 정보를 파일이나 프린터와 같은 다른 출력 위치로 보내는 방법을 설명합니다.




<!--HONumber=Jun16_HO4-->


