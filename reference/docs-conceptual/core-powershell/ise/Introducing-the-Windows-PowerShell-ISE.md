---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell ISE 소개"
ms.openlocfilehash: 7b529c9da7c91c6ca699c70f2674c8bc8734dd33
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="7e95b-103">Windows PowerShell ISE 소개</span><span class="sxs-lookup"><span data-stu-id="7e95b-103">Introducing the Windows PowerShell ISE</span></span>

<span data-ttu-id="7e95b-104">Windows PowerShell ISE(통합 스크립팅 환경)는 Windows PowerShell의 호스트 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="7e95b-105">Windows PowerShell ISE에서 명령을 실행하고 여러 줄 편집, 탭 완성, 구문 색 지정, 선택적 실행, 상황에 맞는 도움말, 오른쪽에서 왼쪽으로 쓰는 언어 지원 등과 같은 기능을 포함하는 단일 Windows 기반 그래픽 사용자 인터페이스에서 스크립트를 작성, 테스트, 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="7e95b-106">메뉴 항목 및 바로 가기 키를 사용하여 Windows PowerShell 콘솔에서 수행하는 것과 동일한 많은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span> <span data-ttu-id="7e95b-107">예를 들어 Windows PowerShell ISE에서 스크립트를 디버그할 때 스크립트에서 줄 중단점을 설정하려면 코드 줄을 마우스 오른쪽 단추로 클릭한 다음 **중단점 설정/해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="7e95b-108">Windows PowerShell ISE에서 이러한 기능을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-108">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="7e95b-109">여러 줄 편집: 명령 창에서 현재 줄 아래에 빈 줄을 삽입하려면 Shift+Enter를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="7e95b-110">선택적 실행: 스크립트의 일부를 실행하려면 실행할 텍스트를 선택한 다음 **스크립트 실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="7e95b-111">또는 F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-111">Or, press F5.</span></span>
- <span data-ttu-id="7e95b-112">상황에 맞는 도움말: **Invoke-Item**을 입력하고 F1 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="7e95b-113">도움말 파일이 **Invoke-Item** cmdlet의 도움말 항목에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="7e95b-114">Windows PowerShell ISE를 사용하여 해당 모양의 일부 측면을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="7e95b-115">또한 Windows PowerShell ISE에서 사용하는 함수, 별칭, 변수 및 명령을 저장할 수 있는 자체 Windows PowerShell 프로필이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="7e95b-116">Windows PowerShell ISE를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="7e95b-116">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="7e95b-117">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-117">Do one of the following:</span></span>

- <span data-ttu-id="7e95b-118">**시작**을 클릭하고 **모든 프로그램**, **Windows Powershell V2**를 차례로 가리킨 다음 **Windows Powershell ISE**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="7e95b-119">Windows PowerShell 콘솔 Cmd.exe 또는 실행 상자에서 **powershell_ise.exe**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="7e95b-120">Windows PowerShell ISE에서 도움말을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="7e95b-120">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="7e95b-121">**도움말** 메뉴에서 **Windows PowerShell 도움말**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="7e95b-122">또는 F1 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-122">Or, press F1.</span></span> <span data-ttu-id="7e95b-123">열린 파일에는 Get-Help cmdlet에서 사용 가능한 모든 도움말을 비롯하여 Windows PowerShell ISE 및 Windows PowerShell이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e95b-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>
