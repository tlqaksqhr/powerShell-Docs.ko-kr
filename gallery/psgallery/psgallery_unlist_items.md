---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell, cmdlet, 갤러리"
ms.date: 2016-10-14
contributor: manikb
title: psgallery_unlist_items
ms.technology: powershell
ms.openlocfilehash: ede07cce7b65b795f48d16cb2862880f84c3eda2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="unlisting-items"></a>목록에서 항목 제거

**옵션으로 노출되지 않는 항목을 PowerShell 갤러리에서 제거해야 하는 것은 무엇 때문일까요?**

PowerShell 갤러리에서는 사용자가 항목을 영구적으로 삭제할 수 없습니다. 따라서 다른 사용자가 이후의 가능한 손상에 대해 염려하지 않고 항목을 사용할 수 있습니다. 예를 들어 Pester 모듈이 Azure 모듈을 사용하는데 Azure 모듈이 갤러리에서 제거되면 사용자가 Pester 모듈을 더 이상 사용할 수 없습니다.

그러나 항목을 제거하는 대신 목록에서 제거할 수 있습니다.

**PowerShell 갤러리의 목록에서 항목을 제거하면 어떻게 될까요?**

PowerShell 갤러리의 목록에서 모듈 또는 스크립트와 같은 항목을 제거하면 항목 탭에서 제거됩니다.
또한 목록에 없는 항목은 검색 표시줄을 사용하여 검색할 수 없습니다.
목록에 없는 항목을 다운로드하려면 항목의 정확한 이름 및 버전을 지정해야 합니다.
이 때문에 목록에서 항목을 제거하는 경우 해당 항목을 사용하는 다른 모듈이나 스크립트가 손상되지 않습니다.

목록에서 항목을 제거하려면 항목 세부 정보 페이지로 이동한 다음 '항목 삭제'를 선택합니다. '목록에 표시' 확인란의 선택을 취소하고 저장을 클릭합니다.

**항목을 제거하려면 어떻게 하나요?**

항목을 삭제해야 하는 시나리오가 발생하면 PowerShell 갤러리 관리자에게 문의하세요.
유효한 삭제 시나리오는 다음과 같습니다.
- 저작권 침해 문제
- 항목에 잠재적으로 유해한 콘텐츠가 포함된 경우
- 항목에 중요한 데이터가 포함된 경우

PowerShell 갤러리 관리자에게 항목 삭제 요청을 제출하려면 항목 세부 정보 페이지로 이동한 다음 고객 지원을 선택합니다.  


