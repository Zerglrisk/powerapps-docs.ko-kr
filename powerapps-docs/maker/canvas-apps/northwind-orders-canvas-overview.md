---
title: Northwind Traders 용 캔버스 앱 개요 | Microsoft Docs
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48966659ca12ada12448543492731fff8431fbde
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "71995823"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Northwind Traders 용 캔버스 앱 개요

[환경에 설치한](northwind-install.md)Northwind Traders 데이터베이스의 관계형 데이터를 관리 하기 위한 캔버스 앱에 대해 알아봅니다. 그런 다음, 다음 항목의 단계별 지침에 따라이 앱을 처음부터 작성 하 여 관계형 데이터를 사용 하는 실무 경험을 얻을 수 있습니다.

이 항목에서는 다음을 검색 합니다.

- 앱 사용자가 앱에서 관계형 데이터를 표시 하 고 관리 하는 방법입니다.
- 앱을 구동 하는 데이터 형식입니다.
- 이러한 데이터 형식 간의 관계를 만드는 방법입니다.

단일 화면에서 앱 사용자는 주문을 표시, 업데이트, 만들기 및 삭제할 수 있습니다.

> [!div class="mx-imgBorder"]
> ![Complete canvas 앱 ](media/northwind-orders-canvas-part1/orders-finished.png)

## <a name="explore-the-user-interface"></a>사용자 인터페이스 탐색

### <a name="order-gallery"></a>주문 갤러리

앱의 왼쪽 가장자리에서 갤러리는 주문 번호, 상태, 고객 이름 및 주문의 총 비용을 포함 한 주문 목록을 표시 합니다. 사용자는 목록을 스크롤하여 주문을 찾은 다음 주문 화살표를 선택 하 여이에 대 한 자세한 정보를 표시할 수 있습니다. 추가 정보: [주문 갤러리 만들기](northwind-orders-canvas-part1.md)

### <a name="summary-form"></a>요약 양식

오른쪽 위 모서리에서 폼은 주문 갤러리에서 사용자가 선택한 순서를 요약 합니다. 요약에는 갤러리와 동일한 정보가 대부분 포함 되어 있지만 요약에는 주문이 생성 되 고 지불 된 날짜 뿐만 아니라 주문을 관리 하는 직원의 이름 및 사진이 표시 됩니다. 사용자는 제목 표시줄의 오른쪽 가장자리 근처에 있는 아이콘을 선택 하 여 양식의 데이터를 변경 하거나, 해당 변경 내용을 저장 하거나, 취소 하거나, 순서를 삭제할 수 있습니다. 추가 정보: [요약 양식을 만듭니다](northwind-orders-canvas-part2.md).

### <a name="detail-gallery"></a>세부 정보 갤러리

