---
title: Canvas 앱에서 세부 정보 갤러리 만들기 | Microsoft Docs
description: Canvas 앱에서 세부 정보 갤러리를 만들어 Northwind Traders의 데이터 관리
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
ms.openlocfilehash: 7a975669d1e22289b7152b830808631992389a1f
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "71991622"
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>캔버스 앱에서 세부 정보 갤러리 만들기

단계별 지침에 따라 Northwind Traders 데이터베이스의 가상 데이터를 관리 하기 위한 캔버스 앱에서 세부 정보 갤러리를 만듭니다. 이 항목은 Common Data Service에서 관계형 데이터에 비즈니스 앱을 빌드하는 방법을 설명 하는 시리즈의 일부입니다. 최상의 결과를 위해 다음 항목을이 순서 대로 탐색 합니다.

1. [주문 갤러리를 만듭니다](northwind-orders-canvas-part1.md).
1. [요약 양식을 만듭니다](northwind-orders-canvas-part2.md).
1. 세부 정보 갤러리 (**이 항목**)를 만듭니다.

> [!div class="mx-imgBorder"]
> 화면 영역의 ![Definition ](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>필수 조건

이 항목의 앞부분에서 설명한 대로이 항목을 시작 하기 전에 데이터베이스를 설치 해야 합니다. 그런 다음 주문 갤러리와 요약 양식을 만들거나, 해당 갤러리와 해당 형식이 이미 포함 된 **Northwind 주문 (Canvas) Begin Part 3** 앱을 열어야 합니다.

## <a name="create-another-title-bar"></a>다른 제목 표시줄 만들기

1. 화면 위쪽에서 제목 표시줄 역할을 하는 [**레이블**](controls/control-text-box.md) 컨트롤을 선택 하 고 Ctrl + C를 눌러 복사한 다음 Ctrl + V를 눌러 붙여넣습니다.

    > [!div class="mx-imgBorder"]
    > 제목 표시줄 ![Copy 및 붙여넣기 ](media/northwind-orders-canvas-part3/details-01.png)

1. 요약 양식 바로 아래에 나타나도록 크기를 조정 하 고 이동 합니다.

1. 다음 방법 중 하나를 수행 하 여 복사본에서 텍스트를 제거 합니다.

    - 텍스트를 두 번 클릭 하 여 선택한 다음 Delete 키를 누릅니다.
    - 레이블의 **Text** 속성을 빈 문자열 ( **""** )로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > 제목 표시줄 복사본의 텍스트를 ![Remove ](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>갤러리 추가

1. **빈 세로** 레이아웃을 사용 하 여 [**갤러리**](controls/control-gallery.md) 컨트롤을 삽입 합니다.

    > [!div class="mx-imgBorder"]
    > 빈 세로 갤러리를 ![Add ](media/northwind-orders-canvas-part3/details-03.png)

    주문 세부 정보를 표시 하는 새 갤러리가 왼쪽 위 모퉁이에 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 주문 세부 정보 갤러리의 ![Default 위치 ](media/northwind-orders-canvas-part3/details-04.png)

1. **데이터** 창을 닫은 다음 크기를 조정 하 고 세부 정보 갤러리를 새 제목 표시줄 아래의 오른쪽 아래 모서리로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 주문 세부 정보 갤러리의 ![Final 위치 ](media/northwind-orders-canvas-part3/details-05.png)

1. 세부 정보 갤러리의 **Items** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > 세부 정보 갤러리의 Items 속성을 ![Set ](media/northwind-orders-canvas-part3/details-06.png)

    오류가 표시 되 면 주문 갤러리의 이름이 **gallery1.selected** (왼쪽 가장자리 근처 **트리 뷰** 창에 표시 됨) 인지 확인 합니다. 갤러리의 이름이 다른 경우 이름을 **gallery1.selected**로 바꿉니다.

    두 갤러리를 연결한 것입니다. 사용자가 주문 갤러리에서 주문을 선택 하면 해당 선택 항목이 **Orders** 엔터티의 레코드를 식별 합니다. 해당 순서에 하나 이상의 줄 항목이 포함 된 경우 **Orders** 엔터티의 레코드는 **order details** 엔터티의 하나 이상의 레코드에 연결 되 고 해당 레코드의 데이터는 세부 정보 갤러리에 표시 됩니다. 이 동작은 **주문** 및 **주문 정보** 엔터티 사이에 생성 된 일 대 다 관계를 반영 합니다. 지정 된 수식에서 점 표기법을 사용 하 여 관계를 "워크" 합니다.

    > [!div class="mx-imgBorder"]
    > Orders 엔터티와 Order Details 엔터티 간의 ![One 일대다 관계 ](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>제품 이름 표시

1. 세부 정보 갤러리의 **삽입 탭에서 항목 추가** 를 선택 하 여 갤러리 템플릿을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 세부 정보 갤러리에 대 한 템플릿을 ![Select ](media/northwind-orders-canvas-part3/details-07.png)

    갤러리 자체 대신 갤러리 템플릿을 선택 했는지 확인 합니다. 경계 상자는 갤러리 경계 내에 있어야 하며 갤러리의 높이 보다 짧을 수 있습니다. 이 템플릿에 컨트롤을 삽입 하면 갤러리의 각 항목에 대해 반복 됩니다.

1. **삽입** 탭에서 세부 정보 갤러리에 레이블을 삽입 합니다.

    레이블이 갤러리 내에 표시 되어야 합니다. 그렇지 않은 경우 다시 시도 하지만 레이블을 삽입 하기 전에 갤러리의 템플릿을 선택 해야 합니다.

    > [!div class="mx-imgBorder"]
    > 세부 정보 갤러리에 레이블을 ![Add ](media/northwind-orders-canvas-part3/details-08.png)

1. 새 레이블의 **Text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    ThisItem.Product.'Product Name'
    ```

    텍스트를 표시 하지 않는 경우 주문 갤러리 아래쪽의 **주문 0901** 에 대 한 화살표를 선택 합니다.

1. 전체 텍스트가 나타나도록 레이블의 크기를 조정 합니다.

    > [!div class="mx-imgBorder"]
    > 주문 세부 정보를 ![Show 제품 이름을 ](media/northwind-orders-canvas-part3/details-09.png)

    이 식은 **Order Details** 엔터티의 레코드를 기반으로 합니다. 레코드는 다 대 일 관계를 통해 **Order Products** 엔터티에 **ThisItem** 됩니다.

    > [!div class="mx-imgBorder"]
    > Order Details 엔터티와 주문 제품 엔터티 간의 ![Many 관계 ](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    **제품 이름** 필드 (및 사용할 다른 필드)는 추출 됩니다.

    > [!div class="mx-imgBorder"]
    > Order Products 엔터티의 ![Fields ](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>제품 이미지 표시

1. **삽입** 탭에서 세부 정보 갤러리에 [**이미지**](controls/control-image.md) 컨트롤을 삽입 합니다.

    > [!div class="mx-imgBorder"]
    > 이미지 컨트롤을 ![Insert ](media/northwind-orders-canvas-part3/details-10.png)

1. 크기를 조정 하 고 이미지와 레이블을 나란히 나란히 이동 합니다.

    > [!TIP]
    > 컨트롤의 크기 및 위치에 대 한 세분화 된 제어를 위해 Alt 키를 누르지 않고 크기를 조정 하거나 이동 하기 시작 하 고 Alt 키를 누른 채 컨트롤의 크기를 조정 하거나 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 이미지 컨트롤을 ![Move ](media/northwind-orders-canvas-part3/details-11.png)

1. 이미지의 **이미지** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    ThisItem.Product.Picture
    ```

    이 식은이 주문 세부 정보와 연결 된 제품을 참조 하 고 표시할 **그림** 필드를 추출 합니다.

    > [!div class="mx-imgBorder"]
    > ![Show 제품 이미지 ](media/northwind-orders-canvas-part3/details-12.png)

1. 두 개 이상의 **주문 세부** 레코드가 한 번에 표시 되도록 갤러리 템플릿의 높이를 줄입니다.

    > [!div class="mx-imgBorder"]
    > 갤러리의 템플릿 ![Shorten ](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>제품 수량 및 비용 표시

1. **삽입** 탭에서 세부 정보 갤러리에 다른 레이블을 삽입 한 다음 크기를 조정 하 고 새 레이블을 제품 정보 오른쪽으로 이동 합니다.

1. 새 레이블의 **Text** 속성을 다음 식으로 설정 합니다.

    ```powerapps-dot
    ThisItem.Quantity
    ```

    이 수식은 **Order Details** 엔터티에서 직접 정보를 가져옵니다 (관계 필요 없음).

    > [!div class="mx-imgBorder"]
    > ![Show 제품 수량 ](media/northwind-orders-canvas-part3/details-13b.png) 

1. **홈** 탭에서이 컨트롤의 맞춤을 **오른쪽**으로 변경 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 맞춤 ](media/northwind-orders-canvas-part3/details-14.png)

1. **삽입** 탭에서 세부 정보 갤러리에 다른 레이블을 삽입 한 다음 크기를 조정 하 고 수량 레이블 오른쪽으로 이동 합니다.

1. 새 레이블의 **Text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Text( ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    언어 태그 ( **[$-en-us]** )를 포함 하지 않는 경우 해당 언어와 지역에 따라 추가 됩니다. 다른 언어 태그를 사용 하는 경우 닫는 대괄호 ( **]** ) 바로 다음에 **$** 를 제거한 다음 해당 위치에 통화 기호를 추가 합니다.

    > [!div class="mx-imgBorder"]
    > ![Show 단가 ](media/northwind-orders-canvas-part3/details-15.png)

1. **홈** 탭에서이 컨트롤의 맞춤을 **오른쪽**으로 변경 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 맞춤 ](media/northwind-orders-canvas-part3/details-16.png)

1. **삽입** 탭에서 세부 정보 갤러리에 다른 레이블 컨트롤을 삽입 한 다음 크기를 조정 하 고 단가의 오른쪽으로 새 레이블을 이동 합니다.

1. 새 레이블의 **Text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Text( ThisItem.Quantity * ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    언어 태그 ( **[$-en-us]** )를 포함 하지 않으면 언어와 지역에 따라 추가 됩니다. 태그가 다른 경우 닫는 대괄호 ( **]** ) 바로 다음에 **$** 대신 사용자 고유의 통화 기호를 사용 하는 것이 좋습니다.

    > [!div class="mx-imgBorder"]
    > ![Show 연장 가격 ](media/northwind-orders-canvas-part3/details-17.png)

1. **홈** 탭에서이 컨트롤의 맞춤을 **오른쪽**으로 변경 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 맞춤 ](media/northwind-orders-canvas-part3/details-18.png)

    지금은 세부 정보 갤러리에 컨트롤을 추가 하는 작업이 완료 되었습니다.

1. **트리 뷰** 창에서 **Screen1** 를 선택 하 여 세부 정보 갤러리가 더 이상 선택 되지 않도록 합니다.

## <a name="add-text-to-the-new-title-bar"></a>새 제목 표시줄에 텍스트 추가

1. **삽입** 탭에서 화면에 다른 레이블을 삽입 합니다.

    > [!div class="mx-imgBorder"]
    > ![Insert 레이블 ](media/northwind-orders-canvas-part3/details-19.png)

1. 두 번째 제목 표시줄에서 제품 그림 위의 새 레이블을 크기 조정 하 고 이동한 다음 **홈** 탭에서 텍스트 색을 흰색으로 변경 합니다.

1. 레이블의 텍스트를 두 번 클릭 한 다음 **Product**:를 입력 합니다.

    > [!div class="mx-imgBorder"]
    > 텍스트를 제품 ](media/northwind-orders-canvas-part3/details-20.png)에 ![Change 레이블

1. 제품 레이블을 복사 하 여 붙여넣고 수량 열 위의 복사본을 크기 조정 하 고 이동 합니다.

1. 새 레이블의 텍스트를 두 번 클릭 한 다음 **Quantity**를 입력 합니다.

    > [!div class="mx-imgBorder"]
    > 수량 ](media/northwind-orders-canvas-part3/details-21.png) 레이블 텍스트 ![Change

1. 수량 레이블을 복사 하 여 붙여넣은 다음 크기를 조정 하 고 단위 가격 열 위의 복사본을 이동 합니다.

1. 새 레이블의 텍스트를 두 번 클릭 한 다음 **Unit Price**를 입력 합니다.

    > [!div class="mx-imgBorder"]
    > 텍스트 ![Change 단위 가격 ](media/northwind-orders-canvas-part3/details-22.png)

1. 단가 레이블을 복사 하 여 붙여넣고 확장 된 가격 열 위의 복사본 크기를 조정 하 고 이동 합니다.

1. 새 레이블의 텍스트를 두 번 클릭 하 고 **확장**을 입력 합니다.

    > [!div class="mx-imgBorder"]
    > 확장 ](media/northwind-orders-canvas-part3/details-23.png) 레이블 텍스트 ![Change

## <a name="display-order-totals"></a>주문 합계 표시

1. 화면 아래쪽의 주문 합계를 위한 공간을 확보 하기 위해 세부 정보 갤러리의 높이를 줄입니다.

    > [!div class="mx-imgBorder"]
    > ![Shorten 주문-세부 정보 갤러리 ](media/northwind-orders-canvas-part3/sum-01.png)

1. 화면 중간에 제목 표시줄을 복사 하 여 붙여넣고 화면 아래쪽으로 복사를 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 제목 표시줄을 ![Copy 하 고 복사를 아래쪽 가장자리로 이동 ](media/northwind-orders-canvas-part3/sum-02.png)

1. 가운데 제목 표시줄에서 제품 레이블을 복사 하 여 붙여넣고 **수량** 열의 왼쪽에 있는 아래쪽 제목 표시줄로 복사본을 이동 합니다.

1. 새 레이블의 텍스트를 두 번 클릭 하 고 다음 텍스트를 입력 합니다.<br>**주문 합계:**

    > [!div class="mx-imgBorder"]
    > 주문 합계에 대 한 ![Add 레이블 ](media/northwind-orders-canvas-part3/sum-03.png)

1. 주문 합계 레이블을 복사 하 여 붙여넣은 다음 크기를 조정 하 고 주문 합계 레이블의 오른쪽으로 이동 합니다.

1. 새 레이블의 **Text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Sum( Gallery1.Selected.'Order Details', Quantity )
    ```

    이 수식에서는 위임 경고를 표시 하지만 단일 주문에 500 개 이상의 제품이 포함 되지 않기 때문에 무시 해도 됩니다.

1. **홈** 탭에서 새 레이블의 텍스트 맞춤을 **오른쪽**으로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 맞춤 ](media/northwind-orders-canvas-part3/sum-04.png)

1. 이 레이블 컨트롤을 복사 하 여 붙여넣고 **확장** 열의 크기를 조정 하 고 복사를 이동 합니다.

1. 복사의 **Text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Text( Sum( Gallery1.Selected.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    이 수식에서는 위임 경고를 표시 하지만 단일 주문에 500 개 이상의 제품이 포함 되지 않기 때문에 무시 해도 됩니다.

    > [!div class="mx-imgBorder"]
    > ![Show 총 주문 비용 ](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>새 세부 정보에 대 한 공간 추가

모든 갤러리에서 데이터를 표시할 수는 있지만 업데이트 하거나 레코드를 추가할 수는 없습니다. 세부 정보 갤러리에서 사용자가 **주문 정보** 엔터티의 레코드를 구성 하 고 해당 레코드를 주문에 삽입할 수 있는 영역을 추가 합니다.

1. 갤러리에서 단일 항목 편집 공간을 위한 공간을 확보 하기에 충분 한 정보 갤러리의 높이를 줄입니다.

    이 공간에서는 사용자가 주문 세부 정보를 추가할 수 있도록 컨트롤을 추가 합니다.

    > [!div class="mx-imgBorder"]
    > 세부 정보 갤러리를 ![Shorten ](media/northwind-orders-canvas-part3/add-details-01.png)

1. **삽입** 탭에서 레이블을 삽입 한 다음, 세부 정보 갤러리에서 크기를 조정 하 고 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 레이블 ![Insert ](media/northwind-orders-canvas-part3/add-details-02.png)

1. 새 레이블의 텍스트를 두 번 클릭 한 다음 Delete 키를 누릅니다.

1. **홈** 탭에서 새 레이블의 **채우기** 색을 **LightBlue**로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 레이블의 채우기 색을 연한 파랑 ](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="add-the-order-details-data-source"></a>주문 정보 데이터 원본 추가

1. **보기** 탭에서 **데이터 원본**을 선택 하 고 **데이터** 창에서 **데이터 원본 추가** 를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Add 데이터 소스 ](media/northwind-orders-canvas-part3/add-details-04.png)

1. **Common Data Service**선택:

    > [!div class="mx-imgBorder"]
    > ![Select Common Data Service ](media/northwind-orders-canvas-part3/add-details-05.png)

1. **데이터** 창의 맨 위에 있는 검색 상자에 **order** 를 입력 하 고 **order Details** 확인란을 선택한 다음 창의 맨 아래에서 **연결** 을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Specify Order details 엔터티 ](media/northwind-orders-canvas-part3/add-details-06.png)

    앱에 다른 데이터 소스를 추가 했습니다.

    > [!div class="mx-imgBorder"]
    > 데이터 원본 ![List ](media/northwind-orders-canvas-part3/add-details-07.png)

    앱이 일 대 다 관계를 통해 읽을 수 있지만 응용 프로그램에서 변경 내용을 다시 쓸 수 없기 때문에이 데이터 원본을 추가 해야 합니다. 앱에서 관련 엔터티를 직접 변경 해야 합니다.

1. **데이터** 창을 닫습니다.

## <a name="select-a-product"></a>제품 선택

1. **삽입** 탭에서 **컨트롤**  > **콤보 상자**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Insert 콤보 상자 ](media/northwind-orders-canvas-part3/add-details-08.png)

    [**콤보 상자**](controls/control-combo-box.md) 컨트롤이 왼쪽 위 모퉁이에 나타납니다.

1. 콤보 상자의 **Items** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > 콤보 상자의 Items 속성을 ![Set ](media/northwind-orders-canvas-part3/add-details-09.png)

    [**Choice**](functions/function-choices.md) 함수는 **Order Details** 엔터티의 **Product** 필드에 사용할 수 있는 모든 값의 테이블을 반환 합니다. 이 필드는 다 대 일 관계에서 조회 이므로 **선택 항목** 은 **Order Products** 엔터티의 모든 레코드를 반환 합니다.

    > [!NOTE]
    > 옵션 집합과 함께 **선택 항목** 을 사용 하 여 모든 옵션의 테이블을 반환할 수도 있습니다. 단계는이 접근 방식을 언급 하지 않았지만 요약 양식에 **주문 상태** 를 표시 하는 콤보 상자를 추가할 때 이미 사용 했습니다.

1. **데이터** 창에서 **주 텍스트** 목록을 열고 **nwind_productname**를 선택 합니다. 

1. **Searchfield** 목록을 열고 **nwind_productname**를 선택 합니다.

    이 경우 **데이터** 창에서 표시 이름을 지원 하지 않으므로 논리적 이름을 지정 합니다.

    > [!div class="mx-imgBorder"]
    > 콤보 상자에 대 한 기본 텍스트를 ![Set ](media/northwind-orders-canvas-part3/add-details-10.png)

1. **데이터** 창을 닫습니다.

1. 오른쪽 가장자리 근처의 **속성** 탭에서 아래로 스크롤하여 **다중 선택 허용**을 해제 하 고 **검색 허용** 이 설정 되어 있는지 확인 합니다.

    > [!div class="mx-imgBorder"]
    > 여러 선택을 ![Disable 하 고 검색을 사용 ](media/northwind-orders-canvas-part3/add-details-12.png)

1. 세부 정보 갤러리의 제품 이름 열 아래에서 콤보 상자를 크기 조정 하 고 밝은 파란색 영역으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![Move 콤보 상자 ](media/northwind-orders-canvas-part3/add-details-13.png)

    이 콤보 상자에서 사용자는 앱이 만들 **주문 정보** 레코드에 대 한 **제품** 엔터티의 레코드를 지정 합니다.

1. Alt 키를 누른 채 콤보 상자의 아래쪽 화살표를 선택 합니다.

    > [!TIP]
    > Alt 키를 누른 채 미리 보기 모드를 열지 않고 PowerApps Studio의 컨트롤과 상호 작용할 수 있습니다.

1. 표시 되는 제품 목록에서 제품을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 콤보 상자에 제품을 ![Select ](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>제품 이미지 추가

1. **삽입** 탭에서 **미디어**  > **이미지**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 이미지 컨트롤을 ![Insert ](media/northwind-orders-canvas-part3/add-details-15.png)

    [**이미지**](controls/control-image.md) 컨트롤이 왼쪽 위 모퉁이에 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 이미지 컨트롤의 ![Default 위치 ](media/northwind-orders-canvas-part3/add-details-16.png)

1. 이미지를 크기 조정 하 고 다른 제품 이미지 아래의 밝은 파란색 영역으로 이동 하 여 콤보 상자 옆에 이동 합니다.

1. 이미지의 **image** 속성을 다음과 같이 설정 합니다.

    ```powerapps-dot
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > 이미지의 이미지 속성을 ![Set ](media/northwind-orders-canvas-part3/add-details-17.png)

    요약 양식에 직원 그림을 표시 하는 데 사용한 것과 동일한 트릭을 사용 하 고 있습니다. 콤보 상자의 **선택** 된 속성은 **그림** 필드를 포함 하 여 사용자가 선택 하는 모든 제품의 전체 레코드를 반환 합니다.

## <a name="add-a-quantity-box"></a>수량 상자 추가

1. **삽입** 탭에서 **텍스트**  > **텍스트 입력**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Add 텍스트-입력 상자 ](media/northwind-orders-canvas-part3/add-details-18.png)

    [**텍스트 입력**](controls/control-text-input.md) 컨트롤이 왼쪽 위 모퉁이에 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 텍스트의 ![Default 위치-입력 상자 ](media/northwind-orders-canvas-part3/add-details-19.png)

