---
title: Northwind Traders에 대 한 캔버스 앱의 개요 | Microsoft Docs
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2f28b07f53646e6fbf5afc0b1510bd37e3262b8
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761054"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Northwind Traders에 대 한 캔버스 앱 개요

Northwind Traders에서 데이터를 데이터베이스 관계형 관리용 캔버스 앱에 알아봅니다 [환경에 설치](northwind-install.md)합니다. 관계형 데이터를 사용 하 여 실습 환경을 얻을 수 있으므로 처음부터이 앱을 빌드하 이후 항목에서 단계별 지침에 따라 합니다.

이 항목에서는 다음을 검색 합니다.

- 앱 사용자 표시 방법과 앱에서 관계형 데이터를 관리 합니다.
- 어떤 유형의 데이터는 응용 프로그램을 구동 합니다.
- 어떻게 이러한 유형의 데이터 간에 관계 생성 되었습니다.

단일 화면에서 앱 사용자 표시, 업데이트를 만들고 삭제할 수 있습니다 주문 합니다.

> [!div class="mx-imgBorder"]
> ![전체 캔버스 앱](media/northwind-orders-canvas-part1/orders-finished.png)

## <a name="explore-the-user-interface"></a>사용자 인터페이스를 탐색 합니다.

### <a name="order-gallery"></a>순서 갤러리

앱의 왼쪽 가장자리를 갤러리에는 주문, 주문 번호, 상태, 이름, 고객의 주문의 총 비용을 포함 하 여 목록을 보여 줍니다. 주문 찾기 및 order의 화살표를 선택 하 여 자세한 정보 표시 목록을 통해 스크롤할 수 있습니다. 자세한 정보는 [순서 갤러리 만들기](northwind-orders-canvas-part1.md)합니다.

### <a name="summary-form"></a>요약 폼

오른쪽 위 모서리에서 폼 순서 갤러리에서 선택한 사용자는 주문을 요약 되어 있습니다. 요약에 포함 됩니다는 대부분의 동일한 정보가 해당 갤러리 있지만 요약에는 또한 순서를 만들고 이름 및 순서를 관리 되는 직원의 사진을 유료 날짜를 보여 줍니다. 사용자 수 형태로 데이터를 변경, 이러한 변경 내용을 저장, 취소 또는 삭제 순서 오른쪽 가장자리 근처에 있는 제목 표시줄의 아이콘을 선택 하 여 합니다. 자세한 정보는 [요약 폼을 만들려면](northwind-orders-canvas-part2.md)합니다.

### <a name="detail-gallery"></a>세부 정보 갤러리

오른쪽 아래 모서리에 있는 다른 갤러리는 수량 및 선택한 순서를 포함 하는 제품에 대 한 정보에 표시 됩니다. 이 갤러리에 있는 각 항목을 주문 세부 정보 라고 합니다. 앱 사용자를 추가 하 고 그 아래에서 컨트롤을 사용 하 여 갤러리에 있는 항목을 삭제 수 있습니다. 자세한 정보는 [세부 정보 갤러리 만들기](northwind-orders-canvas-part3.md)합니다.

