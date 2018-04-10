---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_filelist_feature
ms.openlocfilehash: 92dd22aaf9a1ce3ac40372ffc11d26d8c3e79dd1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2018
---
# <a name="filelist-feature-in-the-gallery"></a><span data-ttu-id="18c63-103">갤러리의 FileList 기능</span><span class="sxs-lookup"><span data-stu-id="18c63-103">FileList Feature in the Gallery</span></span>

<span data-ttu-id="18c63-104">갤러리에 게시된 모든 항목의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18c63-104">You are able to view the contents in all items published in the gallery.</span></span>

<span data-ttu-id="18c63-105">이 기능은 항목 내의 파일 나열 및 지원되는 파일 형식에 대한 파일 내용 표시의 두 부분으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18c63-105">This feature includes two parts: listing the files within the item, and displaying file contents for supported file types.</span></span> <span data-ttu-id="18c63-106">현재 파일 내용 표시가 지원되는 파일 확장명은 .ps1, .psm1, .psd1, .ps1xml, .xml 및 .txt입니다.</span><span class="sxs-lookup"><span data-stu-id="18c63-106">Currently we support displaying the contents of the following file extensions: .ps1, .psm1, .psd1, .ps1xml, .xml and .txt.</span></span> <span data-ttu-id="18c63-107">이후 릴리스에서는 더 많은 파일 확장명이 지원될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="18c63-107">We will be supporting more file extensions in the next releases.</span></span>

## <a name="where-to-find-filelist"></a><span data-ttu-id="18c63-108">FileList를 찾을 수 있는 위치</span><span class="sxs-lookup"><span data-stu-id="18c63-108">Where to Find FileList</span></span>
<span data-ttu-id="18c63-109">각 개별 항목 페이지에서 FileList 섹션과 **표시** 링크를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18c63-109">On each individual item page, you will be able to find FileList section and a **Show** link.</span></span> <span data-ttu-id="18c63-110">표시를 클릭하면 항목에 포함된 항목의 전체 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="18c63-110">Click on the Show and you will find a complete list of items contained in the item.</span></span>

<span data-ttu-id="18c63-111">지원되는 각 파일 형식이 하이퍼링크로 표시되며, 클릭하면 파일 내용이 PowerShell 구문 강조로 표시된 새 페이지로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="18c63-111">Each supported file type is displayed as a hyperlink, and clicking it will take you to a new page with file contents displayed in PowerShell syntax highlighting.</span></span> <span data-ttu-id="18c63-112">화면 맨 위에 표시된 항목의 제목 또는 버전을 클릭하면 항목 세부 정보 페이지로 다시 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="18c63-112">Clicking on the title or the version of the item, which is displayed at the top of the screen, will bring you back to item detail page.</span></span>