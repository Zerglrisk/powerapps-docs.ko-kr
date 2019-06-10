---
title: 세부 정보 갤러리에서 캔버스 앱 만들기 | Microsoft Docs
description: Northwind Traders에 대 한 데이터를 관리 하는 캔버스 앱의 세부 정보 갤러리 만들기
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
ms.openlocfilehash: 9549b8f389cf696cf3fc8e4659da6b418383ac6e
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66760962"
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>캔버스 앱에서 세부 정보 갤러리 만들기

Northwind 데이터베이스에서 가상의 데이터를 관리 하는 것에 대 한 캔버스 앱에서 세부 정보 갤러리를 만드는 단계별 지침을 따릅니다. 이 항목은 Common Data Service의 관계형 데이터에서 비즈니스 앱을 빌드하는 방법을 설명 하는 시리즈의 일부입니다. 최상의 결과이 순서 대로 이러한 항목을 살펴봅니다.

1. [순서 갤러리 만들기](northwind-orders-canvas-part1.md)합니다.
1. [요약 양식을 만드는](northwind-orders-canvas-part2.md)합니다.
1. 세부 정보 갤러리 만들기 (**이 항목에서는**).

> [!div class="mx-imgBorder"]
> ![화면 영역 정의](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>필수 조건

이 항목에서는 시작 하기 전에이 항목의 앞부분에 설명 된 대로 데이터베이스를 설치 해야 합니다. 다음 순서 대로 갤러리를 만들고 요약 폼 하거나 엽니다는 **Northwind 주문 (캔버스)-3 부 시작** 이미 해당 갤러리 및 해당 폼을 포함 하는 앱입니다.

## <a name="create-another-title-bar"></a>다른 제목 표시줄 만들기

1. 화면 맨 위에 있는 선택 합니다 [ **레이블을** ](controls/control-text-box.md) 컨트롤 제목 표시줄을 담아 두는 Ctrl + C를 눌러 복사해 붙여 넣습니다: Ctrl을 눌러

    > [!div class="mx-imgBorder"]
    > ![복사 및 붙여넣기 제목 표시줄](media/northwind-orders-canvas-part3/details-01.png)

1. 크기를 조정 하 고 요약 폼 바로 아래에 나타나도록 복사본을 이동 합니다.

1. 이러한 방법 중 하나로 복사에서 텍스트를 제거 합니다.

    - 선택한 텍스트를 두 번 클릭 하 고 Delete 키를 누릅니다.
    - 레이블 설정 **텍스트** 속성을 빈 문자열 ( **""** ).

    > [!div class="mx-imgBorder"]
    > ![제목 표시줄 복사본에서 텍스트를 제거 합니다.](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>갤러리 추가

1. 삽입 된 [ **갤러리** ](controls/control-gallery.md) 컨트롤을 **빈 세로** 레이아웃:

    > [!div class="mx-imgBorder"]
    > ![비어 있는 세로 갤러리 추가](media/northwind-orders-canvas-part3/details-03.png)

    주문 세부 정보를 보여 주는 새 갤러리 왼쪽 위 모퉁이에 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![주문 세부 정보 갤러리의 기본 위치](media/northwind-orders-canvas-part3/details-04.png)

1. 닫기 합니다 **데이터** 창 및 다음 크기 조정 및 오른쪽 아래 모퉁이 있는 새 제목 표시줄 아래에 자세히 갤러리 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![주문 세부 정보 갤러리의 최종 위치](media/northwind-orders-canvas-part3/details-05.png)

1. 설정 된 **항목** 을 다음이 수식으로 자세히 갤러리의 속성:

    ```powerapps-dot
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![세부 정보 갤러리의 Items 속성 설정](media/northwind-orders-canvas-part3/details-06.png)

    오류가 나타나면 확인 순서 갤러리 라고 **Gallery1** (에 **트리 보기** 창 왼쪽된 가장자리 근처). 갤러리 이름이 다른 경우 이름 바꾸기 **Gallery1**합니다.

    방금 두 갤러리를 연결 했습니다. 사용자가 순서 갤러리의 순서를 선택 하면 해당 선택의 레코드를 식별 합니다 **주문** 엔터티. 경우 순서에는 하나 이상의 줄 항목의 레코드를는 **주문** 엔터티에 하나 이상의 레코드에 연결 된 합니다 **Order details** 엔터티와 해당 레코드에서에서 데이터를 자세히 갤러리에 나타납니다. 이 동작 사이 만들어진에 일 대 다 관계를 반영 합니다 **주문** 및 **Order Details** 엔터티. 지정 된 수식 "설명" 관계 점 표기법을 사용 하 여:

    > [!div class="mx-imgBorder"]
    > ![Order Details 엔터티의 주문 엔터티 사이 일 대 다 관계](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>제품 이름 표시

1. 세부 정보 갤러리에서 선택 **삽입 탭에서 항목 추가** 갤러리 템플릿이 선택:

    > [!div class="mx-imgBorder"]
    > ![세부 정보 갤러리에 대 한 템플릿 선택](media/northwind-orders-canvas-part3/details-07.png)

    갤러리 자체 대신 갤러리 템플릿이 선택 했는지 확인 합니다. 경계 상자는 갤러리의 경계 내 고 갤러리의 높이 보다 짧은 아마도 약간 이어야 합니다. 이 템플릿에 컨트롤을 삽입 하는 대로 해당 갤러리의 각 항목에 대해 반복 됩니다.

1. 에 **삽입** 탭, 세부 정보 갤러리에 레이블을 삽입 합니다.

    레이블을은 갤러리; 내에 표시 됩니다. 그렇지 않은 경우 다시 시도 하지만 레이블을 삽입 하기 전에 갤러리의 템플릿을 선택 해야 합니다.

    > [!div class="mx-imgBorder"]
    > ![레이블을 갤러리에 추가 세부 정보](media/northwind-orders-canvas-part3/details-08.png)

1. 새 레이블 설정 **텍스트** 속성을 다음이 수식:

    ```powerapps-dot
    ThisItem.Product.'Product Name'
    ```

    텍스트가 있으면 선택에 대 한 화살표 **순서 0901** 순서 갤러리 아래쪽 합니다.

1. 전체 텍스트가 표시 되도록 레이블의 크기를 조정 합니다.

    > [!div class="mx-imgBorder"]
    > ![주문 세부 정보에서 제품 이름 표시](media/northwind-orders-canvas-part3/details-09.png)

    레코드에서이 식에 설명 합니다 **Order Details** 엔터티. 레코드에 저장 된 **ThisItem** 조치를 합니다 **주문 제품** 다 대 일 관계를 통해 엔터티:

    > [!div class="mx-imgBorder"]
    > ![Order Details 엔터티 및 주문 제품 엔터티 간의 다 대 일 관계](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    합니다 **Product Name** 필드 (및 다른 필드를 사용 하려는) 추출 됩니다.

    > [!div class="mx-imgBorder"]
    > ![순서 Products 엔터티에서 필드](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>제품 이미지를 표시 합니다.

1. 에 **삽입** 탭에서 삽입을 [ **이미지** ](controls/control-image.md) 세부 갤러리 컨트롤:

    > [!div class="mx-imgBorder"]
    > ![이미지 컨트롤 삽입](media/northwind-orders-canvas-part3/details-10.png)

1. 크기 조정 및 이미지와 함께 되도록 레이블을 이동 합니다.

    > [!TIP]
    > 크기와 컨트롤의 위치를 통해 세분화 된 컨트롤에 대 한 크기를 조정 하거나 Alt 키를 누르지 않고 이동 시작한 다음 계속 해 서 크기를 조정 하거나 Alt 키를 누른 동안 컨트롤을 이동:

    > [!div class="mx-imgBorder"]
    > ![이미지 컨트롤 이동](media/northwind-orders-canvas-part3/details-11.png)

1. 이미지의 설정 **이미지** 속성을 다음이 수식:

    ```powerapps-dot
    ThisItem.Product.Picture
    ```

    마찬가지로이 연관 된 제품 참조 식은 주문 세부 정보 및 추출 합니다 **그림** 표시할 필드입니다.

    > [!div class="mx-imgBorder"]
    > ![제품 이미지를 표시 합니다.](media/northwind-orders-canvas-part3/details-12.png)

1. 따라서 해당 둘 이상의 갤러리의 템플릿의 높이 줄이려면 **Order Detail** 레코드는 한 번에 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![갤러리의 템플릿에 단축](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>제품 수량 및 비용 표시

1. 에 **삽입** 탭 다른 레이블을를 삽입 세부 갤러리 및 다음 크기를 조정 하 고 새 레이블을 제품 정보의 오른쪽으로 이동 합니다.

1. 새 레이블 설정 **텍스트** 속성을이 식:

    ```powerapps-dot
    ThisItem.Quantity
    ```

    이 수식에서 직접 정보를 가져오는 합니다 **Order Details** 엔터티 (관계 필요).

    > [!div class="mx-imgBorder"]
    > ![제품 수량을 표시](media/northwind-orders-canvas-part3/details-13b.png) 

1. 에 **Home** 탭에서이 컨트롤의 맞춤을 변경 **오른쪽**:

    > [!div class="mx-imgBorder"]
    > ![맞춤 변경](media/northwind-orders-canvas-part3/details-14.png)

1. 에 **삽입** 탭 다른 레이블을를 삽입 세부 갤러리 및 다음 크기를 조정 하 고 레이블을 수량 레이블의 오른쪽으로 이동 합니다.

1. 새 레이블 설정 **텍스트** 속성을 다음이 수식:

    ```powerapps-dot
    Text( ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    언어 태그를 포함 하지 않는 경우 ( **[$-EN-US]** ), 언어 및 지역에 따라 추가 됩니다. 제거 하려는 다양 한 언어 태그를 사용 하는 경우는 **$** 닫는 대괄호 바로 뒤 ( **]** ), 한 다음 해당 위치에서 고유한 통화 기호를 추가 합니다.

    > [!div class="mx-imgBorder"]
    > ![표시 단위 가격](media/northwind-orders-canvas-part3/details-15.png)

1. 에 **Home** 탭에서이 컨트롤의 맞춤을 변경 **오른쪽**:

    > [!div class="mx-imgBorder"]
    > ![맞춤 변경](media/northwind-orders-canvas-part3/details-16.png)

1. 에 **삽입** 탭, 세부 갤러리에 다른 레이블 컨트롤을 삽입 한 다음 크기를 조정 및 단가의 오른쪽에 새 레이블을 이동 합니다.

1. 새 레이블 설정 **텍스트** 속성을 다음이 수식:

    ```powerapps-dot
    Text( ThisItem.Quantity * ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    마찬가지로 언어 태그를 포함 하지 않는 경우 ( **[$-EN-US]** ), 언어 및 지역에 따라 추가 됩니다. 대신 사용자 고유의 통화 기호를 사용 하려는 태그와 다른 경우는 **$** 닫는 대괄호 바로 뒤 ( **]** ).

    > [!div class="mx-imgBorder"]
    > ![확장된 가격 표시](media/northwind-orders-canvas-part3/details-17.png)

1. 에 **Home** 탭에서이 컨트롤의 맞춤을 변경 **오른쪽**:

    > [!div class="mx-imgBorder"]
    > ![맞춤 변경](media/northwind-orders-canvas-part3/details-18.png)

    지금은 세부 갤러리에 컨트롤 추가 완료 합니다.

1. 에 **트리 보기** 창 **Screen1** 세부 갤러리 더 이상 선택 되어 있는지 확인 합니다.

## <a name="add-text-to-the-new-title-bar"></a>새 제목 표시줄에 텍스트 추가

1. 에 **삽입** 탭에서 화면에 다른 레이블 삽입 합니다.

    > [!div class="mx-imgBorder"]
    > ![레이블 삽입](media/northwind-orders-canvas-part3/details-19.png)

1. 크기를 조정 하 고 제품의 사진 위에 새 레이블을 이동 하 고 두 번째 제목 표시줄에 다음에 흰색 텍스트의 색을 변경 합니다 **홈** 탭 합니다.

1. 레이블의 텍스트를 두 번 클릭 한 다음 입력 **제품**:

    > [!div class="mx-imgBorder"]
    > ![제품에 레이블 텍스트를 변경 합니다.](media/northwind-orders-canvas-part3/details-20.png)

1. 복사 및 제품 레이블을 붙여 및 다음 크기 조정 및 복사본을 quantity 열 위에 이동 합니다.

1. 새 레이블 텍스트를 두 번 클릭 한 다음 입력 **수량**:

    > [!div class="mx-imgBorder"]
    > ![레이블 텍스트 수량 변경](media/northwind-orders-canvas-part3/details-21.png)

1. 복사 및 수량 레이블 및 다음 크기 조정 붙여넣고-단가 열 위에 복사본을 이동 합니다.

1. 새 레이블 텍스트를 두 번 클릭 한 다음 입력 **단가**:

    > [!div class="mx-imgBorder"]
    > ![Unit Price를 레이블 텍스트를 변경 합니다.](media/northwind-orders-canvas-part3/details-22.png)

1. 복사 및 단가 레이블을 붙여 및 다음 크기 조정 및 확장 가격 열 위에 복사본을 이동 합니다.

1. 새 레이블 텍스트를 두 번 클릭 한 다음 입력 **확장**:

    > [!div class="mx-imgBorder"]
    > ![확장으로 레이블 텍스트를 변경 합니다.](media/northwind-orders-canvas-part3/details-23.png)

## <a name="display-order-totals"></a>주문 합계를 표시 합니다.

1. 화면 맨 아래에 주문 합계에 대 한 공간을 만들기 위해 세부 정보 갤러리의 높이 줄이려면:

    > [!div class="mx-imgBorder"]
    > ![주문 세부 정보 갤러리를 단축 합니다.](media/northwind-orders-canvas-part3/sum-01.png)

1. 복사 하 고 화면 가운데에서 제목 표시줄을 붙여 다음 화면 맨 아래에 복사본을 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![제목 표시줄을 복사 하 고 아래쪽 가장자리에 복사본을 이동](media/northwind-orders-canvas-part3/sum-02.png)

1. 가운데 제목 표시줄의 제품 레이블과 복사 및 붙여넣고 다음 아래쪽 제목 표시줄의 왼쪽에만 복사본을 이동 합니다 **수량** 열입니다.

1. 새 레이블 텍스트를 두 번 클릭 하 고이 텍스트를 입력 합니다.<br>**주문 합계:**

    > [!div class="mx-imgBorder"]
    > ![주문 합계에 대 한 레이블 추가](media/northwind-orders-canvas-part3/sum-03.png)

1. 복사 및 주문 합계 레이블 및 다음 크기 조정 붙여넣고 주문 합계 레이블의 오른쪽에 복사본을 이동 합니다.

1. 새 레이블 설정 **텍스트** 속성을 다음이 수식:

    ```powerapps-dot
    Sum( Gallery1.Selected.'Order Details', Quantity )
    ```

    이 수식은 위임 경고를 표시 하지만 단일 순서 없이 500 개가 넘는 제품에 포함 되므로 무시할 수 있습니다.

1. 에 **Home** 탭에서 새 레이블 텍스트 맞춤을 설정 **오른쪽**:

    > [!div class="mx-imgBorder"]
    > ![맞춤 변경](media/northwind-orders-canvas-part3/sum-04.png)

1. 복사 및이 레이블 컨트롤 붙여넣기 및 다음 크기 조정 및 이동에서 복사 합니다 **확장** 열입니다.

1. 복사본의 설정 **텍스트** 속성을 다음이 수식:

    ```powerapps-dot
    Text( Sum( Gallery1.Selected.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    이 수식은 위임 경고를 표시 하지만 단일 순서 없이 500 개가 넘는 제품에 포함 되므로 무시할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > ![주문의 총 비용이 표시](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>새로운 세부 정보에 대 한 공간 추가

모든 갤러리에서 데이터를 표시할 수 있지만 업데이트 하거나 레코드를 추가할 수 없습니다. 자세히 갤러리에서 사용자의 레코드를 구성할 수 있는 영역 추가 합니다 **Order Details** 엔터티 및 주문으로 기록 하는 insert.

1. 갤러리에서 단일 항목 편집 공간에 대 한 공간을 만들기 위해 충분 한 세부 정보 갤러리의 높이 줄입니다.

    이 공간에 추가할 컨트롤 사용자는 주문 세부 정보를 추가할 수 있도록 합니다.

    > [!div class="mx-imgBorder"]
    > ![세부 정보 갤러리를 단축 합니다.](media/northwind-orders-canvas-part3/add-details-01.png)

1. 에 **삽입** 탭, 레이블, 삽입 및 다음 크기 조정 및 세부 갤러리 아래로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![레이블 삽입](media/northwind-orders-canvas-part3/add-details-02.png)

1. 새 레이블 텍스트를 두 번 클릭 하 고 Delete 키를 누릅니다.

1. 에 **홈** 탭에서 새 레이블의 **채우기** 색 **LightBlue**:

    > [!div class="mx-imgBorder"]
    > ![연한 파란색 레이블의 채우기 변경](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="add-the-order-details-data-source"></a>주문 세부 정보 데이터 원본 추가

1. 에 **뷰** 탭을 선택 **데이터 원본**를 선택한 후 **데이터 원본 추가** 에 **데이터** 창:

    > [!div class="mx-imgBorder"]
    > ![데이터 소스 추가](media/northwind-orders-canvas-part3/add-details-04.png)

1. 선택 **Common Data Service**:

    > [!div class="mx-imgBorder"]
    > ![Common Data Service를 선택 합니다.](media/northwind-orders-canvas-part3/add-details-05.png)

1. 맨 위에 있는 **데이터** 창, 형식 **순서** 검색 상자에서 선택 합니다 **Order Details** 확인란을 선택한 후 **연결** 에 창의 아래쪽:

    > [!div class="mx-imgBorder"]
    > ![Order details 엔터티를 지정 합니다.](media/northwind-orders-canvas-part3/add-details-06.png)

    방금 추가한 다음 다른 데이터 원본 앱:

    > [!div class="mx-imgBorder"]
    > ![데이터 원본 목록](media/northwind-orders-canvas-part3/add-details-07.png)

    앱에 일 대 다 관계를 통해 읽을 수 있지만 앱 수 없습니다. 아직 변경 내용을 다시 작성 하기 때문에이 데이터 소스를 추가 해야 합니다. 앱 관련된 엔터티를 사용 하 여 직접 변경 해야 합니다.

1. 닫기 합니다 **데이터** 창입니다.

## <a name="select-a-product"></a>제품 선택

1. 에 **삽입** 탭을 선택 **컨트롤** > **콤보 상자**:

    > [!div class="mx-imgBorder"]
    > ![콤보 상자 삽입](media/northwind-orders-canvas-part3/add-details-08.png)

    합니다 [ **콤보 상자** ](controls/control-combo-box.md) 컨트롤 왼쪽 위 모퉁이에 나타납니다.

1. 콤보 상자의 설정할 **항목** 속성을 다음이 수식:

    ```powerapps-dot
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > ![콤보 상자의 항목 속성 설정](media/northwind-orders-canvas-part3/add-details-09.png)

    [ **선택** ](functions/function-choices.md) 함수에 대 한 가능한 모든 값의 테이블을 반환 합니다 **제품** 필드에 **Order Details** 엔터티. 이므로이 필드는 다 대 일 관계에서 조회 **선택** 의 모든 레코드를 반환 합니다 **주문 제품** 엔터티.

    > [!NOTE]
    > 사용할 수도 있습니다 **선택** 옵션 집합이 모든 옵션의 테이블을 반환 합니다. 콤보 상자에 추가 했을 때 이미 사용 하지만 단계는이 방법은 언급 하지 않았습니다 **주문 상태** 요약 형식에서입니다.

1. 에 **데이터** 창 열기를 **기본 텍스트** 목록 및 선택한 **nwind_productname**합니다. 

1. 엽니다는 **SearchField** 목록을 선택한 후 **nwind_productname**합니다.

    때문에 논리적 이름을 지정 합니다 **데이터** 창 아직 표시 이름이이 사례에서 지원 하지 않습니다.

    > [!div class="mx-imgBorder"]
    > ![콤보 상자에 대 한 기본 텍스트를 설정 합니다.](media/northwind-orders-canvas-part3/add-details-10.png)

1. 닫기 합니다 **데이터** 창입니다.

1. 에 **속성** 오른쪽 가장자리 근처에서 탭, 아래로 스크롤하여 해제 **다중 선택을 허용**, 되어 있는지 확인 하 고 **허용 검색** 켜져:

    > [!div class="mx-imgBorder"]
    > ![다중 선택을 사용 하지 않도록 설정 하 고 검색을 사용 하도록 설정](media/northwind-orders-canvas-part3/add-details-12.png)

1. 크기 조정 및 콤보 상자를 자세히 갤러리에서 product name 열 바로 아래 연한 파랑 영역으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![콤보 상자를 이동 합니다.](media/northwind-orders-canvas-part3/add-details-13.png)

    이 콤보 상자에서 사용자의 레코드를 지정 합니다는 **제품** 에 대 한 엔터티를 **Order Details** 앱을 통해 생성 되는 레코드입니다.

1. Alt 키를 누른 채 콤보 상자의 아래쪽 화살표를 선택 합니다.

    > [!TIP]
    > Alt 키를 눌러 미리 보기 모드를 열지 않고 PowerApps Studio 컨트롤을 조작할 수 있습니다.

1. 제품 목록이 표시 되는 제품을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![콤보 상자에서 제품을 선택 합니다.](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>제품 이미지를 추가 합니다.

1. 에 **삽입** 탭을 선택 **Media** > **이미지**:

    > [!div class="mx-imgBorder"]
    > ![이미지 컨트롤 삽입](media/northwind-orders-canvas-part3/add-details-15.png)

    합니다 [ **이미지** ](controls/control-image.md) 컨트롤 왼쪽 위 모퉁이에 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![이미지 컨트롤의 기본 위치](media/northwind-orders-canvas-part3/add-details-16.png)

1. 크기를 조정 하 고 다른 제품 이미지 및 콤보 상자 옆에 있는 밝은 파란색 영역에 이미지를 이동 합니다.

1. 설정 된 **이미지** 이미지의 속성:

    ```powerapps-dot
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![이미지의 이미지 속성 설정](media/northwind-orders-canvas-part3/add-details-17.png)

    사용 하는 동일한 트릭 요약 형태로 직원 그림을 표시 하는 데 있습니다. **선택한** 콤보 상자의 속성을 포함 하는 사용자가 선택 하는 모든 제품의 전체 레코드를 반환 합니다 **그림** 필드입니다.

## <a name="add-a-quantity-box"></a>수량 상자 추가

1. 에 **삽입** 탭을 선택 **텍스트** > **텍스트 입력**:

    > [!div class="mx-imgBorder"]
    > ![텍스트 입력 상자를 추가 합니다.](media/northwind-orders-canvas-part3/add-details-18.png)

    합니다 [ **텍스트 입력** ](controls/control-text-input.md) 컨트롤 왼쪽 위 모퉁이에 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![텍스트 입력 상자의 기본 위치](media/northwind-orders-canvas-part3/add-details-19.png)

1. 조정 하 고 콤보 상자의 자세히 갤러리에 있는 quantity 열의 오른쪽에 텍스트 입력 상자를 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![크기 조정 및 텍스트 입력 상자를 이동 합니다.](media/northwind-orders-canvas-part3/add-details-20.png)

    이 텍스트 입력 상자를 사용 하 여 사용자 지정 합니다 **수량** 필드를 **Order Details** 레코드입니다.

1. 설정 된 **기본** 이 컨트롤의 속성 **""** :

    > [!div class="mx-imgBorder"]
    > ![설정의 * * 기본 * * 속성의 텍스트 입력 상자](media/northwind-orders-canvas-part3/add-details-21.png)

1. 에 **홈** 탭에서이 컨트롤의 텍스트 맞춤 **오른쪽**:

    > [!div class="mx-imgBorder"]
    > ![맞춤 변경](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>단위 및 확장된 가격 표시

1. 에 **삽입** 탭에서 삽입을 **레이블** 제어 합니다.

    화면의 왼쪽 위 모퉁이에 레이블이 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![레이블 삽입](media/northwind-orders-canvas-part3/add-details-23.png)

1. 크기를 조정 하 고 레이블 텍스트 입력 컨트롤의 오른쪽으로 이동 합니다. 레이블 설정 **텍스트** 속성을 다음이 수식:

    ```powerapps-dot
    Text( ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![레이블의 텍스트 속성 설정](media/northwind-orders-canvas-part3/add-details-24.png)

    이 컨트롤이 표시 합니다 **정가** 에서 **주문 제품** 엔터티. 이 값에 따라 결정 됩니다는 **Unit Price** 필드를 **Order Details** 레코드입니다.

    > [!NOTE]
    > 이 시나리오에 대 한 값을 읽기 전용 이지만 수정할 앱 사용자에 대 한 다른 시나리오를 호출할 수 있습니다. 사용 하 여 이런 경우는 **텍스트 입력** 설정 해당 **기본** 속성을 **정가**합니다.

1. 에 **홈** 탭에서 목록 가격 레이블의 텍스트 맞춤 **오른쪽**:

    > [!div class="mx-imgBorder"]
    > ![맞춤 변경](media/northwind-orders-canvas-part3/add-details-25.png)

1. 복사 및 목록 가격 레이블 및 다음 크기 조정 붙여넣고 가격 레이블의 오른쪽에 복사본을 이동 합니다.

1. 새 레이블 설정 **텍스트** 속성을 다음이 수식:

    ```powerapps-dot
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![새 레이블의 텍스트 속성 설정](media/northwind-orders-canvas-part3/add-details-27.png)

    이 컨트롤에는 앱 사용자 지정 하는 수량 및 앱 사용자가 선택한 제품의 가격에 따라 확장된 가격 보여 줍니다. 이 앱 사용자에 대 한 정보로 합니다.

1. 수량에 대 한 텍스트 입력 컨트롤을 두 번 클릭 하 고 숫자를 입력 합니다.

    합니다 **확장** 가격 레이블 새 값을 표시 하는 다시 계산 됩니다.

    > [!div class="mx-imgBorder"]
    > ![수량 지정 및 확장된 가격 표시](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>추가 아이콘 추가

1. 에 **삽입** 탭을 선택 **아이콘** > **추가**:

    > [!div class="mx-imgBorder"]
    > ![Insert 추가 아이콘](media/northwind-orders-canvas-part3/add-details-29.png)

    화면의 왼쪽 위 모서리에 아이콘이 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![추가 아이콘의 기본 위치](media/northwind-orders-canvas-part3/add-details-30.png)

1. 연한 파랑 영역의 오른쪽 가장자리로 이동이 아이콘 및 설정한 다음 아이콘의 크기를 조정 **OnSelect** 속성을 다음이 수식:

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
    > ![아이콘의 OnSelect 속성 설정](media/northwind-orders-canvas-part3/add-details-31.png)

    일반적으로 [ **패치** ](functions/function-patch.md) 이 수식에 인수를 함수 되도록 정확한 변경 내용을 확인 하 고 함수를 업데이트 하 고 레코드를 만듭니다.

    - 데이터 소스를 지정 하는 첫 번째 인수 (이 경우에 **Order Details** 엔터티)에 함수를 업데이트 하거나 레코드를 만듭니다.
    - 두 번째 인수는 함수에 대 한 기본값을 사용 하 여 레코드에서 생성 됩니다 지정 합니다 **Order Details** 엔터티 세 번째 인수에 지정 하지 않으면.
    - 세 번째 인수는 새 레코드에는 사용자의 값이 포함 됩니다는 지정 합니다.

      - 합니다 **순서** 열 순서 갤러리에서 선택한 사용자는 주문의 수를 포함 합니다.
      - 합니다 **제품** 열에는 콤보 상자에서 선택한 사용자는 제품을 표시 하는 제품의 이름이 포함 됩니다.
      - 합니다 **수량** 열 텍스트 입력 상자에 사용자 지정 된 값이 포함 됩니다.
      - 합니다 **단가** 열이 주문 세부 정보에 대 한 사용자가 선택한 제품의 가격에 포함 됩니다.

    > [!NOTE]
    > 모든 열에서 데이터를 사용 하는 수식을 빌드할 수 있습니다 (에 **주문 제품** 엔터티) 어떤 제품에 대 한 앱 사용자가 제품을 보여주는 콤보 상자입니다. 사용자가 레코드를 선택 하는 경우는 **주문 제품** 엔터티를 제품의 이름은 해당 콤보 상자에 표시 뿐 아니라 제품의 단가 레이블을에 표시 됩니다. 캔버스 앱에서 각 조회 값을 기본 키만이 아니라 전체 레코드를 참조합니다.

    **새로 고침** 함수는 **주문** 엔터티 레코드에 방금 추가한를 반영 합니다 **Order Details** 엔터티. 합니다 **재설정** 함수를 동일한 순서에 대 한 다른 주문 세부 정보를 더 쉽게 개발할 수 있도록 제품, 수량 및 단가 데이터를 지웁니다.

1. F5 키를 누른 다음을 선택 합니다 **추가** 아이콘입니다.

    순서 지정 된 정보를 반영 합니다.

    > [!div class="mx-imgBorder"]
    > ![주문 세부 정보를 추가 하는 애니메이션](media/northwind-orders-canvas-part3/add-details.gif)

1. (선택 사항) 순서에 다른 항목을 추가 합니다.

1. Esc 키를 눌러 미리 보기 모드를 닫습니다.

## <a name="remove-an-order-detail"></a>주문 세부 정보를 제거 합니다.

1. 센터 화면에서 세부 정보 갤러리의 템플릿을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![갤러리 템플릿이 선택](media/northwind-orders-canvas-part3/remove-details-01.png)

1. 에 **삽입** 탭을 선택 **아이콘** > **휴지통**:

    > [!div class="mx-imgBorder"]
    > ![휴지통 아이콘을 삽입 합니다.](media/northwind-orders-canvas-part3/remove-details-02.png)

    템플릿 갤러리의 왼쪽 위 모서리에서 휴지통 아이콘 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![아이콘의 기본 위치](media/northwind-orders-canvas-part3/remove-details-03.png)

1. 크기 조정 세부 갤러리 템플릿의 오른쪽에 있는 휴지통 아이콘을 이동 하 고 아이콘의 설정 **OnSelect** 속성을 다음이 수식:

    ```powerapps-dot
    Remove( 'Order Details', ThisItem ); Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![아이콘의 OnSelect 속성 설정](media/northwind-orders-canvas-part3/remove-details-04.png)

    이 문서의 작성 시점 현재 관계를 통해 레코드를 제거할 수 없습니다 때문 [ **제거** ](functions/function-remove-removeif.md) 함수는 관련 엔터티에서 직접 레코드를 제거 합니다. **ThisItem** 휴지통 아이콘 나타나는 정보 갤러리에서 동일한 레코드에서 가져온 레코드를 제거 하려면 지정 합니다.

    작업에서는 캐시 된 데이터를 다시 하므로 **새로 고침** 함수에 알립니다 합니다 **주문** 엔터티는 앱이 변경 되었음을 해당 관련된 엔터티 중 하나입니다.

1. 미리 보기 모드를 연 다음 각 옆에 있는 휴지통 아이콘을 선택 하는 F5 키를 눌러 **Order Details** 순서에서 제거 하려는 레코드입니다.

1. 추가 하거나 주문에서 다양 한 주문 세부 정보를 제거 합니다.

    > [!div class="mx-imgBorder"]
    > ![애니메이션을 추가 하 고 주문 세부 정보를 제거 합니다.](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>결론적

정리 하자면, 주문 세부 정보 및 추가 하 고 앱에는 주문 세부 정보를 제거 하는 컨트롤을 표시 하도록 다른 갤러리 추가 했습니다. 이러한 요소를 사용 했습니다.

- 갤러리 컨트롤을 두 번째에 일 대 다 관계를 통해 순서 갤러리에 연결 합니다. **Gallery2.Items** = `Gallery1.Selected.'Order Details'`
- 다 대 일 관계를 **Order Details** 엔터티를 합니다 **주문 제품** 엔터티: `ThisItem.Product.'Product Name'` 및 `ThisItem.Product.Picture`
- 합니다 **선택** 함수 제품의 목록을 가져오려면: `Choices( 'Order Details'.Product' )`
- 합니다 **선택한** 를 완료 하려면 다도 콤보 상자의 속성 관련 레코드: `ComboBox1.Selected.Picture` 및 `ComboBox1.Selected.'List Price'`
- 합니다 **패치** 만들려는 함수는 **Order Details** 레코드: `Patch( 'Order Details', Defaults( 'Order Details' ), ... )`
- **제거할** 함수를 삭제 하는 **Order Details** 레코드: `Remove( 'Order Details', ThisItem )`

이 일련의 항목 Common Data Service 관계를 사용 하 여 빠른 연습은 되었으며 교육용 캔버스 앱에서 옵션을 설정 합니다. 모든 프로덕션 앱을 릴리스하기 전에 필드 유효성 검사, 오류 처리 및 기타 많은 요소를 고려해 야 합니다.
