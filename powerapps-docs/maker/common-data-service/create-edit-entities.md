---
title: Common Data Service에서 엔터티 만들기 및 편집 | MicrosoftDocs
description: 엔터티를 만들고 편집하는 방법 알아보기
ms.custom: ''
ms.date: 04/16/2019
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
ms.openlocfilehash: c13092daaa86abbcba5ef65dc809f29d9a6a6f12
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883711"
---
# <a name="create-and-edit-entities-in-common-data-service"></a>Common Data Service에서 엔터티 만들기 및 편집

사용자 지정 엔터티를 만들려면 먼저 기존 엔터티를 사용하여 요구 사항을 충족하는지 평가합니다. 추가 정보: [새 메타데이터를 만들거나 기존 메타데이터를 사용하시겠습니까?](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

엔터티를 만드는 데 사용할 수 있는 디자이너는 두 가지가 있습니다.

|디자이너| 설명|
|--|--|
|[Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|쉽게 간소화된 환경을 제공하지만 일부 특수 설정은 사용할 수 없습니다.<br />추가 정보: <br />[자습서: Power Apps에서 구성 요소가 있는 사용자 지정 엔터티 만들기](/powerapps/maker/common-data-service/create-custom-entity)<br />[Power Apps 포털을 사용하여 엔터티 만들기 및 편집](create-edit-entities-portal.md)|
|솔루션 탐색기|쉽지 않지만 덜 일반적인 요구 사항에 대한 더 많은 유연성을 제공합니다. <br />추가 정보 [솔루션 탐색기를 사용하여 엔터티 만들기 및 편집](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> 다음을 사용하여 환경에서 엔터티를 만들 수도 있습니다.
> - 엔터티의 정의가 포함된 솔루션을 가져옵니다.
> - 파워 쿼리를 사용하여 새 엔터티를 만들고 데이터로 채웁니다. 추가 정보: [파워 쿼리를 사용하여 Common Data Service의 엔터티에 데이터 추가](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - 개발자는 [메타데이터 서비스](/powerapps/developer/common-data-service/use-web-services#metadata-services)를 사용하여 프로그램을 작성할 수 있습니다.


## <a name="entity-options-not-available-in-the-power-apps-portal"></a>Power Apps 포털에서 사용할 수 없는 엔터티 옵션

이 항목의 정보는 사용할 수 있는 디자이너를 선택하는 데 도움이 됩니다. 다음 요구 사항 중 하나를 해결 해야 하는 경우가 아니면 Power Apps 포털을 사용하여 엔터티를 만들 수 있습니다.

- 사용자 지정 접두사 제어

  만든 사용자 지정 엔터티의 이름 일부는 사용자 지정 접두사입니다. 이 값은 작업 중인 솔루션의 솔루션 게시자에 따라 설정됩니다. 사용자 지정 접두사에 대해 관심이 있을 경우 이 엔터티에 사용할 접두사가 사용자 지정 접두사인 비관리형 솔루션에서 작업하고 있는지 확인하십시오. 추가 정보 [솔루션 게시자 접두사 변경](change-solution-publisher-prefix.md)

- 조직 담당 엔터티 만들기

  기본적으로 Power Apps 포털은 **사용자 또는 팀** 담당 엔터티를 만듭니다. 솔루션 탐색기를 사용하여 **조직**에 소유권을 설정합니다. 추가 정보: [엔터티 소유권](types-of-entities.md#entity-ownership)

- 활동 엔터티 만들기

  활동 엔터티는 일정에서 항목을 만들 수 있는 작업을 추적하는 특수한 종류의 엔터티입니다. 추가 정보: [활동 엔터티](types-of-entities.md#activity-entities)

- 사용자 지정 엔터티의 아이콘을 변경합니다.

  기본적으로 모델 기반 앱의 모든 사용자 지정 엔터티에는 동일한 아이콘이 있습니다. 사용자 지정 엔터티에 대해 원하는 아이콘에 대한 이미지 웹 리소스를 만들 수 있습니다. 추가 정보:  [사용자 지정 아이콘 변경](../model-driven-apps/change-custom-entity-icons.md). 

- 활성화할 수 있는 다음 속성을 변경합니다.

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- 다음 속성을 변경합니다.

  |옵션   |설명  |
  |---------|---------|
  |**액세스 팀**|이 엔터티에 대한 팀 템플릿을 만듭니다. |
  |**빨리 만들기 허용**|이 엔터티에 대해 **빨리 만들기 양식**을 만들어 게시한 후에는 탐색 창에서 **만들기** 단추를 사용하여 새 레코드를 만들 수 있는 옵션이 있습니다. 추가 정보: [양식 만들기 및 디자인](../model-driven-apps/create-design-forms.md)<br /><br /> 사용자 지정 활동 엔터티에 대해 이 옵션이 활성화되어 있으면 탐색 창에서 **만들기** 단추를 사용할 때 활동 엔터티 그룹에 사용자 지정 활동이 표시됩니다. 하지만 활동은 빨리 만들기 양식을 지원하지 않으므로 사용자 지정 엔터티 아이콘을 클릭할 때 기본 양식이 사용됩니다.|
  |**이 엔터티가 표시되는 영역**|웹 응용 프로그램에서 사용 가능한 사이트맵 영역 중 하나를 선택하여 이 엔터티를 표시합니다. 이는 모델 기반 앱에는 적용되지 않습니다.|
  |**감사**|조직에서 감사 기능이 활성화되어 있으면 이 기능을 사용하여 엔터티 레코드에 대한 변경 내용을 시간에 따라 캡처할 수 있습니다. 엔터티에 대한 감사를 활성화하면 이 엔터티에 해당하는 모든 필드에 대해 감사가 활성화됩니다. 감사를 활성화할 필드를 선택하거나 선택을 취소할 수 있습니다.|
  |**변경 내용 추적**|데이터를 데이터가 처음 추출되었거나 마지막 동기화된 이후로 변경된 데이터를 감지함으로써 효율적인 방식으로 동기화를 활성화합니다.  |
  |**Color(색)**|모델 기반 앱에서 엔터티에 사용할 색을 설정합니다.|
  |**문서 관리**|조직의 문서 관리를 활성화하도록 다른 작업을 수행한 후 이 엔터티에 대해 이 기능을 사용하면 SharePoint과의 상호 작용에 참여할 수 있습니다. |
  |**중복 검색**|조직에서 중복 검색이 활성화되어 있을 경우 이 기능을 사용하면 이 엔터티에 대한 중복 검색 규칙을 만들 수 있습니다.|
  |**모바일에 사용**|이 엔터티를 Dynamics 365 for phones 및 Dynamics 365 for tablets 앱에 사용할 수 있도록 합니다. 인 엔터티를 **모바일에서 읽기 전용**으로 설정할 수 있는 옵션도 있습니다.<br /><br /> 엔터티의 양식에 Dynamics 365 for phones 및 Dynamics 365 for tablets 앱에서 지원되지 않는 확장이 필요할 경우 이 설정을 사용하여 해당 엔터티의 데이터를 모바일 앱 사용자가 편집할 수 없는지 확인합니다.|
  |**Phone Express에 사용**|이 엔터티를 Dynamics 365 for phones 앱에 사용할 수 있도록 합니다.|
  |**편지 병합**|사용자는 이 엔터티를 메일과 병합하여 사용할 수 있습니다.|
  |**Dynamics 365 for Outlook의 오프라인 기능**|Dynamics 365 for Outlook 애플리케이션이 네트워크에 연결되어 있지 않은 동안 이 엔터티의 데이터를 사용할 수 있는지 여부입니다.|
  |**Dynamics 365 for Outlook의 읽기 창**|엔터티가 Dynamics 365 for Outlook 앱에 대한 읽기 창에 표시되는지 여부입니다.|
  |**사용자 지정 도움말 사용**|활성화된 경우 도움말 URL을 설정하여 사용자가 응용 프로그램에서 도움말 단추를 클릭할 때 표시되는 페이지를 제어합니다. 이를 사용하여 엔터티에 대한 회사 프로세스에 대한 지침을 제공 합니다.|


### <a name="see-also"></a>참조

[솔루션 탐색기를 사용하여 엔터티 만들기 및 편집](create-edit-entities-solution-explorer.md)<br />
[자습서: Power Apps에서 구성 요소가 있는 사용자 지정 엔터티 만들기](/powerapps/maker/common-data-service/create-custom-entity)<br />
[엔터티 편집](edit-entities.md)<br />
[개발자 설명서: 사용자 지정 엔터티 만들기](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
