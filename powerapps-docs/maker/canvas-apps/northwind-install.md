---
title: Northwind Traders 데이터베이스 및 앱 설치 | Microsoft Docs
description: 환경에 Northwind 데이터베이스와 앱을 설치 하 여 관계형 개념을 살펴보세요.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3a2c3b468c7ccc09c49221c65113e66b562f5ed1
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "71990528"
---
# <a name="install-northwind-traders-database-and-apps"></a>Northwind Traders 데이터베이스 및 앱 설치

[이러한 일련의 항목](northwind-orders-canvas-part1.md)에서 설명 하는 단계를 수행 하 여 Common Data Service의 예제 데이터베이스에 구현 된 관계형 데이터에 대 한 개념을 검색할 수 있습니다. 또한 캔버스와 모델 기반의 샘플 비즈니스 앱을 탐색 하 여 해당 데이터를 관리 하 고 이러한 앱을 만들어 실용적인 경험을 얻을 수 있습니다. 이 첫 번째 항목에서는 사용자 환경에 Northwind Traders 데이터베이스를 설치 하 고 샘플 앱에 대 한 액세스 권한을 얻는 방법을 설명 합니다 .이 앱은 편집을 위해 열어서 작성 된 방법을 표시 하는 데 사용할 수 있습니다.

Northwind Traders는 주문, 제품, 고객, 공급 업체 및 소규모 기업의 기타 많은 측면을 관리 하는 가상의 조직입니다. 이 샘플은 Microsoft Access의 첫 번째 버전으로 표시 되었으며 여전히 Access 템플릿으로 사용할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

