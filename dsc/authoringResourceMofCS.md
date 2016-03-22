# C`#`에서 DSC 리소스 작성

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

일반적으로, Windows PowerShell DSC(필요한 상태 구성) 사용자 지정 리소스는 PowerShell 스크립트로 구현됩니다. 그러나 C#으로 cmdlet을 작성하여 DSC 사용자 지정 리소스의 기능을 구현할 수도 있습니다. C#에서 cmdlet을 작성하는 방법을 알려면 [Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](https://technet.microsoft.com/en-us/library/dd878294.aspx)을 참조합니다.

C#에서 리소스를 cmdlet으로 구현하는 것 외에 MOF 스키마 만들기, 폴더 구조 만들기, 사용자 지정 DSC 리소스 가져오기 및 사용 프로세스는 [MOF를 사용하여 사용자 지정 DSC 리소스 작성](authoringResourceMOF.md)에 설명된 것과 동일합니다.

## cmdlet 기반 리소스 작성
이 예의 경우, 텍스트 파일과 그 내용을 관리하는 간단한 리소스를 구현하게 됩니다.

### MOF 스키마 작성

다음은 MOF 리소스 정의입니다.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### Visual Studio 프로젝트 설정
#### cmdlet 프로젝트 설정

1. Visual Studio를 엽니다.
1. C# 프로젝트를 만들고 이름을 입력합니다.
1. 사용 가능한 프로젝트 템플릿에서 **클래스 라이브러리**를 선택합니다.
1. **확인**을 클릭합니다.
1. System.Automation.Management.dll에 대한 어셈블리 참조를 프로젝트에 추가합니다.
1. 어셈블리 이름을 리소스 이름과 일치하도록 변경합니다. 이 경우 어셈블리의 이름은 **MSFT_XDemoFile**로 지정해야 합니다.

### cmdlet 코드 작성

다음 C# 코드는 **Get-TargetResource**, **Set-TargetResource** 및 **Test-TargetResource** cmdlet을 구현합니다.

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
           } 
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
        [Parameter(Mandatory = true)]
        public string Path { get; set; }
 
        [Parameter(Mandatory = false)]
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }
 
        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### 리소스 배포

컴파일된 dll 파일은 스크립트 기반 리소스와 비슷한 파일 구조에 저장됩니다. 다음은 이 리소스에 대한 폴더 구조입니다.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### 참고 항목
#### 개념
[MOF를 사용하여 사용자 지정 DSC 리소스 작성](authoringResourceMOF.md)
#### 관련 자료
[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](https://msdn.microsoft.com/en-us/library/dd878294.aspx)<!--HONumber=Feb16_HO4-->
