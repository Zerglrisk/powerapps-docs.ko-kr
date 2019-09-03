---
title: Power BI용 PowerApps 사용자 지정 시각적 개체 | Microsoft Docs
description: 동일한 데이터 원본을 사용하고 Power BI에서 다른 보고서 항목 등을 필터링할 수 있는 캔버스 앱 포함에 대한 절차 및 제한 사항
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/30/2019
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 562811ebce59660d6033585868afd42da46442d5
ms.sourcegitcommit: 25a85b462515cb64f3f2b114864a682abf803f4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70213937"
---
# <a name="powerapps-custom-visual-for-power-bi"></a>Power BI용 PowerApps 사용자 지정 시각적 개체

Power BI는 데이터 통찰력 및 더 나은 의사 결정을 가능하게 하고, PowerApps를 통해 모든 사용자는 비즈니스 데이터에 연결하는 앱을 빌드 및 사용할 수 있습니다. PowerApps 사용자 지정 시각적 개체를 사용하여 캔버스 앱에 컨텍스트 인식 데이터를 전달할 수 있으며 이를 통해 보고서에 변경 사항을 만들 때마다 실시간으로 업데이트합니다. 이제 앱 사용자는 비즈니스 통찰력을 파생하고 Power BI 보고서 및 대시보드 내에서 즉시 작업을 수행할 수 있습니다.

## <a name="using-the-powerapps-custom-visual"></a>PowerApps 사용자 지정 시각적 개체 사용

Power BI 보고서에서 PowerApps 사용자 지정 시각적 개체를 사용하는 데 필요한 단계를 살펴보겠습니다.

1. [AppSource](https://appsource.microsoft.com/product/power-bi-visuals/WA104381378?tab=Overview)에서 사용자 지정 시각적 개체를 가져오거나 Power BI 서비스에서 직접 가져옵니다.

    ![마켓플레이스의 사용자 지정 시각적 개체](./media/powerapps-custom-visual/powerapps-store.png) 

2. 보고서에 PowerApps 시각적 개체를 추가하고, 연결된 데이터 필드를 설정합니다.

    ![보고서 데이터 선택](./media/powerapps-custom-visual/add-visual-set-data.png)

    기존 앱을 선택하거나 앱을 만들 수 있는데, 보고서를 Power BI 서비스에 게시하고 Microsoft Edge 또는 Google Chrome에서 열어야 합니다.

3.  앱을 만들도록 선택하는 경우 만들 각 환경에서 선택할 수 있습니다.

    ![새 앱 또는 기존 앱](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    기존 앱을 사용하도록 선택하는 경우 시각적 개체는 PowerApps에서 앱을 열 것인지 묻는 메시지를 표시합니다. 그런 다음, 시각적 개체는 Power BI에서 PowerApps에 데이터를 보낼 수 있도록 앱의 필수 구성 요소를 설정합니다.

    새 앱을 만드는 경우 PowerApps는 이미 설정된 필수 구성 요소로 간단한 앱을 만듭니다.

    ![새 앱](./media/powerapps-custom-visual/new-app.png)

4. 이제 PowerApps Studio에서 2단계에서 설정한 데이터 필드를 사용할 수 있습니다. `PowerBIIntegration` 개체는 다른 PowerApps 읽기 전용 데이터 원본 또는 컬렉션처럼 작동합니다. 개체를 사용하여 모든 컨트롤을 채우거나 다른 데이터 원본으로 조인 및 필터링할 수 있습니다.

    ![사용자 지정 수식](./media/powerapps-custom-visual/custom-formula.png)

    이 수식은 고객 데이터 원본과 Power BI 데이터를 조인합니다. `LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   Power BI 보고서와 실행된 PowerApps Studio의 인스턴스는 라이브 데이터 연결을 공유합니다. 둘 다 열려 있는 동안 보고서의 데이터를 필터링하거나 변경하여 업데이트된 데이터가 PowerApps Studio의 앱에 즉시 반영되는 것을 확인할 수 있습니다.

5. 앱에 대한 빌드 또는 변경을 완료한 후 PowerApps에 앱을 저장 및 게시하여 Power BI 보고서에서 앱을 봅니다.

6. 변경 내용에 만족하면 보고서의 사용자와 PowerApps 앱을 공유한 다음, 보고서를 저장해야 합니다.

7. 또한 사용자가 데이터에서 통찰력을 얻음에 따라 작업을 수행할 수 있는 보고서를 만들었습니다.

    ![보고서 작업](./media/powerapps-custom-visual/working-report.gif)

    앱에 변경 내용을 만들어야 하는 경우 편집 모드에서 보고서를 열고, PowerApps 시각적 개체에서 **더 많은 옵션**( **. . .** )을 클릭하거나 탭하고 **편집**을 선택합니다.

    ![앱 편집](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-powerapps-custom-visual"></a>PowerApps 사용자 지정 시각적 개체의 제한 사항

PowerApps 사용자 지정 시각적 개체에는 다음과 같은 제한 사항이 적용 됩니다.

- 시각적 개체와 연결된 데이터 필드를 변경하는 경우 줄임표(...)를 선택한 다음, **편집**을 선택하여 Power BI 서비스 내에서 앱을 편집해야 합니다. 그렇지 않으면 변경 내용은 PowerApps에 전파되지 않고, 앱은 예기치 않은 방식으로 작동합니다.
- PowerApps 사용자 지정 시각적 개체는 Power BI Desktop 내에서 Power BI 보고서 및 Power BI 데이터 원본에 대 한 새로 고침을 트리거할 수 없습니다. 앱에서 보고서와 동일한 데이터 원본으로 데이터를 다시 작성 하는 경우 변경 내용은 Power BI Desktop에 즉시 반영 되지 않습니다. 변경 내용은 다음 예약된 새로 고침에서 반영됩니다.
- PowerApps 사용자 지정 시각적 개체는 데이터를 필터링하거나 보고서로 데이터를 다시 보낼 수 없습니다.
- 보고서와 별도로 PowerApps 앱을 공유해야 합니다. [PowerApps에서 앱 공유](share-app.md)에 대해 알아봅니다.
- Power BI Report Server 및 Power BI 용 모바일 앱은 PowerApps 사용자 지정 시각적 개체를 지원 하지 않습니다.
- PowerBIIntegration. Refresh () 함수를 사용 하는 경우 [directquery](https://docs.microsoft.com/en-us/power-bi/desktop-directquery-data-sources) 를 지 원하는 원본을 사용 해야 하며 directquery 메서드를 사용 하 여 데이터 연결을 만들어야 합니다.

> [!NOTE]
> 먼저 Power BI 서비스에 보고서를 게시 한 다음 앱을 만들거나 수정 하는 것이 좋습니다.

## <a name="browser-support"></a>브라우저 지원

다음 표에서는 PowerApps 사용자 지정 시각적 개체의 보기, 만들기 및 수정 작업을 위한 브라우저 지원 가능성을 나열 합니다. 지원 되는 브라우저와 작업은 확인 표시 ( &check; )로 식별 됩니다.

|브라우저|보기|만드십시오|변경
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|Safari|&check;
|Mozilla Firefox
|다른 모든 브라우저

## <a name="next-steps"></a>다음 단계

* 간단한 [단계별 자습서](embed-powerapps-powerbi.md)로 진행합니다.
* 우리의 [비디오](https://aka.ms/powerappscustomvisualvideo)를 확인합니다.
