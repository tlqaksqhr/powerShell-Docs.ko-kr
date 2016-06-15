---
title:  ISEEditor 개체
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  0101daf8-4e31-4e4c-ab89-01d95dcb8f46
---

# ISEEditor 개체
  **ISEEditor** 개체는 Microsoft.PowerShell.Host.ISE.ISEEditor 클래스의 인스턴스입니다. 콘솔 창은 **ISEEditor** 개체입니다. 각 [ISEFile](The-ISEFile-Object.md) 개체에는 연결된 **ISEEditor** 개체가 있습니다. 다음 섹션에는 **ISEEditor** 개체의 메서드 및 속성이 나열됩니다.

## 메서드

### Clear\(\)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 편집기에서 텍스트를 지웁니다.

```
# Clears the text in the Console pane.
$psIse.CurrentPowerShellTab.ConsolePane.Clear()

```

### EnsureVisible\(int lineNumber\)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 지정된 **lineNumber** 매개 변수 값에 해당하는 줄이 표시되도록 편집기를 스크롤합니다. 지정된 줄 번호가 유효한 줄 번호를 정의하는 마지막 줄 번호인 1의 범위 밖에 있는 경우 예외를 throw합니다.

 **lineNumber**
 표시할 줄의 수입니다.

```
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psIse.CurrentFile.Editor.EnsureVisible(5)

```

### Focus\(\)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 포커스를 편집기로 설정합니다.

```
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### GetLineLength\(int lineNumber \)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 줄 번호로 지정된 줄에 대한 정수 줄 길이를 가져옵니다.

 **lineNumber**
 길이를 가져올 줄의 번호입니다.

 **Returns**
 지정된 줄 번호의 줄에 대한 줄 길이입니다.

```
# Gets the length of the first line in the text of the Command pane. 
$psIse.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### GoToMatch\(\)
  Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다. 

 편집기 개체의 **CanGoToMatch** 속성이 **$true**인 경우, 캐럿을 일치하는 문자로 이동합니다. 캐럿이 여는 괄호, 대괄호 또는 중괄호\(\(,\[,{\) 바로 앞 또는 닫는 괄호, 대괄호 또는 중괄호\(\),\],}) 바로 뒤에 있을 때 이런 일이 발생합니다.  캐럿은 여는 문자가 앞이나 닫는 문자 뒤에 배치됩니다. **CanGoToMatch** 속성이 **$false**라면, 이 메서드는 아무 작업도 수행하지 않습니다. [CanGoToMatch](#cangotomatch)를 참조하세요.

```
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### InsertText\( text \)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 선택 영역을 텍스트로 바꾸거나, 현재 캐럿 위치에 텍스트를 삽입합니다.

 **text** \- String  삽입할 텍스트입니다.

 이 항목의 뒷부분에 나오는 [스크립팅 예제](#example)를 참조하세요.

### Select\( startLine, startColumn, endLine, endColumn \)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 **startLine**, **startColumn**, **endLine** 및 **endColumn** 매개 변수에서 텍스트를 선택합니다.

 **startLine** \- Integer  선택이 시작되는 줄입니다.

 **startColumn** \- Integer  선택이 시작되는 시작 줄 내의 열입니다.

 **endLine** \- Integer  선택이 끝나는 줄입니다.

 **endColumn** \- Integer  선택이 끝나는 끝 줄 내의 열입니다.

 이 항목의 뒷부분에 나오는 [스크립팅 예제](#example)를 참조하세요.

### SelectCaretLine\(\)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 현재 캐럿을 포함하는 텍스트의 전체 줄을 선택합니다.

```
# First, set the caret position on line 5.
$psIse.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psIse.CurrentFile.Editor.SelectCaretLine()

```

### SetCaretPosition\( lineNumber, columnNumber \)
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 줄 번호 및 열 번호로 캐럿 위치를 설정합니다. 캐럿 줄 번호 또는 캐럿 열 번호가 각각의 유효한 범위를 벗어나는 경우 예외를 throw합니다.

 **lineNumber** \- Integer  캐럿 줄 번호입니다.

 **columnNumber** \- Integer  캐럿 열 번호입니다.

```
# Set the CaretPosition.
$psIse.CurrentFile.Editor.SetCaretPosition(5,1)
```

### ToggleOutliningExpansion\(\)
  Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다. 

 모든 개요 섹션을 확장하거나 축소합니다.

```
# Toggle the outlining expansion
$psIse.CurrentFile.Editor.ToggleOutliningExpansion()

```

## 속성

###  <a name="CanGoToMatch"></a> CanGoToMatch
  Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다. 

 캐럿이 괄호, 대괄호 또는 중괄호(\(\), \[\], {}) 옆에 있는지 여부를 나타내는 읽기 전용 부울 속성입니다. 캐럿이 여는 문자의 바로 앞 또는 닫는 문자 바로 뒤에 있다면 이 속성 값은 **$true**입니다. 그렇지 않으면 **$false**입니다.

```
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psIse.CurrentFile.Editor.CanGoToMatch

```

###  <a name="CaretColumn"></a> CaretColumn
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 캐럿의 위치에 해당하는 열 번호를 가져오는 읽기 전용 속성입니다.

```
# Get the CaretColumn.
$psIse.CurrentFile.Editor.CaretColumn

```

###  <a name="CaretLine"></a> CaretLine
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 캐럿을 포함하는 줄 번호를 가져오는 읽기 전용 속성입니다.

```
# Get the CaretLine.
$psIse.CurrentFile.Editor.CaretLine

```

###  <a name="caretlinetext"></a> CaretLineText
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 캐럿을 포함하는 텍스트의 전체 줄을 가져오는 읽기 전용 속성입니다.

```
# Get all of the text on the line that contains the caret.
$psIse.CurrentFile.Editor.CaretLineText

```

###  <a name="LineCount"></a> LineCount
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 편집기에서 줄 수를 가져오는 읽기 전용 속성입니다.

```
# Get the LineCount.
$psIse.CurrentFile.Editor.LineCount

```

###  <a name="SelectedText"></a> SelectedText
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 편집기에서 선택한 텍스트를 가져오는 읽기 전용 속성입니다.

 이 항목의 뒷부분에 나오는 [스크립팅 예제](#example)를 참조하세요.

###  <a name="Text"></a> 텍스트
  Windows PowerShell ISE 2.0 이상에서 지원됩니다. 

 편집기에 있는 텍스트를 설정하거나 가져오는 읽기\/쓰기 속성입니다.

 이 항목의 뒷부분에 나오는 [스크립팅 예제](#example)를 참조하세요.

##  <a name="example"></a> 스크립팅 예제

```

# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor=$psIse.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line. 
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## 참고 항목
 [ISEFile 개체](The-ISEFile-Object.md) 
 [PowerShellTab 개체](The-PowerShellTab-Object.md) 
 [Windows PowerShell ISE 스크립팅 개체 모델](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 개체 모델 참조](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


