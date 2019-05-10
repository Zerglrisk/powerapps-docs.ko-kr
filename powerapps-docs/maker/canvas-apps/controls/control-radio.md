---
title: '라디오 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 라디오 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/06/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2b1527f8a7bf157c88b85ae9721626b6fc14f5a9
ms.sourcegitcommit: 8d0ba2ec0c97be91d1350180dd6881c14dec8f2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65517359"
---
# <a name="radio-control-in-powerapps"></a>PowerApps의 라디오 컨트롤

사용자가 한 번에 하나만을 선택할 수 있는 여러 옵션을 보여주는 입력 컨트롤입니다.

## <a name="description"></a>설명

표준 HTML 입력 컨트롤인 **Radio** 컨트롤은 몇 가지 상호 배타적인 옵션과 함께 사용되는 것이 가장 적합합니다.

컨트롤에는 가로 또는 세로 레이아웃이 있을 수 있습니다.

## <a name="key-properties"></a>주요 속성

**[Default](properties-core.md)**  – 사용자가 변경하기 전의 컨트롤의 값입니다.

**[Items](properties-core.md)** – 갤러리, 목록 또는 차트와 같은 컨트롤에 표시되는 데이터 원본입니다.

**Layout** – 가로 또는 세로로 레이아웃되는지 옵션입니다.

**[Value](properties-core.md)** – 입력 컨트롤의 값입니다.

**선택한** – 선택한 항목을 나타내는 데이터 레코드입니다.

## <a name="all-properties"></a>모든 속성

**[Align](properties-text.md)** - 컨트롤의 가로 가운데를 기준으로 한 텍스트의 위치입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**[FontWeight](properties-text.md)**  – 컨트롤의 텍스트의 가중치: **굵게**, **Semibold**, **정상**, 또는 **밝은**.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**[LineHeight](properties-text.md)** - 예를 들어 텍스트 선 또는 목록의 항목 사이의 거리입니다.

**[OnChange](properties-core.md)** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 아래쪽 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingTop](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 위쪽 가장자리 사이의 거리입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**RadioBackgroundFill** – 라디오 단추 컨트롤에서 원의 배경색입니다.

**RadioBorderColor** - 라디오 단추 컨트롤에서 각 옵션의 원 색입니다.

**RadioSelectionFill** – 라디오 단추 컨트롤에서 선택된 원 안에 표시되는 색입니다.

**RadioSize** – 라디오 단추 컨트롤에서 원의 직경입니다.

**[Reset](properties-core.md)** – 컨트롤이 기본값으로 되돌아가는지 여부입니다.

**(사용 되지 않음) SelectedText** – 선택한 항목을 나타내는 하는 문자열 값입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수

[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>예

1. **라디오** 컨트롤을 추가하고 이름을 **Pricing**으로 지정한 후, **[Items](properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **["Standard", "Premium"]**

    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?

2. **[레이블](control-text-box.md)** 컨트롤을 추가하고 **라디오** 컨트롤 아래로 이동한 후, **[레이블](control-text-box.md)** 컨트롤의 **[Text](properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **If("Premium" in Pricing.Selected.Value, "$200 per day", "$150 per day")**

    **[If](../functions/function-if.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?

3. Alt 키를 누른 채로 **Radio** 컨트롤에서 옵션 중 하나를 선택합니다.

    **[레이블](control-text-box.md)** 컨트롤이 선택에 적합한 텍스트를 표시합니다.

4. (선택 사항) Alt 키를 누른 채로 다른 옵션을 선택하여 적합한 텍스트가 표시되는지 확인합니다.

## <a name="accessibility-guidelines"></a>접근성 지침

### <a name="color-contrast"></a>색 대비

[표준 색 대비 요구 사항](../accessible-apps-color.md) 외에도 다음 사이에 적절한 색 대비를 확인합니다.

* **RadioSelectionFill** 및 **RadioBackgroundFill**
* **RadioBackgroundFill** 및 **[Fill](properties-color-border.md)**

### <a name="screen-reader-support"></a>화면 reader 지원

* 모든 옵션에 **[값](properties-core.md)** 이 있는지 확인합니다.
* 제목으로 사용할 **라디오** 컨트롤 바로 앞에 **[레이블](control-text-box.md)** 을 추가하는 것이 좋습니다.

### <a name="keyboard-support"></a>키보드 지원

* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 속성을 0 이상으로 설정합니다.
* 집중 지표가 명확하게 표시되도록 **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 속성을 설정합니다.
