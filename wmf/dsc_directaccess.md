# DSC 리소스 메서드에 직접 액세스


DSC 리소스 및 해당 메서드(Get, Set 또는 Test)에 대한 직접 액세스를 허용하도록 `Invoke-DscResource` cmdlet이 추가되었습니다. 이 cmdlet은 DSC 리소스를 활용하고자 하는 타사에서 사용할 수 있습니다. 일반적으로 이 cmdlet은 `refreshMode = ‘Disabled’`와 함께 사용되지만 refreshMode의 설정과 관계없이 사용할 수 있습니다. 다음은 새로운 cmdlet을 사용하는 방법에 대한 몇 가지 예입니다.

## 파일이 있는지 확인

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## 파일이 있는지 테스트

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## 파일의 내용 가져오기

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```


<!--HONumber=Apr16_HO4-->


