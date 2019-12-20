---
title: Power BI에 대 한 Power Apps 사용자 지정 시각적 개체 | Microsoft Docs
description: 동일한 데이터 원본을 사용하고 Power BI에서 다른 보고서 항목 등을 필터링할 수 있는 캔버스 앱 포함에 대한 절차 및 제한 사항
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2019
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a1ff224557bd36074f7c981a5e76a9721943afb
ms.sourcegitcommit: 366f0d1b8309ab1fd533ebd7e1b41a69a99fd25a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302884"
---
# <a name="power-apps-custom-visual-for-power-bi"></a>Power BI에 대 한 Power Apps 사용자 지정 시각적 개체

Power BI를 사용 하면 데이터 정보 및 더 나은 의사 결정을 가능 하 게 하 고, Power Apps를 통해 모든 사용자가 비즈니스 데이터에 연결 하는 앱을 빌드하고 사용할 수 있습니다 Power Apps 사용자 지정 시각적 개체를 사용 하 여 컨텍스트 인식 데이터를 캔버스 앱에 전달할 수 있습니다. 이렇게 하면 보고서를 변경 하는 동안 실시간으로 업데이트 됩니다. 이제 앱 사용자는 비즈니스 통찰력을 파생하고 Power BI 보고서 및 대시보드 내에서 즉시 작업을 수행할 수 있습니다.

## <a name="using-the-power-apps-custom-visual"></a>Power Apps 사용자 지정 시각적 개체 사용

Power BI 보고서에서 Power Apps 사용자 지정 시각적 개체를 사용 하는 데 필요한 단계를 살펴보겠습니다.

1. Power Apps 사용자 지정 시각적 개체는 기본적으로 Power BI 서비스에서 사용할 수 있습니다. Power BI Desktop를 사용 중이 고 표시 되지 않는 경우 최신 버전의 Power BI Desktop로 업그레이드 해야 합니다.

2. Power Apps 시각적 개체를 보고서에 추가 하 고 연결 된 데이터 필드를 설정 합니다.

    ![보고서 데이터 선택](./media/powerapps-custom-visual/add-visual-set-data.png)

    기존 앱을 선택하거나 앱을 만들 수 있는데, 보고서를 Power BI 서비스에 게시하고 Microsoft Edge 또는 Google Chrome에서 열어야 합니다.

