# Update-ScriptFileInfo

Update-ScriptFileInfo cmdlet을 사용하면 기존 스크립트 파일 메타데이터를 업데이트할 수 있습니다.

## 설명

Update-ScriptFileInfo cmdlet은 스크립트에 대한 정보를 업데이트합니다.
- Update-ScriptFileInfo cmdlet은 New-ScriptFileInfo cmdlet을 사용하거나 유효한 PSScriptInfo 주석과 함께 만든 경우에만 스크립트 파일의 메타데이터를 업데이트합니다.
- New-ScriptFileInfo cmdlet을 사용하여 만들지 않은 기존 스크립트 파일에 스크립트 파일 정보를 추가할 수도 있습니다.
- -Force를 지정한 경우 New-ScriptFileInfo cmdlet을 사용하여 만들지 않은 기존 스크립트 파일에 메타데이터를 추가합니다.
- 기존 파일 앞에 스크립트 메타데이터를 추가한 후 Test-ScriptFileInfo가 구문 분석 오류로 실패할 경우 "기존 파일에 메타데이터를 추가할 수 없습니다. new-scriptfileinfo cmdlet을 사용하면 New-ScriptFileInfo cmdlet을 통해 만들지 않은 기존 스크립트 파일에 메타데이터를 추가할 수 있습니다." 등의 오류가 발생합니다.

## Cmdlet 구문

```powershell
Get-Command -Name Update-ScriptFileInfo -Module PowerShellGet -Syntax
```
## Cmdlet 온라인 도움말 참조

[Update-Script](http://go.microsoft.com/fwlink/?LinkId=619793)

## 예제 명령

```powershell
# Use Update-ScriptFileInfo cmdlet to update the script metadata
Update-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1 -Version 2.0

Test-ScriptFileInfo C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1

Version Name Author Description
------- ---- ------ -----------
2.0 Demo-ScriptWithComplet... manikb my new script file
```


### 기존 스크립트 파일에 스크립트 메타데이터 추가

```powershell
PS C:\WINDOWS\system32> New-ScriptFileInfo -Description "Script file description." -PassThru

<#PSScriptInfo

.VERSION 1.0

.GUID 1cfd45e7-4219-4cd2-af21-d8577476be09

.AUTHOR manikb

.COMPANYNAME

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES


#>

<#

.DESCRIPTION
Script file description.

#>
Param()


PS C:\WINDOWS\system32> $content = @'
   Function foo
   {
   "Foo"
   }
>>
   Foo
'@

PS C:\WINDOWS\system32>
PS C:\WINDOWS\system32> Set-Content -Value $content -Path C:\temp\ScriptFileWithoutMetadata.ps1 -Force
PS C:\WINDOWS\system32> Test-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1
Test-ScriptFileInfo : PSScriptInfo is not specified in the script file 'C:\temp\ScriptFileWithoutMetadata.ps1', use the Update-ScriptFileInfo with -Force 
or New-ScriptFileInfo cmdlet to add the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (C:\temp\ScriptFileWithoutMetadata.ps1:String) [Test-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : MissingPSScriptInfo,Test-ScriptFileInfo

PS C:\WINDOWS\system32> # Should Fail
PS C:\WINDOWS\system32> Update-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1
Test-ScriptFileInfo : PSScriptInfo is not specified in the script file 'C:\temp\ScriptFileWithoutMetadata.ps1', use the Update-ScriptFileInfo with -Force 
or New-ScriptFileInfo cmdlet to add the PSScriptInfo to the script file.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:4704 char:29
+ ...      $psscriptInfo = Test-ScriptFileInfo -LiteralPath $scriptFilePath
+                          ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (C:\temp\ScriptFileWithoutMetadata.ps1:String) [Test-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : MissingPSScriptInfo,Test-ScriptFileInfo

PS C:\WINDOWS\system32> # Should Fail
PS C:\WINDOWS\system32> Update-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1 -Force
Update-ScriptFileInfo : Description parameter is missing for adding the metadata to script file. Try again after specifying the description.
At line:1 char:1
+ Update-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1 -Force
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Update-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : DescriptionParameterIsMissingForAddingTheScriptFileInfo,Update-ScriptFileInfo

PS C:\WINDOWS\system32> Update-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1 -Force -Description "Temp script file."
PS C:\WINDOWS\system32> Test-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1

Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        ScriptFileWithoutMetadata manikb               Temp script file.


PS C:\WINDOWS\system32> Get-Content c:\temp\ScriptFileWithoutMetadata.ps1

<#PSScriptInfo

.VERSION 1.0

.GUID 855821be-811c-4eb1-a7a7-afd6081be175

.AUTHOR manikb

.COMPANYNAME

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES


#>

<#

.DESCRIPTION
Temp script file.

#>

Param()


Function foo
{
"Foo"
}

Foo

```

<!--HONumber=Aug16_HO3-->


