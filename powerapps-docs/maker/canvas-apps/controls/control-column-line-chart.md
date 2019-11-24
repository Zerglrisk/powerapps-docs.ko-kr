---
title: '세로 막대형 차트 및 꺾은선형 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯하여 세로 막대형 차트 컨트롤과 꺾은선형 차트 컨트롤에 관한 정보
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 355793d572f6c4b6578d6cabff221c79e0724a93
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650669"
---
# <a name="column-chart-and-line-chart-controls-in-powerapps"></a>PowerApps의 세로 막대형 차트 및 꺾은선형 차트 컨트롤
데이터를 x 및 축이 있는 그래프로 표시하는 컨트롤입니다.

## <a name="description"></a>설명
**세로 막대형 차트** 및 **꺾은선형 차트**는 그룹화된 컨트롤입니다. 각 그룹에는 세 가지 컨트롤 **[레이블](control-text-box.md)** (제목), 차트 그래픽 및 **범례**가 포함됩니다.

## <a name="chart-key-properties"></a>차트 키 속성
**[Items](properties-core.md)** – 갤러리, 목록 또는 차트와 같은 컨트롤에 표시되는 데이터 원본입니다.

**NumberOfSeries** – 세로 막대형 또는 꺾은선형 차트에 반영되는 데이터의 열 수입니다.

## <a name="additional-chart-properties"></a>추가 차트 속성
**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**GridStyle** – 세로 막대형 또는 꺾은선형 차트가 x-축, y-축, 둘 다 또는 없음을 보여줄지 여부를 선택합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**ItemColorSet** – 차트의 각 데이터 요소에 대한 색입니다.

**ItemsGap** – 세로 막대형 차트에서 막대 사이의 거리입니다.

* **ItemsGap** 속성은 **꺾은선형 차트** 컨트롤을 제외한 **세로 막대형 차트**에 사용 가능합니다.

**Markers** – 세로 막대형 또는 꺾은선형 차트가 각 데이터 요소의 값을 표시할지 여부를 선택합니다.

**MarkerSuffix** - **Markers** 속성이 **true**로 설정된 세로 막대형 차트의 각 값 다음에 나타나는 텍스트입니다.

* **MarkerSuffix** 속성은 **꺾은선형 차트** 컨트롤을 제외한 **세로 막대형 차트**에 사용 가능합니다.

**MinimumBarWidth** -막대형 차트에 있는 열의 가능한 가장 좁은 너비입니다.

* **MinimumBarWidth** 속성은 **꺾은선형 차트** 컨트롤을 제외한 **세로 막대형 차트**에 사용 가능합니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 아래쪽 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingTop](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 위쪽 가장자리 사이의 거리입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**SeriesAxisMax** - 세로 막대형 또는 꺾은선형 차트에 대한 y-축의 최대 값입니다.

* **SeriesAxisMax** 속성은 **꺾은선형 차트** 컨트롤을 제외한 **세로 막대형 차트** 컨트롤에 사용 가능합니다.

**SeriesAxisMin** - 세로 막대형 차트에 대한 y-축의 최소값을 결정하는 숫자입니다.

* **SeriesAxisMin** 속성은 **꺾은선형 차트** 컨트롤을 제외한 **세로 막대형 차트**에 사용 가능합니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**XLabelAngle** - 세로 막대형 또는 꺾은선형 차트의 x-축 아래에 레이블의 각도입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

**YAxisMax** - 꺾은선형 차트에 대한 y-축의 최대 값입니다.

* **YAxisMax** 속성은 **세로 막대형 차트** 컨트롤을 제외한 **꺾은선형 차트** 컨트롤에 사용 가능합니다.

**YAxisMin** - 꺾은선형 차트에 대한 y-축의 최소 값입니다.

* **YAxisMin** 속성은 **세로 막대형 차트** 컨트롤을 제외한 **꺾은선형 차트** 컨트롤에 사용 가능합니다.

**YLabelAngle** – 꺾은선형 또는 세로 막대형 차트의 y-축 옆에 있는 레이블의 각도입니다.

## <a name="related-functions"></a>관련된 함수
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>예
1. **[단추](control-button.md)** 컨트롤을 추가하고 이 수식에 **[OnSelect](properties-core.md)** 속성을 설정합니다.<br>
   **Collect(Revenue, {Year:"2013", Europa:24000, Ganymede:22300, Callisto:21200}, {Year:"2014", Europa:26500, Ganymede:25700, Callisto:24700},{Year:"2014", Europa:27900, Ganymede:28300, Callisto:25600})**
   
    [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 방법을 모르시나요?
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
2. F5 키를 누르고, **[단추](control-button.md)** 컨트롤을 클릭하거나 탭한 다음, 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.
3. **세로 막대형 차트** 컨트롤 또는 **꺾은선형 차트** 컨트롤을 추가하고 **[Items](properties-core.md)** 속성을 **Revenue**로 설정하고 **NumberOfSeries** 속성을 **3**으로 설정합니다.
   
    이 컨트롤은 3년 동안 각 제품에 대한 수익 데이터를 표시합니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **ItemColorSet**의 각 항목
* **ItemColorSet**의 모든 항목 및 배경색
* **[Color](properties-color-border.md)** 및 배경색

### <a name="screen-reader-support"></a>화면 판독기 지원
* 제목으로 사용할 차트 그래픽 바로 앞에 **[레이블](control-text-box.md)** 이 있어야 합니다.
* 차트 그래픽의 요약을 추가하는 것이 좋습니다. 예를 들어 “꺾은선형 차트는 올해 3월과 8월 사이의 지속적인 판매 증가세를 보여줍니다.”를 추가합니다.

    > [!NOTE]
  > 차트 그래픽 및 **범례**는 화면 읽기 프로그램 사용자에게 숨겨집니다. 대신 데이터의 테이블 형식으로 표시됩니다. 차트에서 데이터를 선택하는 단추를 순환할 수도 있습니다.

### <a name="low-vision-support"></a>저시력 사용자 지원
* 둘 이상의 계열이 표시되는 경우 **범례**가 있어야 합니다.
* **GridStyle**을 두 축을 모두 표시하는 GridStyle.All로 설정하는 것이 좋습니다. 이렇게 하면 모든 사용자가 데이터의 소수 자릿수를 정확하게 확인할 수 있습니다.
* **세로 막대형 차트**의 경우 **Markers**를 **true**로 설정하는 것이 좋습니다. 이렇게 하면 저시력 사용자가 열 값을 확인할 수 있습니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.

    > [!NOTE]
  > 키보드 사용자가 차트로 이동하면 차트에서 데이터를 선택하는 단추를 순환할 수 있습니다.
