---
title: 옵션 집합 만들기| Microsoft Docs
description: 옵션 집합을 만드는 방법에 대한 단계별 지침입니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6f3f47882800252c91de0efc572954f7397ac251
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757627"
---
# <a name="create-an-option-set"></a>옵션 집합 만들기

옵션 집합을 사용하면 앱 내에서 사용자에게 고정 된 값의 드롭다운 목록을 포함하여 데이터 일관성을 보장하고, 다른 응용 프로그램에서는 선택 목록이라고도 합니다. 엔터티와 유사하게 표준 옵션 집합이 둘 다 있으며 앱 내에서 사용할 사용자 지정 옵션 집합을 만들 수 있습니다.

옵션 집합은 포털 내의 옵션 집합 목록에서 또는 필드를 만드는 동안 엔터티 내에서 직접 두 가지 방법으로 만들 수 있습니다. 엔터티를 만드는 방법에 대한 자세한 내용은 [엔터티 만들기](data-platform-create-entity.md)를 참조하십시오.

## <a name="creating-an-option-set-while-adding-a-field"></a>필드를 추가하는 동안 옵션 집합 만들기

1. [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **데이터** 섹션을 확장하고 왼쪽 탐색 창에서 **엔터티**를 클릭하거나 탭합니다.

    ![엔터티 세부 정보](./media/data-platform-cds-create-entity/entitylist.png "엔터티 목록")

2. 기존 엔터티 클릭 또는 탭 또는 [새 엔터티 만들기](data-platform-create-entity.md)

3. **필드 추가**를 클릭하여 엔터티에 새 필드를 추가합니다.

4. 새 필드 패널에서 필드의 **표시 이름**을 입력 하면 **이름**이 자동으로 채워지고 필드의 고유 이름으로 사용됩니다. **표시 이름**은 사용자에게이 필드를 표시할 때 사용되며,이 **이름**은 앱을 빌드할 때 식과 수식에서 사용됩니다.

    > [!div class="mx-imgBorder"] 
    > ![새 필드](./media/data-platform-cds-create-entity/newfieldpanel.png "새 필드 패널")

5. **데이터 유형** 드롭다운을 클릭하고 **옵션 집합** 또는 **다중 선택 옵션 집합**을 선택합니다.

6. **옵션 집합** 드롭다운을 클릭하고 **새 옵션 집합**을 선택합니다.

    > [!NOTE]
    > 엔터티에 대해 기존 옵션 집합을 사용할 수 있는 경우 새로 만들지 않고 이 목록에서 선택할 수 있습니다.

    ![옵션 집합 목록](./media/data-platform-cds-newoptionset/fieldpanel-1.png "옵션 집합 목록")

7. 새 패널이 열리면 옵션 집합을 만들 수 있으며 **표시 이름** 및 **이름**은 필드 이름에서 기본값이 되지만 필요한 경우 변경할 수 있습니다. **새 항목 추가**를 클릭하여 옵션 목록 만들기를 시작합니다. 모든 항목이 만들어질 때까지 이 단계를 반복합니다.

    > [!div class="mx-imgBorder"] 
    > ![새 옵션 집합](./media/data-platform-cds-newoptionset/field-optionsetpanel.png "새 옵션 집합")

8. 항목을 입력한 후 **저장**을 클릭하여 옵션 집합을 만듭니다.

    > [!div class="mx-imgBorder"] 
    > ![새 옵션 집합](./media/data-platform-cds-newoptionset/field-optionsetpanel-values.png "새 옵션 집합")

9. **완료**를 클릭하여 필드 패널을 닫은 다음 **엔터티 저장**으로 엔터티를 Common Data Service에 저장합니다.

    > [!NOTE]
    > 항목 중 하나를 이 필드의 **기본값**으로 선택할 수 있으며 사용자가 엔터티에 새 레코드를 만들 때 기본적으로 선택됩니다.

    > [!div class="mx-imgBorder"] 
    > ![새 필드](./media/data-platform-cds-newoptionset/fieldpanel-2.png "새 필드 패널")

## <a name="creating-an-option-set-from-the-option-set-list"></a>옵션 집합 목록에서 옵션 집합 만들기

1. [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **데이터** 섹션을 확장하고 왼쪽 탐색 창에서 **옵션 집합**를 클릭하거나 탭합니다.

    > [!div class="mx-imgBorder"] 
    > ![옵션 집합](./media/data-platform-cds-newoptionset/optionsetlist.png "옵션 집합 목록")

2. **새 옵션 집합**을 클릭합니다.

3. 새 패널이 열려 옵션 집합을 만들면 **표시 이름** 및 **이름**을 입력합니다. **새 항목 추가**를 클릭하여 옵션 목록 만들기를 시작합니다. 모든 항목이 만들어질 때까지 이 단계를 반복합니다.

    > [!div class="mx-imgBorder"] 
    > ![옵션 집합 만들기](./media/data-platform-cds-newoptionset/optionset-create.png "옵션 집합 만들기")

4. 항목을 입력한 후 **저장**을 클릭하여 옵션 집합을 만듭니다.

    > [!div class="mx-imgBorder"] 
    > ![새 옵션 집합](./media/data-platform-cds-newoptionset/optionset-create-values.png "새 옵션 집합")

5. 이제 엔터티에 새 필드를 만들어 이 옵션 집합을 사용할 수 있습니다.

## <a name="global-and-local-option-sets"></a>전역 및 로컬 옵션 집합

기본적으로 옵션 집합은 여러 엔터티에 걸쳐 다시 사용할 수 있도록 하는 전역 옵션 집합으로 만들어집니다. 새 옵션 집합을 만들 때 **더 보기** 옵션에서 **로컬** 옵션을 설정하도록 선택할 수 있습니다. 이 옵션은 옵션 집합 목록이 아니라 필드를 추가하는 동안 옵션 집합을 만들 때만 사용할 수 있습니다. 로컬 옵션 집합은 생성되는 엔터티와 필드에서만 사용할 수 있으며 다른 엔터티에 대해 다시 사용할 수 없습니다. 이 방법은 로컬 옵션 집합에 대한 특정 요구를 가진 고급 사용자에게만 권장됩니다.

> [!IMPORTANT]
> 옵션 집합을 로컬 또는 전역으로 만든 후에는 변경할 수 없습니다.
