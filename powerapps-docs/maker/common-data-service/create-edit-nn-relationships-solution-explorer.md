---
title: 솔루션 탐색기를 사용하여 Common Data Service에서 N:N(다대다) 엔터티 관계 만들기 | MicrosoftDocs
description: 다대다 관계를 만드는 방법 알아보기
ms.custom: ''
ms.date: 05/29/2018
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
ms.openlocfilehash: 8c5239874449772922ec9fa89ece7d2b3a5d7f06
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861346"
---
# <a name="create-nn-many-to-many-entity-relationships-in-common-data-service-using-solution-explorer"></a>솔루션 탐색기를 사용하여 Common Data Service에서 N:N(다대다) 엔터티 관계 만들기

솔루션 탐색기를 통해 Common Data Service의 N:N(다대다)를 만들고 편집할 수 있습니다.

[Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 사용하면 가장 일반적인 옵션을 구성할 수 있지만 특정 옵션은 솔루션 탐색기를 사용하여 설정할 수 있습니다. 추가 정보:
- [다대다(N:N) 엔터티 관계 만들기](create-edit-nn-relationships.md)
- [Power Apps 포털을 사용하여 Common Data Service에서 다대다 엔터티 관계 만들기](create-edit-nn-relationships-portal.md)

  
## <a name="open-solution-explorer"></a>솔루션 탐색기를 엽니다.

만든 사용자 지정 관계의 이름 일부는 사용자 지정 접두사입니다. 이 값은 작업 중인 솔루션의 솔루션 게시자에 따라 설정됩니다. 사용자 지정 접두사에 대해 관심이 있을 경우 이 엔터티에 사용할 접두사가 사용자 지정 접두사인 비관리형 솔루션에서 작업하고 있는지 확인하십시오. 추가 정보: [솔루션 게시자 접두사 변경](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entity-relationships"></a>엔터티 관계를 봅니다.

솔루션 탐색기에서 **엔터티**를 선택하여 엔터티를 확장합니다. 해당 엔터티 내에서 **N:N 관계**를 선택합니다.

![N:N 엔터티 관계 보기](media/view-nn-entity-relationships-solution-explorer.png)

## <a name="create-relationships"></a>관계 만들기

[엔터티 관계를 보는](#view-entity-relationships) 동안 명령 모음에서 **새 다대다 관계**를 선택합니다.

> [!NOTE]
> 명령을 사용할 수 없는 경우 엔터티는 사용자 지정 관계를 만들 수 없습니다.

![새 다대다 관계 양식](media/new-nn-entity-relationship-form-solution-explorer.png)

**다른 엔터티** 그룹의 **엔터티 이름** 필드에서 관계를 만들려는 엔터티를 선택합니다. **관계 정의** 그룹의 **이름** 및 **관계 엔터티 이름** 필드가 채워집니다.

![엔터티 관계 저장 단추](media/save-entity-icon-solution-explorer.png)를 클릭하여 엔터티를 저장하고 편집을 계속할 수 있습니다. 추가 정보: [관계 편집](#edit-relationships)

> [!NOTE]
> **이름** 또는 **관계 엔터티 이름** 값이 시스템에 이미 존재하는 경우 저장할 때 오류가 발생합니다. 값을 고유하게 편집하고 다시 시도하십시오.

## <a name="edit-relationships"></a>관계 편집

[엔터티 관계](#view-entity-relationships)를 보는 동안 편집하려는 엔터티를 선택합니다. 

> [!NOTE]
> 관리형 솔루션의 게시자는 해당 솔루션의 일부인 관계를 사용자 지정하지 못하도록 할 수 있습니다.

관계를 만든 후에는 다음 엔터티 관계 속성을 편집할 수 있습니다.

> [!IMPORTANT]
> 이러한 속성을 편집한 후에는 모델 기반 앱에 적용하기 전에 사용자 지정 항목을 게시해야 합니다.

### <a name="edit-display-options"></a>표시 옵션 편집

**현재 엔터티**와 **다른 엔터티**의 경우 모델 기반 앱에 대해 관련 엔터티가 표시되는 방법을 제어하는 표시 옵션 필드를 편집할 수 있습니다.

|필드|설명|
|--|--|
|**표시 옵션**|관련 엔터티 목록을 표시 하는 방법입니다. 추가 정보: [표시 옵션](#display-options)|
|**사용자 지정 레이블**|**표시 옵션**으로 **사용자 지정 레이블 사용**을 선택할 때 복수형 이름 대신 사용할 지역화할 수 있는 텍스트를 지정합니다.|
|**표시 영역**|사용 가능한 그룹 중 하나를 선택하여 이 목록을 표시합니다. 사용 가능한 옵션은 **세부 정보**( *공통* 그룹), **마케팅**, **영업** 및 **서비스**입니다. |
|**표시 순서**|탐색 항목을 선택한 표시 영역 내에 포함할 것인지 여부를 제어합니다. 이 값은 10,000부터 지정할 수 있습니다. 값이 더 작은 탐색 창 항목이 값이 높은 다른 관계보다 위에 나타납니다.|

<!-- TODO: Not sure whether Display Area or Display Order are still used anymore. Might only be used in the Outlook client?-->

#### <a name="display-options"></a>표시 옵션

사용 가능한 표시 옵션은 다음과 같습니다.

|옵션|설명|
|--|--|
|**표시 안 함**|이 관계에 대한 관련 엔터티를 표시하지 않습니다.|
|**사용자 지정 레이블**|이 옵션을 선택하면 **사용자 지정 레이블** 필드가 활성화되어 복수형 이름 대신 지역화할 수 있는 텍스트를 지정합니다.|
|**복수 이름**|관련 엔터티에 대해 정의된 복수 표시 이름을 사용합니다.|

### <a name="searchable"></a>검색 가능

**검색 가능**한 필드를 **아니요**로 설정하여 모델 기반 앱에서 **상세하게 찾기**를 통해 관계를 숨길 수 있습니다.

## <a name="delete-relationships"></a>관계 삭제

[엔터티 관계를 보는](#view-entity-relationships) 동안 삭제하려는 엔터티 관계를 선택하고 ![명령 삭제](media/delete.gif) 명령을 클릭 합니다.

관계를 삭제하면 생성된 관계 엔터티가 삭제됩니다. 관계를 사용하여 엔터티를 연결하는 모든 데이터가 손실됩니다.

### <a name="see-also"></a>참조

[다대다(N:N) 엔터티 관계 만들기](create-edit-nn-relationships.md)<br />
[Power Apps 포털을 사용하여 Common Data Service에서 다대다 엔터티 관계 만들기](create-edit-nn-relationships-portal.md)<br />
[1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships.md)
