---
title: "향상된 끌어오기 서버 등록"
author: jaimeo
contributor: Indhu Sivaramakrishnan
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: d9f7dea63e6541b673ac6be5ccad59368b301440

---

## 향상된 끌어오기 서버 등록 ##

이전 버전의 WMF에서는 ESENT 데이터베이스를 사용하는 동안 DSC 끌어오기 서버에 동시 등록/보고 요청을 하는 경우 LCM이 등록 및/또는 보고에 실패할 수도 있었습니다. 이러한 경우 끌어오기 서버의 이벤트 로그에 "이미 사용 중인 인스턴스 이름" 오류가 표시됩니다.
이는 다중 스레드 시나리오에서 잘못된 패턴을 사용하여 ESENT 데이터베이스에 액세스하기 때문이었습니다. WMF 5.1에서는 이 문제가 해결되었습니다. WMF 5.1에서는 동시 등록 또는 보고(ESENT 데이터베이스 포함)가 올바로 작동합니다. 이 문제는 ESENT 데이터베이스에만 적용되고 OLEDB 데이터베이스에는 적용되지 않습니다. 



<!--HONumber=Jul16_HO3-->


