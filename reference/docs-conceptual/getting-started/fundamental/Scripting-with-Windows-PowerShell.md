---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell을 사용한 스크립팅(Scripting with Windows PowerShell)"
ms.assetid: c425d27a-bb41-4947-8d73-ba5480bc8ee0
ms.openlocfilehash: 693d1bb9329dbb280453fc16738eda63c466e156
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2017
---
# <a name="scripting-with-windows-powershell"></a><span data-ttu-id="9dac3-103">Windows PowerShell을 사용한 스크립팅(Scripting with Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9dac3-103">Scripting with Windows PowerShell</span></span>

<span data-ttu-id="9dac3-104">Windows PowerShell®은 시스템 관리용으로 특별히 설계된 작업 기반 명령줄 셸 및 스크립트 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="9dac3-105">.NET Framework를 기반으로 제작된 Windows PowerShell을 사용하면 IT 전문가와 고급 사용자가 Windows 운영 체제 및 Windows에서 실행되는 응용 프로그램의 관리를 쉽게 제어하고 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-105">Built on the .NET Framework, Windows PowerShell helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="9dac3-106">*cmdlet*이라는 Windows PowerShell 명령을 사용하면 명령줄에서 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-106">Windows PowerShell commands, called *cmdlets*, let you manage the computers from the command line.</span></span> <span data-ttu-id="9dac3-107">Windows PowerShell *공급자*는 파일 시스템에 액세스하는 것처럼 쉽게, 레지스트리 및 인증서 저장소와 같은 데이터 저장소에 액세스하도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-107">Windows PowerShell *providers* let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="9dac3-108">또한 Windows PowerShell에는 서식 있는 식 파서와 완전히 개발된 스크립트 언어가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-108">In addition, Windows PowerShell has a rich expression parser and a fully developed scripting language.</span></span>

<span data-ttu-id="9dac3-109">Windows PowerShell에는 다음과 같은 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-109">Windows PowerShell includes the following features:</span></span>

- <span data-ttu-id="9dac3-110">레지스트리, 서비스, 프로세스 및 이벤트 로그 관리, WMI(Windows Management Instrumentation) 사용 등과 같은 일반 시스템 관리 작업을 수행하기 위한 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9dac3-110">Cmdlets for performing common system administration tasks, such as managing the registry, services, processes, and event logs, and using Windows Management Instrumentation (WMI).</span></span>
- <span data-ttu-id="9dac3-111">기존 스크립트 및 명령줄 도구에 대한 작업 기반 스크립트 언어 및 지원</span><span class="sxs-lookup"><span data-stu-id="9dac3-111">A task-based scripting language and support for existing scripts and command-line tools.</span></span>
- <span data-ttu-id="9dac3-112">일관된 디자인</span><span class="sxs-lookup"><span data-stu-id="9dac3-112">Consistent design.</span></span> <span data-ttu-id="9dac3-113">Cmdlet과 시스템 데이터 저장소에서 공통된 구문과 명명 규칙을 사용하므로, 데이터를 쉽게 공유할 수 있으며, 다시 포맷하거나 조작하지 않고 한 cmdlet의 출력을 다른 cmdlet의 입력으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-113">Because cmdlets and system data stores use common syntax and naming conventions, data can be shared easily and the output from one cmdlet can be used as the input to another cmdlet without reformatting or manipulation.</span></span>
- <span data-ttu-id="9dac3-114">운영 체제의 간소화된 명령 기반 탐색 - 파일 시스템을 탐색하는 데 사용하는 것과 동일한 기술을 사용하여 레지스트리 및 다른 데이터 저장소를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-114">Simplified, command-based navigation of the operating system, which lets users navigate the registry and other data stores by using the same techniques that they use to navigate the file system.</span></span>
- <span data-ttu-id="9dac3-115">강력한 개체 조작 기능</span><span class="sxs-lookup"><span data-stu-id="9dac3-115">Powerful object manipulation capabilities.</span></span> <span data-ttu-id="9dac3-116">개체를 직접 조작하거나 다른 도구 또는 데이터베이스에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-116">Objects can be directly manipulated or sent to other tools or databases.</span></span>
- <span data-ttu-id="9dac3-117">확장 가능한 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9dac3-117">Extensible interface.</span></span> <span data-ttu-id="9dac3-118">독립 소프트웨어 공급업체 및 엔터프라이즈 개발자가 사용자 지정 도구 및 유틸리티를 빌드하여 소프트웨어를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dac3-118">Independent software vendors and enterprise developers can build custom tools and utilities to administer their software.</span></span>

