---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEFile 개체"
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 0e1c09c4a92868448d76cc7b4954d250773ce2f2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="5b938-103">ISEFile 개체</span><span class="sxs-lookup"><span data-stu-id="5b938-103">The ISEFile Object</span></span>
  <span data-ttu-id="5b938-104">**ISEFile** 개체는 Windows PowerShell® ISE(통합 스크립팅 환경)에 있는 파일을 나타내며,</span><span class="sxs-lookup"><span data-stu-id="5b938-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="5b938-105">Microsoft.PowerShell.Host.ISE.ISEFile 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="5b938-106">이 항목에는 멤버 메서드 및 멤버 속성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="5b938-107">**$psISE.CurrentFile**과 PowerShell 탭의 파일 컬렉션에 있는 파일이 Microsoft.PowerShell.Host.ISE.ISEFile 클래스의 전체 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="5b938-108">메서드</span><span class="sxs-lookup"><span data-stu-id="5b938-108">Methods</span></span>

###  <span data-ttu-id="5b938-109"><a name="save-override"></a> Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="5b938-109"><a name="save-override"></a> Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="5b938-110">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5b938-111">파일을 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-111">Saves the file to disk.</span></span>

 <span data-ttu-id="5b938-112">**\[saveEncoding\]** – 선택적 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
. 저장된 파일에 사용할 선택적 문자 인코딩 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="5b938-113">기본값은 **UTF8**입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="5b938-114">**예외**</span><span class="sxs-lookup"><span data-stu-id="5b938-114">**Exceptions**</span></span>
 -   <span data-ttu-id="5b938-115">**System.IO.IOException**: 파일을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <span data-ttu-id="5b938-116"><a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="5b938-116"><a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="5b938-117">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5b938-118">지정한 파일 이름 및 인코딩으로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="5b938-119">**filename** - 파일을 저장하는 데 사용할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="5b938-120">**\[saveEncoding\]** – 선택적 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
. 저장된 파일에 사용할 선택적 문자 인코딩 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="5b938-121">기본값은 **UTF8**입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="5b938-122">**예외**</span><span class="sxs-lookup"><span data-stu-id="5b938-122">**Exceptions**</span></span>
 -   <span data-ttu-id="5b938-123">**System.ArgumentNullException**: **filename** 매개 변수는 null입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

-   <span data-ttu-id="5b938-124">**System.ArgumentException**: **filename** 매개 변수는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

-   <span data-ttu-id="5b938-125">**System.IO.IOException**: 파일을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="5b938-126">속성</span><span class="sxs-lookup"><span data-stu-id="5b938-126">Properties</span></span>

###  <span data-ttu-id="5b938-127"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="5b938-127"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="5b938-128">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5b938-129">이 파일의 표시 이름을 포함하는 문자열을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="5b938-130">이름은 편집기의 맨 위에 있는 **파일** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="5b938-131">이름의 끝에 별표(\(\*\))가 있다면 파일에 저장되지 않은 변경 내용이 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <span data-ttu-id="5b938-132"><a name="Editor"></a> Editor</span><span class="sxs-lookup"><span data-stu-id="5b938-132"><a name="Editor"></a> Editor</span></span>
  <span data-ttu-id="5b938-133">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5b938-134">지정된 파일에 사용되는 [편집기 개체](The-ISEEditor-Object.md)를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <span data-ttu-id="5b938-135"><a name="Encoding"></a> Encoding</span><span class="sxs-lookup"><span data-stu-id="5b938-135"><a name="Encoding"></a> Encoding</span></span>
  <span data-ttu-id="5b938-136">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5b938-137">원래 파일 인코딩을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="5b938-138">**System.Text.Encoding** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <span data-ttu-id="5b938-139"><a name="FullPath"></a> FullPath</span><span class="sxs-lookup"><span data-stu-id="5b938-139"><a name="FullPath"></a> FullPath</span></span>
  <span data-ttu-id="5b938-140">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5b938-141">열려 있는 파일의 전체 경로를 지정하는 문자열을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <span data-ttu-id="5b938-142"><a name="IsSaved"></a> IsSaved</span><span class="sxs-lookup"><span data-stu-id="5b938-142"><a name="IsSaved"></a> IsSaved</span></span>
  <span data-ttu-id="5b938-143">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5b938-144">파일이 마지막으로 수정한 후 저장된 경우 **$true**를 반환하는 읽기 전용 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <span data-ttu-id="5b938-145"><a name="IsUntitled"></a> IsUntitled</span><span class="sxs-lookup"><span data-stu-id="5b938-145"><a name="IsUntitled"></a> IsUntitled</span></span>
  <span data-ttu-id="5b938-146">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="5b938-147">파일에 제목이 지정된 적이 없는 경우 **$true**를 반환하는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="5b938-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="5b938-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b938-148">See Also</span></span>
- [<span data-ttu-id="5b938-149">The ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="5b938-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="5b938-150">Windows PowerShell ISE 스크립팅 개체 모델</span><span class="sxs-lookup"><span data-stu-id="5b938-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="5b938-151">Windows PowerShell ISE 개체 모델 참조</span><span class="sxs-lookup"><span data-stu-id="5b938-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="5b938-152">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="5b938-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
