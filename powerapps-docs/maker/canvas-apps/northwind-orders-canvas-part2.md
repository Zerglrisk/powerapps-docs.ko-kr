---
title: 캔버스 앱에서 요약 양식을 만드는 | Microsoft Docs
description: Northwind Traders에 대 한 데이터를 관리 하는 캔버스 앱에서 요약 폼 만들기
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5c40cb030241d142a2ee2a68d32f7fb839a350ff
ms.sourcegitcommit: 55bc11ac6a964f22301c9fdadb06ee34e1399f83
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66805922"
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>캔버스 앱에서 요약 폼 만들기

Northwind 데이터베이스에서 가상의 데이터를 관리 하는 것에 대 한 캔버스 앱에서 요약 양식을 만드는 단계별 지침을 따릅니다. 이 항목은 Common Data Service의 관계형 데이터에서 비즈니스 앱을 빌드하는 방법을 설명 하는 시리즈의 일부입니다. 최상의 결과이 순서 대로 이러한 항목을 살펴봅니다.

1. [순서 갤러리 만들기](northwind-orders-canvas-part1.md)합니다.
2. 요약 form을 만듭니다 (**이 항목에서는**).
3. [세부 정보 갤러리 만들기](northwind-orders-canvas-part3.md)합니다.

> [!div class="mx-imgBorder"]
> ![화면 영역 정의](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>필수 조건

1. [Northwind Traders 데이터베이스 및 앱 설치](northwind-install.md)합니다.
1. 검토 합니다 [캔버스 앱 개요](northwind-orders-canvas-overview.md) Northwind Traders에 대 한 합니다.
1. [순서 갤러리 만들기](northwind-orders-canvas-part1.md) 를 직접 열거나 합니다 **Northwind 주문 (캔버스)-시작 가이드의 2 부** 이미 해당 갤러리를 포함 하는 앱입니다.

## <a name="add-a-title-bar"></a>제목 표시줄 추가

앱의 위쪽에이 항목의 끝에서 실행 단추를 보유할 제목 표시줄을 만듭니다.

1. 에 **트리 뷰에서** 창 **Screen1** 순서 갤러리에 컨트롤을 실수로 추가 하지 않도록 하려면:

    > [!div class="mx-imgBorder"]
    > ![Screen1 트리 뷰 창에서 선택](media/northwind-orders-canvas-part2/titlebar-01.png)

1. 에 **삽입** 탭을 선택 **레이블을** 삽입 하는 [ **레이블** ](controls/control-text-box.md) 컨트롤:

    > [!div class="mx-imgBorder"]
    > ![레이블 삽입](media/northwind-orders-canvas-part2/titlebar-02.png)

    새 레이블을 갤러리 위쪽 한 번만 나타나야 합니다. 갤러리의 각 항목에 표시 되 면 해당 레이블의 첫 번째 인스턴스를 삭제을 화면으로 선택 된 (이전 단계에 설명)에 레이블을 다시 삽입 합니다.

1. 이동 하 고 화면 위쪽에 걸쳐 새 레이블의 크기를 조정 합니다.

    > [!div class="mx-imgBorder"]
    > ![이동 하 고 레이블의 크기를 조정합니다](media/northwind-orders-canvas-part2/titlebar-03.png)

1. 레이블 텍스트를 두 번 클릭 한 다음 입력 **Northwind 주문**합니다.

    대신 수정 합니다 **텍스트** 동일한 결과 달성 하기 위해 수식 입력줄에서 속성:

    > [!div class="mx-imgBorder"]
    > ![제목 표시줄의 텍스트 변경](media/northwind-orders-canvas-part2/titlebar-04.png)

1. 에 **홈** 탭, 레이블 형식:
    - 24 포인트로 글꼴 크기를 늘립니다.
    - 텍스트를 굵게 표시 합니다.
    - 흰색 텍스트를 확인 합니다.
    - 텍스트를 가운데.
    - 진한 파란색 채우기 백그라운드에 추가 합니다.

    > [!div class="mx-imgBorder"]
    > ![홈 탭에서 서식 옵션](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>편집 양식 컨트롤을 추가 합니다.

이 섹션에서는 사용자가 갤러리에서 선택한 모든 주문의 요약을 표시 하도록 컨트롤을 추가 합니다.

1. 에 **삽입** 탭에서 삽입을 [ **편집 양식** ](controls/control-form-detail.md) 제어:

    > [!div class="mx-imgBorder"]
    > ![편집 양식 컨트롤을 추가 합니다.](media/northwind-orders-canvas-part2/form-01.png)

    기본적으로 폼 있는 다른 컨트롤과 어려울 수도 있습니다 찾으려면 왼쪽 위 모퉁이에 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![편집 양식 컨트롤의 기본 위치](media/northwind-orders-canvas-part2/form-02.png)

1. 이동 하 고 폼 제목 표시줄에서 화면 오른쪽 위 모서리에 맞게 크기를 조정 합니다.

    > [!div class="mx-imgBorder"]
    > ![이동 및 편집 양식 컨트롤 크기 조정](media/northwind-orders-canvas-part2/form-03.png)

1. 수식 입력줄에서 설정 된 **DataSource** 이 값으로 폼의 속성:

    ```powerapps-dot
    Orders
    ```

    > [!div class="mx-imgBorder"]
    > ![편집 양식 컨트롤의 DataSource 속성 설정](media/northwind-orders-canvas-part2/form-04.png)

    동일한 속성을 설정할 수 있습니다 합니다 **속성** 폼에 필요 하지 않은 필드를 추가 하는 방법은 해당 오른쪽 가장자리 근처 탭 합니다. 수식 입력줄을 사용 하는 경우 폼은 비어 있습니다.

## <a name="add-and-arrange-fields"></a>추가 하 고 필드 정렬

1. 에 **속성** 탭 선택의 오른쪽 가장자리 근처 **필드를 편집할** 열려는 **필드** 창:

    > [!div class="mx-imgBorder"]
    > ![필드 창 열기](media/northwind-orders-canvas-part2/form-05.png)

1. 에 **필드** 창 **추가 필드**, 다음에 대 한 확인란을 선택 하 고는 **고객** 및 **직원** 필드입니다.

    > [!div class="mx-imgBorder"]
    > ![편집 양식 컨트롤을 고객 및 직원 필드를 추가 합니다.](media/northwind-orders-canvas-part2/form-06.png)

1. 이러한 필드 표시를 선택한 다음 해당 확인란 때까지 아래로 스크롤하십시오.

    - **설명**
    - **주문 날짜**
    - **주문 번호**
    - **주문 상태**
    - **유료 날짜**

    > [!div class="mx-imgBorder"]
    > ![편집 양식 컨트롤에 다섯 개의 필드를 추가 합니다.](media/northwind-orders-canvas-part2/form-07.png)

1. 맨 아래에 **필드** 창 **추가**를 닫은 다음 합니다 **필드** 창.

    폼에서는 7 개 필드를 보여 줍니다.

    > [!div class="mx-imgBorder"]
    > ![편집 양식 컨트롤 7 필드를 보여 줍니다.](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > 빨간색 오류 아이콘을 표시 하는 모든 필드를 데이터 원본에서 가져와 하는 경우 문제가 발생할 수 있습니다. 오류를 해결 하려면 데이터 새로 고침:
    >
    > 1. **보기**에서 **데이터 원본**을 선택합니다.
    > 1. 에 **데이터** 창 **데이터 원본**합니다.
    > 1. 옆에 **주문을**에서 줄임표 (...)을 선택 **새로 고침**를 닫은 다음 합니다 **데이터** 창.
    >
    > 고객이 나 직원 이름에 대 한 콤보 상자에 오류가 계속 표시 하는 경우 확인 합니다 **기본 텍스트** 및 **SearchField** 선택 하 고 다음을 열어 각 상자의 합니다 **데이터** 창입니다. 기본적으로 고객에 대 한 두 필드에 설정할 **nwind_company**합니다. 직원 상자 두 필드에 설정할 **nwind_lastname**합니다.

1. 양식을 선택 하 고 사용 하 여 양식의 열 수가 3에서 12를로 변경 합니다 **속성** 오른쪽 가장자리 근처에서 탭 합니다.

    이 단계에서는 필드를 정렬 하는 대로 유연성을 추가 합니다.

    > [!div class="mx-imgBorder"]
    > ![편집 양식 컨트롤의 열 수가 변경 후](media/northwind-orders-canvas-part2/form-08b.png)

    대부분의 UI 디자인 1, 2, 3, 4, 6 및 12 컨트롤의 행을 균등 하 게 수용할 수 있습니다 했으므로 12 열 레이아웃에 필요 합니다. 이 항목에서는 1, 2 또는 4 컨트롤을 포함 하는 행을 만들어야 합니다.

1. 이동 하 고 각 행에 지정된 된 순서 대로 이러한 데이터 카드 포함 되도록 다른 컨트롤에는 것 처럼 해당 핸들을 끌어 필드를 크기 조정:

    - 첫 번째 행. **Order Number**, **주문 상태**를 **주문 날짜**, 및 **지불 날짜**
    - 두 번째 행. **고객** 고 **직원**
    - 세 번째 행. **설명**

    > [!NOTE]
    > Widen 쉽게 찾을 수 있습니다 합니다 **노트**, **고객**, 및 **직원** 정렬할 수 전에 데이터 카드.

    > [!div class="mx-imgBorder"]
    > ![이동 및 필드를 크기 조정](media/northwind-orders-canvas-part2/form-rearrange.gif)

    양식의 필드를 정렬 하는 방법에 대 한 자세한 정보: [캔버스 앱에 대 한 데이터 양식 레이아웃 이해](working-with-form-layout.md)합니다.

## <a name="hide-time-controls"></a>시간 컨트롤 숨기기

이 예제에서는 해당 수준의 세분성 사용자 방해가 수 때문에 날짜 필드의 시간 부분을 필요 하지 않습니다. 삭제 된 경우에 날짜 값을 업데이트 하거나 데이터 카드에서 다른 컨트롤의 위치를 확인 하려면 이러한 컨트롤을 사용 하는 수식에서 문제가 발생할 수 있습니다. 설정 하 여 시간 컨트롤을 숨길 수 대신 자신의 **Visible** 속성입니다.

1. 에 **트리 뷰** 창 합니다 **Order Date** 데이터 카드.

    카드에는 다른 이름을 가질 수 있지만 있기 **Order Date**합니다.

1. Shift 키를 누른 채에서 시간, 분 및 콜론 구분 기호 컨트롤을 선택 합니다 **Order Date** 데이터 카드.

    > [!div class="mx-imgBorder"]
    > ![Order Date 카드에서 시간 컨트롤을 선택 합니다.](media/northwind-orders-canvas-part2/form-09.png)

1. 컨트롤의 설정 **Visible** 속성을 **false**합니다.

    선택 된 모든 컨트롤 폼에서 사라집니다.

    > [!div class="mx-imgBorder"]
    > ![Visible 속성을 false로 설정 합니다.](media/northwind-orders-canvas-part2/form-10.png)

1. 크기를 조정 합니다 [ **날짜 선택** ](controls/control-date-picker.md) 완료 날짜를 표시 하도록 컨트롤:

    > [!div class="mx-imgBorder"]
    > ![날짜 선택 컨트롤 크기 조정](media/northwind-orders-canvas-part2/form-11.png)

    에 대 한 마지막 몇 가지 단계를 반복에서는 다음에 **유료 날짜** 필드입니다.

1. 에 **트리 뷰** 창에 컨트롤을 **유료 날짜** 데이터 카드:

    > [!div class="mx-imgBorder"]
    > ![지불 날짜 카드에서 시간 컨트롤을 선택 합니다.](media/northwind-orders-canvas-part2/form-12.png)

1. 선택한 컨트롤을 설정 **Visible** 속성을 **false**:

    > [!div class="mx-imgBorder"]
    > ![Visible 속성을 false로 설정 합니다.](media/northwind-orders-canvas-part2/form-13.png)

1. 날짜 선택에서 크기를 조정 합니다 **날짜 유료** 카드:

    > [!div class="mx-imgBorder"]
    > ![날짜 선택 컨트롤 크기 조정](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>순서 대로 갤러리를 연결 합니다.

1. 에 **트리 뷰에서** 창 순서 갤러리의 이름을 쉽게 찾으려면 폼을 축소 하 고 그런 다음 필요한 경우 이름을 **Gallery1**합니다.

1. 설정 요약 양식의 **항목** 속성을이 식:

    ```powerapps-dot
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > ![항목 속성 설정](media/northwind-orders-canvas-part2/form-15.png)

    형식 목록에서 앱 사용자가 모든 주문의 요약을 보여 줍니다.

    > [!div class="mx-imgBorder"]
    > ![주문을 형태로 해당 개요를 표시 하려면 목록에서 선택](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>데이터 카드 바꾸기

**주문 번호** Common Data Service는 레코드를 만들 때 자동으로 할당 하는 식별자입니다. 이 필드에는 [ **텍스트 입력** ](controls/control-text-input.md) 기본적으로 컨트롤 사용자는이 필드를 편집할 수 없도록 레이블로 대체 됩니다.

1. 폼을 선택 **필드를 편집할** 에 **속성** 탭 오른쪽 가장자리 근처에서 선택한 후는 **Order number** 필드:

    > [!div class="mx-imgBorder"]
    > ![순서 번호 필드를 선택 합니다.](media/northwind-orders-canvas-part2/alt-01.png)

1. 엽니다는 **컨트롤 형식과** 목록:

    > [!div class="mx-imgBorder"]
    > ![열기는 * * 제어 유형 * * 목록](media/northwind-orders-canvas-part2/alt-02.png)

1. 선택 된 **텍스트를 보려면** 데이터 카드:

    > [!div class="mx-imgBorder"]
    > ![선택 된 * * 보기 텍스트 * * 데이터 카드](media/northwind-orders-canvas-part2/alt-02b.png)

1. 닫기 합니다 **필드** 창입니다.

    사용자는 주문 번호를 더 이상 변경할 수 없습니다.

    > [!div class="mx-imgBorder"]
    > ![주문 번호는 읽기 전용](media/northwind-orders-canvas-part2/alt-03.png)

1. 에 **홈** 탭, 필드는 쉽게 찾을 수 있도록 20 지점에 주문 번호의 글꼴 크기를 변경 합니다.

    > [!div class="mx-imgBorder"]
    > ![주문 번호의 글꼴 크기를 변경 합니다.](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>다 대 일 관계를 사용 하 여

합니다 **주문을** 엔터티 간의 관계가 다 대 합니다 **직원** 엔터티: 각 직원에는 여러 개의 주문을 만들 수 있지만 각 주문 하나만 직원에 게 할당할 수 있습니다. 사용자가 직원을 선택 하는 경우는 [ **콤보 상자** ](controls/control-combo-box.md) 컨트롤을 해당 **선택한** 속성에서 해당 직원의 전체 레코드를 제공 합니다 **직원**  엔터티. 결과적으로 구성할 수 있습니다는 [ **이미지** ](controls/control-image.md) 콤보 상자에서 모든 직원의 그림은 사용자에 게 표시할 컨트롤을 선택 합니다.

1. 선택 된 **직원** 데이터 카드:

    > [!div class="mx-imgBorder"]
    > ![직원 데이터 카드 선택](media/northwind-orders-canvas-part2/employee-01.png)

1. 에 **고급** 오른쪽 가장자리 근처에서 탭에서 이전에 읽기 전용 된 수식을 편집할 수 있도록 데이터 카드를 잠금 해제 합니다.

    > [!div class="mx-imgBorder"]
    > ![직원 데이터 카드를 잠금 해제](media/northwind-orders-canvas-part2/employee-02.png)

1. 데이터 카드를 확보 하기 위해 직원 그림 콤보 상자의 너비를 줄입니다.

    > [!div class="mx-imgBorder"]
    > ![콤보 상자 컨트롤 크기 조정](media/northwind-orders-canvas-part2/employee-03b.png)

1. 에 **삽입** 탭을 선택 **Media** > **이미지**:

    > [!div class="mx-imgBorder"]
    > ![이미지 삽입](media/northwind-orders-canvas-part2/employee-04.png)

    이미지에 맞게 확장 되는 데이터 카드에 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![이미지 컨트롤을 사용 하 여 직원 데이터 카드](media/northwind-orders-canvas-part2/employee-05.png)

1. 이미지 크기 조정 및 콤보 상자의 오른쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![이동 및 이미지 컨트롤 크기 조정](media/northwind-orders-canvas-part2/employee-06.png)

1. 설정 된 **이미지** 필요한 경우 DataCardValue의 끝에 있는 숫자를 대체 하 고이 수식에서 이미지의 속성:

    ```powerapps-dot
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![이미지의 이미지 속성 설정](media/northwind-orders-canvas-part2/employee-07.png)

    선택한 직원의 그림에 표시 됩니다.

1. Alt 키를 보유 하는지 확인 하려면 콤보 상자에서 다른 직원을 선택 하는 동안 그림도 변경 됩니다.

    > [!div class="mx-imgBorder"]
    > ![해당 직원의 그림 표시로 직원을 선택 합니다.](media/northwind-orders-canvas-part2/employee-select.gif)

## <a name="add-a-save-icon"></a>저장 아이콘 추가

1. 에 **트리 뷰에서** 창 **Screen1**를 선택한 후 **삽입** > **아이콘**  >  **확인할**:

    > [!div class="mx-imgBorder"]
    > ![확인 표시 아이콘을 삽입 합니다.](media/northwind-orders-canvas-part2/save-01.png)

    합니다 [ **확인할** ](controls/control-shapes-icons.md) 아이콘 왼쪽 위 모퉁이에서 기본적으로 표시를 다른 컨트롤 하기가 어려울 수도 있습니다 아이콘을 찾을:

    > [!div class="mx-imgBorder"]
    > ![기본 위치에 대 한 아이콘](media/northwind-orders-canvas-part2/save-02.png)

1. 에 **홈** 탭으로 변경 합니다 **색** 흰색, 아이콘, 크기 조정 및 제목 표시줄의 오른쪽 가장자리 근처 이동 하기 위한 아이콘의 속성:

    > [!div class="mx-imgBorder"]
    > ![색, 크기 및 저장 위치를 구성 아이콘](media/northwind-orders-canvas-part2/save-03.png)

1. 에 **트리 뷰에서** 창 양식의 이름 인지 확인 **Form1**, 아이콘을 설정한 후 **OnSelect** 속성을 다음이 수식:

    ```powerapps-dot
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![설정 저장 아이콘의 OnSelect 속성](media/northwind-orders-canvas-part2/save-04.png)

    사용자가 아이콘을 선택 합니다 [ **SubmitForm** ](functions/function-form.md) 함수 형태로 변경된 된 값을 수집 하 고 데이터 원본에 전송 합니다. 점 순서 갤러리 프로세스를 완료 한 후 변경 내용을 반영 하 고 데이터가 전송 되 면 화면 위쪽 년 3 월.

1. 아이콘의 설정 **DisplayMode** 속성을 다음이 수식:

    ```powerapps-dot
    If( Form1.Unsaved, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![아이콘의 DisplayMode 속성 설정](media/northwind-orders-canvas-part2/save-05.png)

    아이콘 비활성화 되 고 나타나는 폼의 모든 변경 내용을 저장 하는 경우는 **DisabledColor**, 다음 설정할 수 있습니다.

1. 아이콘의 설정 **DisabledColor** 이 값으로 속성:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![아이콘의 DisabledColor 속성 설정](media/northwind-orders-canvas-part2/save-06.png)

    사용자는 사용 하지 않도록 설정 되며 사용자가 다른 변경 될 때까지 흐리게 표시 확인 아이콘을 선택 하 여 주문에 변경 내용을 저장할 수 있습니다.:

    > [!div class="mx-imgBorder"]
    > ![변경 내용 저장](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>추가 취소 아이콘

1. 에 **삽입** 탭을 선택 **아이콘** > **취소**:

    > [!div class="mx-imgBorder"]
    > ![추가 취소 아이콘](media/northwind-orders-canvas-part2/save-07.png)

    아이콘 왼쪽 위 모퉁이에서 기본적으로 표시를 다른 컨트롤 하기가 어려울 수도 있습니다 아이콘을 찾을:

    > [!div class="mx-imgBorder"]
    > ![기본 위치에서 취소 아이콘](media/northwind-orders-canvas-part2/save-08.png)

1. 에 **홈** 탭에서 아이콘을 변경 **색** 속성을 흰색, 아이콘, 크기를 조정 하 고 확인 아이콘의 왼쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![색, 크기 및 취소 아이콘의 위치를 변경 합니다.](media/northwind-orders-canvas-part2/save-09.png)

1. 취소 아이콘 집합 **OnSelect** 속성을 다음이 수식:

    ```powerapps-dot
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![취소 아이콘의 OnSelect 속성 설정](media/northwind-orders-canvas-part2/save-10.png)

    합니다 [ **ResetForm** ](functions/function-form.md) 함수를 원래 상태로 반환 하는 폼 변경 내용을 모두 취소 합니다.

1. 취소 아이콘 집합 **DisplayMode** 속성을 다음이 수식:

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![취소 아이콘의 DisplayMode 속성 설정](media/northwind-orders-canvas-part2/save-11.png)

    이 수식은 확인 아이콘에 대 한 것과 약간 다릅니다. 모든 변경 내용이 저장 된 경우 양식이 취소 아이콘 사용 안 함 **새로 만들기** 다음을 사용 하 게 하는 모드입니다. 이 경우 **ResetForm** 새 레코드를 삭제 합니다.

1. 취소 아이콘 집합 **DisabledColor** 이 값으로 속성:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![취소 아이콘의 DisabledColor 속성 설정](media/northwind-orders-canvas-part2/save-12.png)

    사용자는 순서에 따라 변경 내용을 취소할 수 및 확인 및 취소 아이콘 비활성화 되 고 모든 변경 내용이 저장 하는 경우 흐리게 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![저장 하 고 변경 내용 취소](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>추가 아이콘 추가

1. 에 **삽입** 탭을 선택 **아이콘** > **추가**합니다.

    > [!div class="mx-imgBorder"]
    > ![Insert는 추가 아이콘](media/northwind-orders-canvas-part2/save-13.png)

    합니다 **추가** 아이콘이 나타납니다 왼쪽 위 모퉁이에서 기본적으로 있는 다른 컨트롤과 어려울 수도 있습니다를 찾으려고 합니다.

    > [!div class="mx-imgBorder"]
    > ![추가 아이콘의 기본 위치](media/northwind-orders-canvas-part2/save-14.png)

1. 에 **홈** 탭, 설정 된 **색** 흰색, 아이콘, 크기 조정 및 취소 아이콘의 왼쪽으로 이동 하기 위한 추가 아이콘의 속성:

    > [!div class="mx-imgBorder"]
    > ![색, 크기 및 추가 아이콘의 위치를 변경 합니다.](media/northwind-orders-canvas-part2/save-15.png)

1. 추가 아이콘 집합 **OnSelect** 속성을 다음이 수식:

    ```powerapps-dot
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![추가 아이콘의 OnSelect 속성 설정](media/northwind-orders-canvas-part2/save-15b.png)

    합니다 [ **NewForm** ](functions/function-form.md) 함수 형태로 빈 레코드를 보여 줍니다.  

1. 추가 아이콘 집합 **DisplayMode** 속성을 다음이 수식:

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![추가 아이콘의 DisplayMode 속성 설정](media/northwind-orders-canvas-part2/save-16.png)

    수식에 이러한 조건에서 추가 아이콘을 비활성화합니다.

    - 사용자가 변경할 하지만 하지 저장 또는 취소, 확인 및 취소 아이콘에서 반대쪽 동작 합니다.
    - 사용자 추가 아이콘을 선택 하지만 변경 하지 않습니다.

1. 추가 아이콘 집합 **DisabledColor** 이 값으로 속성:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![추가 아이콘의 DisabledColor 속성 설정](media/northwind-orders-canvas-part2/save-17.png)

    사용자 변경 하지 않고 또는 저장 되거나 설정한 값 변경 내용을 취소 하는 경우 순서를 만들 수 있습니다. (사용자가이 아이콘을 선택 하는 경우 이러한 수 없습니다. 다시 선택은 하나 이상의 변경 및 저장 하거나 해당 변경 내용을 취소 될 때까지):

    > [!div class="mx-imgBorder"]
    > ![주문 만들기](media/northwind-orders-canvas-part2/save-new.gif)

> [!NOTE]
> 을 만들고 순서를 저장 하는 경우 새 주문을 표시할 순서 갤러리에서 아래로 스크롤하여 해야 합니다. 모든 주문 세부 정보를 아직 추가 하지 않은 했기 때문에 총 가격이 없습니다.

## <a name="add-a-trash-icon"></a>휴지통 아이콘을 추가 합니다.

1. 에 **삽입** 탭을 선택 **아이콘** > **휴지통**합니다.

    > [!div class="mx-imgBorder"]
    > ![휴지통 아이콘을 삽입 합니다.](media/northwind-orders-canvas-part2/save-18.png)

    합니다 **휴지통** 아이콘이 나타납니다 왼쪽 위 모퉁이에서 기본적으로 있는 다른 컨트롤과 어려울 수도 있습니다를 찾으려고 합니다.

    > [!div class="mx-imgBorder"]
    > ![휴지통 아이콘의 기본 위치](media/northwind-orders-canvas-part2/save-19.png)

1. 에 **홈** 탭에서 휴지통 아이콘을 변경 **색** 속성을 흰색, 아이콘, 크기를 조정 하 고 추가 아이콘의 왼쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![색, 크기 및 휴지통 아이콘의 위치를 변경 합니다.](media/northwind-orders-canvas-part2/save-20.png)

1. 휴지통 아이콘을 설정 **OnSelect** 속성을 다음이 수식:

    ```powerapps-dot
    Remove( Orders, Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > ![휴지통 아이콘의 OnSelect 속성 설정](media/northwind-orders-canvas-part2/save-21.png)

    [ **제거할** ](functions/function-remove-removeif.md) 함수는 데이터 원본에서 레코드를 제거 합니다. 이 수식 함수 순서 갤러리에서 선택한 레코드를 제거 합니다. 휴지통 아이콘을 폼 사용자 수식을 삭제 된 레코드를 보다 쉽게 식별할 수 있도록 레코드에 대 한 자세한 정보를 표시 하므로 요약 폼 (순서 갤러리 제외) 옆에 나타납니다.

1. 휴지통 아이콘을 설정 **DisplayMode** 속성을 다음이 수식:

    ```powerapps-dot
    If( Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![휴지통 아이콘의 DisplayMode 속성 설정](media/northwind-orders-canvas-part2/save-22.png)

    이 수식은 사용자가 레코드를 만들 경우 휴지통 아이콘을 해제 합니다. 사용자 레코드에 저장 될 때까지 합니다 **제거** 함수에 삭제할 레코드가 없습니다.

1. 휴지통 아이콘을 설정 **DisabledColor** 이 값으로 속성:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![휴지통 아이콘의 DisabledColor 속성 설정](media/northwind-orders-canvas-part2/save-23.png)

    사용자가 주문을 삭제할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > ![주문 삭제](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>요약

정리 하자면는 사용자가 표시 하 고 각 주문에 대 한 요약을 편집 하 고 이러한 요소를 사용 하는 폼 추가:

- 폼에서 데이터를 표시 하는 **주문** 엔터티: **Form1.DataSource =** `Orders`
- 폼 순서 갤러리 사이 연결 합니다. **Form1.Item =** `Gallery1.Selected`
- 컨트롤을 대체 합니다 **Order number** 필드: **텍스트 보기**
- 다 대 일 관계에서 직원의 그림을 표시할 합니다 **직원** 데이터 카드: `DataCardValue1.Selected.Picture`
- 주문에 변경 내용을 저장 하는 아이콘: `SubmitForm( Form1 )`
- 아이콘을 주문에 대 한 변경 내용을 취소 합니다. `ResetForm( Form1 )`
- 주문을 만들려면 아이콘: `NewForm( Form1 )`
- 주문을 삭제 하려면 아이콘: `Remove( Orders, Gallery1.Selected )`

## <a name="next-step"></a>다음 단계

다음 항목에서는 각 주문에 제품을 표시 하도록 다른 갤러리를 추가 하 고 해당 세부 정보를 사용 하 여 변경 된 [ **패치** ](functions/function-patch.md) 함수입니다.

> [!div class="nextstepaction"]
> [세부 정보 갤러리 만들기](northwind-orders-canvas-part3.md)
