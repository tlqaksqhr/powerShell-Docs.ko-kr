---
title:  중요한 Windows PowerShell 개념 이해
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  3e601e38-4520-4578-a48d-b6779f1d35ee
---

# 중요한 Windows PowerShell 개념 이해
Windows PowerShell 디자인은 다양한 환경의 개념을 통합합니다. 그 중에서 여러 개념은 특정 셸 또는 프로그래밍 환경의 경험자에게 익숙하지만 모든 개념을 알고 있는 사용자는 거의 없습니다. 이러한 개념 중 일부를 살펴보면 셸에 대한 전반적인 유용한 정보를 얻을 수 있습니다.

### 텍스트를 기반으로 하지 않는 명령
이전의 명령줄 인터페이스 명령과 달리 Windows PowerShell cmdlet은 단순히 화면에 표시되는 문자열이 아니라 개체, 즉 구조화된 정보를 처리하도록 설계되었습니다. 명령 출력에는 필요할 때 사용할 수 있는 추가 정보가 항상 포함됩니다. 이 문서에서는 이 항목에 대해 자세히 설명합니다.

Windows PowerShell에서는 텍스트 처리 도구가 이전의 명령줄 인터페이스에서와 다른 방식으로 명령줄 데이터를 처리하기 때문에 대부분의 경우 텍스트 처리 도구를 사용하여 특정 정보를 추출할 필요가 없습니다. 표준 Windows PowerShell 개체 조작 명령을 사용하면 데이터의 일부에 직접 액세스할 수 있습니다.

### 확장 가능한 명령 패밀리
Cmd.exe와 같은 인터페이스에서는 기본 제공 명령 집합을 직접 확장할 수 없습니다. Cmd.exe에서 실행되는 외부 명령줄 도구를 만들 수는 있지만 이러한 외부 도구에는 도움말 통합 같은 서비스가 없기 때문에 Cmd.exe는 이러한 외부 도구가 유효한 명령인지 자동으로 인식하지 못합니다.

*cmdlet*(커맨드렛으로 읽음)이라고 하는 Windows PowerShell의 기본 이진 명령은 cmdlet을 만든 다음 스냅인을 사용하여 cmdlet을 Windows PowerShell에 추가함으로써 확장할 수 있습니다. Windows PowerShell *스냅인*은 다른 모든 인터페이스의 이진 도구처럼 컴파일됩니다. Windows PowerShell 스냅인을 사용하면 셸에 새 cmdlet뿐 아니라 Windows PowerShell 공급자도 추가할 수 있습니다.

이 설명서에서는 Windows PowerShell 내부 명령도 특성상 *cmdlet*이라고 합니다.

> [!NOTE]
> Windows PowerShell에서는 cmdlet 이외의 명령을 실행할 수 있습니다. 이 Windows PowerShell 사용자 가이드에서 자세히 설명하지 않지만 이러한 명령은 명령 유형을 범주로 구분하는 데 유용합니다. Windows PowerShell은 UNIX 셸 스크립트 및 Cmd.exe 배치 파일과 유사하지만 파일 이름 확장명이 .ps1인 스크립트를 지원합니다. 또한 Windows PowerShell에서는 인터페이스나 스크립트에서 직접 사용할 수 있는 내부 함수를 만들 수도 있습니다.

### Windows Powershell은 콘솔 입력 및 표시 처리합니다.
사용자가 명령을 입력하면 Windows PowerShell은 항상 이 명령줄 입력을 직접 처리합니다. 또한 Windows PowerShell은 화면에 표시되는 출력의 형식을 지정합니다. 이 기능은 각 cmdlet에 대해 수행해야 하는 작업을 줄여주고 사용 중인 cmdlet에 관계없이 항상 동일한 방식으로 작업을 수행할 수 있도록 해 주기 때문에 중요합니다. 이 기능을 통해 도구 개발자와 도구 사용자의 작업을 단순화하는 방법의 예로 명령줄 도움말을 들 수 있습니다.

이전의 명령줄 도구는 도움말을 요청하고 표시하는 자체 구성을 갖습니다. 일부 명령줄 도구는 **\/?**를 사용하여 도움말 표시를 트리거하고, 일부 명령줄 도구는 **\-?** 또는 **\/H**뿐 아니라 심지어 **\/\/**를 사용하여 도움말 표시를 트리거합니다. 또한 일부 명령줄 도구는 콘솔 화면 대신 GUI 창에 도움말을 표시합니다. 응용 프로그램 업데이트 프로그램과 같이 일부 복잡한 도구는 도움말을 표시하기 전에 내부 파일의 압축을 풉니다. 사용자가 잘못된 매개 변수를 사용할 경우 이러한 도구는 사용자의 입력 내용을 무시하고 자동으로 작업을 시작할 수 있습니다.

Windows PowerShell에서 명령을 입력하면 Windows PowerShell은 자동으로 이러한 명령을 구문 분석하고 전처리합니다. Windows PowerShell cmdlet에서 **\-?** 매개 변수를 사용하는 경우 이는 항상 "해당 명령에 대한 도움말을 표시"하라는 의미입니다. Cmdlet 개발자는 명령을 구문 분석할 필요 없이 도움말 텍스트만 제공하면 됩니다.

Windows PowerShell에서 이전의 명령줄 도구를 사용하는 경우에도 Windows PowerShell의 도움말 기능은 사용할 수 있습니다. Windows PowerShell은 매개 변수를 처리하고 그 결과를 외부 도구에 전달합니다.

> [!NOTE]
> Windows PowerShell에서 그래픽 응용 프로그램을 실행하면 해당 응용 프로그램의 창이 열립니다. Windows PowerShell은 사용자가 제공하는 명령줄 입력이나 콘솔 창에 반환되는 응용 프로그램 출력을 처리할 때만 개입하고 응용 프로그램이 자체적으로 작업을 수행하는 방식에는 영향을 주지 않습니다.

### 일부 C# 구문 사용
Windows PowerShell은 .NET Framework를 기반으로 하기 때문에 Windows PowerShell에는 C# 프로그래밍 언어에서 사용하는 것과 매우 유사한 구문 기능과 키워드가 포함되어 있습니다. C#에 관심이 있을 경우 Windows PowerShell에 대해 알면 C#을 익히기가 훨씬 더 쉬워집니다.

C# 프로그래머가 아닐 경우 이러한 유사함은 별로 도움이 되지 않지만 C#에 대해 잘 알고 있을 경우 이러한 유사함을 통해 Windows PowerShell을 훨씬 더 쉽게 익힐 수 있습니다.



<!--HONumber=May16_HO2-->


