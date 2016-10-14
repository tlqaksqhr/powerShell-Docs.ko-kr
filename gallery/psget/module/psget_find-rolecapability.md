# Find-RoleCapability

모듈에서 역할 기능을 찾습니다.

## 설명
Find-RoleCapability cmdlet은 모듈에서 PowerShell 역할 기능을 찾습니다. Find-RoleCapability는 등록된 리포지토리에서 모듈을 검색합니다. 이 cmdlet은 찾은 각 역할 기능에 대해 PSGetRoleCapabilityInfo 개체를 반환합니다. 역할 기능이 포함된 모듈을 설치하려면 Install-Module cmdlet에 PSGetRoleCapabilityInfo 개체를 전달할 수 있습니다.
PowerShell 역할 기능은 사용자가 JEA(Just Enough Administration) 끝점에서 사용자가 사용할 수 있는 명령, 응용 프로그램 등을 정의합니다. 역할 기능은 확장명이 .psrc인 파일에서 정의됩니다.

- Find-RoleCapability는 버전 매개 변수(MinimumVersion, RequiredVersion, AllVersions)를 사용하여 필터링할 수 있습니다.
  - 이러한 매개 변수는 함께 사용할 수 없습니다.
  - 이 버전 매개 변수는 와일드카드 없이 단일 모듈 이름과 함께 사용해야 합니다.
  - RequiredVersion 매개 변수를 지정하지 않으면 Find-RoleCapability는 지정된 최소 버전과 같거나 그 이상인 최신 버전의 모듈 또는 최소 버전이 지정되지 않은 경우 최신 버전의 모듈을 반환합니다.
  - RequiredVersion 매개 변수를 지정하면 Find-RoleCapability는 지정된 버전과 정확하게 일치하는 버전의 모듈만 반환합니다.
- Find-RoleCapability는 -Tag 매개 변수를 사용하여 모듈 메타데이터를 필터링할 수 있습니다.
- Find-RoleCapability는 -Filter 매개 변수를 사용하여 리포지토리 관련 검색 언어를 필터링할 수 있습니다.
- Find-RoleCapability는 등록된 모든 또는 일부 리포지토리의 모듈을 필터링할 수 있습니다.

## Cmdlet 구문
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## Cmdlet 온라인 도움말 참조

[Find-RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## 예제 명령
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

<!--HONumber=Aug16_HO3-->


