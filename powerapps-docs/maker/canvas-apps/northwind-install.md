---
title: Northwind Traders 데이터베이스 및 앱 설치 | Microsoft Docs
description: 관계형 개념을 탐색 하는 환경에는 Northwind 데이터베이스 및 앱을 설치 합니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 351f9fd4fe369b3073a9edfb0158883140f50693
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761031"
---
# <a name="install-northwind-traders-database-and-apps"></a>Northwind Traders 데이터베이스 및 앱 설치

단계를 수행 하 여 [이 일련의 항목](northwind-orders-canvas-part1.md), Common Data Service에 샘플 데이터베이스에서 구현 될 때 관계형 데이터에 대 한 개념을 검색할 수 있습니다. 샘플 비즈니스 앱을 탐색할 수도 있습니다, 둘 다가 캔버스 및 모델 기반, 해당 데이터를 관리 하기 위한 이러한 앱을 만들어 실제 경험을 받고 있습니다. 이 첫 번째 항목에는 자체 환경에서 Northwind 데이터베이스를 설치 하 고 기본 제공 하는 방법을 표시 하려면 편집을 위해 열 수 있는 샘플 앱에 액세스할 방법을 설명 합니다.

Northwind Traders는 주문, 제품, 고객, 공급 업체 및 소규모의 다른 많은 요소를 관리 하는 가상의 조직을 합니다. 이 샘플에는 첫 번째 버전의 Microsoft Access를 사용 하 여 표시 이며 액세스 템플릿으로 계속 사용할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

