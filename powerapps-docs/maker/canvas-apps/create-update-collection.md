---
title: 만들기 및 캔버스 앱에서 컬렉션 업데이트 | Microsoft Docs
description: 캔버스 앱에서 컬렉션을 만드는 항목 컬렉션에 추가한에서 하나 또는 모든 항목을 제거
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/28/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6089063e2478c95bb5bfbc5926608d85552cea40
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61561624"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>만들기 및 캔버스 앱에서 컬렉션 업데이트

컬렉션을 사용하여 앱에서 사용자가 관리할 수 있는 데이터를 저장합니다. 컬렉션은 제품 목록의 제품과 같은 비슷한 항목의 그룹입니다. 컬렉션과 같은 변수의 다른 형식에 대한 정보는 [캔버스 앱 변수 이해](working-with-variables.md)를 참조합니다.

## <a name="prerequisites"></a>필수 조건

- PowerApps에 [등록](../signup-for-powerapps.md)한 다음, 등록에 사용한 동일한 자격 증명을 입력하여 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
- PowerApps에서 앱을 만들거나 기존 앱을 엽니다.
- PowerApps에서 [컨트롤 구성](add-configure-controls.md)을 어떻게 하는지 알아봅니다.

## <a name="create-a-multicolumn-collection"></a>여러 열 컬렉션 만들기

1. PowerApps Studio에서, **텍스트 입력** 컨트롤을 추가합니다.

    ![텍스트 입력된 컨트롤을 삽입 합니다.](./media/create-update-collection/add-textbox.png)

1. 왼쪽된 탐색 창에서 줄임표를 선택하여 **이름 바꾸기**를 선택한 다음 **ProductName**을 입력하여 컨트롤의 이름을 변경합니다.

    ![컨트롤 이름 바꾸기](./media/create-update-collection/rename-textbox.png)

1. **드롭다운** 컨트롤을 추가합니다.

    ![드롭다운 목록 추가](./media/create-update-collection/add-dropdown.png)

1. **드롭다운** 컨트롤의 이름을 **Colors**로 변경하고, 속성 목록에서 **Items** 속성이 선택되었는지 확인합니다.

    ![항목 속성](./media/create-update-collection/items-property.png)

1. 수식 입력줄에서 **DropDownSample**을 다음 수식으로 변경합니다.

    `["Red","Green","Blue"]`

1. **단추** 컨트롤을 추가하고, **Text** 속성을 **"추가"** 로 설정하고, **OnSelect** 속성을 다음 수식으로 설정합니다.

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. <F5> 키를 눌러, **ProductName**에 일부 텍스트를 입력하고, **Colors**에서 옵션을 선택한 후 **추가**를 선택합니다.

    ![앱의 미리 보기](./media/create-update-collection/preview-add.png)

1. 이전 단계를 최소한 두 번 더 반복 하 고 Esc 키를 누릅니다.

1. **파일** 메뉴에서 생성한 컬렉션을 보기 위해 **컬렉션**을 선택합니다.

    ![컬렉션 표시](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>컬렉션 표시

1. 세로 **갤러리** 컨트롤을 추가합니다.

    ![세로 갤러리 추가](./media/create-update-collection/add-gallery.png)

1. 갤러리의 **Items** 속성을 **ProductList**로 설정합니다.

1. **데이터** 창에서, 부제목 필드를 **Color**로, 제목 필드를 **Product**로 설정합니다.

    ![갤러리의 항목 속성을 설정 하 고 표시 하는 필드 변경](./media/create-update-collection/configure-gallery.png)

1. **데이터** 창을 닫고, 갤러리를 선택한 다음 **레이아웃** 필드를 **제목 및 부제목**으로 설정합니다.

    ![갤러리의 항목 속성을 설정 하 고 표시 하는 필드 변경](./media/create-update-collection/change-layout.png)

    화면에는 이 예제와 비슷하게 표시될 것입니다.

    ![첫 번째 화면 예제](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>하나 또는 모든 항목 제거

1. 갤러리 아래쪽을 탭하거나 클릭하여, 또는 왼쪽 위 모서리 근처에서 연필 아이콘을 탭하거나 클릭하여 갤러리 템플릿을 선택합니다.

    ![갤러리 템플릿이 선택](./media/create-update-collection/select-template.png)

1. 갤러리 템플릿에 **휴지통** 아이콘을 추가합니다.

    ![휴지통 아이콘 추가](./media/create-update-collection/trash-icon.png)

1. 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `Remove(ProductList, ThisItem)`

1. 갤러리 외부에, 단추를 추가하고 **Text** 속성을 **"지우기"** 로 설정하고 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `Clear(ProductList)`

1. <Alt> 키를 누른 채로 컬렉션에서 해당 항목을 제거하기 위해 항목의 **휴지통** 아이콘을 선택하거나, 컬렉션에서 모든 항목을 제거하기 위해 **지우기** 단추를 선택합니다.

## <a name="put-a-sharepoint-list-into-a-collection"></a>컬렉션에 SharePoint 목록 넣기

1. [SharePoint 목록에 대한 연결을 만듭니다](connections/connection-sharepoint-online.md#create-a-connection).

1. 단추를 추가하고 단추의 **[OnSelect](controls/properties-core.md)** 속성을 이 함수로 설정합니다. 이때 *ListName*을 SharePoint 목록의 이름으로 바꿉니다.<br>

    `Collect(MySPCollection, ListName)`

    이 함수는 SharePoint 목록과 동일한 데이터를 포함하는, **MySPCollection**이라는 컬렉션을 만듭니다.

1. Alt 키를 누른 상태에서 단추를 선택합니다.

1. (선택 사항) 사용자가 만든 컬렉션을 미리 보려면 **파일** 메뉴에서 **컬렉션**을 선택합니다.

갤러리에서 SharePoint 목록(예: 날짜, 선택 및 사용자)의 데이터를 표시하는 방법에 대한 정보는  [갤러리에서 목록 열 표시](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery)를 확인합니다. 폼(드롭다운 목록, 날짜 선택 및 사용자 선택을 사용)에서 데이터를 표시하는 방법에 대한 정보는  [편집 폼 및 표시 폼 컨트롤](controls/control-form-detail.md)을 확인합니다.

## <a name="next-steps"></a>다음 단계

- **Collect** 함수에 대한 [참조 항목](functions/function-clear-collect-clearcollect.md)을 검토합니다.
- [AddColumns, DropColumns, RenameColumns 및 ShowColumns](functions/function-table-shaping.md) 함수를 사용하여 컬렉션에서 데이터를 셰이핑하는 방법을 알아봅니다.
