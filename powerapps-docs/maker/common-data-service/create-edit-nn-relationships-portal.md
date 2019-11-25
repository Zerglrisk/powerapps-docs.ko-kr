---
title: PowerApps 포털을 사용하여 Common Data Service에서 다대다 엔터티 관계 만들기 | MicrosoftDocs
description: 다대다 관계를 만드는 방법 알아보기
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
ms.openlocfilehash: 9a0a8ec96760c6816ea2b6caaf4bcc760b9852de
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757715"
---
# <a name="create-many-to-many-entity-relationships-in-common-data-service-using-powerapps-portal"></a>PowerApps 포털을 사용하여 Common Data Service에서 다대다 엔터티 관계 만들기

[PowerApps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 통해 Common Data Service에 대한 다대다 엔터티 관계를 쉽게 만들고 편집할 수 있습니다.

포털을 사용하면 가장 일반적인 옵션을 구성할 수 있지만 특정 옵션은 솔루션 탐색기를 사용하여 설정만 가능 합니다. 추가 정보: 
- [N:N(다대다) 엔터티 관계 만들기](create-edit-nn-relationships.md)
- [솔루션 탐색기를 사용하여 Common Data Service에서 N:N(다대다) 엔터티 관계 만들기](create-edit-nn-relationships-solution-explorer.md)

## <a name="view-many-to-many-entity-relationships"></a>다대다 엔터티 관계 보기

1. [PowerApps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **모델 기반** 또는 **캔버스** 디자인 모드 중 하나를 선택합니다.
2. **데이터** > **엔터티**를 선택하고 보려는 관계가 있는 엔터티를 선택합니다.
3. **관계** 탭을 선택한 상태에서 다음 보기를 선택할 수 있습니다. 

 |보기|설명|
 |--|--|
 |**모두**| 엔터티에 대한 모든 관계를 표시합니다.|
 |**사용자 지정**|엔터티에 사용자 지정 관계만 표시합니다.|
 |**기본값**|엔터티에 표준 관계만 표시합니다.|
<!-- TODO: What is the actual difference between All and Default? -->

![거래처 엔터티 관계](media/view-account-relationships-portal.png)

다대다 관계에는 **다대다**의**관계 유형**이 있습니다.

> [!NOTE]
> 표시되는 엔터티에는 **다대다** 관계가 없을 수 있습니다.

## <a name="create-relationships"></a>관계 만들기

엔터티 [관계를 보는](#view-many-to-many-entity-relationships) 동안 명령 모음에서 **관계 추가**를 선택하고 **다대다**를 선택합니다.

![관계 종류를 선택합니다.](media/add-relationship-menu-portal.png)

**다대다** 패널에서 현재 엔터티와 관련된 엔터티를 선택합니다.

![계정 엔터티가 선택된 다대다 패널](media/many-to-many-panel-1.png)

**추가 옵션** 을 선택하여 **관계 이름** 및 **관계 엔터티 이름** 필드를 봅니다.

![기타 옵션이 선택된 다대다 패널](media/many-to-many-panel-2.png)

이러한 필드의 값은 선택한 엔터티에 따라 생성됩니다.

> [!NOTE]
> 동일한 두 엔터티를 사용하여 **다대다**관계를 둘 이상 만드는 경우 고유한 것으로 생성된 **관계 이름** 및 **관계 엔터티 이름** 필드를 편집해야 합니다.

**확인**을 선택하여 **다대다** 패널을 닫습니다. 엔터티 변경 내용을 저장할 때 관계가 만들어집니다. 

저장된 후에는 [PowerApps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 사용하여 변경할 수 있는 것이 없습니다. 모델 기반 앱에 대한 관계의 속성을 편집하려면 [솔루션 탐색기](create-edit-nn-relationships-solution-explorer.md)를 사용합니다.

## <a name="delete-relationships"></a>관계 삭제

[엔터티 관계를 보는](#view-many-to-many-entity-relationships) 동안 삭제하려는 관계를 선택합니다.

![엔터티 관계 삭제](media/delete-entity-relationship-portal.png)

명령 모음이나 행 상황에 맞는 메뉴에서 줄임표(**...**)를 선택하면 **관계 삭제** 명령을 사용할 수 있습니다.

다대다 관계를 삭제하면 생성된 관계 엔터티가 삭제됩니다. 관계를 사용하여 엔터티를 연결하는 모든 데이터가 손실됩니다.

### <a name="see-also"></a>참조

[N:N(다대다) 엔터티 관계 만들기](create-edit-nn-relationships.md)<br />
[솔루션 탐색기를 사용하여 Common Data Service에서 N:N(다대다) 엔터티 관계 만들기](create-edit-nn-relationships-solution-explorer.md)