오른쪽 아래 모서리에는 선택한 주문에 포함 된 제품 및 수량에 대 한 정보가 표시 됩니다. 이 갤러리의 각 항목을 주문 세부 정보 라고 합니다. 앱 사용자는 그 아래에 있는 컨트롤을 사용 하 여 갤러리의 모든 항목을 추가 하 고 삭제할 수 있습니다. 추가 정보: [세부 정보 갤러리를 만듭니다](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> 화면 영역의 ![Definition ](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>데이터 원본 탐색

이 앱을 만들려면 5 개 엔터티와 옵션 집합의 데이터를 표시 합니다. 실제로이 앱의 영역 대부분은 여러 엔터티의 데이터를 표시 합니다. 예를 들어 주문 갤러리에는 다음 정보가 포함 됩니다.

- 주문 번호는 **Orders** 엔터티의 필드입니다.
- Status는 orders **상태** 옵션 집합의 옵션인 **orders** 엔터티의 또 다른 필드입니다.
- 고객 이름은 **Customers** 엔터티의 필드입니다.
- 총 비용은 **Order Details** 엔터티의 데이터를 기반으로 계산 됩니다.

요약에는 주문 목록과 동일한 정보 중 일부가 포함 되어 있지만 주문을 관리 하는 직원의 이름과 이름도 포함 됩니다. 이러한 정보는 **Employees** 엔터티의 필드에서 가져옵니다. 세부 정보 갤러리는 **Order details** 엔터티의 레코드를 표시 하 고 이러한 세부 정보의 각 제품은 **order Products** 엔터티의 레코드입니다.

## <a name="explore-the-relationships"></a>관계 탐색

이러한 엔터티에는 데이터베이스에서 생성 된 관계가 있으므로 동일한 갤러리 또는 폼에 다른 원본 (예: 엔터티)의 데이터를 표시할 수 있습니다.

### <a name="many-to-one-relationships"></a>다 대 일 관계

예를 들어 각 주문의 고객 및 직원에 대 한 정보는 **Customers** 및 **Employees** 엔터티에 있습니다. 따라서 **orders** 엔터티는 주문이 많기 때문에 이러한 엔터티와 다 대 일 관계를 포함 합니다. 각각은 한 명의 고객에만 배치 하 고 하나의 직원만 관리할 수 있습니다.

각 주문에는 주문에 포함 된 제품을 나타내는 하나 이상의 줄 항목과 수량이 포함 됩니다. 각 품목은 order **Products** 엔터티에서 각 제품에 대 한 정보를 가져오는 **order Details** 엔터티의 레코드입니다. 각 세부 정보는 하나의 제품만 식별 하지만 각 제품은 여러 세부 정보로 표시 될 수 있습니다. 따라서 **Order Details** 엔터티에는 **order Products** 엔터티와 다 대 일 관계가 있습니다.

### <a name="one-to-many-relationships"></a>일 대 다 관계

각 주문에는 여러 줄 항목이 포함 될 수 있지만 각 줄 항목은 하나의 순서에만 관련 됩니다. 따라서 **Orders** 엔터티는 **Order Details** 엔터티를 사용 하 여 일 대 다 관계를 가집니다.

### <a name="dot-notation-for-relationships"></a>관계에 대 한 점 표기법 

엔터티 간의 관계를 기반으로 데이터를 표시 하려면 점 속성 선택기를 사용 하 여 한 엔터티에서 다른 엔터티로의 관계를 살펴볼 수 있습니다.  예를 들어 **Orders** 엔터티의 각 레코드는 주문 갤러리에서 고객 이름을 표시할 수 있도록 **Customers** 엔터티의 정보를 가져옵니다. 이 갤러리에서는 레이블의 **Text** 속성을 다음 식으로 설정 하 여이 동작을 구성 합니다.<br>`ThisItem.Customer.Company`

**ThisItem** 는 **Orders** 엔터티의 레코드를 지정 하 고 **고객** 엔터티에서 주문을 한 고객에 대 한 정보를 가져옵니다. 이 경우 식은 고객의 회사 이름을 표시 하도록 지정 합니다. 그러나 해당 고객에 대 한 전체 레코드를 끌어올 수 있으므로, 예를 들어 해당 고객의 전자 메일 주소를 쉽게 표시할 수 있습니다.

한 엔터티에서 다른 엔터티로 이동 하는 또 다른 예로, 사용자가 다른 갤러리에서 선택한 레코드를 기반으로 한 엔터티의 레코드를 표시 하 고 다른 엔터티에 있는 레코드를 갤러리에 표시 하도록 지정할 수 있습니다. 주문 세부 정보를 표시 하려면 세부 정보 갤러리의 **Items** 속성을 다음 식으로 설정 합니다.<br>`Gallery1.Selected.'Order Details'`

이 경우 **gallery1.selected** 는 이전 예제에서 **ThisItem** 가 수행한 것 처럼 **Orders** 엔터티의 레코드를 지정 합니다. 그러나이 식은 이전 식에서와 같이 하나의 레코드만 가져오지 않습니다. 대신, 전체 레코드 테이블을 가져와서 각 제품의 이름 및 단가 ( **주문 제품** 엔터티에 반영 됨)와 수량 ( **주문 정보** 엔터티에 반영 됨)을 표시 합니다.

## <a name="do-it-yourself"></a>직접

단계별 지침에 따라 Northwind 주문 캔버스 앱을 만들 수 있습니다.  지침은 다음 세 부분으로 구분 됩니다.

1. [주문 갤러리를 만듭니다](northwind-orders-canvas-part1.md).
1. [요약 양식을 만듭니다](northwind-orders-canvas-part2.md).
1. [세부 정보 갤러리를 만듭니다](northwind-orders-canvas-part3.md).

앞으로 건너뛰려면 솔루션에 각 파트에 대 한 시작 지점 앱이 포함 되어 있습니다.  앱 목록에서 **Northwind 주문 (Canvas)-시작 부분 1** 등을 찾습니다.

> [!div class="nextstepaction"]
> [주문 갤러리를 만들어 계속](northwind-orders-canvas-part1.md)