3.  앱을 만들도록 선택하는 경우 만들 각 환경에서 선택할 수 있습니다.

    ![새 앱 또는 기존 앱](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    기존 앱을 사용 하도록 선택 하는 경우 시각적 개체는 Power Apps에서 앱을 열도록 요청 합니다. 그러면 시각적 개체에서 앱에 필요한 구성 요소를 설정 하 여 Power BI에서 Power Apps로 데이터를 보낼 수 있도록 합니다.

    새 앱을 만드는 경우 Power Apps는 필수 구성 요소가 이미 설정 된 간단한 앱을 만듭니다.

    > [!NOTE]
    > 앱에서 사용할 수 있는 `PowerBIIntegration.Refresh()` 함수를 Power BI 보고서의 Power Apps 사용자 지정 시각적 개체에서 새 앱을 만들어야 합니다.

    ![새 앱](./media/powerapps-custom-visual/new-app.png)

4. 이제 Power Apps Studio에서 2 단계에서 설정한 데이터 필드를 사용할 수 있습니다. `PowerBIIntegration` 개체는 다른 Power Apps 읽기 전용 데이터 원본 또는 컬렉션과 동일 하 게 작동 합니다. 개체를 사용하여 모든 컨트롤을 채우거나 다른 데이터 원본으로 조인 및 필터링할 수 있습니다.

    ![사용자 지정 수식](./media/powerapps-custom-visual/custom-formula.png)

    이 수식은 고객 데이터 원본과 Power BI 데이터를 조인합니다. `LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   Power BI 보고서와 시작 된 Power Apps Studio 인스턴스는 라이브 데이터 연결을 공유 합니다. 둘 다 열려 있는 동안 보고서의 데이터를 필터링 하거나 변경 하 여 업데이트 된 데이터가 Power Apps 스튜디오의 앱에 즉시 반영 되는지 확인할 수 있습니다.

5. 앱 빌드 또는 변경을 완료 한 후에는 앱을 저장 하 고 Power Apps에 게시 하 여 Power BI 보고서에서 앱을 확인 합니다.

6. 변경 내용에 만족 하면 Power Apps 앱을 보고서의 사용자와 공유 하 고 보고서를 저장 해야 합니다.

7. 또한 사용자가 데이터에서 통찰력을 얻음에 따라 작업을 수행할 수 있는 보고서를 만들었습니다.

    ![보고서 작업](./media/powerapps-custom-visual/working-report.gif)

    앱을 변경 해야 하는 경우 편집 모드에서 보고서를 열고 Power Apps 시각적 개체에서 **추가 옵션** (**...**)을 클릭 하거나 탭 한 다음 **편집**을 선택 합니다.

    ![앱 편집](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-power-apps-custom-visual"></a>Power Apps 사용자 지정 시각적 개체의 제한 사항

Power Apps 사용자 지정 시각적 개체에는 다음과 같은 제한 사항이 적용 됩니다.

- 시각적 개체와 연결된 데이터 필드를 변경하는 경우 줄임표(...)를 선택한 다음, **편집**을 선택하여 Power BI 서비스 내에서 앱을 편집해야 합니다. 그렇지 않으면 변경 내용이 전원 앱에 전파 되지 않으며 앱이 예기치 않은 방식으로 작동 합니다.
- Power Apps 사용자 지정 시각적 개체는 Power BI Desktop 내에서 Power BI 보고서 및 Power BI 데이터 원본에 대 한 새로 고침을 트리거할 수 없습니다. 앱에서 보고서와 동일한 데이터 원본으로 데이터를 다시 작성 하는 경우 변경 내용은 Power BI Desktop에 즉시 반영 되지 않습니다. 변경 내용은 다음 예약된 새로 고침에서 반영됩니다.
- Power Apps 사용자 지정 시각적 개체는 데이터를 필터링 하거나 보고서로 데이터를 다시 보낼 수 없습니다.
- Power Apps 앱을 보고서와 별도로 공유 해야 합니다. [Power apps에서 앱을 공유](share-app.md)하는 방법에 대해 알아봅니다.
- Power BI Report Server 및 Power BI 용 모바일 앱은 Power Apps 사용자 지정 시각적 개체를 지원 하지 않습니다.
- `PowerBIIntegration.Refresh()` 함수를 사용 하는 경우 다음 제한 사항이 적용 됩니다.
    - 앱에서이 기능을 사용할 수 있도록 Power BI 보고서의 Power Apps 사용자 지정 시각적 개체에서 새 앱을 만들어야 합니다.
    - [Directquery를 지 원하는](https://docs.microsoft.com/power-bi/desktop-directquery-data-sources) 원본을 사용 해야 하며 directquery 메서드를 사용 하 여 데이터 연결을 만들어야 합니다.
- Power BI Desktop의 power Apps는 편집 하는 동안은 제외 하 고 앱을 만들 때 Power Apps 스튜디오에 데이터를 제공 합니다. Power BI 웹을 사용 하 여 앱을 편집 하는 동안 데이터를 미리 봅니다.

> [!NOTE]
> 먼저 Power BI 서비스에 보고서를 게시 한 다음 앱을 만들거나 수정 하는 것이 좋습니다.

## <a name="browser-support"></a>브라우저 지원

다음 표에서는 Power Apps 사용자 지정 시각적 개체의 보기, 만들기 및 수정 작업에 대 한 브라우저 지원 가능성을 보여 줍니다. 지원 되는 브라우저와 작업은 확인 표시 (&check;)로 식별 됩니다.

|브라우저|뷰|만들기|변경
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|Safari \*|&check;
|Mozilla Firefox
|다른 모든 브라우저

Safari에서 \* 사이트 간 추적 (**기본 설정** > **개인 정보 보호**및 **사이트 간 추적 방지**사용 안 함)을 사용 하도록 설정 하 여 Power Apps 사용자 지정 시각적 개체를 확인 해야 합니다.

## <a name="accessibility-support"></a>내게 필요한 옵션 지원

키보드를 사용 하 여 Power Apps 시각적 개체를 탐색 하려면 다음 단계를 수행 합니다.

1. 원하는 파워 앱 시각적 개체에 대 한 Power BI 보고서에서 포커스를 선택 합니다.
2. 시각적 개체를 강조 표시할 때까지 키보드의 **Tab** 키를 사용 합니다.
3. 키보드에서 **Ctrl + 오른쪽** 키를 사용 하 여 시각적 개체를 입력 합니다.
3. 시각적 개체의 원하는 구성 요소가 선택 될 때까지 키보드의 **Tab** 키를 사용 합니다.

자세한 내용은 [Power BI 내게 필요한 옵션 설명서]( https://docs.microsoft.com/power-bi/desktop-accessibility) 를 참조 하세요.


## <a name="next-steps"></a>다음 단계

* 간단한 [단계별 자습서](embed-powerapps-powerbi.md)로 진행합니다.
* [비디오](https://aka.ms/powerappscustomvisualvideo)를 확인 하세요.
