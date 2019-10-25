---
title: 캔버스 앱에 스크롤 화면 추가 | Microsoft Docs
description: PowerApps에서 캔버스 앱에 화면이 한 번에 표시할 수 있는 것보다 더 많은 유형의 콘텐츠를 표시하도록 사용자가 스크롤할 수 있는 화면을 만듭니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9e1d6f19803e5856083266ff65497e4c0b017eff
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "71987490"
---
# <a name="add-a-scrolling-screen-to-a-canvas-app-in-powerapps"></a>PowerApps의 캔버스 앱에 스크롤 화면 추가

캔버스 앱에서 사용자가 스크롤하여 다른 항목을 표시할 수 있는 화면을 만듭니다. 예를 들어, 사용자가 스크롤하여 표시할 수 있는 여러 차트의 데이터를 표시하는 전화 앱을 만듭니다.

이 섹션에서 여러 컨트롤을 추가하는 경우 휴대폰 앱이든 태블릿 앱이든 상관 없이 컨트롤은 해당 섹션 내 관련 있는 위치를 유지합니다. 화면 크기와 방향에 따라 섹션이 정렬되는 방식이 결정될 수 있습니다.  

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-scrolling-screen"></a>스크롤 화면 만들기

1. **홈** 탭에서 **새 화면**을 클릭하거나 탭합니다.

    ![앱에 화면을 추가하는 옵션][1]

2. **홈** 탭에서 **레이아웃**을 클릭하거나 탭한 다음, 무한 스크롤 캔버스를 추가하는 옵션을 클릭하거나 탭합니다.  
   
    ![무한 스크롤 캔버스를 추가하는 옵션][2]
   
    캔버스가 추가됩니다.  
   
    ![무한 스크롤 캔버스가 있는 화면, 기본적으로 표시됨][3]

## <a name="add-elements"></a>요소 추가
이제 캔버스에 일부 컨트롤을 추가하여 스크롤 화면이 작동하는 방법을 보겠습니다.

1. 추가한 캔버스에서 **삽입 탭에서 항목 추가**를 클릭하거나 탭합니다.
   
    ![][4]
2. **삽입** 탭에서 **차트**를 클릭하거나 탭한 다음 **세로 막대형 차트**를 클릭하거나 탭합니다.
   
    ![세로 막대형 차트를 추가하는 옵션][5]
   
    세로 막대형 차트가 화면에서 첫 번째 카드에 표시됩니다.  
   
    ![기본 세로 막대형 차트][7]
3. **삽입** 탭에서 **텍스트**를 클릭하거나 탭한 다음 **펜 입력**을 클릭하거나 탭합니다.  
   
    ![펜 컨트롤을 추가하는 옵션][8]
4. 차트 아래에 펜 컨트롤을 이동하고 카드의 맨 아래를 덮도록 펜 컨트롤 크기를 조정합니다.  
   
    ![펜 컨트롤 이동 및 크기 조정][9]

## <a name="add-a-section"></a>섹션 추가
이제 다른 컨트롤과 함께 다른 카드를 추가해 보겠습니다.

1. 화면 하단에서 **섹션 추가**를 클릭하거나 탭합니다.  
   
    ![섹션을 추가하는 옵션][10]
   
    새 카드가 화면에 추가됩니다.  
   
    ![기본 섹션 아래에 있는 새 카드][11]
2. 카드를 선택한 상태에서 **삽입** 탭으로 이동하고, **차트**를 클릭하거나 탭한 다음, **꺾은선형 차트**를 클릭하거나 탭합니다.
   
    새 차트가 다른 컨트롤과 함께 화면에 표시하기에 너무 큽니다.  
   
    ![새 카드의 하단에 추가된 꺾은선형 차트][12]
3. F5 키를 눌러 (또는 오른쪽 위 모서리의 재생 아이콘을 클릭하거나 탭하기) 미리 보기 모드를 엽니다.
   
    ![미리 보기 모드 열기](./media/add-scrolling-screen/open-preview.png)
4. 아래로 스크롤하여 새로운 꺾은선형 차트를 표시합니다.  
   
    ![미리 보기에 표시된 꺾은선형 차트][13]

[1]: ./media/add-scrolling-screen/add-screen.png
[2]: ./media/add-scrolling-screen/add-canvas.png
[3]: ./media/add-scrolling-screen/default-canvas.png
[4]: ./media/add-scrolling-screen/insert-visual.png
[5]: ./media/add-scrolling-screen/add-chart.png
[7]: ./media/add-scrolling-screen/default-chart.png
[8]: ./media/add-scrolling-screen/add-pen.png
[9]: ./media/add-scrolling-screen/move-resize-pen.png
[10]: ./media/add-scrolling-screen/add-section.png
[11]: ./media/add-scrolling-screen/new-card.png
[12]: ./media/add-scrolling-screen/add-line-chart.png
[13]: ./media/add-scrolling-screen/line-chart-preview.png
