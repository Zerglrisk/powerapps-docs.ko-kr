---
title: Canvas 앱에서 컬렉션 만들기 및 업데이트 | Microsoft Docs
description: Canvas 앱에서 컬렉션을 만들고, 컬렉션에 항목을 추가 하 고, 항목에서 하나 또는 모든 항목을 제거 합니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/28/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b124a27119a7b91572bdfef563e0f99e9d5da08d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731800"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>Canvas 앱에서 컬렉션 만들기 및 업데이트

컬렉션을 사용 하 여 사용자가 앱에서 관리할 수 있는 데이터를 저장 합니다. 컬렉션은 제품 목록의 제품과 같이 유사한 항목의 그룹입니다. 컬렉션과 같은 다양 한 형식의 변수에 대 한 자세한 내용은 [canvas-앱 변수 이해](working-with-variables.md)를 확인 하세요.

## <a name="prerequisites"></a>필수 조건

- Power Apps에 [등록](../signup-for-powerapps.md) 한 다음 등록 하는 데 사용한 것과 동일한 자격 증명을 제공 하 여 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 합니다.
- 앱을 만들거나 Power Apps에서 기존 앱을 엽니다.
- Power Apps에서 [컨트롤을 구성](add-configure-controls.md) 하는 방법에 대해 알아봅니다.

## <a name="create-a-multicolumn-collection"></a>여러 열 컬렉션 만들기

1. Power Apps 스튜디오에서 **텍스트 입력** 컨트롤을 추가 합니다.

    ![텍스트 입력 컨트롤 삽입](./media/create-update-collection/add-textbox.png)

1. 왼쪽 탐색 창에서 줄임표를 선택 하 고 **이름 바꾸기**를 선택한 다음 **ProductName**을 입력 하 여 컨트롤의 이름을 바꿉니다.

    ![컨트롤 이름 바꾸기](./media/create-update-collection/rename-textbox.png)

1. **드롭다운** 컨트롤을 추가 합니다.

    ![드롭다운 목록 추가](./media/create-update-collection/add-dropdown.png)

1. **드롭다운** 컨트롤 **색**의 이름을 바꾸고 속성 목록에서 **Items** 속성을 선택 했는지 확인 합니다.

    ![항목 속성](./media/create-update-collection/items-property.png)

1. 수식 입력줄에서 **DropDownSample** 을 다음 식으로 바꿉니다.

    `["Red","Green","Blue"]`

1. **단추** 컨트롤을 추가 하 고 **Text** 속성을 **"추가"** 로 설정 하 고 **onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. F5 키를 누르고 **ProductName**에 일부 텍스트를 입력 한 다음 **색**에서 옵션을 선택 하 고 **추가**를 선택 합니다.

    ![앱 미리 보기](./media/create-update-collection/preview-add.png)

1. 이전 단계를 두 번 이상 반복 하 고 Esc 키를 누릅니다.

1. **파일** 메뉴에서 **컬렉션** 을 선택 하 여 사용자가 만든 컬렉션을 표시 합니다.

    ![컬렉션 표시](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>컬렉션 표시

1. 세로 **갤러리** 컨트롤을 추가 합니다.

    ![세로 갤러리 추가](./media/create-update-collection/add-gallery.png)

1. 갤러리의 **Items** 속성을 **ProductList**로 설정 합니다.

1. **데이터** 창에서 부제 필드를 **색**으로 설정 하 고 제목 필드를 **Product**로 설정 합니다.

    ![갤러리의 Items 속성을 설정 하 고 표시 되는 필드를 변경 합니다.](./media/create-update-collection/configure-gallery.png)

1. **데이터** 창을 닫고 갤러리를 선택한 후 **레이아웃** 필드를 **제목 및 부제**로 설정 합니다.

    ![갤러리의 Items 속성을 설정 하 고 표시 되는 필드를 변경 합니다.](./media/create-update-collection/change-layout.png)

    화면은 다음 예와 유사 합니다.

    ![첫 번째 화면 예제](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>하나 또는 모든 항목 제거

1. 갤러리의 아래쪽 근처를 클릭 하거나 탭 한 다음 왼쪽 위 모퉁이 근처의 연필 아이콘을 클릭 하거나 탭 하 여 갤러리 템플릿을 선택 합니다.

    ![갤러리 템플릿 선택](./media/create-update-collection/select-template.png)

1. 갤러리 템플릿에 **휴지통** 아이콘을 추가 합니다.

    ![휴지통 추가 아이콘](./media/create-update-collection/trash-icon.png)

1. 아이콘의 **Onselect** 속성을 다음 수식으로 설정 합니다.

    `Remove(ProductList, ThisItem)`

1. 갤러리 외부에서 단추를 추가 하 고 **Text** 속성을 **"Clear"** 로 설정 하 고 **onselect** 속성을 다음 수식으로 설정 합니다.

    `Clear(ProductList)`

1. Alt 키를 누른 채로 항목에 대 한 **휴지통** 아이콘을 선택 하 여 컬렉션에서 해당 항목을 제거 하거나 **지우기** 단추를 선택 하 여 컬렉션에서 모든 항목을 제거 합니다.

## <a name="put-a-sharepoint-list-into-a-collection"></a>컬렉션에 SharePoint 목록 넣기

1. [SharePoint 목록에 대한 연결을 만듭니다](connections/connection-sharepoint-online.md#create-a-connection).

1. 단추를 추가하고 단추의 **[OnSelect](controls/properties-core.md)** 속성을 이 함수로 설정합니다. 이때 *ListName*을 SharePoint 목록의 이름으로 바꿉니다.<br>

    `Collect(MySPCollection, ListName)`

    이 함수는 SharePoint 목록과 동일한 데이터를 포함하는, **MySPCollection**이라는 컬렉션을 만듭니다.

1. Alt 키를 누른 상태에서 단추를 선택합니다.

1. 필드 만든 컬렉션을 미리 보려면 **파일** 메뉴에서 **컬렉션** 을 선택 합니다.

갤러리에서 SharePoint 목록의 데이터를 표시 하는 방법에 대 한 자세한 내용은 [갤러리에서 목록 열 표시](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery)를 선택 합니다. 폼에 데이터를 표시 하는 방법에 대 한 자세한 내용 (드롭다운 목록, 날짜 선택기 및 사용자 선택기 사용): [양식 편집 및 표시 양식 컨트롤](controls/control-form-detail.md)

## <a name="next-steps"></a>다음 단계

- **Collect** 함수에 대 한 [참조 항목](functions/function-clear-collect-clearcollect.md) 을 검토 합니다.
- [Addcolumns, dropcolumns, RenameColumns 및 showcolumns](functions/function-table-shaping.md) 함수를 사용 하 여 컬렉션의 데이터를 그룹화 하는 방법에 대해 알아봅니다.
