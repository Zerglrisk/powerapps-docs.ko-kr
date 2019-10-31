---
title: 연결 역할 구성 | MicrosoftDocs
ms.custom: ''
ms.date: 05/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-connection-roles"></a>연결 역할 구성

Common Data Service를 사용하면 엔터티 관계를 만들지 않고 엔터티 레코드 간의 **연결**을 정의할 수 있습니다. 모델 기반 앱에서 사용자는 레코드 간에 명명된 링크를 설정하여 실제 엔터티 관계를 만드는 것을 정당화하지 않는 덜 공식적인 관계를 설정할 수 있습니다. 몇 가지 예로는 *친구*, *형제 자매*, *배우자*, *참석자* 및 *이해 관계자*가 있습니다. 또한 일부 연결은 또한 *자녀*와 *부모*, *남편*과 *아내* 또는 *의사*와 *환자* 등의 상호 연결일 수 있습니다.

두 레코드 간에 연결을 설정하면 관계의 시작 및 종료 날짜와 같은 추가 정보나 설명도 추가할 수 있습니다. 추가 정보: [레코드 간의 관계를 정의 및 표시하도록 연결 레코드 만들기](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records).

**연결 역할** 엔터티에 대한 쓰기 권한이 있는 사용자는 사용자가 사용할 수 있는 연결을 설정할 수 있습니다.

## <a name="view-connection-roles"></a>연결 역할 보기

Common Data Service에 이미 구성된 여러 표준 연결 역할이 있습니다. 역할을 보려면 설정 영역으로 이동해야 합니다. 

### <a name="navigate-to-the-settings-area"></a>설정 영역으로 이동합니다.

1. 모델 기반 앱을 보는 동안 URL을 편집하여 `dynamics.com` 후의 모든 것을 제거하고 페이지를 새로 고칩니다.
1. **설정** > **비즈니스** > **비즈니스 관리**로 이동한 다음 **연결 역할**을 선택합니다.

![비즈니스 관리 설정의 연결 역할](media/navigate-settings-connection-roles.png)

이 보기에서는 이 환경에 사용할 수 있는 모든 연결 역할을 볼 수 있으며 여기에서 편집할 수 있습니다.

