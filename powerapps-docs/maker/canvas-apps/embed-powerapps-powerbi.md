---
title: Power BI 보고서에 새 앱 포함 | Microsoft Docs
description: 동일한 데이터 원본을 사용하고 다른 보고서 항목처럼 필터링할 수 있는 앱을 포함합니다
documentationcenter: na
author: mgblythe
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/15/2018
ms.author: mblythe
ms.openlocfilehash: 33656e44f782a626eecc28787af984ace7339cd6
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "31830473"
---
# <a name="tutorial-embed-a-new-app-in-a-power-bi-report"></a>자습서: Power BI 보고서에 새 앱 포함

Power BI를 사용하면 *사용자 지정 시각적 개체*를 보고서에 추가하여 기능을 확장할 수 있습니다. 이 자습서에서는 PowerApps 사용자 지정 시각적 개체를 사용하여 샘플 보고서에 포함되는 새 앱을 만듭니다. 이 앱은 해당 보고서의 다른 항목과 상호 작용합니다.

PowerApps 구독이 없는 경우 시작하기 전에 [체험 계정을 만듭니다](../signup-for-powerapps.md).

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.
> [!div class="checklist"]
> * Power BI 보고서로 PowerApps 사용자 지정 시각적 개체 가져오기
> * 보고서의 데이터를 사용하는 새 앱 만들기
> * 보고서에서 앱 보기

## <a name="prerequisites"></a>필수 조건

* [Google Chrome](https://www.google.com/chrome/browser/) 또는 [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) 브라우저
* [기회 분석 샘플](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample)이 설치된 [Power BI 구독](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi)
* [PowerApps에서 앱을 만드는 방법](data-platform-create-app-scratch.md) 및 [Power BI 보고서를 편집하는 방법](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour)에 대한 이해

## <a name="import-the-powerapps-custom-visual"></a>PowerApps 사용자 지정 시각적 개체 가져오기

첫 번째 단계는 샘플 보고서에서 사용할 수 있도록 PowerApps 사용자 지정 시각적 개체를 가져오는 것입니다.

1. 기회 분석 샘플 보고서에서 **예정된 기회** 탭을 클릭하거나 탭합니다.

2. 보고서 위쪽에서 **보고서 편집**을 클릭하거나 탭합니다.

3. **시각화** 창에서 줄임표(**. . .**) > **마켓플레이스에서 가져오기**를 차례로 클릭하거나 탭합니다. 

    ![마켓플레이스에서 가져오기](media/embed-powerapps-powerbi/import-visual.png)

4. **Power BI 시각적 개체** 화면에서 "PowerApps"를 검색한 다음, **추가**를 클릭하거나 탭합니다. Power BI에서 사용자 지정 시각적 개체 아이콘을 **시각화** 창의 아래쪽에 추가합니다.

    ![PowerApps 시각적 개체 아이콘](media/embed-powerapps-powerbi/powerapps-icon.png)

5. 보고서를 저장합니다.

## <a name="create-a-new-app"></a>새 앱 만들기
이제는 사용자 지정 시각적 개체를 보고서에 추가하고 보고서의 데이터를 기반으로 하여 새 앱을 만듭니다. 앱이 만들어지면 PowerApps와 Power BI 간에 라이브 데이터 연결을 통해 PowerApps Studio가 시작됩니다.

1. 일부 보고서 타일을 이동하고 크기를 조정하여 앱 공간을 확보합니다.

    ![보고서 타일 이동 및 크기 조정](media/embed-powerapps-powerbi/move-resize.png)

2. PowerApps 사용자 지정 시각적 개체 아이콘을 클릭하거나 탭한 다음, 공간에 맞게 타일의 크기를 조정합니다.

3. **필드** 창에서 **이름**, **제품 코드** 및 **영업 스테이지**를 선택합니다. 

    ![필드 선택](media/embed-powerapps-powerbi/select-fields.png)

4. 사용자 지정 시각적 개체 타일에서 앱을 만들려는 PowerApps 환경을 선택한 다음, **새로 만들기**를 클릭하거나 탭합니다.

    ![새 앱 만들기](media/embed-powerapps-powerbi/create-new-app.png)

    PowerApps Studio를 통해 Power BI에서 선택한 필드 중 하나를 표시하는 *갤러리*가 있는 기본 앱이 만들어졌음을 알 수 있습니다.

5.  화면의 절반만 차지하도록 갤러리의 크기를 조정합니다. 

6. 왼쪽 창에서 **Screen1**을 클릭하거나 탭한 다음, 화면의 **Fill** 속성을 "LightBlue"로 설정합니다(그러면 보고서에 더 잘 표시됨).

    ![크기가 조정된 갤러리가 있는 앱](media/embed-powerapps-powerbi/app-gallery.png)

6. **Text** 속성이 `"Opportunity Count: " & CountRows(Gallery1.AllItems)`로 설정된 Label 컨트롤을 갤러리 아래쪽에 추가합니다. 이제 데이터 집합의 총 기회 수가 표시됩니다.

    ![기회 수](media/embed-powerapps-powerbi/opportunity-count.png)

7. 앱을 "기회"라는 이름으로 저장합니다. 


## <a name="view-the-app-in-the-report"></a>보고서에서 앱 보기
이제 앱은 보고서에서 사용할 수 있으며, 동일한 데이터 원본을 공유하므로 다른 시각적 개체와 상호 작용합니다.

Power BI 보고서의 슬라이서에서 **1월**을 선택합니다. 이 경우 앱의 데이터를 포함하여 전체 보고서가 필터링됩니다.

![필터링된 보고서](media/embed-powerapps-powerbi/filtered-report.png)

앱의 기회 수는 보고서의 왼쪽 위에 있는 수와 일치합니다. 보고서에서 다른 항목을 선택할 수 있으며, 앱의 데이터가 업데이트됩니다.


## <a name="clean-up-resources"></a>리소스 정리
기회 분석 샘플을 더 이상 사용하지 않으려는 경우 대시보드, 보고서 및 데이터 집합을 삭제할 수 있습니다.


## <a name="next-steps"></a>다음 단계
이 자습서에서는 다음 작업을 수행하는 방법을 알아보았습니다.
> [!div class="checklist"]
> * Power BI 보고서로 PowerApps 사용자 지정 시각적 개체 가져오기
> * 보고서의 데이터를 사용하는 새 앱 만들기
> * 보고서에서 앱 보기

더 자세히 알아보려면 다음 문서로 계속 진행하세요.
> [!div class="nextstepaction"]
> [Power BI용 PowerApps 사용자 지정 시각적 개체](powerapps-custom-visual.md)

