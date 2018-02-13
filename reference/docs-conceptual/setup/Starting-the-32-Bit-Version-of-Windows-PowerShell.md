---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 32비트 버전 시작"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2018
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="d0db4-103">Windows PowerShell 32비트 버전 시작</span><span class="sxs-lookup"><span data-stu-id="d0db4-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="d0db4-104">64비트 컴퓨터에 Windows PowerShell을 설치하면 64비트 버전뿐 아니라 Windows PowerShell 32비트 버전인 **Windows PowerShell (x86)**도 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="d0db4-105">Windows PowerShell을 실행하는 경우 기본적으로 64비트 버전이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="d0db4-106">그러나 32비트 버전이 필요한 모듈을 사용하거나 32비트 컴퓨터에 원격으로 연결하는 경우와 같이 **Windows PowerShell(x86)**을 실행해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="d0db4-107">Windows PowerShell 32비트 버전을 시작하려면 다음 절차 중 하나를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="d0db4-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="d0db4-108">Windows Server® 2012 R2에서</span><span class="sxs-lookup"><span data-stu-id="d0db4-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="d0db4-109">**시작** 화면에서 **Windows PowerShell(x86)**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="d0db4-110">**Windows PowerShell x86** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="d0db4-111">**서버 관리자**의 **도구** 메뉴에서 **Windows PowerShell(x86)**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-112">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell x86**을 입력하고 **Windows PowerShell(x86)**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-113">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d0db4-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="d0db4-114">Windows Server® 2012에서</span><span class="sxs-lookup"><span data-stu-id="d0db4-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="d0db4-115">**시작** 화면에서 **PowerShell**을 입력하고 **Windows PowerShell(x86)**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-116">**서버 관리자**의 **도구** 메뉴에서 **Windows PowerShell(x86)**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-117">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell**을 입력하고 **Windows PowerShell(x86)**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-118">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d0db4-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="d0db4-119">Windows® 8.1에서</span><span class="sxs-lookup"><span data-stu-id="d0db4-119">In Windows® 8.1</span></span>

- <span data-ttu-id="d0db4-120">**시작** 화면에서 **Windows PowerShell(x86)**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="d0db4-121">**Windows PowerShell x86** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="d0db4-122">Windows 8.1용 [원격 서버 관리 도구](http://go.microsoft.com/fwlink/?LinkID=304145)를 실행하는 경우 **서버 관리자 도구** 메뉴에서 Windows PowerShell x86을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="d0db4-123">**Windows PowerShell(x86)**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-124">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell x86**을 입력하고 **Windows PowerShell(x86)**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="d0db4-125">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d0db4-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="d0db4-126">Windows® 8에서</span><span class="sxs-lookup"><span data-stu-id="d0db4-126">In Windows® 8</span></span>

- <span data-ttu-id="d0db4-127">**시작** 화면에서 커서를 오른쪽 위 모서리로 이동하고 **설정**, **타일**을 차례로 클릭한 다음 **관리 도구 표시** 슬라이더를 예로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="d0db4-128">**PowerShell**을 입력하고 **Windows PowerShell(x86)**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-129">Windows 8용 [원격 서버 관리 도구](http://www.microsoft.com/download/details.aspx?id=28972)를 실행하는 경우 **서버 관리자 도구** 메뉴에서 Windows PowerShell x86을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="d0db4-130">**Windows PowerShell(x86)**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-131">**시작** 화면이나 바탕 화면에서 **PowerShell(x86)**을 입력하고 **Windows PowerShell(x86)**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0db4-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d0db4-132">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d0db4-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

