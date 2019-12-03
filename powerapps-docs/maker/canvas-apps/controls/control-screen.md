---
title: '화면 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 화면 컨트롤 관련 정보
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b0e189bc2bfd922839373f009fcc54a34217daba
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732070"
---
# <a name="screen-control-in-power-apps"></a>Power Apps의 화면 컨트롤

앱에서 하나 이상의 다른 컨트롤을 포함하는 UI 요소입니다.

## <a name="description"></a>설명

대부분의 **[레이블](control-text-box.md)** 컨트롤, **[버튼](control-button.md)** 컨트롤 및 기타 데이터를 표시하고 탐색을 지원하는 컨트롤 등을 포함하는 여러 **화면** 컨트롤이 있습니다. 화면을 추가 하 고, 화면 순서를 변경 하 고, 탐색을 구성 하는 방법에 대 한 자세한 내용은 [화면 추가](../add-screen-context-variables.md)를 참조 하세요.

## <a name="key-properties"></a>주요 속성

**[BackgroundImage](properties-visual.md)** – 화면의 배경에 표시되는 이미지 파일의 이름입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

## <a name="additional-properties"></a>추가 속성

**Height** -화면의 높이입니다. 앱이 응답 하 고 ([**크기 조정**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) 이 **꺼져**있음) 앱이 실행 되는 장치가이 속성 보다 짧으면 화면을 세로로 스크롤할 수 있습니다.

**[ImagePosition](properties-visual.md)** – 이미지와 같은 크기가 아닌 경우 컨트롤 또는 화면에 있는 이미지의 위치입니다(**채우기**, **맞춤**, **늘이기**, **타일** 또는 **가운데**).

**이름** -화면 이름입니다.

**OnHidden** – 사용자가 화면에서 나갈 때 앱의 동작입니다.

**OnVisible** – 사용자가 화면으로 들어올 때 앱의 동작입니다.  이 속성을 사용 하 여 화면에서 사용 하는 변수 및 미리 로드 데이터를 설정 합니다.  앱이 시작 될 때 한 번 설정 하려면 [**app.config**](../functions/object-app.md#onstart-property) 속성을 사용 합니다.

**방향** -화면의 방향입니다. **너비가** **높이**보다 큰 경우 방향은 **레이아웃이 됩니다. 가로**방향입니다. 그렇지 않으면 **레이아웃. 세로입니다.**

**Size** -화면 크기를 분류 하는 양의 정수입니다. 분류는 화면의 **Width** 속성을 [**app.config 중단점**](../functions/signals.md) 속성의 값과 비교 하 여 결정 됩니다. **ScreenSize** 형식은 1에서 4 까지의 정수에 해당 하는 4 개의 값 (**Small**, **Medium**, **Large**및 **ExtraLarge**)으로 구성 됩니다.

**Width** -화면의 너비입니다. 앱이 응답 하 고 ([**크기 조정**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) 이 **꺼져**있음) 앱이 실행 되는 장치가이 속성 보다 좁은 경우 화면은 가로로 스크롤할 수 있습니다.

## <a name="related-functions"></a>관련된 함수

[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>예

1. **[라디오](control-radio.md)** 컨트롤을 추가하고 이름을 **ScreenFills**로 지정한 다음, **[Items](properties-core.md)** 속성을 다음 값으로 설정합니다.

    `["Red", "Green"]`

    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?

1. 기본 **화면** 컨트롤의 이름을 **Source**로 지정한 다음, 다른 **화면** 컨트롤을 추가하고 이름을 **Target**으로 지정합니다.

1. **소스**에서 **[셰이프](control-shapes-icons.md)** 컨트롤 (예: 화살표)을 추가 하 고 **[onselect](properties-core.md)** 속성을 다음 수식으로 설정 합니다.

    `Navigate(Target, ScreenTransition.Fade)`

    **[Navigate](../functions/function-navigate.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?

1. **Target**에서 **[셰이프](control-shapes-icons.md)** 컨트롤(예: 화살표)을 추가하고 **[OnSelect](properties-core.md)** 속성을 다음 수식으로 설정합니다.

    `Navigate(Source, ScreenTransition.Fade)`

1. **Target**의 **[Fill](properties-color-border.md)** 속성을 다음 수식으로 설정합니다.

    `If("Red" in ScreenFills.Selected.Value, RGBA(255, 0, 0, 1), RGBA(54, 176, 75, 1))`

1. **원본** 화면을 선택 하 고 Alt 키를 누른 상태에서 **[라디오](control-radio.md)** 컨트롤의 옵션 중 하나를 선택한 다음 **[셰이프](control-shapes-icons.md)** 컨트롤을 선택 합니다.

    선택한 색에 **대상** 이 표시 됩니다.

1. **대상**에서 **원본**으로 반환할 **[셰이프](control-shapes-icons.md)** 컨트롤을 선택 합니다.

1. 필드 **[라디오](control-radio.md)** 컨트롤에서 기타 옵션을 선택한 다음 **[셰이프](control-shapes-icons.md)** 컨트롤을 선택 하 여 해당 **대상이** 다른 색에 표시 되는지 확인 합니다.

1. 필드 왼쪽 탐색 모음에서 **Target** 을 마우스로 가리켜 표시 되는 줄임표를 선택한 다음 **위로 이동**을 선택 하 여 화면을 다시 정렬 합니다.

    사용자가 앱을 열 때 **대상이** 먼저 표시 됩니다.

## <a name="accessibility-guidelines"></a>접근성 지침

### <a name="color-contrast"></a>색 대비

**화면**이 텍스트의 효과적인 배경인 경우 다음 사이에 적절한 색 대비가 있어야 합니다.

- **[채우기](properties-color-border.md)** 및 텍스트
- **[BackgroundImage](properties-visual.md)** 및 텍스트(해당하는 경우)

예를 들어 **화면**에 **[레이블](control-text-box.md)** 이 포함되어 있고 레이블에 투명한 채우기가 있는 경우 화면의 **[채우기](properties-color-border.md)** 는 효과적으로 레이블의 배경색이 됩니다.

텍스트 외에도 **[평가](control-rating.md)** 컨트롤의 별표 이미지 같은 필수 그래픽 개체에 대한 색 대비를 확인하는 것이 좋습니다.

### <a name="screen-reader-support"></a>화면 판독기 지원

- 각 **화면**에 대한 의미 있는 이름이 있어야 합니다. [컨트롤] 창의 트리 뷰 또는 [속성] 창의 헤더에서 다른 컨트롤과 동일한 방법으로 화면 이름을 보고 편집할 수 있습니다.

    > [!NOTE]
  > 새 **화면**이 로드되면 화면 읽기 프로그램이 해당 이름을 알립니다.