- Common Data Service를 지 원하는 PowerApps 라이선스입니다. 30 일 동안 [무료 평가판 라이선스를 사용할](../signup-for-powerapps.md) 수 있습니다.
- Common Data Service 데이터베이스를 사용 하는 환경입니다. 적절 한 권한이 있는 경우 [이러한 환경을 만들](https://docs.microsoft.com/power-platform/admin/create-environment) 수 있습니다.

## <a name="download-the-solution"></a>솔루션 다운로드

> [!div class="nextstepaction"]
> [Northwind Traders 솔루션 파일 다운로드](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

이 [솔루션](../../developer/common-data-service/introduction-solutions.md) 파일 (.zip)에는 엔터티, 옵션 집합 및 비즈니스 프로세스에 대 한 정의가 포함 되어 있습니다. 캔버스 및 모델 기반 앱 및 함께 사용 되는 다른 모든 부분

## <a name="install-the-solution"></a>솔루션 설치

1. [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인 한 다음 Common Data Service 데이터베이스를 포함 하는 환경에서 작업 하 고 있는지 확인 합니다.

1. 왼쪽 탐색 창에서 **솔루션**을 선택한 다음 화면 위쪽의 도구 모음에서 **가져오기** 를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Solutions 보기 및 가져오기-솔루션 진입점 ](media/northwind-install/solution-import.png)

1. **솔루션 패키지 선택** 페이지에서 **찾아보기**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 패키지를 선택 하기 전에 솔루션 패키지 페이지를 ![Select ](media/northwind-install/select-solution2.png)

1. 다운로드 한 파일을 찾은 다음 **열기**를 선택 합니다.

    다른 위치를 선택 하지 않은 경우 파일은 다운로드 폴더에 표시 됩니다.

1. 올바른 파일 (버전 번호가 다를 수 있음)이 있는 경우 **다음**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 패키지를 선택한 후 솔루션 패키지 페이지를 ![Select ](media/northwind-install/confirm-solution2.png)

1. 솔루션 **정보** 페이지에서 솔루션 이름과 게시자가 올바르면 **다음** 을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Solution 정보 페이지 ](media/northwind-install/confirm-publisher.png)

1. **가져오기 옵션** 페이지에서 **가져오기** 를 선택 하 여 샘플에 필요한 SDK 메시지 처리를 확인 합니다.

    > [!div class="mx-imgBorder"]
    > ![Import 옵션 페이지 ](media/northwind-install/confirm-sdk.png)

    다음 몇 분 동안 솔루션이 설치 되 면 다른 페이지가 표시 되 고 진행률이 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![progress 막대 ](media/northwind-install/solution-progress.png)

    설치가 완료 되 면 원래 페이지에 결과가 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![Importing 솔루션 페이지 ](media/northwind-install/solution-success.png)

1. **닫기**를 선택합니다.

## <a name="load-the-sample-data"></a>샘플 데이터 로드

1. **앱**을 선택한 다음 **Northwind 샘플 데이터**를 선택 합니다.

    솔루션을 설치한 직후에 Northwind 앱이 표시 되지 않는 경우 몇 분 정도 기다립니다.

    > [!div class="mx-imgBorder"]
    > 앱 목록에 ![Northwind 데이터베이스 ](media/northwind-install/sample-data-app.png)

1. 앱이 Common Data Service와 상호 작용할 수 있는 권한을 요청 하는 경우 **허용**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > Common Data Service ](media/northwind-install/sample-data-permission.png)에 대 한 ![Consent 대화 상자

1. 앱이 로드 되 고 샘플 엔터티에 레코드가 없음을 보여 주는 경우 **데이터 로드** 를 선택 하 여 엔터티를 채웁니다.

    > [!div class="mx-imgBorder"]
    > 샘플 Data Manager의 데이터 ![Load 단추 ](media/northwind-install/sample-data-load.png)

    앱이 데이터를 로드 하면 앱 위쪽에서 3 월 점으로 이동 하 고 레코드 수가 늘어납니다.

    엔터티는 레코드 간에 관계를 설정할 수 있도록 특정 순서로 로드 됩니다. 예를 들어 **Order Details** 엔터티에는 **주문** 및 **주문 제품** 엔터티와 가장 먼저 로드 되는 다 대 일 관계가 있습니다.

    언제 든 지 **취소**를 선택 하 여 프로세스를 취소 하 고 **데이터 제거**를 선택 하 여 언제 든 지 데이터를 제거할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 데이터가 로드 될 때 Data Manager를 ![Sample ](media/northwind-install/sample-data-progress.png)

    데이터 로드가 완료 되 면 마지막 행 (**다 대 다 관계**)이 **완료**된 것으로 표시 되 고 **데이터 로드** 및 **데이터 제거** 단추가 다시 사용 하도록 설정 됩니다.

    > [!div class="mx-imgBorder"]
    > 데이터가 로드 된 후 Data Manager ![Sample ](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>샘플 앱

Northwind 솔루션에는 다음 데이터와 상호 작용 하기 위한 이러한 앱이 포함 되어 있습니다.

- Northwind 주문 (Canvas)
- Northwind 주문 (모델 기반)

이전 절차에서 앱을 연 것과 동일한 방식으로 이러한 앱을 엽니다.

### <a name="canvas"></a>캔버스

이 단일 화면 앱은 order 엔터티에 대 한 간단한 마스터 세부 정보 보기를 제공 합니다. **여기서 주문의 요약** 및 주문의 각 품목을 보고 편집할 수 있습니다. 주문 목록은 왼쪽 가장자리 근처에 표시 되며, 해당 목록의 화살표를 선택 하 여 해당 주문의 요약 및 세부 정보를 표시할 수 있습니다. 추가 정보: [Northwind Traders 용 캔버스 앱 개요](northwind-orders-canvas-overview.md)

> [!div class="mx-imgBorder"]
> Northwind 캔버스 앱의 주문 및 세부 정보 ![List ](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>모델 기반

이 앱은 **주문** 엔터티에서 동일한 데이터에 대해 캔버스 앱으로 작동 합니다. 주문 목록에서 해당 숫자를 선택 하 여 주문에 대 한 자세한 정보를 표시 합니다.

> [!div class="mx-imgBorder"]
> Northwind 모델 기반 앱의 주문 ![list ](media/northwind-install/orders-model.png)

주문 요약은 별도의 형식으로 표시 됩니다.

> [!div class="mx-imgBorder"]
> 모델 기반 앱의 ![order 세부 정보 ](media/northwind-install/orders-model-2.png)

폼을 아래로 스크롤하면 캔버스 앱에서 수행 하는 것과 동일한 품목을 표시 합니다.

> [!div class="mx-imgBorder"]
> 모델 기반 앱의 ![more 주문 세부 정보 ](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>직접

단계별 지침에 따라이 항목의 앞부분에 표시 된 canvas 앱을 만들 수 있습니다.  지침은 다음 세 부분으로 구분 됩니다.

1. [주문 갤러리를 만듭니다](northwind-orders-canvas-part1.md).
1. [요약 양식을 만듭니다](northwind-orders-canvas-part2.md).
1. [세부 정보 갤러리를 만듭니다](northwind-orders-canvas-part3.md).

앞으로 건너뛰려면 솔루션에 각 파트에 대 한 시작 지점 앱이 포함 되어 있습니다.  앱 목록에서 **Northwind 주문 (Canvas)-시작 부분 1** 등을 찾습니다.

이 [앱 개요](northwind-orders-canvas-overview.md) 에서는 사용자 인터페이스, 데이터 원본 및 관계가 사용 되는 방식에 대해 설명 합니다.

> [!div class="nextstepaction"]
> [개요를 읽어 시작 합니다.](northwind-orders-canvas-overview.md)
