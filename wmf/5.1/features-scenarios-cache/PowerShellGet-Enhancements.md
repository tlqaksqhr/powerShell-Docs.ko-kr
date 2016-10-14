---
title: "기능 또는 시나리오 기록의 예제 템플릿"
contributor: KeithB
translationtype: Human Translation
ms.sourcegitcommit: 8c55ca4b972c8d708a09b922f27eec585ddc33d0
ms.openlocfilehash: 025565404b60cebefac27e51c70d70edb5e47bc9

---

>참고: 제안된 설명이 포함된 제목과 간단한 설명을 제공합니다.

## PowerShellGet 향상된 기능 ##
WMF 5.1에서는 PowerShellGet 모듈의 cmdlet이 상당히 업데이트되었습니다. 이제 다음과 같은 새 시나리오가 지원됩니다.

- **프록시 지원:** 이제 PowerShellGet 모듈의 모든 Find-, Install-, Save- 및 Publish- cmdlet에 Proxy 및 ProxyCredential 매개 변수가 추가되어 PowerShellGet cmdlet을 내부 프록시와 함께 사용할 수 있습니다. 
- **카탈로그 서명 적용:** 이제 모든 PowerShellGet cmdlet이 서명된 모듈의 업데이트를 확인 및 적용합니다. PowerShellGet cmdlet은 새 카탈로그 cmdlet으로 서명된 모듈을 검사하여 전송 중에 모듈이 수정되지 않았는지 확인하며, 이러한 모듈 업데이트는 원래 게시자만 제공할 수 있습니다. 이 기능은 Install-Module 및 Update-Module cmdlet에 영향을 줍니다. 
- **역할 기능 공유 및 획득:** 역할 기능은 제한할 Just Enough Administration을 구성하는 데 사용되는 끝점 정의이며 PowerShell 모듈의 PowerShell 갤러리를 통해 공유됩니다. cmdlet에는 Find-RoleCapability 및 New-PSRoleCapabilityFile이 포함됩니다. 
- **찾기 명령:** 찾기 명령을 통해 사용자는 찾고 있는 명령이 포함된 PowerShell 갤러리의 모듈을 찾을 수 있습니다. 
- **인증된 리포지토리:** Visual Studio 패키지 관리 피드에는 현재 PowerShellGet cmdlet을 통해 지원되는 인증이 필요합니다.

다음을 포함하여 5.1에서 처리된 추가 개선 영역이 사용자 피드백을 통해 확인되었습니다.

- **Install-Script 변경:** 5.1에서는 Install-Script에서 사용하는 위치가 사용자 경로에 자동으로 추가되지 않습니다. 이 변경은 독립 실행형 버전의 PowerShellGet에서 도입되었으며 현재 WMF 5.1에 포함되었습니다.
- **기존 스크립트에 메타데이터 필드 추가:** 기존 스크립트에 Update-ScriptFileInfo를 사용하여 PowerShellGallery에 게시하는 데 필요한 기본 메타데이터 필드를 추가할 수 있습니다. 이전에는 사용자가 이 필드를 기존 스크립트에 수동으로 병합해야 했습니다.
- **갤러리에 하위 버전 모듈 게시:** 이제 Publish-Module을 사용하여 현재 이전 최고 버전보다 낮은 버전 번호의 모듈을 갤러리에 게시할 수 있습니다. 게시자가 1.x 버전에서 주요 변경 내용이 있는 버전 2.0.0의 모듈을 릴리스한 경우 버전 1.5.0의 수정 프로그램을 쉽게 릴리스할 수 없었습니다. 이제 1.5.1을 게시할 수 있으므로 PowerShell 갤러리의 모듈 유지 관리 지원이 향상됩니다. 
- **스크립트 및 모듈을 설치할 때 명령 덮어쓰기 확인:** 이제 Install-Module 및 Install-Script에서 시스템에 존재하는 명령이 포함되어 있는지 검사하며, 포함된 경우 기본적으로 오류가 발생합니다. 
- **Publish- cmdlet에서 NuGet 부트스트랩:** 이전에는 Publish-Module 또는 Publish-Script를 사용할 때 NuGet 공급자를 자동으로 설치할 방법이 없었으므로 특정 자동화 작업이 매우 어려웠습니다. 이제 사용자가 명령을 추가(강제로 게시)하여 프롬프트를 무시할 수 있습니다. 

>참고: 새로운 개념, 구현, 예제 등을 다루는 추가 세부 정보가 정식 기술 문서에 연결되어 있어야 합니다.

**PowerShellGet 사용 방법에 대한 자세한 정보**
- [About-CatalogSigning]()
- []()
- [CompatiblePSEditions를 기준으로 Get-Module 결과 필터링]()
- [호환되는 PowerShell 버전에서 실행하지 않는 경우 스크립트 실행 방지]()






<!--HONumber=Aug16_HO3-->


