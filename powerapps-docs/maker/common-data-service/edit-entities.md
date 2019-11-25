---
title: PowerApps에서 엔터티 편집 | MicrosoftDocs
description: 엔터티를 편집할 수 있는 다양한 방법 알아보기
ms.custom: ''
ms.date: 05/15/2018
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
ms.assetid: 8b00780c-74f0-4e3a-b570-b9289d0d5383
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3ec64583e2146703711b88456ff7bc91ece3e921
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757451"
---
# <a name="edit-an-entity"></a>엔터티 편집

만든 사용자 지정 엔터티를 편집할 수 있습니다. 표준 엔터티 또는 관리형 사용자 지정 엔터티에 허용되는 변경에 제한이 있을 수 있습니다.  
  
> [!NOTE]
> **표준** 엔터티는 **시스템** 또는 **사용자 지정** 엔터티가 아닌 사용자 환경에 포함된 일반 엔터티입니다. *관리형 사용자 지정 엔터티*는 관리형 솔루션을 가져와서 시스템에 추가된 엔터티입니다. 이러한 엔터티를 편집할 수 있는 수준은 각 엔터티에 대해 설정된 관리형 속성에 따라 결정됩니다. 편집할 수 없는 속성은 비활성화됩니다. 

디자이너를 사용하여 엔터티를 편집하는 방법에는 다음 두 가지가 있습니다.

|디자이너|설명|
|--|--|
|[PowerApps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|쉽게 간소화된 환경을 제공하지만 일부 특수 설정은 사용할 수 없습니다.|
|솔루션 탐색기|쉽지 않지만 덜 일반적인 요구 사항에 대한 더 많은 유연성을 제공합니다.|

PowerApps 포털 및 솔루션 탐색기에서 다음을 수행할 수 있습니다.

- **엔터티 필드 편집**. 추가 정보: [Common Data Service용 필드 만들기 및 편집](create-edit-fields.md)
  
- **엔터티 관계 편집**. 추가 정보:  [엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)

- **키** [레코드를 참조할 대체 키 정의](define-alternate-keys-reference-records.md)
  
또한 엔터티를 지원하는 레코드를 변경할 수 있습니다.  

- **비즈니스 규칙**. 추가 정보: [비즈니스 규칙 및 추천을 만들어 양식의 논리에 적용](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

- **보기**. 추가 정보:  [보기 만들기 또는 편집](../model-driven-apps/create-edit-views.md)
  
- **양식**. 추가 정보:  [양식 만들기 및 디자인](../model-driven-apps/create-design-forms.md)

- **대시보드**. 추가 정보: [대시보드 만들기 또는 편집](../model-driven-apps/create-edit-dashboards.md)

- **차트** [시스템 차트 만들기 또는 편집](../model-driven-apps/create-edit-system-chart.md)

## <a name="edit-using-powerapps-portal-designer"></a>PowerApps 포털 디자이너를 사용하여 편집

PowerApps 포털 디자이너 내에서는 다음과 같은 세 가지 엔터티 속성만 편집할 수 있습니다.
 - 표시 이름
 - 여러 표시 이름
 - 설명

디자이너에서 편집하려는 엔터티를 선택하고 클릭하여 엔터티 디자이너를 엽니다. 엔터티 속성을 수정하려면 **설정** 명령을 클릭하여 아래와 같이 **엔터티** 편집 양식을 봅니다.

![엔터티 속성 편집](media/edit-entity-properties-powerapps-portal-designer.png)

> [!NOTE]
>  많은 표준 엔터티의 이름은 응용 프로그램에서 다른 텍스트로도 사용할 수 있습니다. 이 이름이 사용된 텍스트를 찾아 변경하려면 [표준 엔터티 메시지 편집](edit-system-entity-messages.md)을 참조하십시오.

엔터티 옵션에 대한 다른 변경 사항은 솔루션 탐색기를 사용하여 엔터티를 편집해야 합니다.

## <a name="edit-using-solution-explorer"></a>솔루션 탐색기를 사용하여 편집

솔루션 탐색기를 사용하여 엔터티를 편집하는 경우 이를 추가하려는 비관리형 솔루션을 찾아야 합니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
<a name="BKMK_ChangeEntityName"></a> 
  
## <a name="change-the-name-of-an-entity"></a>엔터티 이름 변경  

**표시 이름** 및 **복수 이름** 속성을 사용하여 응용 프로그램의 엔터티 이름을 변경합니다. 

> [!NOTE]
>  많은 표준 엔터티의 이름은 응용 프로그램에서 다른 텍스트로도 사용할 수 있습니다. 이 이름이 사용된 텍스트를 찾아 변경하려면 [표준 엔터티 메시지 편집](edit-system-entity-messages.md)을 참조하십시오.
  
<a name="BKMK_ChangeEntityIcon"></a>   

###  <a name="change-the-icons-used-for-custom-entities"></a>사용자 지정 엔터티에 사용된 아이콘 변경  

기본적으로 웹 응용 프로그램의 모든 사용자 지정 엔터티에는 동일한 아이콘이 있습니다. 사용자 지정 엔터티에 대해 원하는 아이콘에 대한 이미지 웹 리소스를 만들 수 있습니다. 추가 정보:  [사용자 지정 아이콘 변경](../model-driven-apps/change-custom-entity-icons.md).  
  
<a name="BKMK_EnableOptions"></a>  
 
###  <a name="entity-options-that-can-only-be-enabled"></a>활성화만 될 수 있는 엔터티 옵션  

다음 표에는 엔터티를 활성화할 수 있는 옵션이 나열되지만 이러한 항목을 활성화한 후에는 다시 비활성화할 수 없습니다.  

[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)] 
  
<a name="BKMK_EnableDisableOptions"></a>  
 
###  <a name="enable-or-disable-entity-options"></a>엔터티 옵션 활성화 또는 비활성화  

다음 표에는 언제든지 활성화하거나 비활성화할 수 있는 엔터티 옵션이 나열됩니다.  

[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)] 

### <a name="see-also"></a>참조

[엔터티 만들기](create-edit-entities.md)<br />
[솔루션 탐색기를 사용하여 엔터티 만들기 및 편집](create-edit-entities-solution-explorer.md)
