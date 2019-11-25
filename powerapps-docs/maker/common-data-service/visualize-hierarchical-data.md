---
title: 모델 기반 앱을 사용하여 계층적 데이터 시각화 | MicrosoftDocs
description: 계층적 관련 데이터 쿼리 및 시각화 방법 알아보기
ms.custom: ''
ms.date: 05/28/2019
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2328d35af7be35e3aae8d38bc1157adce513cb7c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758551"
---
# <a name="visualize-hierarchical-data-with-model-driven-apps"></a>모델 기반 앱을 사용하여 계층적 데이터 시각화

엔터티가 계층적 자체 참조 관계를 갖도록 구성된 경우 해당 계층을 사용하여 시각화를 구성할 수 있습니다. 추가 정보: [계층적으로 관련된 데이터 정의 및 쿼리](../common-data-service/define-query-hierarchical-data.md)

기본적으로 사용 가능한 시각화가 있는 엔터티에는 [계정](/powerapps/developer/common-data-service/reference/entities/account), [위치](/powerapps/developer/common-data-service/reference/entities/position)및 [사용자](/powerapps/developer/common-data-service/reference/entities/systemuser)가 포함됩니다. 이러한 엔터티의 표 보기에서 레코드 이름 왼쪽의 계층 구조 차트를 나타내는 아이콘을 볼 수 있습니다. 계층 구조 아이콘은 기본적으로 모든 레코드에 대해 표시되지는 않습니다. 계층적 관계를 사용하여 관련 된 레코드에 대한 아이콘이 표시됩니다.  
> [!div class="mx-imgBorder"] 
> ![계층 구조 보기 단추](media/view-hierarchy-button.png)  
  
 계층 구조 아이콘을 선택하면 아래 그림처럼 왼쪽에는 트리 보기가, 오른쪽에는 타일 보기가 있는 계층 구조를 볼 수 있습니다.  
  
> [!div class="mx-imgBorder"] 
> ![계정에서 트리 및 타일 보기](media/tree-view-and-tile-view-in-hierarchy.png)  
  
 계층 구조에 대해 다른 엔터티를 몇 개 사용하도록 설정할 수 있습니다. 이러한 엔터티에는 [연락처](/powerapps/developer/common-data-service/reference/entities/contact) 및 [팀](/powerapps/developer/common-data-service/reference/entities/team)이 포함됩니다. 계층 구조에 대해 모든 사용자 지정 엔터티를 사용하도록 설정할 수 있습니다.  
  
시각화를 만들 때 기억할 중요한 사항:  
  
- 엔터티당 하나의(1: N) 자체 참조 관계만 계층적으로 설정할 수 있습니다. 자체 참조 관계에서 기본 엔터티와 관련 엔터티는 동일한 형식이어야 합니다.  
- 계층 구조 또는 시각화는 한 엔터티만 기반으로 합니다. 여러 수준에서 거래처를 보여주는 거래처 계층 구조를 나타낼 수 있지만 동일한 계층 구조 시각화로 거래처와 연락처를 표시할 수 없습니다. 
- 타일에 표시할 수 있는 최대 필드 수는 4개입니다. 타일 보기에 사용되는 퀵 양식에 필드를 추가하는 경우 처음 4개의 필드만 표시됩니다. 

## <a name="hierarchy-settings"></a>계층 구조 설정

계층 구조에 대한 시각화를 사용하려면 빠른 보기 양식에 계층 구조를 연결해야 합니다. 이 작업은 솔루션 탐색기를 통해서만 수행할 수 있습니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

계층 설정은 솔루션 탐색기의 엔터티와 연결됩니다. 

