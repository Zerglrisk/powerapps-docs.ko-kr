---
title: Canvas 앱에서 주문 갤러리 만들기 | Microsoft Docs
description: Canvas 앱에서 주문 갤러리를 만들어 Northwind Traders의 데이터 관리
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 06c3a02d1ea3943f64661334ca419f6f205e8b7e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675811"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>캔버스 앱에서 주문 갤러리 만들기

단계별 지침에 따라 Northwind Traders 데이터베이스의 가상 데이터를 관리 하기 위한 캔버스 앱의 주문 갤러리를 만듭니다. 이 항목은 Common Data Service에서 관계형 데이터에 비즈니스 앱을 빌드하는 방법을 설명 하는 시리즈의 일부입니다. 최상의 결과를 위해 다음 항목을이 순서 대로 탐색 합니다.

1. 주문 갤러리를 만듭니다 (**이 항목**).
1. [요약 양식을 만듭니다](northwind-orders-canvas-part2.md).
1. [세부 정보 갤러리를 만듭니다](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> 화면 영역의 ![정의](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>필수 조건

- [Northwind Traders 데이터베이스 및 앱을 설치](northwind-install.md)합니다.
- Northwind Traders 용 [캔버스 앱의 개요](northwind-orders-canvas-overview.md) 를 참조 하세요.

## <a name="create-a-blank-app"></a>빈 앱 만들기

1. [PowerApps에 로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)한 다음 빈 태블릿 앱을 만듭니다.

    > [!div class="mx-imgBorder"]
    > 빈 타일에서 캔버스 앱 ![](media/northwind-orders-canvas-part1/start-01.png)

1. 앱 이름을 원하는 대로 지정한 다음, **만들기**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 빈 대화 상자에서 캔버스 앱 ![](media/northwind-orders-canvas-part1/start-02.png)

    앱에 데이터 소스 및 컨트롤을 추가할 수 있도록 Power Apps Studio가 열립니다.

    > [!div class="mx-imgBorder"]
    > ![Power Apps 스튜디오](media/northwind-orders-canvas-part1/start-03.png)

## <a name="add-the-data"></a>데이터 추가

1. **보기** 탭에서 **데이터 원본**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![보기, 데이터 원본, 데이터 원본 추가를 선택](media/northwind-orders-canvas-part1/datasource-01.png)

1. 검색 상자에 **orders** 를 입력 합니다.

    > [!div class="mx-imgBorder"]
    > 연결 ![목록](media/northwind-orders-canvas-part1/datasource-02.png)

1. 앱에서 사용할 **주문** 데이터 원본을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 엔터티 목록 ![](media/northwind-orders-canvas-part1/datasource-03.png)

    **Orders** 엔터티에는 다양 한 형식의 여러 필드가 포함 되어 있습니다.

    > [!div class="mx-imgBorder"]
    > Orders 엔터티의 필드 목록 ![](media/northwind-orders-canvas-part1/datasource-05.png)

    각 필드에는 논리적 이름이 라고도 하는 **표시 이름과** **이름이**있습니다. 두 이름 모두 동일한 작업을 참조 합니다. 일반적으로 앱을 빌드할 때 표시 이름을 사용 하지만 일부 경우에는 절차에서 설명한 것 처럼 더 복잡 한 **이름이**필요 합니다.

1. 화면 및 컨트롤 작업을 수행할 때 Power Apps 스튜디오에서 3 개의 누적 사각형 아이콘을 눌러 왼쪽의 **트리 뷰로** 다시 전환 합니다. 원통 아이콘을 눌러 언제 든 지 **데이터 원본** 으로 돌아갈 수 있습니다.

## <a name="create-the-order-gallery"></a>주문 갤러리 만들기

1. **삽입** 탭에서 **갤러리** 를 선택 하 > **세로** 를 선택 하 여 [**갤러리**](controls/control-gallery.md) 컨트롤을 추가 하면 주문이 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![삽입, 갤러리, 빈 세로](media/northwind-orders-canvas-part1/orders-01.png)

    컨트롤이 캔버스에 배치 되 고, 연결 하려는 데이터 원본을 묻는 플라이 아웃 대화 상자가 표시 됩니다.  


    > [!div class="mx-imgBorder"]
    > 갤러리의 ![항목 설정 속성](media/northwind-orders-canvas-part1/orders-02.png)

1. 여기서는 **주문** 에 직접 연결할 수 있지만 대신 갤러리의 정렬 순서를 제어 하려고 합니다.  플라이 아웃 대화 상자를 무시 하 고 수식 입력줄에서 갤러리의 **Items** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    Sort 함수는 가장 높은 주문 번호가 있는 가장 먼저 표시 되도록 목록을 [**정렬**](functions/function-sort.md) 합니다.

    > [!div class="mx-imgBorder"]
    > 갤러리의 ![항목 설정 속성](media/northwind-orders-canvas-part1/orders-02b.png)

1. 몇 분 후에 결과 보기가 수식 입력줄 아래에 표시 됩니다.  왼쪽에 있는 화살표를 끌어 수식의 결과를 확인 합니다.  오른쪽으로 스크롤하여 **주문 번호** 열을 확인 하 고 원하는 방식으로 정렬 되었는지 확인 합니다 (최고에서 가장 낮음).  

    > [!div class="mx-imgBorder"]
    > 갤러리의 ![항목 설정 속성](media/northwind-orders-canvas-part1/orders-02c.png)

1. 오른쪽 가장자리 근처의 **속성** 탭에서 **레이아웃** 목록을 엽니다.

    > [!div class="mx-imgBorder"]
    > ![레이아웃 옵션 목록](media/northwind-orders-canvas-part1/orders-03.png)

1. 옵션 목록에서 **제목 및 부제**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 레이아웃을 선택 ![](media/northwind-orders-canvas-part1/orders-04.png)

    갤러리의 템플릿에 두 개의 [**Label**](controls/control-text-box.md) 컨트롤이 추가 됩니다. 기본적으로 이러한 컨트롤은 **Orders** 엔터티의 두 열을 표시 하며,이는 다음에 변경 됩니다. 갤러리의 템플릿은 엔터티의 각 레코드에 대해 세로로 복제 됩니다.

1. 오른쪽 가장자리 근처에 있는 **속성** 탭에서 **필드**옆에 있는 **편집** 을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 레이아웃을 선택 ![](media/northwind-orders-canvas-part1/orders-04b.png)

1. **데이터** 창에서 **Title1** 를 선택 하거나 갤러리 템플릿에서 위쪽 레이블을 선택 합니다.

1. 수식 입력줄에서 레이블의 **Text** 속성을 다음 식으로 설정 합니다.

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > 제목 레이블의 텍스트 속성을 설정 ![](media/northwind-orders-canvas-part1/orders-06.png)

    주문 번호는 각 갤러리 항목의 위쪽에 표시 됩니다. 갤러리 템플릿에서 **ThisItem** 는 **Order** 엔터티의 모든 필드에 대 한 액세스 권한을 부여 합니다.

1. **데이터** 창에서 **Subtitle1** 를 선택 하거나 갤러리 템플릿에서 하위 레이블을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 부제목 레이블 ![선택](media/northwind-orders-canvas-part1/orders-07.png)

1. 수식 입력줄에서 레이블의 **Text** 속성을 다음 식으로 설정 합니다.

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > 자막 레이블의 텍스트 속성을 설정 ![](media/northwind-orders-canvas-part1/orders-08.png)

    이 수식을 입력 하면 잠시 동안 빨간색 물결 모양의 오류가 표시 될 수 있습니다. 수식 입력줄 외부에서 항목을 선택한 다음 수식 입력줄에 커서를 반환 하는 경우이 오류를 지워야 합니다. 오류가 계속 발생 하거나 값이 표시 되지 않으면 **보기** 탭을 선택 하 고 **데이터 원본**을 선택한 다음 데이터 원본 이름 오른쪽에 있는 줄임표 (...)를 선택 하 여 **Orders** 엔터티를 새로 고칩니다.

    **ThisItem**를 지정 하는 경우 **주문과** **고객** 엔터티 간의 다 대 일 관계를 활용 하 여 각 주문에 연결 된 고객 레코드를 검색 합니다. 고객 레코드에서 표시를 위해 **회사** 열의 데이터를 추출 하는 중입니다.

    **Orders** 엔터티에서 **Customer** 엔터티를 포함 하 여 다른 엔터티로 모든 관계를 표시할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > ![관계 목록](media/northwind-orders-canvas-part1/orders-09.png)

1. 오른쪽 위 모서리에서 닫기 아이콘 (x)을 선택 하 여 **데이터** 창을 닫습니다.

## <a name="show-each-orders-status"></a>각 주문의 상태를 표시 합니다.

이 절차에서는 갤러리에서 레이블에 대 한 공간을 추가 하 고 각 주문의 상태를 데이터를 기반으로 하는 다른 색으로 표시 하도록 구성 합니다.

1. 갤러리의 템플릿에서 첫 번째 레이블의 **Title1**을 줄입니다.

    > [!div class="mx-imgBorder"]
    > 갤러리 템플릿에서 Title1을 ![](media/northwind-orders-canvas-part1/status-01.png)

1. 두 번째 레이블 **Subtitle1**를 사용 하 여 이전 단계를 반복 합니다.

    > [!div class="mx-imgBorder"]
    > 갤러리 템플릿에서 Subtitle1을 ![](media/northwind-orders-canvas-part1/status-02.png)

1. 갤러리 템플릿 (또는 템플릿의 컨트롤)을 선택 하 고 **삽입** 탭에서 **레이블** 을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 레이블 추가 ![](media/northwind-orders-canvas-part1/status-03.png)

1. 새 레이블을 **Title1** 레이블 오른쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 레이블 ![이동 하 고 크기를 조정](media/northwind-orders-canvas-part1/status-04.png)

1. 새 레이블의 **Text** 속성을 다음 식으로 설정 합니다.

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > 텍스트 속성을 설정 ![](media/northwind-orders-canvas-part1/status-05.png)

    **Orders** 엔터티의 주문 **상태** 필드에는 **주문 상태** 옵션 집합의 값이 포함 됩니다. 옵션 집합은 다른 프로그래밍 도구의 열거와 유사 합니다. 각 옵션 집합은 데이터베이스에 정의 되므로 사용자는 집합에 있는 옵션만 지정할 수 있습니다. **Orders 상태** 옵션 집합은 로컬이 아닌 전역 이기도 하므로 다른 엔터티에서 사용할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > ![주문 상태 옵션 집합](media/northwind-orders-canvas-part1/status-06.png)

    집합의 각 옵션에는 레이블에 표시 되는 경우 표시 되는 이름이 있습니다. 이러한 이름을 지역화할 수 있으며, 앱은 영어 사용자가 **Apple**을 선택 하거나, 프랑스어 사용자가 **Pomme**를 선택 하거나, 스페인어 사용자가 **Manzana**를 선택 하는지 여부에 관계 없이 동일한 옵션을 인식 합니다. 따라서이 항목에서 나중에 설명 하는 것 처럼 옵션에 대해 하드 코드 된 문자열을 사용 하는 수식을 만들 수 없습니다.

    수식에서는 공백이 포함 되어 있으므로 **주문 상태** 를 작은따옴표로 묶어야 합니다. 그러나이 이름은 Power Apps의 다른 이름 (예: **고객** 또는 **회사**)과 동일한 방식으로 작동 합니다.

1. **홈** 탭에서 상태 레이블의 글꼴 크기를 20 포인트로 늘리고 텍스트를 오른쪽에 맞춥니다.

    > [!div class="mx-imgBorder"]
    > ![글꼴 크기와 맞춤](media/northwind-orders-canvas-part1/status-07.png) 변경

1. 수식 입력줄에서 상태 레이블의 **Color** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > 상태 레이블의 Color 속성을 설정 ![](media/northwind-orders-canvas-part1/status-08.png)

    Power Apps를 사용 하면 옵션 이름이 지역화 된 경우에도 해당 수식이 잘못 된 결과를 생성할 수 있기 때문에 집합에서 각 옵션에 대해 하드 코드 된 문자열을 사용 하는 수식을 만들 수 없습니다. 대신 **Switch** 함수는 사용자의 설정을 기반으로 레이블에 표시 되는 문자열을 기준으로 색을 결정 합니다.

    이 수식을 그대로 사용 하면 이전 그래픽에 표시 된 것 처럼 다른 상태 값이 다른 색으로 표시 됩니다.

## <a name="display-each-orders-total"></a>각 주문의 합계를 표시 합니다.

1. 갤러리의 템플릿 인 갤러리에서 첫 번째 항목을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 갤러리 템플릿을 선택 ![](media/northwind-orders-canvas-part1/aggregate-01.png)

1. **삽입** 탭에서 **레이블** 을 선택 하 여 다른 레이블을 추가 합니다.

    > [!div class="mx-imgBorder"]
    > 레이블 추가 ![](media/northwind-orders-canvas-part1/aggregate-02.png)

1. 새 레이블이 상태 레이블 아래에 표시 되도록 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![새 레이블의 크기를 조정 하 고 이동](media/northwind-orders-canvas-part1/aggregate-03.png)

1. 수식 입력줄에서 새 레이블의 **Text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > 주문의 총 비용을 계산 하는 ![수식](media/northwind-orders-canvas-part1/aggregate-04.png)

    이 수식에서 [**Sum**](functions/function-aggregates.md) 함수는 일 대 다 관계를 통해 **order** 엔터티의 각 레코드와 연결 된 **주문 정보** 엔터티의 레코드를 추가 합니다. 이러한 줄 항목은 각 주문을 구성 하므로 동일한 일 대 다 관계를 사용 하 여 화면의 오른쪽 아래 영역에 있는 항목을 표시 하 고 편집 합니다.

    이 수식은 Common Data Service 복잡 한 집계 함수 (예: 곱셈의 합계)의 위임을 지원 하지 않으므로 파란색 밑줄과 [위임 경고](delegation-overview.md) 를 표시 합니다. 이 예제에는 500 개 이상의 줄 항목이 포함 되지 않으므로이 정보를 무시할 수 있습니다. 다른 앱에 필요한 경우 **앱 설정**에서이 제한을 늘릴 수 있습니다.

    이 수식의 [**텍스트**](functions/function-text.md) 함수는 통화 기호를 추가 하 고 천 단위 및 소수 구분 기호를 사용 하 여 결과의 서식을 지정 합니다. 작성 된 대로 수식에는 미국 영어 ( **[$-en-us]** ) 및 달러 기호 ( **$** )의 언어 태그가 포함 됩니다. 언어 태그를 제거 하는 경우 언어 설정에 따라 하나로 바뀌고 레이블에 해당 태그에 대 한 적절 한 형식이 표시 됩니다. 달러 기호를 벗어나면 레이블의 사용자 설정에 따라 적절 한 통화 기호가 표시 됩니다. 그러나 달러 기호를 원하는 것으로 바꿔 다른 기호를 강제로 표시할 수 있습니다.

1. **홈** 탭에서 최신 레이블의 글꼴 크기를 20 포인트로 변경 하 고 텍스트를 오른쪽 맞춤 합니다.

    > [!div class="mx-imgBorder"]
    > 레이블의 글꼴 크기와 맞춤 ![변경](media/northwind-orders-canvas-part1/aggregate-05.png)

1. 갤러리를 화면 왼쪽 가장자리로 이동 하 고 갤러리의 너비를 줄여 일부 공간을 닫습니다.

1. 갤러리의 높이를 확대 하 여 화면 높이와 거의 동일 하 게 유지 하 고 제목 표시줄의 맨 위에 공간을 남겨 두면 다음 항목의 시작 부분에 추가 합니다.

    > [!div class="mx-imgBorder"]
    > 갤러리를 이동 하 고 크기를 조정 ![](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>정리

다음 요소를 포함 하는 주문 갤러리를 추가 하 여 단일 화면 캔버스 앱 빌드를 시작 했습니다.

- 주문 번호를 표시 하는 식: `"Orders " & ThisItem.OrderNumber`
- 다 대 일 관계의 필드: `ThisItem.Customer.Company`
- 집합의 옵션 이름을 표시 하는 레이블: `ThisItem.'Order Status'`
- 레이블에 표시 되는 옵션에 따라 형식을 변경 하는 레이블: `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- 일 대 다 관계에 대 한 복합 집계 함수: `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>다음 항목

다음 항목에서는 [**편집 양식**](controls/control-form-detail.md) 컨트롤을 추가 하 여 사용자가 방금 만든 갤러리에서 선택 하는 모든 주문의 요약을 표시 하 고 편집 합니다.

> [!div class="nextstepaction"]
> [요약 양식 만들기](northwind-orders-canvas-part2.md)
