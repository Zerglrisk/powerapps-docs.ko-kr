---
title: PowerApp으로 계층적 데이터 쿼리 및 시각화 | MicrosoftDocs
description: 계층적 관련 데이터 쿼리 및 시각화 방법 알아보기
ms.custom: ''
ms.date: 06/20/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="query-and-visualize-hierarchically-related-data"></a>계층적으로 관련된 데이터를 쿼리하고 가시화하기

관련 데이터를 계층적으로 시각화하여 귀중한 비즈니스 통찰력을 얻을 수 있습니다. 계층 구조 모델링 및 가상화 기능을 사용하면 많은 이점이 있습니다.  
  
-   복잡한 계층 구조 정보를 보고 탐색합니다.  
  
-   계층 구조의 컨텍스트 보기에서 핵심 성과 지표(KPI)를 봅니다.  
  
-   웹 및 태블릿을 통해 주요 정보를 시각적으로 분석합니다.  
  
이런 거래처와 사용자 등 일부 엔터티의 경우 시각화는 기본 제공됩니다. 사용자 지정 엔터티를 포함하여 다른 엔터티를 계층 구조에 사용할 수 있으며 이에 대한 시각화를 만들 수 있습니다. 사용자 요구에 따라 사용자는 전체 계층 구조를 보여주는 트리 보기 사용이나 계층 구조의 더 작은 부분을 보여주는 타일 보기에서 선택할 수 있습니다. 두 보기 모두 나란히 표시됩니다. 계층 구조 트리를 확대하고 축소하여 계층 구조를 탐색할 수 있습니다. 시각화에 대한 동일한 계층 구조 설정은 한 번 설정되지만 웹 및 모바일 클라이언트에 모두 적용됩니다. 태블릿에서 시각화는 더 작은 양식 요소에 적합한 수정된 형식으로 렌더링합니다. 계층 구조 시각화에 필요한 사용자 지정 가능한 구성 요소는 인식되므로 다른 사용자 지정 같은 조직 간에 전송될 수 있습니다. 양식 편집기를 사용하여 퀵 양식을 사용자 지정하여 시각화에 표시되는 특성을 구성할 수 있습니다. 코드 작성 요구 사항은 없습니다.  
  
<a name="BKMK_Querydata"></a>   
## <a name="query-hierarchical-data"></a>계층적 데이터 쿼리  
 Common Data Service에서 계층 구조 데이터 구조는 관련 레코드의 자체 참조 일대다(1:N) 관계에서 지원됩니다. 과거에는 계층 구조 데이터를 보려면 관련 레코드에 대해 반복적으로 쿼리해야 합니다. 현재 한 단계에서 관련 데이터를 계층 구조로 쿼리할 수 있습니다. **이하** 및 **이상** 논리를 사용하여 레코드를 쿼리할 수 있습니다. **이하** 및 **이상** 계층적 연산자는 상세하게 찾기 및 워크플로 편집기에 표시됩니다. 이러한 연산자를 사용하는 방법에 대한 자세한 내용은 [워크플로 단계 구성](/flow/configure-workflow-steps)을 참조하십시오. 상세하기 찾기에 대한 자세한 내용은 [상세하게 찾기 검색 만들기, 편집 또는 저장](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)을 참조하십시오.  
  
 다음 예제에서는 계층 구조를 쿼리하는 다양한 시나리오를 보여줍니다.  
  
 거래처 계층 구조 쿼리  
  
 ![거래처 계층 구조에서 거래처 쿼리](media/query-accounts.png "거래처 계층 구조에서 거래처 쿼리")  
  
 관련 활동을 포함하는 거래처 계층 구조를 쿼리합니다.  
  
 ![거래처의 관련 활동 쿼리](media/query-account-related-activities.png "거래처의 관련 활동 쿼리")  
  
 관련 영업 기회를 포함하는 거래처 계층 구조를 쿼리합니다.  
  
 ![거래처의 관련 영업 기회 쿼리](media/query-account-related-opportunities.png "거래처의 관련 영업 기회 쿼리")  
  
 데이터를 계층 구조로 쿼리하려면 엔터티의 일대다(1:N) 자체 참조 관계를 계층적으로 설정해야 합니다. 계층 구조를 켜려면:  
  
