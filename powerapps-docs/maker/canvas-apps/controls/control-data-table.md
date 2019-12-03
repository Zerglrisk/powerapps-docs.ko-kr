---
title: '데이터 테이블 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 데이터 테이블 컨트롤 정보
author: jasongre
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2017
ms.author: jasongre
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4eaa58bc7bb27746a574c52fcd49253858a471ca
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723188"
---
# <a name="data-table-control-in-power-apps"></a>Power Apps의 데이터 테이블 제어
테이블 형식으로 데이터 집합을 보여 줍니다.

## <a name="description"></a>설명
**데이터 테이블** 컨트롤은 컨트롤이 표시하는 각 필드에 대한 머리글을 포함하는 형식으로 데이터 세트를 보여 줍니다. 앱 제작자는 표시할 필드와 순서를 완전히 제어할 수 있습니다. **갤러리** 컨트롤처럼 **데이터 테이블** 컨트롤도 선택된 행을 가리키는 **Selected** 속성을 유지합니다. 따라서 **데이터 테이블**을 다른 컨트롤에 연결할 수 있습니다.

## <a name="capabilities"></a>기능
Power Apps는 5 월 5 일 2017에 **데이터 테이블** 컨트롤을 도입 했습니다. 이 섹션에서는 지원되는 기능과 지원되지 않는 기능에 대한 정보를 제공합니다.

### <a name="now-available"></a>지금 사용 가능
* **데이터 테이블** 컨트롤의 데이터는 읽기 전용입니다.
* **데이터 테이블** 컨트롤에서는 항상 단일 행이 선택됩니다.
* **데이터 테이블** 컨트롤을 연결된 또는 로컬 데이터 원본에 연결합니다.
* 앱을 실행하는 동안 변경 내용이 저장되지 않더라도 **데이터 테이블** 컨트롤의 열 너비를 조정합니다.
* Common Data Service 등, 이 기능을 구현하는 커넥터에 연결할 때 **데이터 테이블** 컨트롤에 기본 필드 집합이 표시됩니다. 그런 다음 필요에 따라 이 필드 및 기타 항목을 표시하거나 숨길 수 있습니다.
* 열 너비와 제목 텍스트를 사용자 지정합니다.
* **데이터 테이블** 컨트롤에 하이퍼링크를 표시합니다.
* **데이터 테이블** 컨트롤을 복사하여 붙여넣습니다.

### <a name="not-yet-available"></a>아직 사용할 수 없음
* 개별 열의 스타일을 사용자 지정합니다.
* 양식 컨트롤에 **데이터 테이블** 컨트롤을 추가합니다.
* 모든 행의 높이를 변경합니다.
* **데이터 테이블** 컨트롤에 이미지를 표시합니다.
* 관련된 엔터티로부터 필드를 표시합니다.
* 기본 기능을 사용하여 열 머리글에 따라 데이터를 필터링 및 정렬합니다.
* **갤러리** 컨트롤에 **데이터 테이블** 컨트롤을 추가합니다.
* **데이터 테이블** 컨트롤에서 데이터를 편집합니다.
* 여러 행을 선택합니다.

### <a name="known-issues"></a>알려진 문제
* **Items** 속성에서 **FirstN** 함수를 사용할 때 데이터가 표시되지 않습니다.

## <a name="key-properties"></a>주요 속성
* [**Items**](properties-core.md) – **데이터 테이블** 컨트롤에 표시되는 데이터의 원본입니다.
* **Selected** – **데이터 테이블** 컨트롤에서 선택된 행입니다.

## <a name="other-properties"></a>기타 속성
* [**BorderColor**](properties-color-border.md) - **데이터 테이블** 컨트롤의 테두리 색입니다.
* [**BorderColor**](properties-color-border.md) - **데이터 테이블** 컨트롤의 테두리 스타일입니다. 옵션은 **Solid**, **Dashed**, **Dotted** 및 **None**입니다.
* [**BorderThickness**](properties-color-border.md) - **데이터 테이블** 컨트롤의 테두리 굵기입니다.
* [**Color**](properties-color-border.md) – 모든 데이터 행의 기본 텍스트 색입니다.
* [**Fill**](properties-color-border.md) – 모든 데이터 행의 기본 배경색입니다.
* [**Font**](properties-text.md) - 모든 데이터 행의 기본 글꼴입니다.
* [**FontWeight**](properties-text.md) - 모든 데이터 행의 기본 글꼴 두께입니다.
* **HeadingColor** - 열 머리글의 텍스트 색입니다.
* **HeadingFill** - 열 머리글의 배경색입니다.
* **HeadingFont** - 열 머리글의 글꼴입니다.
* **HeadingFontWeight** - 열 머리글의 글꼴 두께입니다.
* **HeadingSize** – 열 머리글의 글꼴 크기입니다.
* [**Height**](properties-size-location.md) – **데이터 테이블** 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.
* [**HoverColor**](properties-color-border.md) – 마우스 포인터가 가리키는 행의 텍스트 색입니다.
* [**HoverFill**](properties-color-border.md) – 마우스 포인터가 가리키는 행의 배경색입니다.
* **NoDataText** – **데이터 테이블** 컨트롤에 표시되는 레코드가 없을 때 사용자에게 표시하는 메시지입니다.
* **SelectedColor** – 선택된 행의 텍스트 색입니다.
* **SelectedFill** – 선택된 행의 배경색입니다.
* [**Size**](properties-text.md) – 모든 데이터 행의 기본 글꼴크기입니다.
* [**Visible**](properties-core.md) – **데이터 테이블** 컨트롤의 표시 또는 숨김 여부를 결정하는 값입니다.
* [**Width**](properties-size-location.md) – **데이터 테이블** 컨트롤의 왼쪽과 오른쪽 가장자리 사이의 간격입니다.
* [**X**](properties-size-location.md) – **데이터 테이블** 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면의 왼쪽 가장자리) 사이의 거리입니다.
* [**Y**](properties-size-location.md) – **데이터 테이블** 컨트롤의 맨 위 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면의 맨 위 가장자리) 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
* [**Filter(DataSource, Formula)** ](../functions/function-filter-lookup.md)(*DataSource*, *Formula*)
* [**Search(DataSource, SearchString, Column)** ](../functions/function-filter-lookup.md)(*DataSource*, *SearchString*, *Column*)

