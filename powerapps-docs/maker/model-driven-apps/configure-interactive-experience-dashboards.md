---
title: Power Apps에서 모델 기반 앱 상호 작용 환경 대시보드 구성 | Microsoft Docs
description: Power Apps에서 상호 작용 환경 대시보드를 구성하는 방법 이해
keywords: 상호 작용 대시보드; 고객 서비스; Microsoft Dynamics 365; 상호 작용 서비스 허브
author: Mattp123
ms.author: matp
manager: kvivek
ms.custom: ''
ms.date: 04/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: d1446a95-14bf-4b15-a905-72fce07f4c76
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fefeebb0106907e59ea1fd5a13d620cdeb315774
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2885008"
---
# <a name="configure-model-driven-app-interactive-experience-dashboards"></a>모델 기반 앱 상호 작용 환경 대시보드 구성

대화식 경험 대시 보드는 서비스 담당자와 같은 앱 사용자가 워크로드 정보를 보고 조치를 취할 수 있는 원스톱 작업 영역이 될 수 있습니다. 대시보드는 완벽하게 구성할 수 있는 보안 역할 기반이며 실시간으로 여러 스트림에서 워크로드 정보를 제공합니다. 대화형 대시보드 사용자는 특정 레코드를 찾는 응용 프로그램 페이지가 필요하지 않습니다. 그들은 대시 보드에서 직접 작업할 수 있습니다. 

 상호 작용 환경의 대시보드에는 멀티 스트림과 단일 스트림 두 종류의 양식이 제공됩니다. 또한 멀티 스트림 대시보드는 홈 페이지 또는 엔터티 특정 대시보드가 될 수 있습니다. 엔터티 특정 대시보드는 사용자 인터페이스의 여러 부분에서 구성되며 부분적으로 엔터티 특정 구성 정보로 미리 로드됩니다.  
  
 멀티 스트림 대시보드는 여러 데이터 스트림을 통해 실시간으로 데이터를 표시합니다. 대시보드에서 구성할 수 있는 스트림 수에는 제한이 없습니다. 스트림의 데이터는 한 엔터티만을 기반으로 할 수 있지만 각 스트림은 다른 엔터티를 기반으로 할 수 있습니다. 엔터티 특정 대시보드에서 모든 스트림은 같은 엔터티를 기반으로 합니다. 데이터는 **내 활동**, **내 서비스 케이스** 또는 **금융 큐의 서비스 케이스** 같은 다양한 보기나 큐에서 이동합니다. 
  
 단일 스트림 대시보드는 엔터티 보기 또는 큐를 기반으로 한 스트림을 통해 데이터를 실시간으로 표시합니다. 타일은 대시보드 오른쪽에 위치하며 항상 표시됩니다. 단일 스트림 대시보드는 일반적으로 수는 적지만 더 복잡하거나 에스컬레이션된 서비스 케이스를 모니터링하는 계층 2 서비스 리드 또는 관리자에게 유용합니다.  
  
 멀티 스트림과 단일 스트림 대시보드에는 우선 순위 또는 상태별 서비스 케이스 같이 관련 레코드 수를 제공하는 대화식 차트가 포함되어 있습니다. 이러한 차트는 시각적 필터 역할도 합니다. 시각적 필터(대화식 차트)는 단일 스트림 대시보드의 여러 엔터티를 기반으로 하고 데이터 스트림의 엔터티는 시각적 필터 엔터티를 정의합니다.   
  
 글로벌 필터 및 시간 프레임 필터가 있는 추가 필터링을 적용할 수 있습니다. 글로벌 필터는 모든 차트 및 필터 엔터티를 기반으로 하는 스트림 및 타일의 필드 수준에서 작동합니다(시각적 필터를 구성할 때 필터 엔터티를 지정). 
  
