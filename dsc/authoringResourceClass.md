# PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성

> 적용 대상: Windows Windows PowerShell 5.0

Windows PowerShell 5.0의 PowerShell 클래스 도입으로 이제 클래스를 만들어 DSC 리소스를 정의할 수 있습니다. 클래스는 리소스의 스키마와 구현을 모두 정의하며, 따라서 별도의 MOF 파일을 만들 필요가 없습니다. **DSCResources** 폴더가 필요하지 않으므로 클래스 기반 리소스의 폴더 구조도 더 간단합니다.

클래스 기반 DSC 리소스에서 스키마는 속성 유형을 지정하는 특성으로 수정할 수 있는 클래스의 속성으로 정의됩니다. 리소스는 스크립트 리소스에 있는 **Get()**, **Set()** 및 **Test()** 메서드(**Get-TargetResource**, **Set-TargetResource** 및 **Test-TargetResource** 함수에 해당)에 의해 구현됩니다.

이 항목에서는 지정된 경로에 있는 파일을 관리하는 **FileResource**라는 간단한 리소스를 만듭니다.

DSC 리소스에 대한 자세한 내용은[사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드](authoringResource.md)를 참조하세요.

## 클래스 리소스에 대한 폴더 구조

PowerShell 클래스를 사용하여 DSC 사용자 지정 리소스를 구현하려면 다음 폴더 구조를 만듭니다. 클래스는 **MyDscResource.psm1**에 정의되어 있으며, 모듈 매니페스트는 **MyDscResource.psd1**에 정의되어 있습니다.

```
$env: psmodulepath (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## 클래스 만들기

클래스 키워드를 사용하여 PowerShell 클래스를 만듭니다. 클래스가 DSC 리소스임을 지정하려면 **DscResource()** 특성을 사용합니다. 클래스의 이름은 DSC 리소스의 이름입니다.

```powershell
[DscResource()]
class FileResource {
}
```

### 속성 선언

DSC 리소스 스키마는 클래스의 속성으로 정의됩니다. 세 가지 속성을 다음과 같이 선언합니다.

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

속성은 특성으로 수정되고 있습니다. 특성의 의미는 다음과 같습니다.

- **DscProperty(Key)**: 필수 속성입니다. 속성이 키입니다. 키로 표시된 모든 속성의 값은 구성 내 리소스 인스턴스를 고유하게 식별하도록 결합해야 합니다.
- **DscProperty(Mandatory)**: 필수 속성입니다.
- **DscProperty(NotConfigurable)**: 읽기 전용 속성입니다. 이 특성으로 표시된 속성은 구성으로 설정할 수 없지만 존재할 경우 **Get()** 메서드로 채워집니다.
- **DscProperty()**: 이 속성은 구성이 가능하지만 필수는 아닙니다.

**$Path** 및 **$SourcePath** 속성은 모두 문자열입니다. **$CreationTime**은 [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx) 속성입니다. **$Ensure** 속성은 다음과 같이 정의하는 열거형 형식입니다.

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### 메서드 구현

**Get()**, **Set()** 및 **Test()** 메서드는 스크립트 리소스의 **Get-TargetResource**, **Set-TargetResource** 및 **Test-TargetResource** 함수와 유사합니다.

이 코드에는 **$SourcePath**의 파일을 **$Path**에 복사하는 도우미 함수인 CopyFile() 함수도 포함되어 있습니다. 

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### 전체 파일
전체 클래스 파일은 다음과 같습니다.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## 매니페스트 만들기

DSC 엔진에 사용할 수 있는 클래스 기반 리소스를 만들려면 매니페스트 파일에 리소스를 내보내도록 모듈에게 지시하는 **DscResourcesToExport** 문을 포함해야 합니다. 이 매니페스트는 다음과 같습니다.

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
} 
```

## 리소스 테스트

앞에서 설명한 대로 폴더 구조에 클래스 및 매니페스트 파일을 저장한 후에는 새 리소스를 사용하는 구성을 만들 수 있습니다. DSC 구성을 실행하는 방법에 대한 정보는 [구성 시행](enactingConfigurations.md)을 참조하세요. 다음 구성은 `c:\test\test.txt`의 파일이 있는지 여부를 확인하게 되며, 없을 경우 `c:\test.txt`의 파일을 복사합니다(구성을 실행하기 전에 `c:\test.txt`를 만들어야 함).

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    } 
}
Test
Start-DscConfiguration -Wait -Force Test
```

## 참고 항목
### 개념
[사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드](authoringResource.md)


<!--HONumber=Mar16_HO4-->