> [!NOTE]
> 솔루션에 연결 역할을 배포하려는 경우 배포하려는 솔루션에 포함되어 있는지 확인합니다. 추가 정보: [솔루션에 연결 역할 추가](#add-connection-roles-to-a-solution)

## <a name="view-connection-roles-in-the-solution-explorer"></a>솔루션 탐색기에서 연결 역할을 봅니다.

연결 역할은 *솔루션에 따라 달라지므로*, 즉 솔루션에 포함 될 수 있으므로 배포하는 솔루션에 연결 역할을 추가할 수도 있습니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

**설정** 영역에서 볼 수 있는 대부분의 연결 역할은 *내부* **기본 솔루션**(**Common Data Service의 기본 솔루션**과 혼동되어서는 안 됨) 내에서 정의됩니다. 이 내부 **기본 솔루션**에는 시스템의 모든 사용자 지정이 포함되어 있습니다. **기본 솔루션**을 보려면 **모든 솔루션 - 내부** 보기를 선택합니다.

## <a name="add-connection-roles-to-a-solution"></a>솔루션에 연결 역할 추가

일반적으로 내부 **기본 솔루션**의 구성 요소는 편집하지 않는 것이 좋습니다. **Common Data Service의 기본 솔루션** 또는 작업을 위해 만든 솔루션 내에서 **기존 추가** 명령을 사용하여 솔루션에 기본 연결 역할을 가져올 수 있습니다.

![기존 연결 역할 추가](media/add-existing-connection-role.png)

솔루션에 연결 역할을 추가하고 나면 표시되는 위치에 관계없이 편집할 수 있습니다.

## <a name="create-or-edit-connection-roles"></a>연결 역할을 만들거나 편집합니다.

> [!IMPORTANT]
> 새 연결 역할 또는 기존 연결 역할에 대한 변경 내용이 포함된 솔루션을 배포하려는 경우 배포할 솔루션에 이를 추가해야 합니다. **설정** 영역을 사용하여 새 연결 역할을 편집하거나 추가하면 이러한 연결 역할이 내부 **기본 솔루션**에 추가되며, 배포하는 솔루션에는 이 역할을 먼저 추가하지 않는 한 포함되지 않습니다. 추가 정보 [솔루션에 연결 역할 추가](#add-connection-roles-to-a-solution)

**연결 역할** 목록에서 편집할 연결 역할 중 하나를 선택합니다.
양식에서 명확하게 호출 되는 연결 역할을 정의하는 세 가지 단계가 있습니다.

![연결 역할 양식 만들기](media/create-connection-role-form.png)

### <a name="describe-the-connection-role"></a>연결 역할 설명

다음 필드를 설정합니다.

|필드|설명|
|--|--|
|**이름**|(필수) 연결을 설명하는 텍스트입니다.|
|**연결 역할 범주**|연결 범주를 설명하는 그룹입니다. 추가 정보: [연결 역할 범주 값](#connection-role-category-values)|
|**설명**|역할의 정의를 입력합니다.|

#### <a name="connection-role-category-values"></a>연결 역할 범주 값

기본 **연결 역할 범주** 값은 다음과 같습니다.
- 비즈니스
- 가족
- 소셜
- Sales
- 기타
- 이해 관계자
- 영업 팀
- 서비스

**범주** 전역 옵션 집합을 편집하여 새 범주를 추가하거나 기존 범주를 수정할 수 있습니다. 추가 정보: [Common Data Service에 대한 전역 옵션 집합(선택 목록) 만들기 및 편집](create-edit-global-option-sets.md)

### <a name="select-record-types"></a>레코드 종류 선택

연결할 수 있는 레코드 종류를 선택합니다.

> [!NOTE]
> **모두** 기본적으로 선택되어 있지만 추가하는 연결 역할에 적합한 형식을 고려해야 합니다.

### <a name="matching-connection-roles"></a>일치하는 연결 역할

이 선택적 단계에서는 상호 방식으로 적용되는 모든 역할을 정의할 수 있습니다. 필수는 아니지만 연결이 정의된 경우 더 알기 쉽습니다.

예를 들어 사용자가 글렌을 메리의 *친구*로 설정할 수 있지만 그렇다고 해서 메리가 글렌의 *친구*라는 의미입니까? 그러면 좋을 것입니다. 그러나 글렌이 메리의 *아버지*라면 메리가 글렌의 *아버지*라는 의미는 될 수 없습니다. 올바른 상호 관계를 설정하려면 이 추가 단계가 필요합니다.

사용자가 연결 역할이 일치하지 않는 연결 역할을 설정하는 경우 연결이 적용된 레코드에서 연결을 볼 때만 역할이 표시됩니다. 연결된 레코드에서 볼 때 일치하는 역할이 설정되어 있지 않으면 역할이 비어 있습니다.

*친구*, *배우자*, *동료* 또는 *형제 자매*와 같은 역할 정의의 경우 일치하는 역할을 자체에 할당하는 것이 가장 좋습니다. 일치하는 단일 연결 역할이 구성된 경우 일치하는 단일 연결 역할이 양방향으로 적용됩니다.

> [!IMPORTANT]
> 일치하는 연결 역할을 자체적으로 설정하기 전에 이 일치하는 연결 역할 없이 새 연결 역할을 저장해야 합니다.

일부 연결 역할은 이미 일치하는 연결 역할로 구성되어 있음을 알 수 있습니다. *이전 직원*은 *이전 고용주*와 일치되고 그 반대도 마찬가지입니다. 이 일대일 일치 연결 역할 종류가 가장 일반적입니다.

일치하는 여러 가지 연결 역할을 구성하여 복잡한 관계를 설명할 수 있습니다. *아버지*와 같은 연결 역할을 만드는 경우 *딸* 및 *아들* 같은 두 가지 역할을 더 구성하고 둘 다를 *아버지*와 일치시키는 연결 역할로 적용할 수 있습니다. 차례대로, *딸*과 *아들* 연결 역할은 *아버지*와 일치되어야 합니다. 그러면 당연히 이와 비슷하게 *딸* 및 *아들*과 일치되는 *어머니*에 해당하는 역할을 설정해야 합니다.

> [!TIP]
> 복잡한 연결 역할 집합을 만들기 전에 보다 간단한 역할 집합이 충분한지 고려해야 합니다. 예를 들어 *아버지*, *어머니*, *아들* 및 *딸*과 같은 복잡한 연결 역할 집합을 만드는 대신 *부모*와 *자녀*만 사용해도 효과가 있는지 고려하십시오.

일치하는 연결 역할이 둘 이상 구성된 경우 해당 연결 역할은 유일하게 유효한 상호 역할을 나타냅니다. 첫 번째 값은 자동으로 기본값으로 적용됩니다. 기본값이 올바르지 않으면 사용자가 수동으로 연결을 편집하고 구성에 정의된 유효한 옵션 중에서 선택해야 합니다.

### <a name="see-also"></a>참조
<!-- This is in the basics guide. It needs to be migrated -->
[레코드 간의 관계를 정의하고 보도록 연결 레코드 만들기](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)<br />
[Common Data Service용 전역 옵션 집합(선택 목록) 만들기 또는 편집](create-edit-global-option-sets.md)<br />
[엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)