> [!div class="mx-imgBorder"]
> ![화면 영역 정의](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>데이터 원본 탐색

이 앱을 만들려면 5 개 엔터티 및 옵션 집합에서 데이터를 표시 해 봅니다. 사실,이 앱의 영역 대부분 여러 엔터티로부터 데이터를에서 표시 합니다. 예를 들어 주문 갤러리에는이 정보가 들어 있습니다.

- 주문 번호는 필드를 **주문** 엔터티.
- 상태에 있는 다른 필드는 합니다 **주문** 엔터티에서 옵션을 **주문 상태** 옵션이 설정 합니다.
- 고객 이름은 필드에는 **고객** 엔터티.
- 총 비용 데이터를 기반으로 계산 되는 **Order Details** 엔터티.

요약 주문 목록과 같은 정보 중 일부 있지만 이름과 순서를 관리 되는 직원의 사진을 포함 합니다. 필드에서 정보를 끌어오는 하는 **직원** 엔터티. 자세히 갤러리에서 레코드를 표시 합니다.는 **Order Details** 엔터티와 해당 세부 정보에서 각 제품 레코드입니다 합니다 **주문 제품** 엔터티.

## <a name="explore-the-relationships"></a>관계 탐색

이러한 엔터티를 데이터베이스에서 생성 된 관계에 있으므로 동일한 갤러리 또는 양식에서 다양 한 원본 (예를 들어, 엔터티)에서 데이터를 표시할 수 있습니다.

### <a name="many-to-one-relationships"></a>다 대 일 관계

각 주문에 대 한 직원 및 고객에 대 한 정보는 예를 들어 합니다 **고객이** 및 **직원** 엔터티. 따라서 합니다 **주문** 엔터티에 각각 하나만 고객별 배치 하 고 관리할 수만 명 이상의 직원으로 여러 개의 주문이 있기 때문에 해당 엔터티를 사용 하 여 다 대 일 관계를 포함 합니다.

또한 각 주문에 순서를 포함 하는 제품을 나타내는 하나 이상의 줄 항목 및 수량은 있습니다. 각 품목 레코드입니다 합니다 **Order Details** 에서 각 제품에 대 한 정보를 가져오는 엔터티는 **주문 제품** 엔터티. 하나의 제품을 식별 하는 각 세부 있지만 각 제품이 여러 세부 정보에 나타날 수 있습니다. 따라서 합니다 **Order Details** 엔터티 간의 관계가 다 대 합니다 **주문 제품** 엔터티.

### <a name="one-to-many-relationships"></a>1 대 다 관계

각 주문에는 여러 줄 항목을 포함할 수 있습니다 하지만 각 품목 한 가지 순서로 관련이 있습니다. 따라서 합니다 **주문** 엔터티를 일 대 다 관계가 있는 **Order Details** 엔터티.

### <a name="dot-notation-for-relationships"></a>관계에 대 한 점 표기법 

엔터티 간의 관계를 기반으로 데이터를 표시 하려면 다른 엔터티 간의 관계를 가로질러 걸어가도록에 점 속성 선택기를 사용할 수 있습니다.  예를 들어, 각 레코드에는 **주문** 엔터티 정보를 가져오는 합니다 **고객** 엔터티 순서 갤러리 고객 이름을 표시할 수 있도록 합니다. 갤러리를 설정 하 여이 동작 구성 합니다 **텍스트** 을이 식으로 레이블의 속성:<br>`ThisItem.Customer.Company`

**ThisItem** 의 레코드를 지정 합니다 **주문** 에서 엔터티 및 풀 정보를 **고객** 주문한 고객에 대 한 엔터티. 이 경우 식 고객의 회사 이름 표시 되는지 지정 합니다. 그러나 해당 고객에 대 한 전체 레코드 가져오면 손쉽게을 나타낼 수 있습니다, 예를 들어 있으므로 해당 고객에 대 한 전자 메일 주소 대신 합니다.

다른 엔터티 간에 탐색의 다른 예로, 갤러리는 다른 갤러리에서 선택한 사용자는 다른 엔터티의 레코드를 기준으로 한 엔터티의 레코드를 표시할지를 지정할 수 있습니다. 주문 세부 정보를 표시 하려면 세부 정보 갤러리의 설정 **항목** 속성을이 식:<br>`Gallery1.Selected.'Order Details'`

이 경우 **Gallery1.Selected** 의 레코드를 지정 합니다 **주문** 엔터티를 처럼 **ThisItem** 앞의 예제에서 합니다. 그러나이 식은 이전 식은 동일 하나의 레코드를 끌어오기 하지 않습니다. 각 제품의 이름 및 단위 비용에 표시할 레코드의 전체 테이블을 가져오는 대신 (에 반영 되는 **주문 제품** 엔터티) 및 수량 (에 반영 되는 **Order Details** 엔터티).

## <a name="do-it-yourself"></a>사용자가 직접 수행

Northwind 주문 캔버스 앱을 만드는 단계별 지침을 따르면 됩니다.  지침에는 세 부분으로 구분 됩니다.

1. [순서 갤러리 만들기](northwind-orders-canvas-part1.md)합니다.
1. [요약 양식을 만드는](northwind-orders-canvas-part2.md)합니다.
1. [세부 정보 갤러리 만들기](northwind-orders-canvas-part3.md)합니다.

건너 뛰 세요 하려는 경우 솔루션 각 부분에 대 한 시작 지점은 앱을 포함 합니다.  앱 목록에서 찾습니다 **Northwind 주문 (캔버스)-시작 가이드의 1 부** 등입니다.

> [!div class="nextstepaction"]
> [순서 대로 갤러리를 만들어 계속 합니다.](northwind-orders-canvas-part1.md)
