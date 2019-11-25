---
title: 솔루션 탐색기를 사용하여 엔터티 만들기 및 편집 | MicrosoftDocs
description: 솔루션 탐색기를 사용하여 엔터티를 만드는 방법 알아보기
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2ec1fb0471ad1f47f4afad083ad89e87633ce9ed
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2707302"
---
# <a name="create-and-edit-entities-using-solution-explorer"></a>솔루션 탐색기를 사용하여 엔터티 만들기 및 편집

대부분의 일반적인 상황에서 PowerApps 포털을 사용하여 엔터티를 쉽게 만들 수 있지만 모든 기능이 구현되는 것은 아닙니다. [Common Data Service에서 엔터티 만들기 및 편집](create-edit-entities.md)에 설명된 요구 사항을 충족해야 하는 경우 솔루션 탐색기를 사용하여 엔터티를 만들거나 편집하여 이를 달성할 수 있습니다.

## <a name="open-solution-explorer"></a>솔루션 탐색기를 엽니다.

만든 엔터티의 이름 일부는 사용자 지정 접두사입니다. 이 값은 작업 중인 솔루션의 솔루션 게시자에 따라 설정됩니다. 사용자 지정 접두사에 대해 관심이 있을 경우 이 엔터티에 사용할 접두사가 사용자 지정 접두사인 비관리형 솔루션에서 작업하고 있는지 확인하십시오. 추가 정보: [솔루션 게시자 접두사 변경](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entities"></a>엔터티 보기

솔루션 탐색기 **구성 요소** 노드에서 **엔터티** 노드를 선택합니다.

![솔루션 탐색기에서 엔터티를 봅니다.](media/view-entities-solution-explorer.png)

## <a name="create-an-entity"></a>엔터티 만들기

[엔터티를 보는](#view-entities) 동안 **새로 만들기**를 선택하여 새 엔터티 양식을 엽니다.

![솔루션 탐색기의 새 엔터티 양식](media/new-entity-form-solution-explorer.png)

새 엔터티 양식에는 두 개의 탭이 있습니다. **일반** 탭은 엔터티 옵션에 대한 것입니다. **기본 필드** 탭은 조회 필드에서 엔터티를 여는 링크가 있을 때 표시되는 텍스트를 정의하는 각 엔터티에 있는 텍스트 필드의 특수 한 줄에 대한 옵션입니다.

각 섹션에 대한 자세한 내용은 다음을 참조하십시오.
- [기본 필드 구성](#configure-the-primary-field)
- [필수 필드 구성](#configure-required-fields)

> [!NOTE]
> 엔터티를 사용자 지정 활동으로 만들 수도 있습니다. 이 선택은 일부 기본 옵션 값을 변경합니다. 추가 정보: [사용자 지정 활동 엔터티 만들기](#create-custom-activity-entity)

엔터티에 대해 필요한 옵션을 설정한 후 클릭하여 ![저장 명령](media/save-entity-icon-solution-explorer.png) 사용자 지정 엔터티를 만듭니다.

### <a name="configure-the-primary-field"></a>기본 필드 구성

**기본 필드** 탭에서는 일반적으로 기본 필드의 기본값을 사용할 수 있지만 다음과 같은 옵션이 있습니다.

|필드   |설명  |
|---------|---------|
|**표시 이름**|양식 및 목록에서 이 필드에 대해 표시할 지역화할 수 있는 레이블을 입력합니다. 기본값은 **이름**입니다.|
|**이름**|이 필드에 시스템에 사용되는 이름을 설정합니다. 기본값은 `<customization prefix>_name`입니다.|
|**최대 길이**|필드 값의 최대 길이를 입력합니다. 기본값은 100입니다.|

> [!NOTE]
> 엔터티가 활동 엔터티인 경우에는 이러한 옵션이 적용되지 않습니다. 추가 정보:  [사용자 지정 활동 엔터티 만들기](#create-custom-activity-entity)

### <a name="configure-required-fields"></a>필수 필드 구성

**일반** 탭에서 엔터티를 저장하기 전에 일부 옵션이 필요합니다.

|필드   |설명  |
|---------|---------|
|**표시 이름**|이것은 앱에 표시되는 엔터티의 단일 이름입니다.<br />이것은 나중에 변경할 수 있습니다.|
|**복수 이름**|이것은 앱에 표시되는 엔터티의 복수 이름입니다.<br />이것은 나중에 변경할 수 있습니다.|
|**이름**|이 필드는 입력한 표시 이름에 따라 미리 채워집니다. 여기에는 솔루션 게시자 사용자 지정 접두사가 포함됩니다.|
|**소유권 형태**|사용자 또는 팀 담당이나 조직 담당 중에서 선택할 수 있습니다. 추가 정보: [엔터티 소유권](types-of-entities.md#entity-ownership)|

## <a name="edit-an-entity"></a>엔터티 편집

[엔터티 를 보는](#view-entities) 동안 편집하려는 엔터티를 선택하거나 방금 저장한 새 엔터티를 계속 편집합니다.

> [!NOTE]
> 관리형 솔루션에 속하는 표준 엔터티 또는 사용자 지정 엔터티에는 적용할 수 있는 변경 사항이 제한 되어 있을 수 있습니다. 옵션을 사용할 수 없거나 사용하지 않도록 설정한 경우에는 변경할 수 없습니다.

#### <a name="set-once-options"></a>한 번 설정 옵션

다음 옵션은 한 번만 설정할 수 있으며 설정한 후에는 변경할 수 없습니다. 필요한 경우에만 이러한 옵션을 설정하십시오.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

#### <a name="options-that-you-can-change"></a>변경할 수 있는 옵션

다음 속성은 언제든지 변경할 수 있습니다.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)]

또한 다음과 같이 변경할 수 있습니다.
- [Common Data Service에 대한 필드 만들기 및 편집](create-edit-fields.md)
- [엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)
- [양식 만들기 및 디자인](../model-driven-apps/create-design-forms.md)
- [프로세스를 표준화하는 비즈니스 프로세스 흐름 만들기](/flow/create-business-process-flow)

## <a name="delete-an-entity"></a>엔터티 삭제

시스템 관리자 보안 역할을 가진 사용자는 관리형 솔루션에 포함되지 않은 사용자 지정 엔터티를 삭제할 수 있습니다.  
  
> [!IMPORTANT]
>  사용자 지정 엔터티를 삭제하면 해당 엔터티에 대한 데이터를 저장하는 데이터베이스 테이블이 삭제되고 그 안에 포함된 모든 데이터가 손실됩니다. 사용자 지정 엔터티에 대한 상위/하위 관계가 있는 관련 레코드도 삭제됩니다. 상하 관계에 대한 자세한 내용은 [엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)을 참조하십시오.  
  
> [!NOTE]
> 삭제된 엔터티에서 데이터를 복구할 수 있는 유일한 방법은 엔터티가 삭제되기 이전 시점에서 데이터베이스를 복원하는 것입니다. 추가 정보: [인스턴스 백업 및 복원](/dynamics365/customer-engagement/admin/backup-restore-instances)

[엔터티를 보는](#view-entities) 동안 도구 모음에서 ![명령 삭제](media/delete.gif) 명령을 클릭합니다.

엔터티를 보는 동안 메뉴 모음에서 삭제 명령을 사용합니다.

![삭제 명령](media/delete-custom-entity-solution-explorer.png)

> [!WARNING]
> 데이터를 포함하는 엔터티를 삭제하면 모든 데이터가 제거됩니다. 이 데이터는 데이터베이스 백업으로만 검색할 수 있습니다.

> [!NOTE]
> 엔터티 종속성이 있는 경우 해당 엔터티를 삭제할 수 없는 이유에 대한 정보를 검색하는 데 사용할 수 있는 **세부 정보** 링크를 사용하여 **구성 요소 삭제 불가능** 오류를 가져옵니다. 대부분의 경우 이 종속성을 제거해야 하는 때문입니다. 
>
> 엔터티의 삭제를 차단하는 두 개 이상의 종속성이 있을 수 있습니다. 이 오류 메시지는 첫 번째 메시지만 표시할 수 있습니다. 종속성을 검색하는 다른 방법은 [엔터티 종속성 식별](#identify-entity-dependencies)을 참조하십시오.



### <a name="identify-entity-dependencies"></a>엔터티 종속성 식별

엔터티를 삭제하기 전에 삭제되지 않도록 하는 종속성을 식별할 수 있습니다. 

1. 선택한 엔터티가 있는 솔루션 탐색기에서 명령 모음에서 **종속성 표시**를 클릭합니다.

![종속성 표시 명령](media/entity-show-dependencies.png)

2. 열리는 대화 상자 창에서 오른쪽으로 목록을 스크롤하여 **종속성 유형** 열을 봅니다.

![게시된 종속성 유형](media/published-entity-dependency.png)

**게시된** 종속성은 엔터티 삭제를 차단합니다. **내부** 종속성은 시스템에서 확인해야 합니다.  

3. 이러한 게시된 종속성을 제거하고 엔터티를 삭제할 수 있어야 합니다.

 > [!NOTE]
 > 매우 일반적인 종속성은 다른 엔터티 양식에 삭제하려는 엔터티에 대한 조회 필드가 있다는 것입니다. 양식에서 조회 필드를 제거하면 종속성이 해결됩니다.

## <a name="create-custom-activity-entity"></a>사용자 지정 활동 엔터티 만들기

엔터티를 활동 엔터티로 만들려면 이 항목에서 설명하는 것과 동일한 단계를 사용하여 **활동 엔터티로 정의**를 선택합니다.

![활동 엔터티로 정의](media/create-activity-entity-solution-explorer.png)

활동 엔터티는 일정에서 항목을 만들 수 있는 작업을 추적하는 특수한 종류의 엔터티입니다. 추가 정보: [활동 엔터티](types-of-entities.md#activity-entities)

이 옵션을 설정하면 일부 엔터티 속성이 호환되지 않습니다. 활동 엔터티는 모든 활동 엔터티가 사용하는 표준 동작을 준수해야 합니다.

기본 필드 **이름** 및 **표시 이름**은 **제목**으로 설정되며 이를 변경할 수 없습니다.

다음 옵션은 기본적으로 설정되어 있으며 변경할 수 없습니다.

 - **피드백**
 - **메모(첨부 파일 포함)**
 - **연결**
 - **큐**
 - **Dynamics 365 for Outlook의 오프라인 기능**

다음 옵션은 설정할 수 없습니다.

- **이 엔터티가 표시되는 영역**
- **활동**
- **전자 메일 보내기**
- **편지 병합**
- **단일 레코드 감사**
- **여러 레코드 감사**

## <a name="create-a-virtual-entity"></a>가상 엔터티 만들기

일부 옵션은 가상 엔터티를 만들 때만 사용됩니다.

|옵션   |설명  |
|---------|---------|
|**가상 엔터티**|엔터티가 가상 엔터티인지 여부입니다.|
|**데이터 원본**|엔터티의 데이터 소스입니다.|

추가 정보: [외부 데이터 원본에서 데이터를 포함하는 가상 엔터티 만들기 및 편집](create-edit-virtual-entities.md)

### <a name="see-also"></a>참조
[Common Data Service에서 엔터티 만들기 및 편집](create-edit-entities.md)<br />
[자습서: PowerApps에서 구성 요소가 있는 사용자 지정 엔터티 만들기](/powerapps/maker/common-data-service/create-custom-entity)<br />
[솔루션 만들기](create-solution.md)
