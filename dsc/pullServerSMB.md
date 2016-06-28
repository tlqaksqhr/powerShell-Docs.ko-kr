---
title: "DSC SMB 끌어오기 서버 설정"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 35ac9b38086b12fb48844c56a488854f63529e21

---

# DSC SMB 끌어오기 서버 설정

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC [SMB](https://technet.microsoft.com/en-us/library/hh831795.aspx) 끌어오기 서버는 대상 노드에서 DSC 구성 파일 및/또는 DSC 리소스를 요청 시 사용할 수 있게 해주는 SMB 파일 공유입니다.

DSC에 대해 SMB 끌어오기 서버를 사용하려면 다음을 수행해야 합니다.
- PowerShell 4.0 이상을 실행 중인 서버에서 SMB 파일 공유 설정
- PowerShell 4.0 이상을 실행 중인 클라이언트에서 해당 SMB 공유에서 끌어오도록 구성

## XSmbShare 리소스를 사용하여 SMB 파일 공유 만들기

다양한 방법으로 SMB 파일 공유를 설정할 수 있지만 여기서는 DSC를 사용하여 설정하는 방법을 살펴봅니다.

### XSmbShare 리소스 설치

[Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet을 호출하여 **xSmbShare** 모듈을 설치합니다.
>**참고**: **Install-Module**은 PowerShell 5.0에 포함된 **PowerShellGet** 모듈에 포함되어 있습니다. [PackageManagement PowerShell 모듈 미리 보기](https://www.microsoft.com/en-us/download/details.aspx?id=49186)에서 PowerShell 3.0 및 4.0용 **PowerShellGet** 모듈을 다운로드할 수 있습니다. **xSmbShare**에는 SMB 파일 공유를 만드는 데 사용할 수 있는 DSC 리소스 **xSmbShare**가 포함되어 있습니다.

### 디렉터리 및 파일 공유 만들기

다음 구성에서는 [파일](fileResource.md) 리소스를 사용하여 공유의 디렉터리를 만들고 **xSmbShare** 리소스를 사용하여 SMB 공유를 설정합니다.

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }
        
    }
 
}
```

이 구성은 아직 없는 경우 `C:\DscSmbShare` 디렉터리를 만든 다음 해당 디렉터리를 SMB 파일 공유로 사용합니다. 파일 공유에 쓰거나 파일 공유에서 삭제해야 하는 모든 계정에는 **FullAccess**를 부여해야 하고 공유에서 구성 및/또는 DSC 리소스를 가져오는 모든 클라이언트 노드에는 **ReadAccess**를 부여해야 합니다. 왜냐하면 DSC는 기본적으로 시스템 계정으로 실행되므로 컴퓨터 자체에서 공유에 액세스할 수 있어야 하기 때문입니다.


### 파일 시스템에 끌어오기 클라이언트에 대한 액세스 권한 부여

클라이언트 노드에 **ReadAccess**를 부여하면 해당 노드에서 SMB 공유에 액세스할 수 있지만 해당 공유 내의 파일이나 폴더에는 액세스할 수 없습니다. SMB 공유 폴더 및 하위 폴더에 대한 액세스 권한을 클라이언트 노드에 명시적으로 부여해야 합니다. DSC에서 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 모듈에 포함된 **cNtfsPermissionEntry** 리소스 사용을 추가하여 이렇게 할 수 있습니다. 다음 구성에서는 끌어오기 클라이언트에 ReadAndExecute 액세스를 부여하는 **cNtfsPermissionEntry** 블록을 추가합니다.

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }

        cNtfsPermissionEntry PermissionSet1 {
            
        Ensure = 'Present'
        Path = 'C:\DSCSMB'
        Principal = 'myDomain\Contoso-Server$'
        AccessControlInformation = @(
            cNtfsAccessControlInformation
            {
                AccessControlType = 'Allow'
                FileSystemRights = 'ReadAndExecute'
                Inheritance = 'ThisFolderSubfoldersAndFiles'
                NoPropagateInherit = $false
            }
        )
        DependsOn = '[File]CreateFolder'
        
        }
 
        
    }
 
}
```

## 구성 및 리소스 배치

클라이언트 노드가 SMB 공유 폴더에서 끌어올 모든 구성 MOF 파일 및/또는 DSC 리소스를 저장합니다.

모든 구성 MOF 파일의 이름은 _ConfigurationID_.mof로 지정해야 합니다. 여기서 _ConfigurationID_는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다. 끌어오기 클라이언트 구성에 대한 자세한 내용은 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)을 참조하세요.

>**참고:** SMB 끌어오기 서버를 사용하는 경우 구성 ID를 사용해야 합니다. SMB에서는 구성 이름이 지원되지 않습니다.

클라이언트에 필요한 모든 리소스를 SMB 공유 폴더에 압축된 `.zip` 파일로 배치해야 합니다.  

## MOF 체크섬 만들기
구성 MOF 파일은 대상 노드의 LCM이 구성에 대한 유효성을 검사할 수 있도록 체크섬 파일과 함께 사용해야 합니다. 체크섬을 만들려면 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet을 호출합니다. 이 cmdlet은 구성 MOF가 있는 폴더를 지정하는 **Path** 매개 변수를 사용합니다. cmdlet은 `ConfigurationMOFName.mof.checksum`이라는 체크섬 파일을 만들며, 여기서 `ConfigurationMOFName`은 구성 mof 파일의 이름입니다. 지정된 폴더에 구성 MOF 파일이 두 개 이상 있는 경우, 폴더에 있는 각 구성에 대해 체크섬이 만들어집니다.

체크섬 파일은 구성 MOF 파일과 동일한 디렉터리에 있어야 하며(기본적으로 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`), 동일한 이름에 확장명으로 `.checksum`을 사용해야 합니다.

>**참고**: 어떤 식으로든 구성 MOF 파일을 변경하는 경우 체크섬 파일도 다시 만들어야 합니다.

## 감사의 말

다음 분들에게 특히 감사드립니다.

- Mike F. Robbins. 그가 게시한 DSC에 SMB 사용에 대한 게시물은 이 항목의 내용을 알리는 데 도움이 되었습니다. 그의 블로그는 [Mike F Robbins](http://mikefrobbins.com/)입니다.
- Serge Nikalaichyk. **cNtfsAccessControl** 모듈을 작성했습니다. 이 모듈의 원본은 https://github.com/SNikalaichyk/cNtfsAccessControl에 있습니다.

## 참고 항목
- [Windows PowerShell 필요한 상태 구성 개요](overview.md)
- [구성 시행](enactingConfigurations.md)
- [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)

 



<!--HONumber=Jun16_HO4-->


