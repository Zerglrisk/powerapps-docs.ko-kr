---
title: Common Data Service 메타데이터에서 관리 속성 설정 | MicrosoftDocs
description: 솔루션에서 메타데이터 항목의 관리 속성을 설정하는 방법에 대해 알아봅니다.
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: edaa7d4a-a95f-4d66-a9d9-2ad6051332f7
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 287df9ac6daa38022a269177247a5b446bdfa1fa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2869991"
---
# <a name="set-managed-properties-in-common-data-service-metadata"></a>Common Data Service 메타데이터에서 관리 속성 설정 

관리형 속성은 관리형 솔루션으로 메타데이터를 포함하고 다른 환경으로 가져올 경우에만 적용됩니다. 이러한 설정을 통해 관리형 솔루션 제작자는 해당 솔루션을 설치하는 사용자에게 허용하려는 사용자 지정 수준을 일부 제어할 수 있습니다. 

> [!TIP]
> 일반적으로 사용자가 비즈니스 데이터와 함께 작동하는 솔루션에서 메타데이터를 확장할 수 있도록 하는 것이 좋습니다. 그러면 표준 엔터티에 대해 수행할 수 있는 것과 동일한 방식으로 사용자의 요구에 맞게 솔루션을 조정할 수도 있습니다.
>
>솔루션을 지원하는 기능을 제공하지만 비즈니스 데이터는 포함하지 않는 메타데이터의 경우 허용되는 사용자 지정을 제한하는 것이 좋습니다.

관리 속성 설정은 솔루션 탐색기를 사용하여 수행 해야 합니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="entity-managed-properties"></a>엔터티 관리 속성

[엔터티를 보는](create-edit-entities-solution-explorer.md#view-entities) 동안 엔터티를 선택하고 메뉴 모음에서 **관리 속성**을 선택합니다.  그러면 **관리 속성 설정** 대화 상자가 열립니다.

![관리 속성 설정](media/set-managed-properties.png)
  
엔터티에는 다른 유형의 솔루션 구성 요소보다 관리 속성이 더 많습니다. 엔터티를 사용자 지정할 수 있는 경우 다음 옵션을 설정할 수 있습니다.  

|옵션|설명|
|--|--|
|**사용자 지정할 수 있음** |다른 모든 옵션을 제어합니다. 이 옵션이 `False`이면 다른 어떤 설정도 적용되지 않습니다. 이 옵션이 `True`이면 다른 사용자 지정 옵션을 지정할 수 있습니다. `False`인 경우 다른 모든 옵션을 false로 설정하는 것과 같습니다.|
|**표시 이름을 수정할 수 있음**|엔터티 표시 이름을 수정할 수 있는지 여부입니다.|
|**추가 속성 변경 가능** |다른 옵션에서 다루지 않는 모든 항목에 적용됩니다.|
|**새 양식을 만들 수 있음**|엔터티에 대해 새 양식을 만들 수 있는지 여부입니다.|
|**새 차트를 만들 수 있음**|엔터티에 대해 새 차트를 만들 수 있는지 여부입니다.|
|**새 보기를 만들 수 있음** |엔터티에 대해 새 보기를 만들 수 있는지 여부입니다.|
|**계층적 관계를 변경할 수 있음**|계층적 관계 설정을 변경할 수 있는지 여부입니다. 추가 정보: [계층적으로 관련된 데이터 정의 및 쿼리](define-query-hierarchical-data.md)|
|**변경 추적 기능을 활성화할 수 있음** |엔터티 **변경 내용 추적** 속성을 변경할 수 있는지 여부입니다.|
|**외부 검색 색인과 동기화할 수 있음** |관련성 검색을 사용하도록 엔터티를 구성할 수 있는지 여부입니다. 추가 정보: [관련성 검색을 구성하여 검색 결과 및 성능 향상](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="field-managed-properties"></a>필드 관리 속성

필드를 편집하는 방법에 대한 자세한 내용은 [Power Apps 솔루션 탐색기를 사용하여 Common Data Service에 대한 필드 만들기 및 편집](create-edit-field-solution-explorer.md)을 참조하십시오.

[필드 를 보는](create-edit-field-solution-explorer.md#view-fields) 동안 비관리형 솔루션에서 사용자 지정 필드를 선택한 다음 메뉴 모음에서 **추가 작업** >  **관리 속성**을 선택합니다.

![필드 관리 속성 보기](media/view-field-managed-properties-solution-explorer.png)  
  
그러면 **관리 속성 설정** 대화 상자가 열립니다.

![필드 관리 속성 설정](media/set-field-managed-property.png)

**사용자 지정할 수 있음** 옵션은 모든 다른 옵션을 제어합니다. 이 옵션이 **False**이면 다른 어떤 설정도 적용되지 않습니다. 이 옵션이 **True**이면 다른 사용자 지정 옵션을 지정할 수 있습니다.  
  
필드를 사용자 지정할 수 있으면 다음 옵션을 **True** 또는 **False**로 설정합니다.  
  
- **표시 이름을 수정할 수 있음**
- **요구 수준을 변경할 수 있음** 
- **추가 속성을 변경할 수 있음** : 이 속성은 특정 관리 속성을 갖지 않는 다른 모든 사용자 지정을 제어합니다.

모든 개별 옵션을 **False**로 설정하면 **False**로 **사용자 지정할 수 있음** 설정과 동등합니다.  

선택 사항을 적용하고 **설정**을 클릭하여 대화 상자를 닫습니다.

> [!NOTE]
> 이 필드가 **날짜 및 시간** 필드인 경우 **날짜 및 시간 동작 을 추가로 변경할 수 있음** 속성을 사용할 수 있습니다. 추가 정보: [날짜 및 시간 필드의 동작 및 형식](behavior-format-date-time-field.md)

## <a name="relationship-managed-properties"></a>관계 관리 속성

엔터티 관계를 보는 동안 비관리형 솔루션에서 관계를 선택한 다음 메뉴 모음에서 **추가 작업** > **관리 속성**을 선택합니다.
  
관계를 가진 유일한 관리 속성은 **사용자 지정할 수 있음**입니다. 이 단일 설정은 엔터티 관계에 수행될 수 있는 모든 변경 내용을 제어합니다. 


### <a name="see-also"></a>참조

[관리 속성](solutions-overview.md#managed-properties)<br />
[솔루션 탐색기를 사용하여 엔터티 만들기 및 편집](create-edit-entities-solution-explorer.md)<br />
[Power Apps 솔루션 탐색기를 사용하여 Common Data Service에 대한 필드 만들기 및 편집](create-edit-field-solution-explorer.md)<br />
[솔루션 탐색기를 사용하여 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-solution-explorer.md)<br />
[솔루션 탐색기를 사용하여 Common Data Service에서 N:N(다대다) 엔터티 관계 만들기](create-edit-nn-relationships-solution-explorer.md)
