---
ms.date:  06/09/2017
schema:  2.0.0
locale:  en-us
keywords:  powershell,cmdlet
online version:  http://go.microsoft.com/fwlink/?LinkId=301310
external help file:  Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
---

# Export-BinaryMiLog

## 개요

바이너리 표현으로 인코딩된 오브젝트를 생성하고 파일로 저장합니다.

## 구문

```powershell
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String>
```

## 설명

**Export-BinaryMILog** cmdlet 은 바이너리 표현으로 인코딩된 오브젝트를 생성하고 파일로 저장합니다. 
Import-BinaryMiLog cmdlet 을 사용하여 파일로 저장된 오브젝트의 내용을 다시 불러들일 수 있습니다.

이 cmdlet 은 Import-Clixml 과 유사합니다, 차이점이라면, Export-BinaryMILog 는 오브젝트를 바이너리 표현으로 인코딩된 파일을 저장한다는 것입니다.

## 예제

### 바이너리 표현으로 인코딩된 CimInstances 생성

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

이 명령어는 CimInstance 를 -Path 매개 변수로 지정된 바이너리 표현으로 인코딩된 MI 로그 파일로 저장합니다.
위 명령어를 통해 파일로 저장된 CimInstances를 불러오는 법을 알고 싶은 경우 Import-BinaryMiLog 예제를 참고하십시오.


## 요구 매개변수

### -InputObject

이 cmdlet의 입력값을 지정합니다.
이 매개변수를 사용하거나 혹은 파이프라인을 이용해서 입력값을 지정할 수 있습니다.

```yaml
타입: CimInstance
파라미터 셋: (All)
별칭:

필수 파라미터: False
파라미터 포지션: Named
기본값: None
파이프라인 입력 허용: True (ByValue)
와일드카드 문자열 허용: False
```

### -Path

바이너리 표현으로 저장된 오브젝트 파일의 경로를 지정합니다.

Path 파라미터는 와일드카드와 상대경로를 지원합니다.
이 cmdlet 은 경로가 둘 이상의 파일을 가리키는 경우 오류가 발생합니다.

```yaml
타입: String
파라미터 셋: (All)
별칭:

필수 파라미터: True
파라미터 포지션: 0
기본값: None
파이프라인 입력 허용: False
와일드카드 문자열 허용: False
```

## INPUTS

### Microsoft.Management.Infrastructure.CimInstance


## OUTPUTS

### System.Object

## 노트

## 관련 링크

[Get-CimInstance](get-ciminstance.md)

[Import-BinaryMiLog](import-binarymilog.md)

[Import-Clixml](../microsoft.powershell.utility/import-clixml.md)