1.  [솔루션 탐색기](../model-driven-apps/advanced-navigation.md#solution-explorer)를 엽니다. 
  
2.  원하는 엔터티를 선택하고 **1:N 관계**를 선택한 다음 (1:N) 관계를 선택합니다. 

3.  **관계 정의**에서 **계층**을 **예**로 설정합니다.  
  
> [!NOTE]
> - 일부 기본(1:N) 관계는 사용자 지정할 수 없습니다. 이는 이러한 관계를 계층적으로 설정하는 것이 방지됩니다.  
> - 시스템 자체 참조 관계를 위한 계층적 관계를 지정할 수 있습니다. 여기에는 "contact_master_contact" 관계 같은 시스템 유형의 1:N 자체 참조 관계가 포함됩니다.  
  
<a name="BKMK_Visualizedata"></a>   
## <a name="visualize-hierarchical-data"></a>계층적 데이터 시각화  
 기본 제공되는 사용 가능한 시각화가 있는 시스템 엔터티에는 `Account`, `Position`, `Product` 및 `User`가 포함됩니다. 이러한 엔터티의 표 보기에서 레코드 이름 왼쪽의 계층 구조 차트를 나타내는 아이콘을 볼 수 있습니다. 계층 구조 아이콘은 기본적으로 모든 레코드에 대해 표시되지는 않습니다. 아이콘은 상위 레코드, 하위 레코드 또는 둘 다 있는 레코드에 대해 표시됩니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![활성 거래처](media/cust-hs-active-account.png "활성 거래처")  
  
 계층 구조 아이콘을 선택하면 아래 그림처럼 왼쪽에는 트리 보기가, 오른쪽에는 타일 보기가 있는 계층 구조를 볼 수 있습니다.  
  
> [!div class="mx-imgBorder"] 
> ![거래처 트리 및 타일 보기](media/hierachy-security-accounts-tile-view.png "거래처 트리 및 타일 보기")  
  
 일부 다른 기본 제공 시스템 엔터티는 계층 구조에 대해 사용할 수 있습니다. 이러한 엔터티에는 `Case`, `Contact`, `Opportunity`, `Order`, `Quote`, `Campaign` 및 `Team`이 포함됩니다. 계층 구조에 대해 모든 사용자 지정 엔터티를 사용하도록 설정할 수 있습니다.  
  
> [!TIP]
>  계층 구조에 대해 엔터티를 사용하도록 설정할 수 있는 경우:  
>  솔루션 탐색기에서 원하는 엔터티를 확장합니다. **계층 구조 설정**이라는 엔터티 구성 요소가 있습니다. 계층 구조에 대해 활성화할 수 없는 엔터티에는 Dynamics 365 Customer Engagement 영업권역 엔터티를 제외하고 이 구성 요소가 없습니다. 영업권역 엔터티의 경우 **계층 구조 설정**이 나타나지만 엔터티는 계층 구조에 대해 활성화될 수 없습니다.  
  
 시각화를 만들 때 기억할 중요한 사항:  
  
-   엔터티당 하나의(1: N) 자체 참조 관계만 계층적으로 설정할 수 있습니다. 이 관계에서 기본 엔터티와 관련 엔터티는 account_parent_account 또는 new_new_widget_new_widget 같은 동일한 유형이어야 합니다.  
  
-   현재 계층 구조 또는 시각화는 한 엔터티만 기반으로 합니다. 여러 수준에서 거래처를 보여주는 거래처 계층 구조를 나타낼 수 있지만 동일한 계층 구조 시각화로 거래처와 연락처를 표시할 수 없습니다.  
  
-   타일에 표시할 수 있는 최대 필드 수는 4개입니다. 타일 보기에 사용되는 퀵 양식에 필드를 추가하는 경우 처음 4개의 필드만 표시됩니다.  
  
### <a name="visualization-example"></a>시각화 예  
 사용자 지정 엔터티를 위한 시각화를 만드는 예를 살펴 보겠습니다. 우리는 여기에서 볼 수 있는 것처럼 new_Widget이라고 하는 사용자 지정 엔터티를 만들었고, 하나의 (1:N) 자체 참조 관계 **new_new_widget_new_widget**을 만들었으며 계층적으로 표시했습니다.  
  
 ![위젯 관계 정의](media/widget-relationship-definition.png "위젯 관계 정의")  
  
 그런 다음 **계층적 설정** 표 보기에서 **new_new_widget_new_widget** 계층적 관계를 선택했습니다. 양식에서 필요한 필드를 채웠습니다. 아직 (1:N) 관계를 계층적으로 표시하지 않은 경우 양식에 있는 링크는 관계 정의 양식으로 돌아가며, 여기에서 관계를 계층적으로 표시할 수 있습니다.  
  
 **빠른 보기 양식**에서는 **위젯 계층 구조 타일 양식** 이라는 퀵 양식을 만들었습니다. 이 양식에서 각 타일에 표시할 4개의 필드를 추가했습니다.  
  
> [!div class="mx-imgBorder"] 
> ![위젯을 위한 퀵 양식 만들기](media/create-quickf-orm.png "위젯을 위한 퀵 양식 만들기")  
  
 설치를 완료한 후 표준 위젯과 프리미엄 위젯의 두 레코드를 만들었습니다. 프리미엄 위젯을 조회 필드를 사용하여 표준 위젯의 상위 위젯으로 표시한 후 아래 그림처럼 new_Widget 표 보기는 계층 구조 아이콘을 나타냈습니다.  
  
> [!div class="mx-imgBorder"] 
> ![위젯의 계층 구조](media/widget-hierarchy-grid.png "위젯의 계층 구조")  
  
> [!TIP]
>  계층 구조 아이콘은 레코드가 상위 하위 관계로 쌍을 이룰 때까지 레코드 표 보기에 나타나지 않습니다.  
  
 계층 구조 아이콘을 선택하면 왼쪽에는 트리 보기가, 오른쪽에는 두 레코드를 보여주는 타일 보기가 있는 new_Widget 계층 구조가 표시됩니다. 각 타일에는 **위젯 계층 구조 타일 양식**에서 제공한 4개의 필드가 포함되어 있습니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![위젯의 트리 및 타일 보기](media/widget-tree-tiles.png "위젯의 트리 및 타일 보기")  
  
## <a name="see-also"></a>참조  
 [비디오: 계층적 보안 모델링 설정](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)   
 [비디오: 계층 구조 시각화](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
