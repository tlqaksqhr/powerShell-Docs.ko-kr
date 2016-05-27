---
title:   Windows PowerShell 필요한 상태 구성 개요 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Windows PowerShell 필요한 상태 구성 개요 

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

이 항목에서는 Windows PowerShell의 Windows PowerShell DSC(필요한 상태 구성) 기능에 대해 설명합니다. 이 항목에서 DSC에 대한 개요를 알고, DSC를 사용하고 이해하는 데 필요한 설명서 리소스를 찾을 수 있습니다.

## 기능 설명
DSC는 소프트웨어 서비스에 대한 구성 데이터를 배포 및 관리하고 이러한 서비스가 실행되는 환경을 관리할 수 있도록 해주는 Windows PowerShell의 새로운 관리 플랫폼입니다.

DSC에서는 소프트웨어 환경을 어떻게 구성할지를 선언적으로 지정하는 데 사용할 수 있는 Windows PowerShell 언어 확장, 새로운 Windows PowerShell cmdlet 및 리소스들을 제공합니다. 또한 기존 구성을 유지하고 관리하는 수단을 제공합니다.

## 유용한 팁
다음은 기본 제공 DSC 리소스를 사용하여 자동화된 방식으로 컴퓨터들(대상 노드라고도 함)을 구성하고 관리할 수 있는 몇 가지 예제 시나리오입니다.

* 서버 역할 및 기능 사용 여부 설정
* 레지스트리 설정 관리
* 파일 및 디렉터리 관리
* 프로세스 및 서비스 시작, 중지 및 관리
* 그룹 및 사용자 계정 관리
* 새 소프트웨어 배포
* 환경 변수 관리
* Windows PowerShell 스크립트 실행
* 필요한 상태에서 변경된 구성 수정
* 지정된 노드에서 실제 구성 상태 검색

## 주요 개념
DSC는 시스템의 구성, 배포 및 관리에 사용되는 선언적 플랫폼입니다. 이것은 세 가지 기본 요소로 구성됩니다.

* [구성](configurations.md)은 리소스의 인스턴스를 정의 및 구성하는 선언적 PowerShell 스크립트입니다. 구성 실행 시, DSC(및 구성에 의해 호출되는 리소스)는 시스템이 구성에 의해 배치된 상태로 존재하도록 단순히 "그대로 수행"하게 됩니다. 또한 DSC 구성은 idempotent입니다. LCM(로컬 구성 관리자)은 구성에서 선언하는 상태가 무엇이든 계속 컴퓨터가 해당 상태로 구성되어 있도록 합니다.
* 리소스는 하위 시스템의 다양한 구성 요소를 모델링하고 변화하는 상태들에 대한 제어 흐름을 구현하도록 작성된 DSC의 필수 구성 요소입니다. 또한 리소스는 PowerShell 모듈 내에 상주하며, 파일이나 Windows 프로세스만큼 일반적이거나 Azure에서 실행되는 IIS 서버 또는 VM만큼 특별한 것을 모델링하도록 작성할 수 있습니다.
* LCM(로컬 구성 관리자)은 DSC에서 리소스와 구성 간 상호 작용을 이용할 때 사용하는 엔진입니다. LCM은 리소스가 구현한 제어 흐름을 사용하여 구성으로 배치된 상태를 유지하도록 시스템을 정기적으로 폴링합니다. 시스템이 상태를 벗어나면 LCM에서는 리소스 내에서 더 많은 논리를 사용하여 구성 선언에 따라 "그대로 수행"합니다. 

또한 DSC은 구성을 만들 수 있도록 해주고, DSC 리소스를 빌드하도록 도와주고, 구성을 호출하고, LCM을 관리하는 다양한 새로운 언어 키워드, cmdlet 및 도구를 포함하고 있습니다. 이러한 cmdlet 중 많은 수는 PSDesiredStateConfiguration 모듈의 일부로서 Windows 8.1에서 찾을 수 있습니다(`Start-DscConfiguration`, `Set-DscLocalConfigurationManager`, `Get-DscResource` 포함). xDscResourceDesigner([PowerShell 갤러리](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)에 있음)는 DSC 리소스의 개발을 단순화하는 cmdlet 컬렉션입니다.

## 참고 항목
* [DSC 구성](configurations.md)
* [DSC 리소스](resources.md)
* [로컬 구성 관리자 구성](metaConfig.md)



<!--HONumber=May16_HO3-->