1. 텍스트 상자 크기를 조정 하 고 세부 정보 갤러리의 quantity 열 아래에 있는 콤보 상자의 오른쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 텍스트 ![Resize 및 이동-입력 상자 ](media/northwind-orders-canvas-part3/add-details-20.png)

    이 텍스트 입력 상자를 사용 하 여 사용자는 **주문 정보** 레코드의 **수량** 필드를 지정 합니다.

1. 이 컨트롤의 **기본** 속성을 **""** 로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > 텍스트 입력 상자의 * * Default * * 속성을 ![Set ](media/northwind-orders-canvas-part3/add-details-21.png)

1. **홈** 탭에서이 컨트롤의 텍스트 맞춤을 **오른쪽**으로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 맞춤 ](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>단위 및 연장 가격 표시

1. **삽입** 탭에서 **레이블** 컨트롤을 삽입 합니다.

    레이블은 화면의 왼쪽 위 모퉁이에 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 레이블 ![Insert ](media/northwind-orders-canvas-part3/add-details-23.png)

1. 텍스트 입력 컨트롤의 오른쪽으로 레이블을 크기 조정 하 고 이동 하 고 레이블의 **text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Text( ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > 레이블의 텍스트 속성을 ![Set ](media/northwind-orders-canvas-part3/add-details-24.png)

    이 컨트롤은 **Order Products** 엔터티의 **정가를 표시 합니다.** 이 값은 **Order Details** 레코드에서 **Unit Price** 필드를 결정 합니다.

    > [!NOTE]
    > 이 시나리오의 경우이 값은 읽기 전용 이지만 다른 시나리오에서 앱 사용자에 대해를 호출 하 여 수정할 수 있습니다. 이 경우 **텍스트 입력** 컨트롤을 사용 하 고 **기본** 속성을 **가격 목록**으로 설정 합니다.

1. **홈** 탭에서 목록 가격 레이블의 텍스트 맞춤을 **오른쪽**으로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 맞춤 ](media/northwind-orders-canvas-part3/add-details-25.png)

1. 목록 가격 레이블을 복사 하 여 붙여넣은 다음 크기를 조정 하 고 목록 가격 레이블 오른쪽으로 이동 합니다.

1. 새 레이블의 **Text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > 새 레이블의 텍스트 속성을 ![Set ](media/northwind-orders-canvas-part3/add-details-27.png)

    이 컨트롤은 앱 사용자가 지정한 수량과 앱 사용자가 선택한 제품의 정가를 기준으로 하는 연장 된 가격을 표시 합니다. 앱 사용자에 게는 전적으로 정보를 제공 합니다.

1. 수량에 대 한 텍스트 입력 컨트롤을 두 번 클릭 한 다음 숫자를 입력 합니다.

    **확장** 된 가격 레이블은 새 값을 표시 하도록 다시 계산 됩니다.

    > [!div class="mx-imgBorder"]
    > 수량을 ![Specify 하 고 확장 된 가격을 표시 ](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>추가 아이콘 추가

1. **삽입** 탭에서 **아이콘** 을 선택 하  > **추가**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 아이콘 추가 ![Insert ](media/northwind-orders-canvas-part3/add-details-29.png)

    아이콘은 화면의 왼쪽 위 모퉁이에 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 추가 아이콘 ![Default 위치 ](media/northwind-orders-canvas-part3/add-details-30.png)

1. 이 아이콘의 크기를 조정 하 고 밝은 파란색 영역의 오른쪽 가장자리로 이동한 다음 아이콘의 **Onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Patch( 'Order Details',
        Defaults('Order Details'),
        {
            Order: Gallery1.Selected,
            Product: ComboBox1.Selected,
            Quantity: Value(TextInput1.Text),
            'Unit Price': ComboBox1.Selected.'List Price'
        }
    );
    Refresh( Orders );
    Reset( ComboBox1 );
    Reset( TextInput1 )
    ```

    > [!div class="mx-imgBorder"]
    > 아이콘의 OnSelect 속성을 ![Set ](media/northwind-orders-canvas-part3/add-details-31.png)

    일반적으로 [**Patch**](functions/function-patch.md) 함수는 레코드를 업데이트 하 고 만들며,이 수식의 특정 인수는 함수에서 수행 하는 정확한 변경 내용을 결정 합니다.

    - 첫 번째 인수는 함수에서 레코드를 업데이트 하거나 만들 데이터 원본 (이 경우 **Order Details** 엔터티)을 지정 합니다.
    - 두 번째 인수는 세 번째 인수에 달리 지정 되지 않은 경우 함수가 **Order Details** 엔터티의 기본값이 포함 된 레코드를 만들도록 지정 합니다.
    - 세 번째 인수는 새 레코드의 네 열이 사용자의 값을 포함 하도록 지정 합니다.

      - 주문 **열에** 는 사용자가 주문 갤러리에서 선택한 주문 번호가 포함 됩니다.
      - **Product** 열에는 제품을 표시 하는 콤보 상자에서 사용자가 선택한 제품의 이름이 포함 됩니다.
      - **Quantity** 열에는 사용자가 텍스트 입력 상자에 지정한 값이 포함 됩니다.
      - **단가** 열에는이 주문 세부 정보에 대해 사용자가 선택한 제품의 정가 가격이 포함 됩니다.

    > [!NOTE]
    > 제품을 표시 하는 콤보 상자에서 앱 사용자가 선택 하는 제품에 대 한 모든 열 ( **Order Products** 엔터티의)의 데이터를 사용 하는 수식을 작성할 수 있습니다. 사용자가 **Order Products** 엔터티의 레코드를 선택 하면 해당 콤보 상자에 제품의 이름만 표시 되 고 제품 단가도 레이블에 표시 됩니다. 캔버스 앱의 각 조회 값은 기본 키가 아니라 전체 레코드를 참조 합니다.

    **Refresh** 함수를 사용 하면 주문 **엔터티는 주문** **정보** 엔터티에 방금 추가한 레코드를 반영할 수 있습니다. **Reset** 함수는 제품, 수량 및 단가 데이터를 지워 동일한 순서로 다른 주문 세부 정보를 더 쉽게 만들 수 있습니다.

1. F5 키를 누른 다음 **추가** 아이콘을 선택 합니다.

    지정 된 정보를 반영 하는 순서는 다음과 같습니다.

    > [!div class="mx-imgBorder"]
    > 주문 세부 정보를 추가 ![Animation ](media/northwind-orders-canvas-part3/add-details.gif)

1. 필드 순서에 다른 항목을 추가 합니다.

1. Esc 키를 눌러 미리 보기 모드를 닫습니다.

## <a name="remove-an-order-detail"></a>주문 세부 정보 제거

1. 화면 가운데에서 세부 정보 갤러리의 템플릿을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 갤러리 템플릿 ![Select ](media/northwind-orders-canvas-part3/remove-details-01.png)

1. **삽입** 탭에서**휴지통** >  **아이콘** 을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 휴지통 아이콘 ![Insert ](media/northwind-orders-canvas-part3/remove-details-02.png)

    갤러리 템플릿의 왼쪽 위 모퉁이에 휴지통 아이콘이 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 아이콘의 ![Default 위치 ](media/northwind-orders-canvas-part3/remove-details-03.png)

1. 휴지통 아이콘의 크기를 조정 하 고 세부 정보 갤러리 템플릿의 오른쪽으로 이동한 다음 아이콘의 **Onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Remove( 'Order Details', ThisItem ); Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > 아이콘의 OnSelect 속성을 ![Set ](media/northwind-orders-canvas-part3/remove-details-04.png)

    이 문서를 작성할 당시에는 관계에서 직접 레코드를 제거할 수 없으므로 [**remove**](functions/function-remove-removeif.md) 함수는 관련 엔터티에서 직접 레코드를 제거 합니다. **ThisItem** 제거할 레코드를 지정 합니다. 세부 정보 갤러리에서 휴지통 아이콘이 표시 되는 동일한 레코드에서 가져옵니다.

    다시, 작업은 캐시 된 데이터를 사용 하므로 **Refresh** 함수는 앱이 관련 엔터티 중 하나를 변경 했음을 **주문** 엔터티에 알립니다.

1. F5 키를 눌러 미리 보기 모드를 연 다음 주문에서 제거 하려는 각 **주문 정보** 레코드 옆의 휴지통 아이콘을 선택 합니다.

1. 주문에서 다양 한 주문 정보를 추가 하 고 제거 해 보세요.

    > [!div class="mx-imgBorder"]
    > 주문 정보 추가 및 제거 ![Animation ](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>결론

요약 하자면 주문 세부 정보를 표시 하는 다른 갤러리를 추가 하 고 앱에서 주문 세부 정보를 추가 및 제거 하는 컨트롤을 추가 했습니다. 다음 요소를 사용 했습니다.

- 일 대 다 관계를 통해 주문 갤러리에 연결 된 두 번째 갤러리 컨트롤: **프로그램도 있습니다**  =  `Gallery1.Selected.'Order Details'`
- **Order Details** 엔터티에서 **order Products** 엔터티: `ThisItem.Product.'Product Name'` 및 `ThisItem.Product.Picture`에 대 한 다대일 관계
- 제품 목록을 가져오는 **선택** 함수: `Choices( 'Order Details'.Product' )`
- 다 대 일 관련 레코드로 전체 콤보 상자의 **선택** 된 속성: `ComboBox1.Selected.Picture` 및 `ComboBox1.Selected.'List Price'`
- **주문 정보** 레코드를 만드는 **Patch** 함수: `Patch( 'Order Details', Defaults( 'Order Details' ), ... )`
- **주문 정보** 레코드를 삭제 하는 **Remove** 함수: `Remove( 'Order Details', ThisItem )`

이 항목 시리즈는 교육용으로 캔버스 앱에서 Common Data Service 관계와 옵션 집합을 사용 하는 간단한 연습입니다. 앱을 프로덕션으로 릴리스 하기 전에 필드 유효성 검사, 오류 처리 및 기타 많은 요인을 고려해 야 합니다.
