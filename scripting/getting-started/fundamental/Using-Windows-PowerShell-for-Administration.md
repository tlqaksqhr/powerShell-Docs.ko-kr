---
title:  Windows PowerShell을 사용하여 관리
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  db6334ec-ace6-436d-ab88-77aefc817511
---

# Windows PowerShell을 사용하여 관리
Windows PowerShell의 기본적인 목표는 대화형 환경이나 스크립트에서 시스템을 보다 쉽고 보다 잘 관리하는 것입니다. 이 장에서는 Windows PowerShell을 사용하여 Windows 시스템을 관리할 때 발생하는 다양한 문제를 해결하는 방법을 설명합니다. Windows PowerShell 사용자 가이드에는 스크립트나 함수에 대한 설명이 나와 있지 않지만 이러한 해결 방법은 나중에 스크립트에서 또는 함수로 사용할 수 있습니다. 여기에는 문제 해결 방법의 일부로 함수를 사용하는 예제도 제공됩니다.

이 장에서 설명하는 문제 해결 방법에는 특정 cmdlet이나 일반 Get\-WmiObject cmdlet뿐 아니라 Windows 및 .NET Framework 인프라에 포함된 외부 도구를 사용하는 다양한 문제 해결 방법이 포함되어 있습니다. 외부 도구의 사용은 Windows PowerShell의 장기적인 디자인 의도에 따른 것입니다. 시스템까지 확장되면서 사용 가능한 도구 집합으로 필요한 작업을 모두 수행할 수 없는 상황이 지속적으로 발생합니다. Windows PowerShell은 cmdlet 구현에만 의존하지 않고 가능한 모든 방법을 동원하여 문제를 해결하려고 합니다.



<!--HONumber=May16_HO2-->