> [!NOTE]
>  대화식 대시보드는 솔루션에 따라 달라지며 다른 환경에 솔루션으로 내보낸 다음 가져올 수 있습니다. 그러나 스트림과 타일이 기반으로 하는 큐는 솔루션에 따라 달라지지 않습니다. 대시보드 솔루션을 대상 시스템으로 가져오기 전에 **설정** > **서비스 관리** > **큐**에서 대상 시스템에 큐를 수동으로 만들어야 합니다. 큐를 만든 다음 대시보드 솔루션을 대상 시스템에 가져오고 스트림이나 새로 만든 큐를 적절하게 할당하는 큐를 기반으로 하는 타일을 편집합니다.  
  
 이 항목의 그림은 헤더 창이 있는 멀티 스트림 및 단일 스트림 대시보드를 보여줍니다. 헤더 아래에서 시각적 필터와 스트림을 볼 수 있습니다. 단일 스트림 대시보드에는 타일도 있습니다. 각 대시보드 타입의 경우 표시되는 여러 가지 레이아웃에서 선택할 수 있습니다. 대시보드 헤더에는 왼쪽부터 오른쪽까지 대시보드 선택기, 새로 고침, 시각적 필터 아이콘, 글로벌 필터 아이콘 및 시간 프레임 필터 등과 같은 컨트롤과 선택 가능한 아이콘이 포함되어 있습니다.  
  
### <a name="multi-stream-dashboard-standard-view"></a>멀티 스트림 대시보드 표준 보기  
 멀티 스트림 대시보드에는 아래에 데이터 스트림이 있는 시각적 필터의 행이 상단에 표시됩니다.  
 
![멀티 스트림 대화형 대시보드](media/interactive-dashboards-multi-stream.png) 
   
### <a name="multi-stream-dashboard-tile-view"></a>멀티 스트림 대시보드 타일 보기  
 같은 대시보드이며 타일 보기만 표시됩니다.  
  
 ![멀티 스트림 대시보드 타일 보기](media/interactive-dashboards-multi-stream-tiles.png "멀티 스트림 대시보드 타일 보기")  
  
### <a name="multi-stream-dashboard-layouts"></a>멀티 스트림 대시보드 레이아웃  
 멀티 스트림 대시보드의 경우 네 가지 레이아웃 중에서 선택할 수 있습니다.  

 > [!div class="mx-imgBorder"] 
 > ![멀티 스트림 대시보드 레이아웃](media/interactive-dashboards-multi-stream-layout.png "멀티 스트림 대시보드 레이아웃")  
  
### <a name="multi-stream-entity-specific-dashboard"></a>멀티 스트림 엔터티 특정 대시보드  
 케이스 엔터티를 위한 엔터티별 대시보드가 여기에 표시됩니다.  
  
 ![시작된 서비스 케이스 대시보드](media/interactive-dashboard-cases-entity-specific.png "시작된 서비스 케이스 대시보드")  
  
### <a name="single-stream-dashboard"></a>단일 스트림 대시보드  
 단일 스트림 대시보드에는 왼쪽에 데이터 스트림과 오른쪽에 시각적 필터 및 타일이 포함되어 있습니다.  
  
 ![단일 스트림 대화식 서비스 허브 대시보드](media/interactive-dashboards-single-stream.png "단일 스트림 대화식 서비스 허브 대시보드")  
  
### <a name="single-stream-dashboard-layouts"></a>단일 스트림 대시보드 레이아웃  
 단일 스트림 대시보드의 경우 네 가지 레이아웃 중에서 선택할 수 있습니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![단일 스트림 대시보드 레이아웃.](media/interactive-dashboards-single-stream-layout.png "단일 스트림 대시보드 레이아웃.")  
  
<a name="BKMK_Enable"></a>   
## <a name="configure-filter-fields-and-security-roles-for-the-interactive-dashboards"></a>대화식 대시보드를 위한 필터 필드 및 보안 역할 구성  
 상호 작용 대시보드를 구성할 때 첫 번째 작업은 필터 필드 및 보안 역할을 활성화하여 상호 작용 대시보드가 구성될 수 있도록 하는 것입니다. 기본적으로 모든 엔터티와 사용자 지정 엔터티에 대해 대화형 대시보드가 활성화됩니다. 
  
