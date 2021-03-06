---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 갤러리 검색 구문
ms.openlocfilehash: 52fca21a00bcc6e3789bceb331acf5bc771bb0f2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188414"
---
# <a name="gallery-search-syntax"></a>갤러리 검색 구문

PowerShell 갤러리는 단어, 구 및 키워드 식을 사용하여 검색 결과 범위를 좁힐 수 있는 텍스트 검색 상자를 제공합니다.

## <a name="search-by-keywords"></a>키워드로 검색

    dsc azure sql

검색은 3가지 키워드를 모두 포함하는 관련 문서를 찾으려고 하며 일치하는 문서를 반환합니다.

## <a name="search-using-phrases-and-keywords"></a>구문 및 키워드를 사용하여 검색

    "azure sql" deployment

따옴표("") 사이에 구를 입력하면 별도 키워드가 아닌 특정 구를 찾도록 검색이 변경됩니다.
일반적으로 일치하는 문서에는 대/소문자 변형(예: "Azure SQL")을 포함하여 "azure sql" 구가 정확하게 포함되어야 하며, 대체로 '배포'라는 단어도 포함됩니다.

## <a name="filtering-on-fields"></a>필드 필터링

특정 항목 ID(또는 'Id' 또는 'id')를 검색하거나 검색어 앞에 필드 이름을 추가하여 다른 특정 필드를 검색할 수 있습니다.

현재 검색 가능한 필드는 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' 및 'PowerShellVersion'입니다.

[ID와 제목 간의 차이점은 무엇인가요? ID는 콘솔에서 사용하는 이름입니다. 제목은 검색 결과에서 항목 페이지의 맨 위에 표시되는 내용입니다.]

## <a name="examples"></a>예

    ID:"PSReadline"
    id:"AzureRM.Profile"

ID 필드에 각각 "PSReadline" 또는 "AzureRM.Profile"이 포함된 항목을 찾습니다.

    Id:"AzureRM.Profile"

ID 필드에 "AzureRM.Profile"이 포함된 항목을 찾는 다른 방법입니다.

'Id' 필터는 부분 문자열 일치이므로 다음을 검색하는 경우

    Id:"azure"

'AzureRM.Profile' 및 'Azure.Storage'와 같은 결과가 표시됩니다.

또한 단일 필드에서 여러 키워드를 검색할 수 있습니다. 또는 필드를 섞어서 일치시킵니다.

    id:azure tags:intellisense
    id:azure id:storage

구를 검색할 수도 있습니다.

    id:"azure.storage"


DSC 태그가 있는 항목을 모두 검색합니다.

    Tags:"DSC"

지정된 함수가 있는 항목을 모두 검색합니다.

    Functions:"Update-AzureRM"

지정된 cmdlet이 있는 항목을 모두 검색합니다.

    Cmdlets:"Get-AzureRmEnvironment"

지정된 DSC 리소스 이름이 있는 항목을 모두 검색합니다.

    DscResources:"xArchive"

지정된 PowerShellVersion이 있는 항목을 모두 검색합니다.

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


마지막으로, 지원되지 않는 필드(예: 'commands')를 사용하는 경우 필드가 무시되고 모든 필드가 검색됩니다. 따라서 다음 쿼리의 경우

    commands:blobs storage

다음 쿼리와 똑같이 해석됩니다.

    blobs storage