---
title: "'using module'에 대한 FullyQuilifiedModuleName"
author: jaimeo
contributor: vors
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: e09cfe0994ac523fd10658955731a93b6c176c88

---

'using module'에 대한 FullyQuilifiedModuleName
=========================

이제 `using module`은 PowerShell의 다른 모듈 관련 생성과 동일하게 동작합니다.

WMF 5.0 문제
----------

* 사용자가 `using module`에서 모듈 버전을 지정할 방법이 없습니다.
* 시스템에서 여러 버전의 모듈을 사용할 수 있는 경우 오류가 발생합니다.

WMF 5.1
----------

* 사용자가 `ModuleSpecification`[hashtable](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx)(해시 테이블)을 사용할 수 있습니다. 이 해시 테이블은 형식이 같습니다. `Get-Module -FullyQualifiedName`

**예:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 모듈의 여러 버전이 있는 경우 powershell에서는 `Import-Module`과 **동일한 해결 논리**를 사용하고 오류가 발생하지 않습니다.

* 따라서 `using module`이 `Import-Module` 및 `Import-DscResource`에 맞게 조정됩니다.



<!--HONumber=Aug16_HO3-->