### <a name="configure-filter-fields"></a>필터 필드 구성  
 필드가 글로벌 필터에 나타나고 데이터 스트림 정렬에 포함되려면 두 개의 플래그를 설정해야 합니다:

- 상호 작용 환경의 글로벌 필터에 표시
- 상호 작용 환경 대시보드에서 정렬 가능

이 예제에는 **IsEscalated** 필드에 대해 서비스 케이스 엔터티에서 사용할 수 있는 두 개의 대화형 대시 보드 옵션이 있습니다.  

 > [!div class="mx-imgBorder"] 
 > ![글로벌 필터 및 정렬을 위한 필드 사용](media/enable-filter-sort.png "글로벌 필터 및 정렬을 위한 필드 사용")  
  
### <a name="configure-the-appears-in-global-filter-in-interactive-experience-option"></a>'상호 작용 환경의 글로벌 필터에 표시' 옵션 구성

1. [솔루션 탐색기](advanced-navigation.md#solution-explorer)를 엽니다.  
2. **구성 요소**에서 **엔터티**를 확장한 다음 원하는 엔터티를 확장합니다.
3. 탐색 창에서 **필드**를 선택하고 표에서 활성화하려는 필드를 더블클릭합니다.
4. **일반** 탭에서 **상호 작용 환경의 글로벌 필터에 표시** 확인란을 선택합니다. **저장 후 닫기**를 선택합니다.
5. **모든 맞춤 항목 게시**를 선택하여 변경 사항을 발효시킵니다.
  
 **상호 작용 환경의 글로벌 필터에 표시**에 대해 활성화하는 필드는 대시보드 머리글에서 전역 필터 아이콘을 클릭하면 전역 필터 플라이아웃 창에 나타납니다. 플라이아웃 창에서 서비스 담당자는 차트 및 필터 엔터티를 기반으로 하는 스트림과 타일에서 글로벌적으로 필터링하려는 필드를 선택할 수 있습니다.   
  
 글로벌 필터 플라이아웃 창이 여기에 표시됩니다.  
  
 ![글로벌 필터 필드 두 개 추가](media/global-filter-escalated.png "글로벌 필터 필드")  
  
> [!TIP]
>  우선 순위 또는 상태 같은 필드를 기반으로 시각적 필터를 구성할 때 가장 좋은 방법은 글로벌 필터에 나타나도록 이러한 필드(우선 순위, 상태)를 활성화하는 것입니다.  
  
### <a name="configure-the-sortable-in-interactive-experience-dashboard-option"></a>'상호작용 환경 대시보드에서 정렬 가능' 옵션 구성
  
1. [솔루션 탐색기](advanced-navigation.md#solution-explorer)를 엽니다.  
2. **구성 요소**에서 **엔터티**를 확장한 다음 원하는 엔터티를 확장합니다.
3. 탐색 창에서 필드를 선택하고 표에서 활성화하려는 필드를 더블클릭합니다.
4. **일반** 탭에서 **상호 작용 환경 대시보드에서 정렬 가능** 확인란을 선택합니다. **저장 후 닫기**를 선택합니다.
5. **모든 맞춤 항목 게시**를 선택하여 변경 사항을 발효시킵니다.
  
정렬을 위해 구성하는 필드는 스트림 헤더에서 드롭다운 목록에 나타납니다. 

다음 그림은 드롭다운 목록에서 정렬에 사용할 수 있는 필드 목록이 있는 대화 상자를 보여줍니다. 기본 정렬은 항상 **수정한 날짜** 필드에 설정됩니다.  
  
 ![드롭다운 목록으로 정렬](media/sort-field.png "드롭다운 목록으로 정렬")    
    
### <a name="enable-security-roles"></a>보안 역할 사용  
 대화식 대시보드를 보는 데 사용할 수 있는 보안 역할을 선택하고 활성화합니다.  
  
#### <a name="enable-security-roles-for-interactive-dashboards"></a>상호 작용 대시보드에 대한 보안 역할 활성화

1. [솔루션 탐색기](advanced-navigation.md#solution-explorer)를 엽니다.  
  
2. **구성 요소**에서 **대시보드**를 선택합니다.  
  
3.  표에서 원하는 대화식 대시보드를 선택하고 작업 표시줄에서 **보안 역할 활성화**를 선택합니다.  
  
4.  **보안 역할 할당** 대화 상자에서 **선택한 보안 역할에만 표시** 옵션을 선택한 다음 사용하려는 역할을 선택합니다. **확인**을 선택합니다.  
  
5.  **모든 맞춤 항목 게시**를 선택하여 변경 사항을 발효시킵니다.    
  
 ![보안 역할 사용](media/security-roles.png "보안 역할 사용")    
  
<a name="BKMK_Configure"></a>   
## <a name="configure-interactive-experience-dashboards"></a>상호 작용 환경 대시보드 구성  
 다음 섹션에서는 대화식 대시보드의 다양한 유형을 구성하는 방법을 설명합니다.  
  
### <a name="configure-a-multi-stream-interactive-dashboard-using-the-4-column-layout"></a>4열 레이아웃을 사용하여 멀티 스트림 대화형 대시보드를 구성합니다.  
 
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다. 
  
2.  **데이터** > **엔터티**를 선택하고 원하는 엔터티를 선택합니다. 

3.  **대시보드** 탭을 선택한 다음 도구 모음에서 **대시보드 추가**를 선택합니다. 
  
4.  레이아웃을 2, 3 또는 4열 너비 중에서 선택합니다.  
  
5.  대시보드 양식이 열리면 여기에 표시된 것처럼 양식 상단에 필터링 정보를 입력합니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![시각적 필터 추가](media/interactive-dashboards-add-visual-filters.png "시각적 필터 추가")  
  
   - **필터 엔터티**: 시각적 필터 및 글로벌 필터 속성은 이 엔터티를 기반으로 합니다.  
      
    - **엔터티 보기**: 시각적 필터는 이 보기를 기반으로 합니다.  
      
    - **필터 기준**: 시간 프레임 필터가 적용되는 필드입니다.  
      
    - **시간 프레임**: **필터 기준** 필드에 대한 기본 시간 프레임 필터 값입니다.  
      
 필터링 정보를 지정한 후 차트 및 데이터 스트림에 대한 구성 요소 추가를 시작합니다. 구성 요소를 추가하려면 차트 또는 스트림의 중앙에 있는 요소를 선택하고 대화 상자가 나타나면 다음 그림에 표시된 것처럼 드롭다운 목록에서 요구되는 정보를 선택합니다.  
  
 **우선 순위별 서비스 케이스** 도넛형 차트를 추가합니다.
  
 > [!div class="mx-imgBorder"] 
 > ![도넛형 차트 구성 요소 추가.](media/interactive-dashboards-add-chart-circle.png "도넛형 차트 구성 요소 추가.")  
  
 막대형 차트 또는 원형 차트 같은 일부 차트는 시스템에 저장된 데이터를 보여주도록 렌더링됩니다. 도넛형 차트와 태그 차트는 정적 이미지를 로드하고 실제 데이터의 미리 보기를 표시하지 않습니다.  
  
> [!NOTE]
>  시각적 필터용으로 구성된 차트는 **필터** 엔터티와 관련된 엔터티 필드를 사용할 수 있습니다. 관련 엔터티 필드에 따라 차트를 사용하면, 고개 지원 담당자가 이러한 관련 엔터티 필드를 사용하여 차트를 필터링할 수 있습니다. 관련 엔터티를 바탕으로 하는 필드는 일반적으로 차트 구성 창에 **수정한 사람(대리인)** 필드처럼 '필드 이름(엔터티 이름)' 형식입니다. 다중 엔터티 차트를 만들려면 관련 엔터티의 필드를 보기에 추가하고 차트를 만들 때 이러한 필드를 사용해야 합니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![시각적 필터를 위해 차트 작성](media/interactive-dashboard-visual-charts-x-y-axes.PNG "시각적 필터를 위해 차트 작성")  
  
 그런 다음 스트림을 구성합니다. 차트에 구성 요소를 추가하는 것처럼 스트림 패널 내의 요소를 선택합니다. 대화 상자가 나타나면 해당 스트림이 사용하기 원하는 요소에 따라 **보기** 또는 **큐**를 선택합니다. 다음 그림에 표시된 것처럼 필수 정보를 입력합니다.  
  
 여기에 보이는 것처럼 **작업 가능한 항목**에 대한 스트림을 구성합니다.  
  
 ![활성 서비스 케이스 스트림 추가.](media/add-stream-dashboard.png "활성 서비스 케이스 스트림 추가.")  

> [!NOTE]
>  **큐** 옵션은 엔터티 큐 사용이 가능한 경우에 대화 상자에서 사용할 수 있습니다. 대시보드 엔터티, 엔터티 큐가 활성화되지 않은 경우 대화 상자에 **큐** 옵션이 나타나지 않습니다. 큐를 사용할 수 없는 엔터티에 대한 **보기 옵션**을 대시보드 스트림에 사용할 수 있습니다.    
 
다음 그림은 완전하게 구성된 차트 패널과 스트림 패널의 예입니다:  
 
 > [!div class="mx-imgBorder"] 
 > ![완전히 구성된 대시보드](media/example-stream-visual.png "완전히 구성된 대시보드")  
  
 대시보드 구성을 완료한 후 변경 내용이 적용되도록 사용자 지정을 저장하고 게시합니다.   
  
#### <a name="edit-or-delete-individual-streams-of-an-existing-dashboard"></a>기존 대시보드의 개별 스트림을 편집 또는 삭제합니다.  
  
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.   
  
2. **데이터** > **엔터티**를 선택하고 원하는 엔터티를 선택합니다. **대시보드** 탭을 선택합니다.  
  
     또는  
   
   [솔루션 탐색기](advanced-navigation.md#solution-explorer)를 열고 **구성 요소**에서 **대시보드**를 선택합니다.
  
3.  표에서 편집하려는 대화식 대시보드를 선택하여 엽니다.  
  
4.  편집하려는 스트림을 선택한 다음 **구성 요소 편집**을 선택합니다.  
  
5.  뷰 또는 큐 스트림에 추가할 것인지 여부에 따라, 스트림에 명령에 대한 보기 또는 큐 세부 사항을 선택한 다음 **설정**을 선택합니다.  
  
6.  **저장**을 선택합니다.  
  
 대시보드에서 각 스트림을 삭제할 수도 있습니다. 이렇게 하려면 스트림을 선택한 후 명령줄에서 **삭제**를 선택합니다.  
  
### <a name="configure-an-entity-specific-dashboard"></a>엔터티 특정 대시보드 구성  
 엔터티 특정 대시보드는 멀티 스트림 대시보드입니다. 이 대시보드 구성은 홈 페이지 멀티 스트림 대시보드 구성과 유사하지만 UI의 다른 곳에서 수행하고 다른 사소한 차이가 있습니다. 

예를 들어, 엔터티 특정 대시보드에 있는 일부 필드는 대시보드를 만들고 있는 엔터티로 사전 설정됩니다.  
  
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

2.  **데이터** > **엔터티**를 선택하고 원하는 엔터티를 선택합니다. 

3.  **대시보드** 탭을 선택한 다음 도구 모음에서 **대시보드 추가**를 선택합니다.  
4.  레이아웃을 2, 3 또는 4열 너비 중에서 선택합니다.    
  
5.  대시보드 양식이 열리면 **필터 엔터티**는 대시보드를 만들고 있는 엔터티로 사전 설정됩니다. **엔터티 보기** 드롭다운 목록에는 엔터티에 사용할 수 있는 보기가 포함되어 있습니다. 보기를 선택하고 페이지에서 나머지 필수 정보를 입력합니다.  
  
 나머지 설정은 이전 섹션에서 설명한 홈 페이지 멀티 스트림 대시보드 설정과 매우 유사합니다.  
  
### <a name="configure-a-single-stream-dashboard"></a>단일 스트림 대시보드 구성  
 단일 스트림 대시보드를 구성하는 것은 멀티 스트림 대시보드와 비슷합니다. 모든 UI 탐색 단계는 멀티 스트림 대시보드와 동일합니다. 타일을 포함하는 레이아웃 또는 타일을 포함하지 않는 레이아웃을 선택할 수 있습니다. 타일이 포함된 경우 항상 대시보드에 표시됩니다. 타일을 구성하려면 타일 가운데에 있는 아이콘을 선택합니다. **타일 추가** 창이 열리면 필요한 데이터를 입력합니다. 다음 그림은 타일 설정의 예를 보여 줍니다.  
  
 ![단일 스트림 대시보드에 타일 추가](media/add-tile.png "단일 스트림 대시보드에 타일 추가")  
  
<a name="BKMK_ConfigureColors"></a>   
## <a name="configure-dashboard-colors"></a>대시보드 색상 구성  
 **케이스** 엔터티의 **케이스 타입**, **IsEscalated** 또는 **우선 순위** 같은 모든 **옵션 집합** 및 **두 개 옵션** 타입 필드의 경우, 차트 및 스트림에 나타날 특정 필드 값을 위한 특정 색상을 구성할 수 있습니다. 예를 들어, 대화식 차트에서는 높은 우선 순위 서비스 케이스는 빨간색, 중간 우선 순위 서비스 케이스는 파란색, 낮은 우선 순위 서비스 케이스는 녹색으로 표시할 수 있습니다. 스트림에서 작업 항목 설명 옆에 컬러로 된 얇은 세로 선이 있을 것입니다.  
  
> [!NOTE]
>  태그 차트 및 도넛형 차트에는 색상 코딩을 사용할 수 없습니다. 이러한 차트는 대시보드에 흰색, 회색 및 검정색 음영으로 나타납니다.  
  
1.  [솔루션 탐색기](advanced-navigation.md#solution-explorer)를 엽니다.  
2.  **구성 요소**에서 **엔터티**를 확장한 다음 원하는 엔터티를 확장합니다. 원하는 엔터티가 표시되지 않으면 **기존 항목 추가**를 선택하여 추가합니다.  
  
3.  탐색 창에서 **필드**를 선택합니다. 표에서 색상을 구성할 필드를 두 번 클릭합니다.  
  
4.  **일반** 탭의 **타입** 하위 영역에서 **예**를 선택하고 **편집**을 선택합니다.  
  
5.  **목록 값 수정** 대화 상자가 나타나면 **색상** 텍스트 상자에서 새 값을 설정합니다. **확인**을 선택합니다.  
  
     **저장 후 닫기**를 선택합니다.  
  
7.  변경 사항을 발효시키려면 **게시**를 선택합니다.  
  
다음 예제에서 **IsEscalated** 필드에 대한 색상을 변경합니다. **편집** 단추를 사용하여 **목록 값 수정** 대화 상자를 엽니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![대시보드에서 색상 변경](media/edit-color.png "대시보드에서 색상 변경")  
  
여기에 보이는 것처럼 **목록 값 수정** 대화 상자가 열리면 색상을 선택합니다.  
  
 ![대시보드 색상 수정](media/modify-color.png "대시보드 색상 수정")  

마찬가지로, **우선순위** 필드로 이동하여 케이스 우선순위 옵션의 색상을 수정하려면, 아래와 같이 **일반 탭** 탭의 **옵션** 하위 영역에서 색상을 선택합니다:

 ![대시보드 색상 수정](media/priority-color-modify.png "서비스 케이스 우선 순위에 대해 대시보드 색상 변경")  
  
### <a name="see-also"></a>참조  
 
[대시보드 만들기 또는 편집](create-edit-dashboards.md)
 

