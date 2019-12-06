---
title: 모델 기반 앱에서 대시보드 및 차트를 사용 하 여 진행 상황 추적 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/4/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 70c6f97c2617c9d6084c3aa8a0861793a0c059d5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74726188"
---
# <a name="track-your-progress-with-dashboards-and-charts"></a>대시보드 및 차트를 사용하여 진행률 추적

대시보드는 앱 데이터의 컬렉션을 사용 하 고, KPI (핵심 성과 지표) 및 기타 중요 한 데이터를 쉽게 읽을 수 있는 대화형 차트 및 그래프로 표시 하는 정보를 제공 합니다. 모든 레코드 유형에 대시보드를 사용할 수 있습니다.

> [!div class="mx-imgBorder"]
> ![대시보드](media/Dashboard.png "ダッシュボード") 

-  다른 대시보드 레이아웃을 보려면 대시보드 이름 옆에 있는 아래쪽 화살표를 선택 하 고 원하는 레이아웃을 선택 합니다.
-  기본 대시보드를 선택 하려면 원하는 대시보드를 표시 한 다음 화면 위쪽에서 **기본값으로 설정** 을 선택 합니다.

   > [!div class="mx-imgBorder"]
   > ![대시보드 추가 또는 변경](media/add_dashboard.png "대시보드 추가 또는 변경") 

## <a name="create-a-new-dashboard"></a>새 대시보드 만들기

1. 새 대시보드를 만들려면 **Dynamics 365 대시보드 만들기**를 선택 합니다. 

   > [!div class="mx-imgBorder"]
   > ![새 대시보드 추가](media/new_dashboard.png "새 대시보드 추가")
   
2. 대시보드 레이아웃을 선택 하 고 **만들기**를 선택 합니다.  

   > [!div class="mx-imgBorder"]
   > ![대시보드 만들기](media/create_dashboard.png "대시보드 만들기")
 
3. 대시보드의 이름을 입력 합니다. 
4. 대시보드의 각 영역에 원하는 항목을 추가 합니다. 예를 들어 차트를 추가 해 보겠습니다. 

   > [!div class="mx-imgBorder"]
   > ![차트 추가](media/add_chart.png "차트 추가")
 
 5. 차트에 대 한 **레코드 종류** 를 선택 합니다.
 6. 차트의 데이터가 표시 되는 **보기** 를 선택 합니다.
 7. 차트를 선택한 다음 **추가**를 선택 합니다.
 8. 대시보드에 구성 요소를 계속 추가 하 고 완료 되 면 **저장**을 선택 합니다. 
 
만든 대시보드가 사용 가능한 대시보드의 드롭다운 메뉴에 표시 됩니다.

## <a name="use-charts"></a>차트 사용 

차트는 목표를 추적 하는 방법에 대 한 간략 한 보기를 제공 합니다. 또한 대화형 이므로 차트의 영역을 클릭 하거나 탭 하 여 자세한 정보를 볼 수 있습니다.

-   차트 위로 마우스를 가져가면 차트의 해당 영역에 대 한 빠른 정보를 제공 하는 도구 설명이 표시 됩니다.
-   차트의 영역을 클릭 하면 차트의 데이터에 대 한 자세한 정보가 포함 된 그리드 보기가 표시 됩니다.
-   차트를 확장 하려면 차트 **확장**  ![차트 보기](media/expandviewbutton.png "차트 뷰 확장") 단추를 선택 합니다.
-   차트에서 레코드를 보거나 차트를 새로 고치려면 ![추가 명령](media/MoreButton.png "추가 명령") 을 선택한 다음 작업: **새로 고침** 또는 **레코드 보기**를 선택 합니다.
     
     > [!div class="mx-imgBorder"]
     > ![Power Apps의 차트 보기](media/ViewOfCharts.png "Power Apps의 차트 보기")  
       

**차트 뷰 변경**
 
차트 보기를 변경 하면 특정 기간 내에 열린 기회와 같이 데이터에 대 한 다양 한 분석 결과가 표시 됩니다. 그리드 페이지에서 보기 선택기를 선택 하 여 차트 뷰를 변경할 수 있습니다.

예를 들어 "모든 기회"를 선택한 다음 다른 보기를 선택 하면 차트와 눈금이 모두 새로 고쳐집니다.

> [!div class="mx-imgBorder"]
> ![Power Apps에서 차트 뷰 변경](media/ChangeChartView.png "Power Apps에서 차트 뷰 변경")

## <a name="known-issues"></a>알려진 문제  
차트 디자이너에서 특정 계산 필드에 order by를 추가 하는 것은 지원 되지 않으며 오류가 발생 합니다.  이를 발생 시키는 계산 필드는 다른 계산 필드, 관련 엔터티 필드 또는 엔터티의 로컬 필드를 사용 합니다.



