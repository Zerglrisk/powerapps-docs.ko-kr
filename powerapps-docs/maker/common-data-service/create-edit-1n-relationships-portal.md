---
title: PowerApps 포털을 사용하여 일대다 또는 다대일 엔터티 관계 만들기 및 편집 | MicrosoftDocs
description: PowerApps 포털을 사용하여 일대다 또는 다대일 엔터티 관계를 만들고 편집하는 방법 알아보기
ms.custom: ''
ms.date: 06/11/2018
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
---
# <a name="create-and-edit-one-to-many-or-many-to-one-entity-relationships-using-powerapps-portal"></a>PowerApps 포털을 사용하여 일대다 또는 다대일 엔터티 관계 만들기 및 편집

[PowerApps 포털](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 통해 Common Data Service에 대한 1: N(일대다) 또는 N:1(다대일) 관계를 쉽게 만들고 편집할 수 있습니다.

포털을 사용하면 가장 일반적인 옵션을 구성할 수 있지만 특정 옵션은 솔루션 탐색기를 사용하여 설정만 가능 합니다. 추가 정보: 
- [1:N(일대다) 또는 N:1(다대일) 관계 만들기 및 편집](create-edit-1n-relationships.md)
- [솔루션 탐색기를 사용하여 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-solution-explorer.md).

## <a name="view-entity-relationships"></a>엔터티 관계를 봅니다.

1. [PowerApps 포털](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **모델 기반** 또는 **캔버스** 디자인 모드 중 하나를 선택합니다.
2. **데이터** > **엔터티**를 선택하고 보려는 관계가 있는 엔터티를 선택합니다.
3. **관계** 탭을 선택한 상태에서 다음 보기를 선택할 수 있습니다. 

 |보기|설명|
 |--|--|
 |**모두**| 엔터티에 대한 모든 관계를 표시합니다.|
 |**사용자 지정**|엔터티에 사용자 지정 관계만 표시합니다.|
 |**기본값**|엔터티에 표준 관계만 표시합니다.|
<!-- TODO: What is the actual difference between All and Default? -->

![거래처 엔터티 관계](media/view-account-relationships-portal.png)

## <a name="create-relationships"></a>관계 만들기

엔터티 [관계를 보는](#view-entity-relationships) 동안 명령 모음에서 **관계 추가**를 선택하고 **다대일** 또는 **일대다** 중 하나를 선택합니다.

![관계 종류를 선택합니다.](media/add-relationship-menu-portal.png)

> [!NOTE]
> **다대다** 관계에 대한 자세한 내용은 [N:N ( 다대다) 관계 만들기](create-edit-nn-relationships.md)를 참조하십시오.

<!-- This may change going forward, but this is the way it is now. #2534972 -->
> [!Important]
> 포털은 솔루션 탐색기와 다른 용어를 사용합니다. 솔루션 탐색기 **기본 엔터티**는 포털의 **현재 엔터티**입니다.

선택에 따라 다음 중 하나를 볼 수 있습니다.

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
|그런 다음|창|
|--|--|
|**다대일**|![다대일 관계 패널](media/many-to-one-relationship-panel.png)|
|**일대다**|![일대다 관계 패널](media/one-to-many-relationship-panel.png)|

두 엔터티 사이에 만들려는 관계에 대해 **관련 엔터티**를 선택합니다. 

> [!NOTE]
> 두 옵션 중 하나를 선택하면 *현재* 엔터티에 조회 필드가 생성됩니다.

엔터티를 선택하면 관계의 세부 정보를 편집할 수 있습니다. 이 예제에서는 여러 연락처 엔터티 레코드를 단일 계정에 연결할 수 있습니다.

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
![일대다 관계 거래처 및 연락처](media/One-to-many-account-contact.png)

저장하기 전에 제공된 기본값을 편집할 수 있습니다. **추가 옵션** 을 선택하여 **관계 이름** 및 **조회 필드 설명** 값을 봅니다.

|필드|설명|
|--|--|
|**조회 필드 표시 이름**|관련 엔터티에 대해 만들어지는 조회 필드의 지역화할 수 있는 텍스트입니다.<br />이는 나중에 편집할 수 있습니다.|
|**조회 필드 이름**|관련 엔터티에 대해 만들어지는 조회 필드의 이름입니다.|
|**관계 이름**|만들 관계의 이름입니다.|
|**조회 필드 설명**|조회 필드에 대한 설명입니다. 모델 기반 앱에서는 사용자가 마우스를 필드 위로 가져가면 도구 설명으로 표시됩니다. <br />이는 나중에 편집할 수 있습니다.|

엔터티 편집을 계속할 수 있습니다. **엔터티 저장**을 선택하여 구성한 관계를 만듭니다.

## <a name="edit-relationships"></a>관계 편집

[엔터티 관계](#view-entity-relationships)를 보는 동안 편집하려는 관계를 선택합니다.

> [!NOTE]
> 각 관계는 기본 엔터티 또는 관련 엔터티 내에서 **다대일** 또는 **일대다** 관계로 찾을 수 있습니다. 어느 위치에서나 편집할 수 있지만 동일한 관계입니다.
>
> 관리형 솔루션의 게시자는 해당 솔루션의 일부인 관계를 일부 사용자 지정하지 못하도록 할 수 있습니다.

편집할 수 있는 필드는 **조회 필드 표시 이름** 및 **조회 필드 설명**뿐입니다. 이러한 항목은 관련 엔터티의 조회 필드 속성에서 편집할 수도 있습니다. 추가 정보: [필드 편집](create-edit-field-portal.md#edit-a-field)

## <a name="delete-relationships"></a>관계 삭제

[엔터티 관계를 보는](#view-entity-relationships) 동안 삭제하려는 관계를 선택합니다.

![엔터티 관계 삭제](media/delete-entity-relationship-portal.png)

명령 모음이나 행 상황에 맞는 메뉴에서 줄임표(**...**)를 클릭하면 **관계 삭제** 명령을 사용할 수 있습니다.

관계를 삭제하면 관련 엔터티의 조회 필드가 삭제됩니다.

> [!NOTE]
> 종속성이 있는 관계는 삭제할 수 없습니다. 예를 들어 관련 엔터티의 양식에 조회 필드를 추가한 경우 관계를 삭제하기 전에 양식에서 해당 필드를 제거해야 합니다.

### <a name="see-also"></a>참조

[엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)<br />
[1:N(일대다) 또는 N:1(다대일) 관계 만들기 및 편집](create-edit-1n-relationships.md)<br />
[솔루션 탐색기를 사용하여 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-solution-explorer.md)<br />
[필드 편집](create-edit-field-portal.md#edit-a-field)
