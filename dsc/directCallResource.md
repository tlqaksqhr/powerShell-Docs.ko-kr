---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 리소스 메서드를 직접 호출
ms.openlocfilehash: 3ec3a3a8da615f45f3fdd28b1c1e46e312507ed5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189621"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="33abc-103">DSC 리소스 메서드를 직접 호출</span><span class="sxs-lookup"><span data-stu-id="33abc-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="33abc-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="33abc-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="33abc-105">[Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet을 사용해 DSC 리소스의 함수 또는 메서드(MOF 기반 리소스의 **Get-TargetResource**, **Set-TargetResource**및 **Test-TargetResource** 함수 또는 클래스 기반 리소스의 **Get**, **Set** 및 **Test** 메서드)를 직접 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33abc-105">You can use the [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="33abc-106">이 기능은 DSC 리소스를 사용하려는 타사에서, 또는 리소스를 개발하는 유용한 도구로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33abc-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="33abc-107">일반적으로 이 cmdlet은 메타구성 속성 `refreshMode = 'Disabled'`와 함께 사용되지만 **refreshMode**의 설정과 관계없이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33abc-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="33abc-108">**Invoke-DscResource** cmdlet을 호출하는 경우 **Method** 매개 변수를 사용해 호출할 메서드 또는 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="33abc-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="33abc-109">해시 테이블을 **Property** 매개 변수 값으로 전달해 리소스의 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="33abc-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="33abc-110">다음은 리소스 메서드를 직접 호출하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="33abc-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="33abc-111">파일이 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="33abc-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="33abc-112">파일이 있는지 테스트</span><span class="sxs-lookup"><span data-stu-id="33abc-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="33abc-113">파일의 내용 가져오기</span><span class="sxs-lookup"><span data-stu-id="33abc-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="33abc-114">**참고:** 복합 리소스 메서드를 직접 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33abc-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="33abc-115">대신 복합 리소스를 구성하는 기본 리소스의 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="33abc-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="33abc-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33abc-116">See Also</span></span>
- [<span data-ttu-id="33abc-117">Writing a custom DSC resource with MOF(MOF를 사용하여 사용자 지정 DSC 리소스 작성)</span><span class="sxs-lookup"><span data-stu-id="33abc-117">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="33abc-118">PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성</span><span class="sxs-lookup"><span data-stu-id="33abc-118">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="33abc-119">DSC 리소스 디버그</span><span class="sxs-lookup"><span data-stu-id="33abc-119">Debugging DSC resources</span></span>](debugResource.md)