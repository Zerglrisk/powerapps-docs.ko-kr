---
title: PowerApps 포털을 사용하여 엔터티 만들기 및 편집 | MicrosoftDocs
description: PowerApps 포털을 사용하여 엔터티를 만들고 편집하는 방법 알아보기
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
author: Mattp123
ms.assetid: fa04f99d-a5f9-48cb-8bfb-f0f50718ccee
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6b1fb1e479237face89e0a19ee145f7fa428cb62
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758111"
---
# <a name="create-and-edit-entities-using-powerapps-portal"></a>PowerApps 포털을 사용하여 엔터티 만들기 및 편집

[PowerApps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 사용하면 Common Data Service용 엔터티를 쉽게 만들고 편집할 수 있습니다.

포털을 사용하면 가장 일반적인 옵션을 구성할 수 있지만 특정 옵션은 솔루션 탐색기를 사용하여 설정만 가능 합니다. 추가 정보: 
- [Common Data Service에서 엔터티 만들기 및 편집](create-edit-entities.md)
- [솔루션 탐색기를 사용하여 엔터티 만들기 및 편집](create-edit-entities-solution-explorer.md)

## <a name="view-entities"></a>엔터티 보기

1. [PowerApps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **모델 기반** 또는 **캔버스** 디자인 모드 중 하나를 선택합니다.
2. **데이터** > **엔터티**를 선택합니다.

![엔터티 보기](media/view-entities-portal.png)

목록에서 다음 보기를 사용하여 표시되는 엔터티를 필터링 할 수 있습니다. 

![엔터티 보기](media/entity-views-portal.png)

 |보기|설명|
 |--|--|
 |**모두**| 모든 엔터티를 표시합니다.|
 |**사용자 지정**|사용자 지정 엔터티만 표시합니다.|
 |**기본값**|표준 엔터티만 표시합니다. |

**그룹**을 선택하여 적용된 **태그**를 기준으로 요소를 그룹화할 수도 있습니다.

## <a name="create-an-entity"></a>엔터티 만들기

[엔터티를 보는](#view-entities) 동안 메뉴 모음에서 **새 엔터티**를 선택합니다. 이렇게 하면 새 엔터티 패널이 열립니다.

![새 엔터티 패널](media/new-entity-panel.png)

다음 필드에 데이터를 입력합니다.

|필드|설명|
|--|--|
|**표시 이름**|이것은 앱에 표시되는 엔터티의 단일 이름입니다. 이것은 나중에 변경할 수 있습니다.|
|**여러 표시 이름**|이것은 앱에 표시되는 엔터티의 복수 이름입니다. 이것은 나중에 변경할 수 있습니다.|
|**이름**|이 필드는 입력한 **표시 이름**에 따라 미리 채워집니다. 여기에는 Common Data Service 솔루션 게시자의 사용자 지정 접두사가 포함됩니다. 엔터티를 저장한 후에는 변경할 수 없습니다.|
|**설명**|엔터티의 용도에 대해 알기 쉬운 설명을 제공합니다.|

계속하려면 **다음**을 선택하고 **새 엔터티** 패널을 닫고 필드 목록을 표시합니다.

**기본 이름** 필드는 이 시점에서 볼 수 있는 유일한 필드입니다. 필드의 **표시 이름** 또는 **이름**을 변경하려면 **기본 이름** 필드를 선택하여 편집합니다. 기본값은 아래에 표시됩니다.

![기본 이름 패널](media/primary-name-panel.png)

**엔터티 저장**을 선택하여 엔터티를 만들거나 계속해서 엔터티를 편집합니다.

![엔터티 저장](media/save-entity-portal.png)

## <a name="edit-an-entity"></a>엔터티 편집

[엔터티를 보는](#view-entities) 동안 편집하려는 엔터티를 선택합니다.

엔터티의 **표시 이름**, **복수 표시 이름** 또는 **설명을** 편집하려면 메뉴에서 설정을 선택합니다.

![엔터티 설정](media/entity-settings-portal.png)

다른 항목에 대한 탭에서 선택합니다.

### <a name="fields"></a>필드

[필드 만들기 및 편집](create-edit-fields.md)을 참조하십시오.

### <a name="relationships"></a>관계

[엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)을 참조하십시오.

### <a name="business-rules"></a>비즈니스 규칙

[비즈니스 규칙 및 추천을 만들어 양식에 논리 적용](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)을 참조하십시오.

### <a name="views"></a>Views

[보기 만들기 또는 편집](../model-driven-apps/create-edit-views.md)을 참조하십시오.

### <a name="forms"></a>양식

[양식 만들기 및 디자인](../model-driven-apps/create-design-forms.md)을 참조하십시오.

### <a name="dashboards"></a>대시보드

[대시보드 만들기 또는 편집](../model-driven-apps/create-edit-dashboards.md)을 참조하십시오.

### <a name="charts"></a>차트

[시스템 차트 만들기](../model-driven-apps/create-edit-system-chart.md)를 참조하십시오.

### <a name="keys"></a>키

[레코드를 참조할 대체 키 정의](define-alternate-keys-reference-records.md)를 참조하십시오.

### <a name="data"></a>데이터

엔터티에서 데이터를 봅니다.
**보기 선택** 메뉴를 사용하여 엔터티에 대해 사용 가능한 보기를 선택하거나 모든 필드를 표시할 수 있습니다.

![보기 선택](media/entity-data-select-view.png)

양식의 아래쪽에 있는 **다음 페이지** 및 **이전 페이지** 명령을 사용하여 더 많은 데이터를 볼 수 있습니다.

## <a name="delete-an-entity"></a>엔터티 삭제

시스템 관리자 보안 역할을 가진 사용자는 관리형 솔루션에 포함되지 않은 사용자 지정 엔터티를 삭제할 수 있습니다.  
  
> [!IMPORTANT]
>  사용자 지정 엔터티를 삭제하면 해당 엔터티에 대한 데이터를 저장하는 데이터베이스 테이블이 삭제되고 그 안에 포함된 모든 데이터가 손실됩니다. 사용자 지정 엔터티에 대한 상위/하위 관계가 있는 관련 레코드도 삭제됩니다. 상하 관계에 대한 자세한 내용은 [엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)을 참조하십시오.  
  
> [!NOTE]
> 삭제된 엔터티에서 데이터를 복구할 수 있는 유일한 방법은 엔터티가 삭제되기 이전 시점에서 데이터베이스를 복원하는 것입니다. 추가 정보: [인스턴스 백업 및 복원](/dynamics365/customer-engagement/admin/backup-restore-instances)

[엔터티 를 보는](#view-entities) 동안 엔터티를 선택하고 메뉴 또는 상황에 맞는 메뉴에서 **엔터티 삭제**를 선택합니다.

![PowerApps 포털을 사용하여 엔터티 삭제](media/delete-entity-powerapps-portal.png)

엔터티에 삭제되지 않도록 하는 종속성이 있는 경우 오류 메시지가 표시됩니다. 종속성을 식별하고 제거하려면 솔루션 탐색기를 사용해야 합니다. 추가 정보 [엔터티 종속성 식별](create-edit-entities-solution-explorer.md#identify-entity-dependencies)

### <a name="see-also"></a>참조

[Common Data Service에서 엔터티 만들기 및 편집](create-edit-entities.md)<br />
[솔루션 탐색기를 사용하여 엔터티 만들기 및 편집](create-edit-entities-solution-explorer.md)


