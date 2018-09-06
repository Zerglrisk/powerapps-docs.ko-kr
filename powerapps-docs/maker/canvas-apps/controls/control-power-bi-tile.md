---
title: 'Power BI 타일 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 Power BI 타일 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/07/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ab5542adb68bbd07e2725197230000bdd02b320f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833764"
---
# <a name="power-bi-tile-control-in-powerapps"></a>PowerApps의 Power BI 타일 컨트롤

앱 내부에 있는 [Power BI](https://powerbi.microsoft.com) 타일을 보여주는 컨트롤입니다.

Power BI가 없나요? [가입](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi)하세요.

## <a name="description"></a>설명

앱 내부에 있는 **[Power BI 타일](https://docs.microsoft.com/power-bi/service-dashboard-tiles)** 을 표시하여 기존 데이터 분석 및 보고를 활용합니다. 옵션 패널의 **데이터** 탭에서 **Workspace**, **Dashboard** 및 **Tile** 속성을 설정하여 표시하려는 타일을 지정합니다.

## <a name="sharing-and-security"></a>공유 및 보안

Power BI 콘텐츠가 포함된 앱을 공유하는 경우 타일을 제공하는 [대시보드](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports)뿐만 아니라 앱 자체를 공유해야합니다. 그렇지 않은 경우 Power BI 콘텐츠는 앱을 여는 사용자에 대해서도 표시되지 않습니다. Power BI 콘텐츠가 포함된 앱에는 해당 콘텐츠에 대한 사용 권한을 적용합니다.

## <a name="performance"></a>Performance

네 개 이상의 Power BI 타일을 앱 내에서 동시에 로드하지 않는 것이 좋습니다. **LoadPowerBIContent** 속성을 설정하여 타일 로드 및 언로드를 제어할 수 있습니다.

## <a name="key-properties"></a>주요 속성

**작업 영역** – 타일이 제공되는 Power BI 작업 영역입니다.

**대시보드** – 타일이 제공되는 Power BI 대시보드입니다.

**타일** – 표시하려는 Power BI 타일의 이름입니다.

**LoadPowerBIContent** – true로 설정하는 경우 Power BI 콘텐츠가 로드되고 표시됩니다. false로 설정하는 경우 Power BI 콘텐츠가 언로드됩니다. 그러면 메모리를 해제하고 성능을 최적화합니다.

## <a name="additional-properties"></a>추가 속성

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다. 기본적으로 타일과 연결된 Power BI 보고서가 열립니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="example"></a>예

1. **삽입** 탭에서 **컨트롤** 메뉴를 연 다음, **Power BI 타일** 컨트롤을 추가합니다.

    [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 방법을 모르시나요?

2. 옵션 패널의 **데이터** 탭에서 **작업 영역** 설정에 대해 **내 작업 영역**을 선택합니다.

3. 대시보드 목록에서 대시보드를 선택한 다음, 타일 목록에서 타일을 선택합니다.

    컨트롤은 Power BI 타일을 렌더링합니다.

## <a name="accessibility-guidelines"></a>접근성 지침

**Power BI 타일**은 단순히 Power BI 콘텐츠용 컨테이너입니다. 이러한 [Power BI 접근성 팁](https://docs.microsoft.com/power-bi/desktop-accessibility)을 사용하여 접근성 있는 콘텐츠를 만드는 방법을 알아봅니다.

Power BI 콘텐츠에 제목이 없는 경우 **[레이블](control-text-box.md)** 컨트롤을 사용하는 제목을 추가하고 화면 reader를 지원합니다. Power BI 타일 바로 앞에 레이블을 지정할 수 있습니다.
