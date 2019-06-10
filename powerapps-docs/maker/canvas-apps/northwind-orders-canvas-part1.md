---
title: 순서 갤러리에서 캔버스 앱 만들기 | Microsoft Docs
description: Northwind Traders에 대 한 데이터를 관리 하는 캔버스 앱에서 순서 갤러리 만들기
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
ms.openlocfilehash: 94d6c104cb888bb13f3724231d7891d622f5377b
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761008"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>캔버스 앱에서 순서 갤러리 만들기

Northwind 데이터베이스에서 가상의 데이터를 관리 하는 것에 대 한 캔버스 앱에서 순서 대로 갤러리를 만드는 단계별 지침을 따릅니다. 이 항목은 Common Data Service의 관계형 데이터에서 비즈니스 앱을 빌드하는 방법을 설명 하는 시리즈의 일부입니다. 최상의 결과이 순서 대로 이러한 항목을 살펴봅니다.

1. 순서 갤러리 만들기 (**이 항목에서는**).
1. [요약 양식을 만드는](northwind-orders-canvas-part2.md)합니다.
1. [세부 정보 갤러리 만들기](northwind-orders-canvas-part3.md)합니다.

> [!div class="mx-imgBorder"]
> ![화면 영역 정의](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>필수 조건

- [Northwind Traders 데이터베이스 및 앱 설치](northwind-install.md)합니다.
- 읽고 합니다 [캔버스 앱 개요](northwind-orders-canvas-overview.md) Northwind Traders에 대 한 합니다.

## <a name="create-a-blank-app"></a>빈 앱 만들기

1. [PowerApps에 로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), 한 다음 빈 태블릿 앱을 만듭니다.

    > [!div class="mx-imgBorder"]
    > ![빈 타일에서 캔버스 앱](media/northwind-orders-canvas-part1/start-01.png)

1. 원하는 선택한 후 원하는 앱의 이름을 **만들기**합니다.

    > [!div class="mx-imgBorder"]
    > ![빈 대화 상자에서 캔버스 앱](media/northwind-orders-canvas-part1/start-02.png)

    PowerApps Studio는 앱에 데이터 원본 및 컨트롤을 추가할 수 있도록 열립니다.

    > [!div class="mx-imgBorder"]
    > ![PowerApps Studio](media/northwind-orders-canvas-part1/start-03.png)

1. 사용 하도록 설정 된 [실험적 기능](working-with-experimental.md) 수식 입력줄에서 직접 수식의 결과 표시 하는 데 합니다.

    1. 에 **파일** 메뉴에서 **앱 설정**를 선택한 후 **고급 설정**합니다.
    1. 기능을 목록 아래쪽으로 스크롤하여 켭니다 **수식 입력줄 결과 뷰를 사용 하도록 설정**:

        > [!div class="mx-imgBorder"]
        > ![실험적 기능 목록](media/northwind-orders-canvas-part1/start-04.png)

1. 왼쪽 위 모퉁이에서 빈 캔버스로 돌아가려면 뒤로 화살표를 선택 합니다.

## <a name="add-the-data"></a>데이터를 추가 합니다.

1. 에 **뷰** 탭을 선택 **데이터 원본**를 선택한 후 **데이터 원본 추가** 에 **데이터** 창:

    > [!div class="mx-imgBorder"]
    > ![보기, 데이터 원본, 데이터 원본 추가 선택 합니다.](media/northwind-orders-canvas-part1/datasource-01.png)

1. 선택 **Common Data Service**합니다.

    하는 경우 **Common Data Service** 연결을 select 목록에 나타나지 **새 연결**를 추가 합니다.

    > [!div class="mx-imgBorder"]
    > ![연결 목록](media/northwind-orders-canvas-part1/datasource-02.png)

1. 아래 **엔터티 선택**, 형식 **주문**를 선택 합니다 **주문** 확인란을 선택한 후 **연결**:

    > [!div class="mx-imgBorder"]
    > ![엔터티 목록](media/northwind-orders-canvas-part1/datasource-03.png)

    추가한 합니다 **주문** 앱에 데이터 원본:

    > [!div class="mx-imgBorder"]
    > ![데이터 창](media/northwind-orders-canvas-part1/datasource-04.png)

    합니다 **주문** 엔터티 다양 한 형식의 여러 필드를 포함 합니다.

    > [!div class="mx-imgBorder"]
    > ![Orders 엔터티의 필드 목록](media/northwind-orders-canvas-part1/datasource-05.png)

    각 필드에는 **표시 이름** 와 **이름**는 라고도 하는 논리적 이름입니다. 두 이름이 동일한 작업을 가리킵니다. 일반적으로 응용 프로그램을 구축 하지만 일부 경우 필요한 더 복잡 한 경우 표시 이름을 사용 합니다 있습니다 **이름을**절차에서 설명 했 듯이, 합니다.

1. PowerApps Studio 닫을 합니다 **데이터** 의 오른쪽 위 모서리의 닫기 아이콘 (x)를 선택 하 여 창입니다.

## <a name="create-the-order-gallery"></a>순서 갤러리 만들기

1. 에 **삽입** 탭을 선택 **갤러리** > **빈 세로** 추가 하는 [ **갤러리** ](controls/control-gallery.md)주문을 보여 주는 컨트롤입니다.

    > [!div class="mx-imgBorder"]
    > ![Insert, 갤러리, 빈 세로](media/northwind-orders-canvas-part1/orders-01.png)

1. 수식 입력줄에서 갤러리의 설정 **항목** 속성을 다음이 수식:

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    합니다 [ **정렬** ](functions/function-sort.md) 함수 최신 순서 (가장 높은 순서 번호가) 첫 번째 표시 되도록 목록을 정렬 합니다.

    > [!div class="mx-imgBorder"]
    > ![갤러리의 Items 속성 설정](media/northwind-orders-canvas-part1/orders-02.png)

1. 에 **속성** 열고 오른쪽 가장자리 근처 탭의 **레이아웃** 목록:

    > [!div class="mx-imgBorder"]
    > ![레이아웃 옵션의 목록](media/northwind-orders-canvas-part1/orders-03.png)

1. 옵션의 목록에서 선택 **제목 및 부제목**:

    > [!div class="mx-imgBorder"]
    > ![레이아웃 선택](media/northwind-orders-canvas-part1/orders-04.png)

    두 개의 [ **레이블을** ](controls/control-text-box.md) 컨트롤 갤러리의 템플릿에 추가 됩니다. 기본적으로 이러한 컨트롤의 두 열을 표시 합니다 **주문** 엔터티와 다음 변경 합니다. 갤러리의 템플릿에 각 엔터티 레코드에 대 한 세로 방향으로 복제 됩니다.

1. 닫은 경우 합니다 **데이터** 창 **편집** (옆에 **필드**)에 **속성** 오른쪽 가장자리 근처에서 탭 합니다.

1. 에 **데이터** 창 **Title1** (또는 위에 레이블을 갤러리의 템플릿에서 선택).

1. 수식 입력줄 설정 레이블의 **텍스트** 속성을이 식:

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > ![제목 레이블 텍스트 속성 설정](media/northwind-orders-canvas-part1/orders-06.png)

    주문 번호를 각 갤러리 항목의 맨 위에 나타납니다. 갤러리 템플릿에 **ThisItem** 의 모든 필드에 대 한 액세스 권한을 부여 합니다 **순서** 엔터티.

1. 에 **데이터** 창 **Subtitle1** (또는 하위 레이블을 갤러리의 템플릿에서 선택):

    > [!div class="mx-imgBorder"]
    > ![선택 자막 레이블](media/northwind-orders-canvas-part1/orders-07.png)

1. 수식 입력줄 설정 레이블의 **텍스트** 속성을이 식:

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > ![부제목 레이블의 텍스트 속성 설정](media/northwind-orders-canvas-part1/orders-08.png)

    이 수식에 입력 하면 빨간색의 구불구불한 오류를 잠시 표시 될 수 있습니다 것입니다. 수식 입력줄 외부에서 아무것도 선택 하 고 다음 수식 입력줄는 커서를 반환 하는 경우 오류를 지워야 합니다. 선택 계속 되 면 오류 또는 값이 표시 되지 않는 경우는 **보기** 탭을 선택 **데이터 원본**, 및 다음 새로 고침 합니다 **주문** 줄임표 (...)를 선택 하 여 엔터티는 데이터 원본 이름 오른쪽의입니다.

    지정 하는 경우 **ThisItem.Customer**, 간에 다 대 일 관계를 활용 하는 **주문** 및 **고객** 엔터티와 고객 레코드를 검색 합니다. 각 순서와 연관 된 합니다. 고객 레코드에서의 데이터를 추출 하는 **회사** 표시에 대 한 열입니다.

    모든 관계를 표시할 수 있습니다는 **주문을** 엔터티가 다른 엔터티를 포함 하는 **고객** 엔터티:

    > [!div class="mx-imgBorder"]
    > ![관계 목록](media/northwind-orders-canvas-part1/orders-09.png)

1. 닫을 합니다 **데이터** 의 오른쪽 위 모서리의 닫기 아이콘 (x)를 선택 하 여 창입니다.

## <a name="show-each-orders-status"></a>각 주문의 상태를 표시 합니다.

이 절차에서는 레이블에 대 한 갤러리의 공간을 추가 하 고 데이터를 기반으로 다른 색으로 각 주문의 상태를 표시 하도록 구성 키를 누릅니다.

1. 갤러리의 템플릿에서 첫 번째 레이블의 너비를 줄일 **Title1**:

    > [!div class="mx-imgBorder"]
    > ![갤러리의 템플릿에서 Title1](media/northwind-orders-canvas-part1/status-01.png)

1. 두 번째 레이블 사용 하 여 이전 단계를 반복 **Subtitle1**:

    > [!div class="mx-imgBorder"]
    > ![갤러리의 템플릿에서 Subtitle1](media/northwind-orders-canvas-part1/status-02.png)

1. 갤러리를 사용 하 여 선택한 템플릿 (또는 템플릿에 컨트롤)을 선택 **레이블을** 에 **삽입** 탭:

    > [!div class="mx-imgBorder"]
    > ![레이블 추가](media/northwind-orders-canvas-part1/status-03.png)

1. 오른쪽에 새 레이블을 이동 하 여 **Title1** 레이블:

    > [!div class="mx-imgBorder"]
    > ![이동 하 고 레이블의 크기를 조정합니다](media/northwind-orders-canvas-part1/status-04.png)

1. 설정 된 **텍스트** 을이 식으로 새 레이블의 속성:

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![Text 속성 설정](media/northwind-orders-canvas-part1/status-05.png)

    에 **주문** 엔터티를를 **주문 상태** 필드에서 값을 보유 합니다 **주문 상태** 옵션이 설정. 옵션 집합을 다른 프로그래밍 도구에서 열거 하는 것과 비슷합니다. 각 옵션 집합에는 사용자 집합에 있는 이러한 옵션을 지정할 수 있도록 데이터베이스에 정의 됩니다. 합니다 **주문 상태** 옵션 집합은 또한 전역, 로컬, 다른 엔터티에 사용할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > ![상태 옵션 집합을 정렬](media/northwind-orders-canvas-part1/status-06.png)

    집합의 각 옵션에는 레이블에 표시 하는 경우 표시 되는 이름입니다. 이러한 이름은 지역화할 수 있는 하 고 사용자가 있는지 여부를 앱 같은 옵션을 인식 **Apple**, 프랑스어 사용자가 선택할 **Pomme**, 또는 스페인어 사용자가 선택할 **Manzana**. 따라서이 항목 뒷부분에서 설명 하는 대로 하드 코드 된 문자열 옵션을 사용 하는 수식을 만들 수 없습니다.

    수식에 묶어야 **주문 상태** 사용 하 여 작은따옴표에 공백을 포함 하므로 합니다. 그러나 해당 이름을 동일한 PowerApps의 마찬가지로 다른 이름과 같은 함수 **고객** 하거나 **회사**, 않습니다.

1. 에 **홈** 탭, 20 지점에 상태 레이블 글꼴 크기를 늘리고, 텍스트를 오른쪽 맞춤 합니다.

    > [!div class="mx-imgBorder"]
    > ![글꼴 크기 변경 및 맞춤](media/northwind-orders-canvas-part1/status-07.png)

1. 수식 입력줄에서 설정 합니다 **Color** 속성을 다음이 수식으로 상태 레이블:

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![상태 레이블 색 속성 설정](media/northwind-orders-canvas-part1/status-08.png)

    PowerApps에서 옵션 이름은 지역화 하는 경우 이러한 수식 부적절 한 결과 생성할 수 없습니다 때문에 집합의 각 옵션에 대 한 하드 코드 된 문자열에 의존 하는 수식을 만들 수 없습니다. 대신 합니다 **스위치** 함수 사용자의 설정에 따라 레이블에 표시 되는 문자열에 따라 색을 결정 합니다.

    현재 위치에서이 수식을 사용 하 여 이전 그래픽 에서처럼 다른 상태 값 서로 다른 색으로 표시 됩니다.

## <a name="display-each-orders-total"></a>각 주문의 합계를 표시 합니다.

1. 갤러리의 템플릿에 갤러리에서 첫 번째 항목을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![갤러리 템플릿이 선택](media/northwind-orders-canvas-part1/aggregate-01.png)

1. 에 **삽입** 탭을 선택 **레이블을** 다른 레이블을 추가 하려면:

    > [!div class="mx-imgBorder"]
    > ![레이블 추가](media/northwind-orders-canvas-part1/aggregate-02.png)

1. 상태 레이블 아래에 나타나는 새 레이블을 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![크기를 조정 하 고 새 레이블을 이동합니다](media/northwind-orders-canvas-part1/aggregate-03.png)

1. 수식 입력줄에서 새 레이블 설정 **텍스트** 속성을 다음이 수식:

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![주문을 총 비용을 계산 하는 것에 대 한 수식](media/northwind-orders-canvas-part1/aggregate-04.png)

    이 수식에서의 [ **합계** ](functions/function-aggregates.md) 에서 레코드를 추가 하는 함수를 **Order Details** 의 각 레코드와 연결 된 엔터티는 **순서**-다 관계를 통해 엔터티. 이러한 줄 항목 각 주문에 등록 하 고 동일한-다 관계 표시 하 고 화면 오른쪽 아래 영역에서 줄 항목을 편집 하는 데 사용 됩니다.

    이 수식에 파란색 밑줄이 표시와 [위임 경고](delegation-overview.md) Common Data Service에는 복잡 한 집계 함수 (예를 들어 곱하기의 합)의 위임을 지원 하지 않기 때문입니다. 이 예제의 순서 없이 500 개 이상의 품목 포함 되므로이 정보를 무시할 수 있습니다. 경우 다른 앱에 대해 필요한 제한을 늘릴 수 있습니다 하에 **앱 설정**합니다.

    합니다 [ **텍스트** ](functions/function-text.md) 이 수식에 함수 통화 기호를 추가 하 고 천 단위 및 소수 구분 기호를 사용 하 여 결과 형식을 지정 합니다. 미국에 대 한 수식 언어 태그에 작성 된 대로 영어 ( **[$-EN-US]** ) 및 달러 기호 ( **$** ). 언어 태그를 제거 하면 언어 설정을 기반으로 바뀝니다 및 레이블을 해당 태그에 대 한 적절 한 형식에 표시 됩니다. 달러 기호를 두면 레이블을 사용자의 설정에 따라 적합 한 통화 기호가 표시 됩니다. 그러나 선호 하는 것을 사용 하 여 달러 기호를 대체 하 여 표시할 다른 기호를 강제할 수 있습니다.

1. 에 **홈** 탭 20 지점에 최신 레이블의 글꼴 크기를 변경 하 고 해당 텍스트를 오른쪽 맞춤 합니다.

    > [!div class="mx-imgBorder"]
    > ![글꼴 크기 및 레이블의 맞춤 변경](media/northwind-orders-canvas-part1/aggregate-05.png)

1. 화면의 왼쪽된 가장자리에 갤러리를 이동 하 고 일부 공간을 확대 하려면 갤러리의 너비를 줄입니다.

1. 화면으로 긴 것 갤러리의 높이 늘어나지만 확보 약간 맨 위에 있는 다음 항목의 시작 부분에 추가 하는 제목 표시줄:

    > [!div class="mx-imgBorder"]
    > ![이동 및 갤러리 크기 조정](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>요약

정리 하자면, 이러한 요소를 포함 하는 순서 대로 갤러리를 추가 하 여 단일 화면 캔버스 앱 빌드 시작:

- 주문 번호를 표시 하는 식: `"Orders " & ThisItem.OrderNumber`
- 다 대 일 관계에 있는 필드: `ThisItem.Customer.Company`
- 집합의 옵션 이름을 보여 주는 레이블: `ThisItem.'Order Status'`
- 옵션 집합의 레이블에 표시에 따라 형식을 변경 하는 레이블: `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- 1 대 다 관계를 통해 복잡 한 집계 함수: `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>다음 항목

다음 항목에서는 추가 [ **편집 양식** ](controls/control-form-detail.md) 컨트롤을 표시 하 고 방금 만든 갤러리에서 선택 하는 사용자를 순서 대로의 요약 정보를 편집 합니다.

> [!div class="nextstepaction"]
> [요약 폼을 만들려면](northwind-orders-canvas-part2.md)