1. [엔터티를 보는](../common-data-service/create-edit-entities-solution-explorer.md#view-entities) 동안 **계층 설정**을 선택합니다.
2. 기존 계층 설정이 있으면 편집할 수 있습니다. 그렇지 않으면 **새로 만들기**를 클릭하여 새로 만듭니다.
    
    > [!NOTE]
    > 계층 설정이 존재하지 않는 경우 엔터티가 구성된 계층 구조를 가지기에 적합하지 않습니다.
    >계층 구조 설정은 한 개만 있을 수 있습니다. 

1. 다음 필드의 데이터를 설정합니다.

|필드|설명|
|--|--|
|**이름**|*필수 특성:* 계층 설정에 대한 고유 이름을 추가합니다. 일반적으로 엔터티의 이름입니다. 이 값에는 솔루션 게시자 사용자 지정 접두사가 포함됩니다.|
|**기본 빠른 보기 양식**|*필수 특성:* 기존 빠른 보기 양식에서 선택하거나 **새로 만들기**를 선택하여 빠른 보기 양식 편집기를 열어 새 양식을 만듭니다.|
|**계층적 관계**|*필수 특성:* 계층 관계가 엔터티에 대해 이미 정의되어 있으면 여기에서 값을 설정합니다. 값이 없는 경우 **계층에 대해 사용으로 관계 표시**를 선택하여 사용 가능한 자체 참조 관계 중 하나를 선택하는 대화 상자를 엽니다.|
|**설명**|앞으로 시스템을 사용자 지정하는 사용자가 이 작업을 수행한 이유를 이해할 수 있도록 이 계층 구조의 용도에 대한 설명을 포함합니다.|
    

시각화에 대한 동일한 계층 구조 설정은 한 번 설정되지만 웹 및 모바일 클라이언트에 모두 적용됩니다. 태블릿에서 시각화는 더 작은 양식 요소에 적합한 수정된 형식으로 렌더링합니다. 계층 구조 시각화에 필요한 사용자 지정 가능한 구성 요소는 인식되므로 다른 사용자 지정 같은 조직 간에 전송될 수 있습니다. 양식 편집기를 사용하여 퀵 양식을 사용자 지정하여 시각화에 표시되는 특성을 구성할 수 있습니다.
  
## <a name="visualization-walk-through"></a>시각화 연습

사용자 지정 엔터티를 위한 시각화를 만드는 예를 살펴 보겠습니다. 여기에 표시된 것처럼 `new_Widget`이라고 하는 사용자 지정 엔터티를 만들고, 하나의 (1:N) 자체 참조 관계 `new_new_widget_new_widget`을 만들어 계층적으로 표시했습니다.  
  
![위젯 관계 정의](media/widget-relationship-definition.png)  
  
그런 다음 **계층적 설정** 표 보기에서 `new_new_widget_new_widget` 계층적 관계를 선택했습니다. 양식에서 필요한 필드를 채웠습니다. 아직 (1:N) 관계를 계층적으로 표시하지 않은 경우 양식에 있는 링크는 관계 정의 양식으로 돌아가며, 여기에서 관계를 계층적으로 표시할 수 있습니다.  

> [!IMPORTANT]
> 각 엔터티는 단일 계층적 관계만 맺을 수 있습니다. 이를 다른 자체 참조 관계로 변경하면 원치 않는 결과가 발생할 수 있습니다. 자세한 내용: [계층적 데이터 정의](../common-data-service/define-query-hierarchical-data.md#define-hierarchical-data)

> [!div class="mx-imgBorder"] 
> ![계층 구조 설정](media/hierarchy-settings.png)  
  
**빠른 보기 양식**에서는 **위젯 계층 구조 타일 양식** 이라는 퀵 양식을 만들었습니다. 이 양식에서 각 타일에 표시할 4개의 필드를 추가했습니다.  

> [!div class="mx-imgBorder"] 
> ![위젯에 대한 퀵 양식 만들기](media/create-quickform.png)  
  
설치를 완료한 후 *표준 위젯*과 *프리미엄 위젯*의 두 레코드를 만들었습니다. 프리미엄 위젯을 조회 필드를 사용하여 표준 위젯의 상위 위젯으로 표시한 후 아래 그림처럼 `new_Widget` 표 보기는 계층 구조 아이콘을 나타냈습니다.  

> [!div class="mx-imgBorder"] 
> ![위젯의 계층 구조 표](media/widget-hierarchy-grid.png)  
  
> [!NOTE]
>  계층 구조 아이콘은 레코드가 계층적 관계를 사용하여 관련된 레코드 표 보기에 나타나지 않습니다.  
  
계층 구조 아이콘을 선택하면 왼쪽에는 트리 보기가, 오른쪽에는 두 레코드를 보여주는 타일 보기가 있는 `new_Widget` 계층 구조가 표시됩니다. 각 타일에는 **위젯 계층 구조 타일 양식**에서 제공한 4개의 필드가 포함되어 있습니다.  

> [!div class="mx-imgBorder"] 
> ![위젯의 트리와 타일 보기](media/widget-tree-tiles.png)  

사용자 요구에 따라 사용자는 전체 계층 구조를 보여주는 트리 보기 사용이나 계층 구조의 더 작은 부분을 보여주는 타일 보기에서 선택할 수 있습니다. 두 보기 모두 나란히 표시됩니다. 계층 구조 트리를 확대하고 축소하여 계층 구조를 탐색할 수 있습니다. 

### <a name="see-also"></a>참조 

[계층적으로 관련된 데이터를 정의하고 쿼리하기](../common-data-service/define-query-hierarchical-data.md)<br />
[비디오: 계층 구조 시각화](https://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