- Common Data Service를 지 원하는 PowerApps 라이선스. 할 수 있습니다 [무료 평가판 라이선스를 사용 하 여](../signup-for-powerapps.md) 30 일에 대 한 합니다.
- Common Data Service 데이터베이스를 사용 하 여 환경입니다. 할 수 있습니다 [이러한 환경을 만들려면](https://docs.microsoft.com/power-platform/admin/create-environment) 적절 한 권한이 있는 경우.

## <a name="download-the-solution"></a>솔루션 다운로드

> [!div class="nextstepaction"]
> [Northwind Traders 솔루션 파일을 다운로드 합니다.](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

이렇게 [솔루션](../../developer/common-data-service/introduction-solutions.md) 엔터티, 옵션 집합 및 비즈니스 프로세스 정의; 캔버스 및 모델 기반 앱, 함께 사용 되는 다른 어떤 부분이 든 (.zip) 파일에 포함 되어 있습니다.

## <a name="install-the-solution"></a>솔루션 설치

1. 에 로그인 [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), Common Data Service 데이터베이스를 포함 하는 환경에서 작업 중인 확인 합니다.

1. 왼쪽된 탐색 창에서 선택 **솔루션**를 선택한 후 **가져오기** 화면의 위쪽 도구 모음에서:

    > [!div class="mx-imgBorder"]
    > ![솔루션 보기 및 솔루션 가져오기 진입점](media/northwind-install/solution-import.png)

1. 에 **솔루션 패키지 선택** 페이지에서 선택 **찾아보기**합니다.

    > [!div class="mx-imgBorder"]
    > ![패키지를 선택 하기 전에 솔루션 패키지 페이지를 선택 합니다.](media/northwind-install/select-solution2.png)

1. 다운로드 한 다음 선택 된 파일을 찾을 **열려**합니다.

    다른 위치를 선택 하지 않으면 파일의 다운로드 폴더 됩니다.

1. (버전 번호가 달라질 수 있음) 올바른 파일에 있는 경우 선택할 **다음**:

    > [!div class="mx-imgBorder"]
    > ![패키지를 선택한 후 솔루션 패키지 페이지를 선택 합니다.](media/northwind-install/confirm-solution2.png)

1. 에 **솔루션 정보** 페이지에서 **다음** 솔루션 및 게시자의 이름이 올바른 경우.

    > [!div class="mx-imgBorder"]
    > ![솔루션 정보 페이지](media/northwind-install/confirm-publisher.png)

1. 에 **가져오기 옵션** 페이지에서 **가져오기** 샘플 필요한 SDK 메시지 처리를 확인 하려면:

    > [!div class="mx-imgBorder"]
    > ![가져오기 옵션 페이지](media/northwind-install/confirm-sdk.png)

    다른 페이지가 표시 되 고 솔루션이 다음 몇 분 동안 설치 진행률을 보여 줍니다.

    > [!div class="mx-imgBorder"]
    > ![진행률 표시줄](media/northwind-install/solution-progress.png)

    설치가 완료 되 면 원래 페이지 결과 보여 줍니다.

    > [!div class="mx-imgBorder"]
    > ![솔루션 페이지 가져오기](media/northwind-install/solution-success.png)

1. **닫기**를 선택합니다.

## <a name="load-the-sample-data"></a>샘플 데이터 로드

1. 선택 **앱**를 선택한 후 **Northwind 샘플 데이터**입니다.

    Northwind 앱 솔루션을 설치한 후에 즉시 표시 되지 않는 경우 몇 분 기다립니다.

    > [!div class="mx-imgBorder"]
    > ![앱 목록에 Northwind 데이터베이스](media/northwind-install/sample-data-app.png)

1. 앱을 Common Data Service를 사용 하 여 상호 작용 하는 데 필요한 권한 요청 선택 **허용**:

    > [!div class="mx-imgBorder"]
    > ![Common Data Service에 대 한 동의 대화 상자](media/northwind-install/sample-data-permission.png)

1. 앱 로드를 시작한 후 샘플 엔터티 레코드가 포함 표시 선택 **데이터 로드** 엔터티를 채우는 데:

    > [!div class="mx-imgBorder"]
    > ![데이터 단추 샘플 데이터 관리자에서 로드](media/northwind-install/sample-data-load.png)

    앱 데이터를 로드, 점 앱의 위쪽 및 레코드 증가 수 년 3 월.

    엔터티는 레코드 간의 관계를 설정할 수 있도록 특정 순서 대로 로드 됩니다. 예를 들어를 **Order Details** 엔터티 간의 관계가 다 대는 **주문** 및 **주문 제품** 먼저 로드 되는 엔터티.

    프로세스를 선택 하 여 언제 든 지 취소할 수 있습니다 **취소할**를 선택 하 여 언제 든 지 데이터를 제거할 수 있습니다 **데이터 제거**:

    > [!div class="mx-imgBorder"]
    > ![데이터를 로드 하는 대로 데이터 관리자 샘플](media/northwind-install/sample-data-progress.png)

    데이터를 로드 하 고 마지막 행을 완료 하면 (**다대다 관계**)를 보여 줍니다 **수행**, 및 **Load Data** 및 **데이터 제거** 단추가 다시 활성화 됩니다.

    > [!div class="mx-imgBorder"]
    > ![데이터가 로드 된 후의 샘플 데이터 관리자](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>샘플 앱

Northwind 솔루션에이 데이터와 상호 작용에 대 한 이러한 앱에 포함 됩니다.

- Northwind 주문 (캔버스)
- Northwind 주문 (모델 기반)

이전 절차에서 앱을 열는 동일한 방식으로 이러한 앱을 엽니다.

### <a name="canvas"></a>캔버스

이 단일 화면 앱의 간단한 마스터-세부 뷰를 제공 합니다 **주문** 엔터티를 확인 하 고 순서 및 각 품목을 주문에 대 한 요약을 편집할 수 있는 합니다. 왼쪽된 가장자리 근처의 주문 목록을 표시 하 고 요약 하 고 해당 주문의 세부 정보를 표시 하려면 목록에서 화살표를 선택할 수 있습니다. 자세한 정보는 [Northwind Traders에 대 한 캔버스 앱 개요](northwind-orders-canvas-overview.md)합니다.

> [!div class="mx-imgBorder"]
> ![주문 및 Northwind의 세부 정보 목록을 캔버스 앱](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>모델 기반

이 앱은 동일한 데이터에서 작동 (에 **주문** 엔터티) 캔버스 앱. 주문 목록에서 해당 번호를 선택 하 여 주문에 대 한 자세한 정보를 보여 줍니다.

> [!div class="mx-imgBorder"]
> ![Northwind 모델 기반 앱의 주문 목록](media/northwind-install/orders-model.png)

주문 요약 별도 폼에 나타납니다.

> [!div class="mx-imgBorder"]
> ![모델 기반 앱에서 주문 세부 정보](media/northwind-install/orders-model-2.png)

폼 아래로 스크롤하면 캔버스 앱 처럼 동일한 줄 항목을 표시 합니다.

> [!div class="mx-imgBorder"]
> ![모델 기반 앱에서 자세한 주문 세부 정보](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>사용자가 직접 수행

이 항목의 앞부분에 나와 있는 캔버스 앱을 만드는 단계별 지침을 따르면 됩니다.  지침에는 세 부분으로 구분 됩니다.

1. [순서 갤러리 만들기](northwind-orders-canvas-part1.md)합니다.
1. [요약 양식을 만드는](northwind-orders-canvas-part2.md)합니다.
1. [세부 정보 갤러리 만들기](northwind-orders-canvas-part3.md)합니다.

건너 뛰 세요 하려는 경우 솔루션 각 부분에 대 한 시작 지점은 앱을 포함 합니다.  앱 목록에서 찾습니다 **Northwind 주문 (캔버스)-시작 가이드의 1 부** 등입니다.

이렇게 [앱의 개요](northwind-orders-canvas-overview.md) 사용자에 설명 인터페이스, 데이터 원본 및 관계를 사용 하는 방법입니다.

> [!div class="nextstepaction"]
> [개요를 참조 하 여 시작](northwind-orders-canvas-overview.md)
