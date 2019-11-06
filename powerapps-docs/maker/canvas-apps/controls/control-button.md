---
title: '단추 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 단추 컨트롤에 관한 정보
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
ms.openlocfilehash: 750b02bdd3363f03ad0f32ae1fcbc59d7c5c3f3e
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650729"
---
# <a name="button-control-in-powerapps"></a>PowerApps의 단추 컨트롤
사용자가 클릭하거나 탭하여 앱과 상호 작용할 수 있는 컨트롤입니다.

## <a name="description"></a>설명
**단추** 컨트롤의 **[OnSelect](properties-core.md)** 속성을 구성하여 사용자가 컨트롤을 클릭하거나 탭할 때 하나 이상의 수식을 실행합니다.

## <a name="key-properties"></a>주요 속성
**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[Text](properties-core.md)** – 컨트롤에 표시되는 텍스트 또는 사용자가 컨트롤에 입력하는 텍스트입니다.

## <a name="additional-properties"></a>추가 속성
**[Align](properties-text.md)** - 컨트롤의 가로 가운데를 기준으로 한 텍스트의 위치입니다.

**AutoDisableOnSelect** – **OnSelect** 동작이 실행 중일 때 컨트롤을 자동으로 비활성화합니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**[FontWeight](properties-text.md)** - 컨트롤의 텍스트 굵기입니다. **Bold**, **Semibold**, **Normal** 또는 **Lighter**로 설정합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[HoverColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 하단 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 상단 가장자리 사이의 거리입니다.

**Pressed** – 컨트롤을 누른 상태이면 *True*, 그렇지 않으면 *false*입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[RadiusBottomLeft](properties-size-location.md)** – 컨트롤 왼쪽 아래 모서리의 둥근 정도입니다.

**[RadiusBottomRight](properties-size-location.md)** – 컨트롤 오른쪽 아래 모서리의 둥근 정도입니다.

**[RadiusTopLeft](properties-size-location.md)** – 컨트롤 왼쪽 위 모서리의 둥근 정도입니다.

**[RadiusTopRight](properties-size-location.md)** – 컨트롤 오른쪽 위 모서리의 둥근 정도입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[VerticalAlign](properties-text.md)** – 컨트롤의 세로 가운데를 기준으로 한 텍스트의 위치입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
**[Navigate( *ScreenName*, *ScreenTransitionValue* )](../functions/function-navigate.md)**

## <a name="examples"></a>예
### <a name="add-a-basic-formula-to-a-button"></a>단추에 기본 수식 추가
1. **[텍스트 입력](control-text-input.md)** 컨트롤을 추가하고 이름을 **Source**로 지정합니다.
   
    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. **단추** 컨트롤을 추가하고 **[Text](properties-core.md)** 속성을 "Add"로 설정하고 **[OnSelect](properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
   **UpdateContext({Total:Total + Value(Source.Text)})**
   
    **[UpdateContext](../functions/function-updatecontext.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
3. **[레이블](control-text-box.md)** 컨트롤을 추가하고 **[Text](properties-core.md)** 속성을 **Total**로 설정한 다음 **F5**를 누릅니다.
4. **원본**에서 기본 텍스트를 지우고 그 안에 숫자를 입력한 다음 **추가**를 클릭하거나 탭합니다.
   
    **[레이블](control-text-box.md)** 컨트롤이 입력한 숫자를 보여 줍니다.
5. **원본**에서 숫자를 지우고 그 안에 다른 숫자를 입력한 다음 **추가**를 클릭하거나 탭합니다.
   
    **[레이블](control-text-box.md)** 컨트롤이 입력한 두 숫자의 합계를 표시합니다.
6. (선택 사항) 이전 단계를 한 번 이상 반복합니다.
7. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다(또는 오른쪽 위 모서리에 있는 닫기 아이콘을 클릭하거나 탭합니다).

### <a name="configure-a-button-with-multiple-formulas"></a>여러 수식으로 단추 구성
입력 사이에 **텍스트 입력** 컨트롤을 지우는 수식을 추가합니다.

1. **원본**의 **[HintText](control-text-input.md)** 속성을 "숫자 입력"으로 설정합니다.
2. **추가**의 **[OnSelect](properties-core.md)** 속성을 이 수식으로 설정합니다.
   
    **UpdateContext({Total:Total + Value(Source.Text)});<br>UpdateContext({ClearInput: ""})**
   
    > [!NOTE]
   > 여러 수식은 세미콜론 “ **;** ”으로 구분합니다.
3. **원본**의 **[기본](properties-core.md)** 속성을 **ClearInput**으로 설정합니다.
4. **F5** 키를 누른 다음 여러 숫자를 동시에 추가하여 앱을 테스트합니다.

### <a name="add-another-button-to-reset-the-total"></a>총계를 재설정하는 다른 단추 추가
계산 사이에 합계를 지우는 두 번째 단추를 추가합니다.

1. 다른 **단추** 컨트롤을 추가하고 **[Text](properties-core.md)** 속성을 "Clear"로 설정하고 **[OnSelect](properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **UpdateContext({Total:0})**
2. **F5**를 누르고 여러 숫자를 함께 추가한 다음 **지우기**를 클릭하거나 탭하여 총계를 재설정합니다.

### <a name="change-a-buttons-appearance"></a>단추의 모양 변경
#### <a name="change-a-buttons-shape"></a>단추 모양 변경
기본적으로 PowerApps는 모서리가 둥근 직사각 **단추** 컨트롤을 만듭니다. **단추** 컨트롤의 **[Height](properties-size-location.md)** , **[Width](properties-size-location.md)** 및 **[Radius](properties-size-location.md)** 속성을 설정하여 기본적인 모양을 수정할 수 있습니다.

> [!NOTE]
> [아이콘 및 셰이프](control-shapes-icons.md)는 다양한 디자인을 제공하며 **단추** 컨트롤이 수행하는 것과 동일한 기본 함수 중 일부를 수행할 수 있습니다. 그러나  **[아이콘 및 셰이프](control-shapes-icons.md)** 에는 **[Text](properties-core.md)** 속성이 없습니다.

1. **단추** 컨트롤을 추가하고 **[Height](properties-size-location.md)** 및 **[Width](properties-size-location.md)** 속성을 **300**으로 설정하여 큰 정사각 단추를 만듭니다.
2. **[RadiusTopLeft](properties-size-location.md)** , **[RadiusTopRight](properties-size-location.md)** , **[RadiusBottomLeft](properties-size-location.md)** 및 **[RadiusBottomRight](properties-size-location.md)** 속성을 수정하여 각 모서리의 곡률 정도를 조절합니다. 각각 300 x 300 정사각 단추에서 시작하는 다양한 셰이프의 예는 다음과 같습니다.
   
   * 4개 **[Radius](properties-size-location.md)** 값을 모두 **150**으로 설정하여 원을 만듭니다.
   * **[RadiusTopLeft](properties-size-location.md)** 및 **[RadiusBottomRight](properties-size-location.md)** 의 값을 **300**으로 설정하여 리프형 **단추**를 만듭니다.
   * **[RadiusTopLeft](properties-size-location.md)** 및 **[RadiusTopRight](properties-size-location.md)** 의 값을 **300**, **[RadiusBottomLeft](properties-size-location.md)** 및 **[RadiusBottomRight](properties-size-location.md)** 의 값을 **100** 으로 설정하여 탭 모양 단추를 만듭니다.

#### <a name="change-a-buttons-color-when-you-hover-over-it"></a>마우스로 가리킬 때 단추의 색 변경
기본적으로 **단추** 컨트롤의 채우기 색은 마우스로 가리킬 때 20% 흐려집니다. **[ColorFade](../functions/function-colors.md)** 함수를 사용하는 **[HoverFill](properties-color-border.md)** 속성을 변경하여 이 동작을 조정할 수 있습니다. **[ColorFade](../functions/function-colors.md)** 수식을 양의 백분율로 설정하면 마우스를 단추에 가져갔을 때 색이 더 밝아지며 음수로 설정하면 더 어두워집니다.

* 만든 단추 중 하나의 **[HoverFill](properties-color-border.md)** 속성에서 **[ColorFade](../functions/function-colors.md)** 를 변경하고 결과를 확인합니다.

**ColorValue("Red")** 에서처럼 **[ColorFade](../functions/function-colors.md)** 함수 대신 **[HoverFill](properties-color-border.md)** 속성을 **[ColorValue](../functions/function-colors.md)** 함수가 포함된 수식으로 설정하여 **단추** 색을 지정할 수도 있습니다.

> [!NOTE]
> 색 값은 이름 또는 16진 값의 CSS 색 정의가 될 수 있습니다.

* 만든 버튼 중 하나에서 **[ColorFade](../functions/function-colors.md)** 함수를 **[ColorValue](../functions/function-colors.md)** 함수로 대체하고 결과를 확인합니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
* [표준 색 대비 요구 사항](../accessible-apps-color.md)이 적용됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[Text](properties-core.md)** 가 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
 
