---
title:   DSC 구성에 대한 도움말 작성
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# DSC 구성에 대한 도움말 작성

>적용 대상: Windows Windows PowerShell 5.0

DSC 구성에 설명 기반 도움말을 사용할 수 있습니다. 사용자는 `-?`가 포함된 구성 함수를 호출하거나 [Get-Help](https://technet.microsoft.com/en-us/library/hh849696.aspx) cmdlet을 사용하여 도움말에 액세스할 수 있습니다. PowerShell 설명 기반 도움말에 대한 자세한 내용은 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/hh847834.aspx)를 참조하세요.

다음 예제는 두 개의 구성이 포함된 스크립트와 각 구성에 대한 설명 기반 도움말을 보여줍니다.

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER computername
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword. 
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description. 
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters 
(and their descriptions) appear in help topic. To change the order, change the syntax.

.PARAMETER filePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$computername,[string]$filePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## 구성 도움말 보기

구성에 대한 도움말을 보려면 함수의 이름과 함께 **Get-Help** cmdlet을 사용하거나 함수의 이름 뒤에 `-?`를 붙여 입력하세요. 다음은 **Get-Help**로 전달된 경우의 이전 함수 출력입니다.

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1
    
SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.
    
    
SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-computername] 
    <String>] [[-filePath] <String>] [<CommonParameters>]
    
    
DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.
    

RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## 참고 항목
* [DSC 구성](configurations.md)



<!--HONumber=May16_HO3-->


