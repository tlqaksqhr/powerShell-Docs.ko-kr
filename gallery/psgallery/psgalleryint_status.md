---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a>PowerShell 갤러리 상태
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017/03/27 - 해결됨: 개별 모듈 및 스크립트 페이지를 볼 수 없음

__영향 요약__: https://www.powershellgallery.com에서 개별 모듈 및 스크립트 페이지로 연결되는 직접 링크가 끊어졌습니다. 이 문제는 모든 지역에서 보고되었습니다. 이 문제는 Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt와 같은 PowerShellGet cmdlet이 계속 작동하는 데는 영향을 주지 않았습니다.

__근본 원인__: 엔지니어들은 Facebook과 같은 소셜 미디어 단추를 페이지에 가져오는 과정에서 문제가 생긴 것을 알아냈습니다.  

__해결 방법__: 엔지니어가 Facebook 개수 정보를 사용하지 않도록 설정하여 문제를 해결했습니다.

__다음 단계__: Facebook API 사용 문제를 해결하기 위해 내부 추적 문제를 열었습니다.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>2016/12/15 - PowerShellGallery 웹 사이트를 통해 메일을 보낼 수 없음

__영향 요약__: 2016/12/13과 2016/12/15 사이에 소유자에게 문의, 소유자 관리, 고객 지원 또는 신고하기를 통해 전송된 모든 메시지는 PowerShell 갤러리 관리자가 받지 못했습니다.  
__근본 원인__: 엔지니어는 SMTP 서버와의 인증 문제를 원인으로 식별했습니다.  
__해결 방법__: 엔지니어는 인증 문제를 해결하고 SMTP 서버에 대한 연결을 복원할 수 있었습니다.  
__다음 단계__: 이 시간 동안 소유자에게 문의, 소유자 관리, 고객 지원 또는 신고하기 링크를 사용하여 cgadmin@microsoft.com으로 메일을 보냈고 응답을 받지 못한 경우 다시 시도하세요. 불편을 드려 죄송합니다.   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>2016년 8월 10일 - 해결됨: cgadmin@microsoft.com으로 메일을 보낼 수 없음
__영향 요약__: 2016년 8월 5일에서 2016년 8월 10일 사이 고객이 cgadmin@microsoft.com으로 메일을 보내거나 문의처 기능을 사용할 수 없었습니다.  
__근본 원인__: 엔지니어가 원인을 메일 계정의 구성 변경으로 식별했습니다.  
__해결 방법__: 엔지니어가 구성 문제를 해결하기 위해 노력했습니다.  
__다음 단계__: 이 시간 동안 문의처 링크를 사용하거나 cgadmin@microsoft.com으로 메일을 보내고 응답을 받지 못한 경우 다시 시도하세요. 기다려 주셔서 감사합니다.