## <a name="examples"></a>예
### <a name="basic-usage"></a>기본 사용법
1. 빈 태블릿 앱을 만듭니다.
2. **삽입** 탭에서 클릭하거나 **데이터 테이블**을 탭합니다.
   
    ![데이터 테이블 컨트롤을 화면에 추가](./media/control-data-table/insert-data-table.png)
   
    **데이터 테이블** 컨트롤이 화면에 추가됩니다.
3. **데이터 테이블** 컨트롤의 이름을 **SalesOrderTable**로 변경하고 전체 화면에 맞게 크기를 변경합니다.
4. 오른쪽 창에서 **데이터 원본을 선택하지 않음** 텍스트의 오른쪽에서 아래 화살표를 클릭하거나 탭하고 **데이터 원본 추가**를 클릭하거나 탭합니다.
   
    ![데이터 원본 추가](./media/control-data-table/add-data-to-data-table.png)
5. 연결 목록에서 Common Data Service 데이터베이스에 대한 연결을 클릭하거나 탭합니다.
   
    ![데이터 원본에 대한 연결 선택](./media/control-data-table/choose-cds-data-table.png)
6. 엔터티 목록에서 **Sales order**를 클릭하거나 탭하고 **연결**을 클릭하거나 탭합니다.
   
    ![Sales order 엔터티 선택](./media/control-data-table/choose-so-data-table.png)
   
    **데이터 테이블** 컨트롤이 이제 **Sales order** 데이터 원본에 연결되었습니다. 이 기능을 지원하는 커넥터를 사용하고 있기 때문에 **데이터 테이블** 컨트롤에 몇 가지 초기 필드가 표시됩니다.
   
    ![데이터 테이블](./media/control-data-table/pre-order-data-table.png)
7. 오른쪽 창에 개별 필드를 표시하거나 숨기기 위해 하나 이상의 확인란을 선택합니다.
   
    예를 들어 **CustomerPurchaseOrderReference** 옆의 확인란을 선택하면 이 필드를 숨깁니다.
8. 오른쪽 창에서 위 또는 아래로 필드를 끌어 순서를 다시 정렬합니다.
   
    ![원하는 대로 필드 순서 다시 정렬](./media/control-data-table/field-re-order-data-table.png)
   
    **SalesOrderTable** 컨트롤이 사용자가 지정한 순서대로 필드를 표시합니다.
   
    ![업데이트된 데이터 테이블](./media/control-data-table/post-order-data-table.png)

### <a name="restyle-the-header-for-the-data-table-control"></a>데이터 테이블 컨트롤의 제목 스타일 변경
1. **데이터 테이블** 컨트롤을 선택한 상태로 오른쪽 창에서 **고급** 탭을 클릭하거나 탭합니다.
2. **HeadingFill** 속성에 대한 필드를 클릭하거나 탭한 다음 이 값을 **RGBA(62,96,170,1)** 로 변경합니다.
3. **HeadingColor** 속성에 대한 필드를 클릭하거나 탭한 다음 이 값을 **White**로 변경합니다.
4. **HeadingSize** 속성에 대한 필드를 클릭하거나 탭한 다음 이 값을 **14**로 변경합니다.
   
    ![데이터 테이블](./media/control-data-table/restyled-data-table.png)

### <a name="connect-a-data-table-control-to-another-control"></a>데이터 테이블 컨트롤을 다른 컨트롤에 연결
1. **편집 양식** 컨트롤을 화면에 추가합니다.
2. **데이터 테이블** 및 **편집 양식** 컨트롤의 크기를 조절하여 **데이터 테이블** 컨트롤이 화면의 왼쪽에 표시되고 **편집 양식** 컨트롤이 화면의 오른쪽에 표시되게 합니다.
   
    ![동일한 화면의 데이터 테이블과 편집 양식](./media/control-data-table/data-table-empty-form.png)
3. 반면 **Form1**을 선택하면 오른쪽 창에서 열의 숫자가 **1**로 바뀝니다.
4. **Form1**을 **Sales order** 데이터 원본에 연결합니다.
   
    몇 가지 초기 필드가 **Form1**에 표시됩니다.
   
    ![초기 필드가 있는 Form1](./media/control-data-table/data-table-disconnected-form.png)
5. 오른쪽 창에서 **고급** 탭을 클릭하거나 탭합니다.
6. **Form1**의 **Item** 속성을 **SalesOrderTable.Selected**로 설정합니다.
   
    **Form1**이 **데이터 테이블** 컨트롤에서 선택된 행의 정보를 표시합니다.
   
    ![데이터 테이블에 연결된 편집 양식](./media/control-data-table/connected-form-data-table.png)


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* [**Color**](properties-color-border.md) 및 [**Fill**](properties-color-border.md)
* **HeadingColor** 및 **HeadingFill**
* **SelectedColor** 및 **SelectedFill**
* [**HoverColor**](properties-color-border.md) 및 [**HoverFill**](properties-color-border.md)

이는 [표준 색 대비 요구 사항](../accessible-apps-color.md)에 추가됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **NoDataText**가 있어야 합니다.
