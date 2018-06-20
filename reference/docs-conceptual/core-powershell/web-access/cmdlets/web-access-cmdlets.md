---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: PowerShell 웹 액세스 Cmdlet
ms.openlocfilehash: 34a7a01f154b2e43416dfe8ea43d4d8e937816d9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188023"
---
# <a name="windows-powershell-web-access-cmdlets"></a>Windows PowerShell 웹 액세스 Cmdlet

이 참조는 모든 Windows PowerShell® 웹 액세스 특정 cmdlet에 대한 cmdlet 설명 및 구문을 제공합니다. cmdlet은 cmdlet의 시작 부분에 있는 동사에 따라 사전순으로 나열됩니다.

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)

새로운 권한 부여 규칙을 Windows PowerShell® 웹 액세스 권한 부여 규칙 집합에 추가합니다.

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)

일련의 Windows PowerShell 웹 액세스 권한 부여 규칙을 반환합니다.

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[Install-PswaWebApplication](install-pswawebapplication.md)

IIS에서 Windows PowerShell 웹 액세스 웹 응용 프로그램을 구성합니다.

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)

지정된 권한 부여 규칙을 Windows PowerShell 웹 액세스에서 제거합니다.

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)

권한 부여 규칙을 테스트하여 특정 사용자, 컴퓨터, 끝점 액세스 요청이 인증되었는지 확인합니다.

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[Uninstall-PswaWebApplication](uninstall-pswawebapplication.md)

IIS에서 Windows PowerShell 웹 응용 프로그램을 제거합니다.

>**참고**:
>
>사용 가능한 모든 cmdlet을 나열하려면 다음을 사용합니다.
>
> `Get-Command –Module PowerShellWebAccess` cmdlet

cmdlet 또는 해당 구문에 대한 자세한 내용을 보려면 `Get-Help `‘&lt;cmdlet name&gt;’을 사용하세요. 여기서 ‘&lt;cmdlet name&gt;’은 알아보려는 cmdlet의 이름입니다.

자세한 내용을 보려면 다음 cmdlet 중 하나를 실행하면 됩니다.

- `Get-Help `*&lt;cmdlet name&gt;*` -Detailed`
- `Get-Help `*&lt;cmdlet name&gt;*` -Examples`
- `Get-Help `*&lt;cmdlet name&gt;*` -Full`

### <a name="more-information"></a>자세한 정보

PowerShell 웹 액세스에 대한 자세한 내용은 다음을 참조하세요.

- [Windows PowerShell 웹 액세스 설치 및 사용](../install-and-use-windows-powershell-web-access.md)