---
title: 솔루션 탐색기를 사용하여 Common Data Service에 대한 전역 옵션 집합 만들기 및 편집 | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
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
# <a name="create-and-edit-global-option-sets-for-common-data-service-using-solution-explorer"></a>솔루션 탐색기를 사용하여 Common Data Service에 대한 전역 옵션 집합 만들기 및 편집

솔루션 탐색기를 통해 Common Data Service의 전역 옵션 집합을 만들고 편집할 수 있습니다.

[PowerApps 포털](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 사용하면 가장 일반적인 옵션을 구성할 수 있지만 특정 옵션은 솔루션 탐색기를 사용하여 설정할 수 있습니다. <br />추가 정보: 
- [Common Data Service용 전역 옵션 집합 만들기 또는 편집](create-edit-global-option-sets.md)
- [옵션 집합 만들기](custom-picklists.md)

## <a name="open-solution-explorer"></a>솔루션 탐색기를 엽니다.

만든 전역 옵션 집합의 이름 일부는 사용자 지정 접두사입니다. 이 값은 작업 중인 솔루션의 솔루션 게시자에 따라 설정됩니다. 사용자 지정 접두사에 대해 관심이 있을 경우 이 전역 옵션 집합에 사용할 접두사가 사용자 지정 접두사인 비관리형 솔루션에서 작업하고 있는지 확인하십시오. 추가 정보: [솔루션 게시자 접두사 변경](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-global-option-sets"></a>전역 옵션 집합 보기

솔루션 탐색기를 연 상태에서 **구성 요소**에서 **옵션 집합**을 선택합니다.

![전역 옵션 집합 보기](media/view-global-option-sets-solution-explorer.png)

> [!NOTE]
> 일부 시스템 전역 옵션 집합은 사용자 지정할 수 없습니다. 이러한 옵션은 업데이트 또는 새 버전으로 변경할 수 있으므로 사용자의 요구 사항이 Common Data Service에서 이러한 값을 사용하는 방식과 일치하는지 확실하지 않을 경우 사용하지 않는 것이 좋습니다.

## <a name="create-a-global-option-set"></a>전역 옵션 집합 만들기

> [!NOTE]
> 사용자 지정 필드 내에서 사용하기 전에 전역 옵션 집합을 만들 필요가 없습니다. 새 옵션 집합 필드를 만들 때 새 전역 옵션 집합을 만들거나 기존 항목을 사용하는 옵션이 있습니다. [옵션 집합 필드 옵션](create-edit-field-solution-explorer.md#option-set-field-options)을 참조하십시오.

전역 옵션 집합을 보는 동안 **새로 만들기** 를 클릭하여 전역 옵션 집합을 정의하는 양식을 엽니다.

![전역 옵션 집합 만들기](media/create-global-option-set-solution-explorer.png)

시스템 관리자 또는 사용자 지정자 역할이 있는 사용자가 볼 수 있는 **표시 이름**을 입력하여 이 전역 옵션 집합을 사용하는 새 필드를 정의할 때 이 설정을 선택합니다. 이 이름은 앱을 사용하는 사용자에 게 표시되지 않습니다.

**이름** 필드 값은 입력한 **표시 이름**에 따라 사용자를 위해 생성됩니다. 여기에는 작업 중인 솔루션의 컨텍스트에서 솔루션 게시자에 대한 사용자 지정 접두사가 포함됩니다. 저장하기 전에 **이름** 필드 값의 생성된 부분을 변경할 수 있습니다.

전역 옵션 집합의 **설명**을 입력합니다. 

> [!TIP]
> **설명을** 사용하여 이 전역 옵션 집합의 용도를 설명합니다. 이 값은 응용 프로그램 사용자에 게 표시되지 않으며,이 특정 전역 옵션 집합이 만들어진 이유를 알고 싶은 시스템 관리자나 사용자 지정자 역할이 있는 다른 사람을 위한 것입니다.

### <a name="configure-options"></a>옵션 구성

[!INCLUDE [cc_configure-option-set-options-solution-explorer](../../includes/cc_configure-option-set-options-solution-explorer.md)]

## <a name="edit-a-global-option-set"></a>전역 옵션 집합 편집

전역 옵션 집합을 보는 동안 편집하려는 옵션 집합을 선택하여 패널을 열어서 편집합니다.

**이름** 필드 값 또는 옵션에 지정된 숫자 **값** 을 변경하는 경우를 제외하고 전역 옵션 집합을 만들 때 수행할 수 있는 모든 변경 작업을 수행할 수 있습니다.

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-global-option-set"></a>전역 옵션 집합 삭제

전역 옵션 집합을 삭제하려면 목록을 보는 동안 ![삭제 명령](media/delete.gif) 명령 모음에서 명령을 실행 합니다.

> [!IMPORTANT]
> 전역 옵션 집합을 필드에서 사용하는 경우 해당 필드를 삭제할 때까지 삭제할 수 없습니다.
  
### <a name="see-also"></a>참조
 
[Common Data Service용 전역 옵션 집합 만들기 또는 편집](create-edit-global-option-sets.md)<br />
[옵션 집합 만들기](custom-picklists.md)<br />
[필드 만들기 및 편집](create-edit-fields.md)<br />
[개발자 설명서: 전역 옵션 집합 사용자 지정](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)
