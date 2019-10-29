---
title: Canvas 앱에서 요약 양식 만들기 | Microsoft Docs
description: Canvas 앱에서 Northwind Traders의 데이터를 관리 하는 요약 양식 만들기
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d151249caebdb2a6f142943074a409bc626ff662
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "71995867"
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>Canvas 앱에서 요약 양식 만들기

단계별 지침에 따라 Northwind Traders 데이터베이스의 가상 데이터를 관리 하기 위한 캔버스 앱에서 요약 양식을 만듭니다. 이 항목은 Common Data Service에서 관계형 데이터에 비즈니스 앱을 빌드하는 방법을 설명 하는 시리즈의 일부입니다. 최상의 결과를 위해 다음 항목을이 순서 대로 탐색 합니다.

1. [주문 갤러리를 만듭니다](northwind-orders-canvas-part1.md).
2. 요약 양식 만들기 (**이 항목**)
3. [세부 정보 갤러리를 만듭니다](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> 화면 영역의 ![정의](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>필수 조건

1. [Northwind Traders 데이터베이스 및 앱을 설치](northwind-install.md)합니다.
1. Northwind Traders 용 [캔버스 앱의 개요](northwind-orders-canvas-overview.md) 를 검토 합니다.
1. [주문 갤러리](northwind-orders-canvas-part1.md) 를 직접 만들거나, 해당 갤러리가 이미 포함 된 **Northwind 주문 (Canvas)-시작 2 부** 앱을 엽니다.

## <a name="add-a-title-bar"></a>제목 표시줄 추가

앱의 맨 위에서이 항목의 끝에 있는 작업 단추를 포함 하는 제목 표시줄을 만듭니다.

1. **트리 뷰** 창에서 **Screen1** 를 선택 하 여 주문 갤러리에 컨트롤을 실수로 추가 하지 않도록 합니다.

    > [!div class="mx-imgBorder"]
    > 트리 뷰 창에서 Screen1을 선택 ![](media/northwind-orders-canvas-part2/titlebar-01.png)

1. **삽입** 탭 **에서 레이블을 선택 하** 여 [**레이블**](controls/control-text-box.md) 컨트롤을 삽입 합니다.

    > [!div class="mx-imgBorder"]
    > 레이블](media/northwind-orders-canvas-part2/titlebar-02.png) 삽입 ![

    새 레이블은 갤러리 위에 한 번만 표시 됩니다. 갤러리의 각 항목에 표시 되는 경우 레이블의 첫 번째 인스턴스를 삭제 하 고 이전 단계에서 설명한 대로 화면이 선택 되었는지 확인 한 다음 레이블을 다시 삽입 합니다.

1. 화면 위쪽으로 이동 하 여 새 레이블을 이동 하 고 크기를 조정 합니다.

    > [!div class="mx-imgBorder"]
    > 레이블 ![이동 하 고 크기를 조정](media/northwind-orders-canvas-part2/titlebar-03.png)

1. 레이블 텍스트를 두 번 클릭 한 다음 **Northwind Orders**를 입력 합니다.

    또는 수식 입력줄에서 **Text** 속성을 수정 하 여 동일한 결과를 얻을 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 제목 표시줄의 텍스트를 변경 ![](media/northwind-orders-canvas-part2/titlebar-04.png)

1. **홈** 탭에서 레이블 형식을 지정 합니다.
    - 글꼴 크기를 24 포인트로 늘립니다.
    - 텍스트를 굵게 표시 합니다.
    - 텍스트를 흰색으로 만듭니다.
    - 텍스트를 가운데에 맞춥니다.
    - 배경에 짙은 파란색 채우기를 추가 합니다.

    > [!div class="mx-imgBorder"]
    > 홈 탭의 서식 옵션을 ![](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>편집 양식 컨트롤 추가

이 섹션에서는 사용자가 갤러리에서 선택 하는 모든 주문의 요약을 표시 하는 컨트롤을 추가 합니다.

1. **삽입** 탭에서 [**편집 양식**](controls/control-form-detail.md) 컨트롤을 삽입 합니다.

    > [!div class="mx-imgBorder"]
    > 편집 양식 컨트롤을 추가 ![](media/northwind-orders-canvas-part2/form-01.png)

    기본적으로 폼은 왼쪽 위 모퉁이에 표시 됩니다 .이 경우 다른 컨트롤을 사용 하면 찾기가 어려울 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 기본 위치의 편집 양식 컨트롤을 ![](media/northwind-orders-canvas-part2/form-02.png)

1. 폼을 이동 하 고 크기를 조정 하 여 제목 표시줄 아래의 화면 오른쪽 위 모서리를 표시 합니다.

    > [!div class="mx-imgBorder"]
    > 편집 양식 컨트롤을 이동 하 고 크기를 조정 ![](media/northwind-orders-canvas-part2/form-03.png)

1. 수식 입력줄에서 양식의 **DataSource** 속성을이 값으로 설정 합니다.

    ```powerapps-dot
    Orders
    ```

    > [!div class="mx-imgBorder"]
    > 편집 양식 컨트롤의 DataSource 속성을 설정 ![](media/northwind-orders-canvas-part2/form-04.png)

    오른쪽 가장자리 근처의 **속성** 탭에서 동일한 속성을 설정할 수 있지만,이 방법은 폼에 필요 하지 않은 필드를 추가 합니다. 수식 입력줄을 사용 하는 경우 양식이 비어 있는 상태로 유지 됩니다.

## <a name="add-and-arrange-fields"></a>필드 추가 및 정렬

1. 오른쪽 가장자리 근처의 **속성** 탭에서 **필드 편집** 을 선택 하 여 **필드** 창을 엽니다.

    > [!div class="mx-imgBorder"]
    > 필드 창을 열 ![](media/northwind-orders-canvas-part2/form-05.png)

1. **필드** 창에서 **필드 추가**를 선택 하 고 **Customer** 및 **Employee** 필드의 확인란을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 편집 양식 컨트롤에 Customer 및 Employee 필드를 추가 ![](media/northwind-orders-canvas-part2/form-06.png)

1. 이러한 필드가 나타날 때까지 아래로 스크롤한 다음 해당 확인란을 선택 합니다.

    - **설명**
    - **주문 날짜**
    - **주문 번호**
    - **주문 상태**
    - **유료 날짜**

    > [!div class="mx-imgBorder"]
    > 편집 양식 컨트롤에 5 개 이상의 필드를 추가 ![](media/northwind-orders-canvas-part2/form-07.png)

1. **필드** 창 맨 아래에서 **추가**를 선택 하 고 **필드** 창을 닫습니다.

    이 폼에는 7 개의 필드가 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 편집 양식 컨트롤 ![7 개의 필드를 표시](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > 필드에 빨간색 오류 아이콘이 표시 되 면 원본에서 데이터를 끌어올 때 문제가 발생 했을 수 있습니다. 오류를 해결 하려면 데이터를 새로 고칩니다.
    >
    > 1. **보기**에서 **데이터 원본**을 선택합니다.
    > 1. **데이터** 창에서 **데이터 원본**을 선택 합니다.
    > 1. **주문**옆에서 줄임표 (...)를 선택 하 고 **새로 고침**을 선택한 다음 **데이터** 창을 닫습니다.
    >
    > Customer 또는 employee name의 콤보 상자에 오류가 계속 표시 되는 경우 각 상자의 **기본 텍스트** 와 **searchfield** 를 선택한 다음 **데이터** 창을 열어 확인 합니다. 고객 상자의 경우 두 필드 모두 **nwind_company**로 설정 해야 합니다. Employee 상자의 경우 두 필드 모두 **nwind_lastname**로 설정 해야 합니다.

1. 폼을 선택한 상태로 오른쪽 가장자리 근처의 **속성** 탭에서 폼의 열 수를 3에서 12로 변경 합니다.

    이 단계에서는 필드를 정렬할 때 유연성을 추가 합니다.

    > [!div class="mx-imgBorder"]
    > 편집 양식 컨트롤의 열 수를 변경 ![](media/northwind-orders-canvas-part2/form-08b.png)

    대부분의 UI 디자인은 1, 2, 3, 4, 6, 12 컨트롤의 행을 균등 하 게 수용할 수 있으므로 12 열 레이아웃을 사용 합니다. 이 항목에서는 1, 2 또는 4 개의 컨트롤이 포함 된 행을 만듭니다.

1. 다른 컨트롤과 마찬가지로 핸들을 끌어 필드를 이동 하 고 크기를 조정 하 여 각 행에 지정 된 순서로 이러한 데이터 카드를 포함 하도록 합니다.

    - 첫 번째 행: **주문 번호**, **주문 상태**, **주문 날짜**및 **유료 날짜**
    - 두 번째 행: **Customer** 및 **Employee**
    - 세 번째 행: **메모**

    > [!NOTE]
    > **노트**, **고객**및 **직원** 데이터 카드를 정렬 하기 전에 확장 하는 것이 더 쉬울 수 있습니다.

    > [!div class="mx-imgBorder"]
    > ![필드를 이동 하 고 크기를 조정](media/northwind-orders-canvas-part2/form-rearrange.gif)

    양식에서 필드를 정렬 하는 방법에 대 한 자세한 내용: [canvas 앱에 대 한 데이터 양식 레이아웃 이해](working-with-form-layout.md)

## <a name="hide-time-controls"></a>시간 컨트롤 숨기기

이 예에서는 세분성 수준이 사용자를 방해 수 있기 때문에 날짜 필드의 시간 부분이 필요 하지 않습니다. 이러한 항목을 삭제 하는 경우 해당 컨트롤을 사용 하 여 날짜 값을 업데이트 하거나 데이터 카드에서 다른 컨트롤의 위치를 결정 하는 수식에서 문제가 발생할 수 있습니다. 대신 **Visible** 속성을 설정 하 여 시간 컨트롤을 숨깁니다.

1. **트리 뷰** 창에서 **주문 날짜** 데이터 카드를 선택 합니다.

    카드 이름이 다를 수 있지만 **주문 날짜**를 포함 합니다.

1. Shift 키를 누른 채 **수주일 데이터 카드의 시간** , 분 및 콜론 구분 기호 컨트롤을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 주문 날짜 카드에서 시간 컨트롤을 선택 ![](media/northwind-orders-canvas-part2/form-09.png)

1. 컨트롤의 **Visible** 속성을 **false**로 설정 합니다.

    선택한 모든 컨트롤이 다음 형식으로 사라집니다.

    > [!div class="mx-imgBorder"]
    > Visible 속성을 false로 설정 ![합니다.](media/northwind-orders-canvas-part2/form-10.png)

1. [**날짜 선택**](controls/control-date-picker.md) 컨트롤의 크기를 조정 하 여 전체 날짜를 표시 합니다.

    > [!div class="mx-imgBorder"]
    > 날짜 선택 컨트롤의 크기를 조정 ![](media/northwind-orders-canvas-part2/form-11.png)

    다음으로, **유료 날짜** 필드에 대 한 마지막 몇 단계를 반복 합니다.

1. **트리 뷰** 창의 **유료 날짜** 데이터 카드에서 시간 컨트롤을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 유료 날짜 카드에서 시간 컨트롤을 선택 ![](media/northwind-orders-canvas-part2/form-12.png)

1. 선택한 컨트롤의 **Visible** 속성을 **false**로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > Visible 속성을 false로 설정 ![합니다.](media/northwind-orders-canvas-part2/form-13.png)

1. **유료** 카드의 날짜 선택 크기 조정:

    > [!div class="mx-imgBorder"]
    > 날짜 선택 컨트롤의 크기를 조정 ![](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>주문 갤러리 연결

1. **트리 뷰** 창에서 양식을 축소 하 여 주문 갤러리의 이름을 더 쉽게 찾은 다음 필요한 경우 **gallery1.selected**로 이름을 바꿉니다.

1. 요약 양식의 **Item** 속성을 다음 식으로 설정 합니다.

    ```powerapps-dot
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > 양식의 항목 속성 ![설정](media/northwind-orders-canvas-part2/form-15.png)

    양식은 앱 사용자가 목록에서 선택 하는 순서에 대 한 요약을 표시 합니다.

    > [!div class="mx-imgBorder"]
    > 목록에서 순서를 선택 하 여 양식에 개요를 표시 ![](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>데이터 카드 바꾸기

**Order number** 는 레코드를 만들 때 Common Data Service 자동으로 할당 하는 식별자입니다. 이 필드에는 기본적으로 [**텍스트 입력**](controls/control-text-input.md) 컨트롤이 있지만 사용자가이 필드를 편집할 수 없도록 레이블으로 바꿉니다.

1. 양식을 선택 하 고, 오른쪽 가장자리 근처의 **속성** 탭에서 **필드 편집** 을 선택한 다음, **주문 번호** 필드를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![주문 번호 필드를 선택](media/northwind-orders-canvas-part2/alt-01.png)

1. **컨트롤 형식** 목록을 엽니다.

    > [!div class="mx-imgBorder"]
    > \* * 컨트롤 형식 * * 목록을 ![엽니다](media/northwind-orders-canvas-part2/alt-02.png)

1. 텍스트 데이터 **보기** 카드를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![* * 텍스트 보기 * * 데이터 카드를 선택](media/northwind-orders-canvas-part2/alt-02b.png)

1. **필드** 창을 닫습니다.

    사용자는 더 이상 주문 번호를 변경할 수 없습니다.

    > [!div class="mx-imgBorder"]
    > ![주문 번호는 읽기 전용](media/northwind-orders-canvas-part2/alt-03.png)

1. **홈** 탭에서 주문 번호의 글꼴 크기를 20 포인트로 변경 하 여 필드를 더 쉽게 찾을 수 있도록 합니다.

    > [!div class="mx-imgBorder"]
    > 주문 번호의 글꼴 크기를 변경 ![](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>다 대 일 관계 사용

**Orders** 엔터티는 **Employees** 엔터티와 다 대 일 관계를 갖습니다. 각 직원은 여러 주문을 만들 수 있지만 각 주문은 하나의 직원 에게만 할당 될 수 있습니다. 사용자가 [**콤보 상자**](controls/control-combo-box.md) 컨트롤에서 직원을 선택 하면 **선택** 된 속성은 **Employees** 엔터티의 직원 전체 레코드를 제공 합니다. 결과적으로, 사용자가 콤보 상자에서 선택 하는 모든 직원의 그림을 표시 하도록 [**이미지**](controls/control-image.md) 컨트롤을 구성할 수 있습니다.

1. **직원** 데이터 카드를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 직원 데이터 카드를 선택 ![](media/northwind-orders-canvas-part2/employee-01.png)

1. 오른쪽 가장자리 근처에 있는 **고급** 탭에서 이전에 읽기 전용으로 작성 된 수식을 편집할 수 있도록 데이터 카드의 잠금을 해제 합니다.

    > [!div class="mx-imgBorder"]
    > 직원 데이터 카드를 ![잠금 해제](media/northwind-orders-canvas-part2/employee-02.png)

1. 데이터 카드에서 콤보 상자의 너비를 줄여서 직원 그림의 공간을 만듭니다.

    > [!div class="mx-imgBorder"]
    > 콤보 상자 컨트롤의 크기를 조정 ![](media/northwind-orders-canvas-part2/employee-03b.png)

1. **삽입** 탭에서 **미디어**  > **이미지**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 이미지](media/northwind-orders-canvas-part2/employee-04.png) 삽입 ![

    이미지는 데이터 카드에 표시 되며,이를 수용 하기 위해 확장 됩니다.

    > [!div class="mx-imgBorder"]
    > 이미지 컨트롤을 사용 하 여 직원 데이터 카드 ![](media/northwind-orders-canvas-part2/employee-05.png)

1. 이미지 크기를 조정 하 고 콤보 상자의 오른쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 이미지 컨트롤을 이동 하 고 크기를 조정 ![](media/northwind-orders-canvas-part2/employee-06.png)

1. 필요한 경우 이미지의 **이미지** 속성을이 수식으로 설정 하 여 DataCardValue 끝에 있는 숫자를 바꿉니다.

    ```powerapps-dot
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > 이미지의 이미지 속성을 설정 ![](media/northwind-orders-canvas-part2/employee-07.png)

    선택한 직원의 그림이 표시 됩니다.

1. Alt 키를 누른 채 콤보 상자에서 다른 직원을 선택 하 여 그림이 변경 되는지 확인 합니다.

    > [!div class="mx-imgBorder"]
    > 직원을 선택 하 ![직원의 그림](media/northwind-orders-canvas-part2/employee-select.gif) 표시

## <a name="add-a-save-icon"></a>저장 아이콘 추가

1. **트리 뷰** 창에서 **Screen1**를 선택 하 고  > **아이콘** **삽입** ** >  선택**합니다.

    > [!div class="mx-imgBorder"]
    > ![삽입 확인 표시 아이콘](media/northwind-orders-canvas-part2/save-01.png)

    [**확인**](controls/control-shapes-icons.md) 아이콘은 기본적으로 왼쪽 위 모퉁이에 표시 되며, 다른 컨트롤에서 아이콘을 찾기 어려울 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 기본 위치의 아이콘을 ![](media/northwind-orders-canvas-part2/save-02.png)

1. **홈** 탭에서 아이콘의 **Color** 속성을 흰색으로 변경 하 고, 아이콘의 크기를 조정 하 고, 제목 표시줄의 오른쪽 가장자리 근처로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 저장 아이콘의 색, 크기 및 위치를 구성 ![](media/northwind-orders-canvas-part2/save-03.png)

1. **트리 뷰** 창에서 양식의 이름이 **Form1**인지 확인 하 고 아이콘의 **onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > 저장 아이콘의 OnSelect 속성을 설정 ![](media/northwind-orders-canvas-part2/save-04.png)

    사용자가이 아이콘을 선택 하면 [**submitform**](functions/function-form.md) 함수는 폼에서 변경 된 모든 값을 수집 하 여 데이터 원본으로 전송 합니다. 데이터가 전송 될 때 화면 위쪽에서 3 월을 나타내며, 주문 갤러리에는 프로세스가 완료 된 후의 변경 내용이 반영 됩니다.

1. 아이콘의 **DisplayMode** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( Form1.Unsaved, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > 아이콘의 DisplayMode 속성을 설정 ![](media/northwind-orders-canvas-part2/save-05.png)

    양식의 모든 변경 내용이 저장 되 면 아이콘이 비활성화 되 고 **DisabledColor**에 표시 되며,이는 다음에 설정 합니다.

1. 아이콘의 **DisabledColor** 속성을 다음 값으로 설정 합니다.

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > 아이콘의 DisabledColor 속성을 설정 ![](media/northwind-orders-canvas-part2/save-06.png)

    사용자는 확인 아이콘을 선택 하 여 변경 내용을 순서 대로 저장할 수 있습니다. 그러면 사용자가 다른 변경 작업을 수행 하기 전에는 비활성화 되 고 흐리게 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 변경 내용 저장 ![](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>취소 아이콘 추가

1. **삽입** 탭에서 **아이콘**  > **취소**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 취소 아이콘 추가 ![](media/northwind-orders-canvas-part2/save-07.png)

    아이콘은 기본적으로 왼쪽 위 모퉁이에 표시 되며, 다른 컨트롤에서 아이콘을 찾기 어려울 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 기본 위치의 취소 아이콘을 ![](media/northwind-orders-canvas-part2/save-08.png)

1. **홈** 탭에서 아이콘의 **Color** 속성을 흰색으로 변경 하 고, 아이콘의 크기를 조정 하 고, 확인 아이콘의 왼쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![취소 아이콘의 색, 크기 및 위치를 변경](media/northwind-orders-canvas-part2/save-09.png)

1. 취소 아이콘의 **Onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > 취소 아이콘의 OnSelect 속성을 설정 ![](media/northwind-orders-canvas-part2/save-10.png)

    [**Resetform**](functions/function-form.md) 함수는 폼의 모든 변경 내용을 삭제 하 고 원래 상태로 되돌립니다.

1. 취소 아이콘의 **DisplayMode** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![취소 아이콘의 DisplayMode 속성을 설정](media/northwind-orders-canvas-part2/save-11.png)

    이 수식은 확인 아이콘의 수식과 약간 다릅니다. 모든 변경 내용이 저장 되었거나 양식이 **새** 모드에 있으면 취소 아이콘을 사용할 수 없습니다 .이 경우 다음을 사용 하도록 설정 합니다. 이 경우 **Resetform** 은 새 레코드를 삭제 합니다.

1. 취소 아이콘의 **DisabledColor** 속성을이 값으로 설정 합니다.

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![취소 아이콘의 DisabledColor 속성을 설정](media/northwind-orders-canvas-part2/save-12.png)

    사용자는 주문에 대 한 변경 내용을 취소할 수 있으며 모든 변경 내용이 저장 되 면 체크 및 취소 아이콘이 비활성화 되 고 흐리게 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 변경 내용을 저장 하 고 취소 하는 ![](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>추가 아이콘 추가

1. **삽입** 탭에서 **아이콘**  > **추가**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 추가 아이콘을 삽입 ![](media/northwind-orders-canvas-part2/save-13.png)

    **추가** 아이콘은 기본적으로 왼쪽 위 모퉁이에 표시 됩니다 .이 경우 다른 컨트롤을 사용 하면 찾기가 어려울 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 추가 아이콘의 기본 위치를 ![](media/northwind-orders-canvas-part2/save-14.png)

1. **홈** 탭에서 추가 아이콘의 **Color** 속성을 흰색으로 설정 하 고, 아이콘의 크기를 조정 하 고, 취소 아이콘의 왼쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![추가 아이콘의 색, 크기 및 위치를 변경](media/northwind-orders-canvas-part2/save-15.png)

1. 추가 아이콘의 **Onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > 추가 아이콘의 OnSelect 속성을 설정 ![](media/northwind-orders-canvas-part2/save-15b.png)

    [**NewForm**](functions/function-form.md) 함수는 폼의 빈 레코드를 표시 합니다.  

1. 추가 아이콘의 **DisplayMode** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![추가 아이콘의 DisplayMode 속성을 설정](media/northwind-orders-canvas-part2/save-16.png)

    수식은 다음 조건에서 추가 아이콘을 사용 하지 않도록 설정 합니다.

    - 사용자가 변경 내용을 적용 하지만 저장 하거나 취소 하지 않으며,이는 검사 및 취소 아이콘과 반대 동작입니다.
    - 사용자가 추가 아이콘을 선택 하 고 변경 하지는 않습니다.

1. 추가 아이콘의 **DisabledColor** 속성을이 값으로 설정 합니다.

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![추가 아이콘의 DisabledColor 속성을 설정](media/northwind-orders-canvas-part2/save-17.png)

    사용자가 변경 하지 않거나 변경한 내용을 저장 하거나 취소 하는 경우 주문을 만들 수 있습니다. 사용자가이 아이콘을 선택 하는 경우 하나 이상의 변경을 수행한 후 해당 변경 내용을 저장 하거나 취소할 때까지 다시 선택할 수 없습니다.

    > [!div class="mx-imgBorder"]
    > 주문](media/northwind-orders-canvas-part2/save-new.gif) ![만듭니다.

> [!NOTE]
> 주문을 만들고 저장 하는 경우 새 주문을 표시 하려면 주문 갤러리에서 아래로 스크롤해야 할 수도 있습니다. 주문 정보를 아직 추가 하지 않았기 때문에 총 가격이 없습니다.

## <a name="add-a-trash-icon"></a>휴지통 아이콘 추가

1. **삽입** 탭에서**휴지통** >  **아이콘** 을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 휴지통 아이콘을 삽입 ![](media/northwind-orders-canvas-part2/save-18.png)

    **휴지통** 아이콘은 기본적으로 왼쪽 위 모퉁이에 표시 됩니다. 그러면 다른 컨트롤에서 찾기 어려울 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 휴지통 아이콘의 기본 위치를 ![](media/northwind-orders-canvas-part2/save-19.png)

1. **홈** 탭에서 휴지통 아이콘의 **Color** 속성을 흰색으로 변경 하 고, 아이콘의 크기를 조정 하 고, 추가 아이콘의 왼쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 휴지통 아이콘의 색, 크기 및 위치를 변경 ![](media/northwind-orders-canvas-part2/save-20.png)

1. 휴지통 아이콘의 **Onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Remove( Orders, Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > 휴지통 아이콘의 OnSelect 속성을 설정 ![](media/northwind-orders-canvas-part2/save-21.png)

    [**Remove**](functions/function-remove-removeif.md) 함수는 데이터 원본에서 레코드를 제거 합니다. 이 수식에서 함수는 주문 갤러리에서 선택한 레코드를 제거 합니다. 레코드에 대 한 자세한 정보를 표시 하기 때문에 사용자가 수식이 삭제할 레코드를 보다 쉽게 식별할 수 있으므로 휴지통 아이콘이 요약 형식 (주문 갤러리가 아님) 근처에 나타납니다.

1. 휴지통 아이콘의 **DisplayMode** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > 휴지통 아이콘의 DisplayMode 속성을 설정 ![](media/northwind-orders-canvas-part2/save-22.png)

    사용자가 레코드를 만드는 경우이 수식에서 휴지통 아이콘을 사용 하지 않도록 설정 합니다. 사용자가 레코드를 저장할 때까지 **제거** 함수에 삭제할 레코드가 없습니다.

1. 휴지통 아이콘의 **DisabledColor** 속성을이 값으로 설정 합니다.

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > 휴지통 아이콘의 DisabledColor 속성을 설정 ![](media/northwind-orders-canvas-part2/save-23.png)

    사용자가 주문을 삭제할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 주문을 삭제 하는 ![](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>정리

사용자가 각 주문의 요약을 표시 하 고 편집할 수 있는 양식을 추가 하 고 다음 요소를 사용 했습니다.

- **Orders** 엔터티의 데이터를 표시 하는 폼: **Form1. DataSource =** `Orders`
- 폼과 주문 갤러리 간의 연결: **Form1. Item =** `Gallery1.Selected`
- **주문 번호** 필드에 대 한 대체 컨트롤: **텍스트 보기**
- **직원** 데이터 카드의 직원 그림을 표시 하는 다 대 일 관계: `DataCardValue1.Selected.Picture`
- 주문에 대 한 변경 내용을 저장 하는 아이콘: `SubmitForm( Form1 )`
- 주문에 대 한 변경 내용을 취소 하는 아이콘: `ResetForm( Form1 )`
- 주문을 만드는 아이콘: `NewForm( Form1 )`
- 주문을 삭제 하는 아이콘: `Remove( Orders, Gallery1.Selected )`

## <a name="next-step"></a>다음 단계

다음 항목에서는 각 주문의 제품을 표시 하는 다른 갤러리를 추가 하 고 [**Patch**](functions/function-patch.md) 함수를 사용 하 여 해당 세부 정보를 변경 합니다.

> [!div class="nextstepaction"]
> [세부 정보 갤러리 만들기](northwind-orders-canvas-part3.md)
