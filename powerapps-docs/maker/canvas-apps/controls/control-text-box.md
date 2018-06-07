---
title: '레이블 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 레이블 컨트롤에 관한 정보
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: caa8cf8678a509e4d66442f790b8d89905d48b92
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "31838605"
---
# <a name="label-control-in-powerapps"></a>PowerApps의 레이블 컨트롤
텍스트, 숫자, 날짜 또는 통화와 같은 데이터를 표시하는 상자입니다.

## <a name="description"></a>설명
레이블은 사용자가 지정한 데이터를 사용자가 입력한 대로 정확히 나타나는 텍스트의 리터럴 문자열, 또는 텍스트의 문자열로 평가되는 수식으로 표시합니다. 레이블은 다른 컨트롤(예: 등급 또는 오디오 컨트롤)을 식별하는 레이블로 다른 컨트롤(예: 화면을 식별하는 배너) 외부 또는 항목에 대한 특정 유형 정보를 표시하기 위해 갤러리에 나타나는 경우가 많습니다.

## <a name="key-properties"></a>주요 속성
**[AutoHeight](properties-core.md)**  – 구성된 모든 텍스트를 표시하도록 레이블이 높이를 자동 조절할 수 있게 하려면 true로 설정합니다. 텍스트를 할당된 높이로 자르려면 false로 설정합니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**[Text](properties-core.md)** – 컨트롤에 표시되는 텍스트 또는 사용자가 컨트롤에 입력하는 텍스트입니다.

**[DelayOutput](properties-core.md)**  – 텍스트를 입력하는 동안 작업을 지연하려면 true로 설정합니다.

## <a name="additional-properties"></a>추가 속성
**[Align](properties-text.md)** - 컨트롤의 가로 가운데를 기준으로 한 텍스트의 위치입니다.

**AutoHeight** – **[Text](properties-core.md)** 속성에 컨트롤이 한번에 표시할 수 있는 것보다 더 많은 문자가 포함된 경우 레이블이 **[Height](properties-size-location.md)** 속성을 자동으로 높일지 여부를 선택합니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[FontWeight](properties-text.md)** - 컨트롤의 텍스트 굵기입니다. **Bold**, **Semibold**, **Normal** 또는 **Lighter**로 설정합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[HoverColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**[LineHeight](properties-text.md)** - 예를 들어 텍스트 선 또는 목록의 항목 사이의 거리입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**Overflow** – **Wrap** 속성이 **true**로 설정되고 컨트롤의 **[Text](properties-core.md)** 속성에 해당 컨트롤이 1회에 표시할 수 있는 것보다 더 많은 문자가 포함된 경우 스크롤바를 레이블에 표시할지 여부를 선택합니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 아래쪽 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingTop](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 위쪽 가장자리 사이의 거리입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[VerticalAlign](properties-text.md)** – 컨트롤의 세로 가운데를 기준으로 한 텍스트의 위치입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**Wrap** – 너무 길어서 레이블에 들어 맞지 않는 텍스트를 다음 줄로 줄바꿈할지 여부를 선택합니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**Text**( *Number*, "*FormatCodes*" )](../functions/function-text.md)

## <a name="examples"></a>예
### <a name="show-a-literal-string"></a>리터럴 문자열을 표시합니다.
* 레이블을 추가하고 **[Text](properties-core.md)** 속성을 **"Hello, world"**(큰따옴표 포함)로 설정합니다.
  
    [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 방법을 모르시나요?

### <a name="show-the-result-of-a-formula"></a>수식의 결과를 표시합니다.
* 레이블을 추가하고 **[Text](properties-core.md)** 속성을 다음과 같은 수식으로 설정합니다.<br>
  **Today()**
  
    > [!NOTE]
> 식을 지정할 때 수식의 인수가 리터럴 문자열이 아닌 한 따옴표를 사용하지 않습니다. 이러한 경우에는 수식이 아닌 인수를 큰따옴표에 넣으세요.
  
    **[Today](../functions/function-now-today-istoday.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?

### <a name="show-data-in-a-gallery"></a>갤러리에 데이터 표시
이 절차에서는 유럽의 다양한 도시의 인구에 대한 데이터가 포함된 **CityPopulations**라고 하는 컬렉션을 만듭니다. 다음으로, 세 개의 레이블이 포함된 갤러리에서 해당 데이터를 보여주며 각 레이블이 표시할 데이터 형식을 지정합니다.

1. 단추 하나를 추가하고 이 수식에 **[OnSelect](properties-core.md)** 속성을 설정합니다.<br>
   **ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
2. F5 키를 누르고 단추를 선택한 다음, Esc 키를 누릅니다.
3. 텍스트 갤러리를 추가하고 **[Items](properties-core.md)** 속성을 **CityPopulations**로 설정합니다.
   
    갤러리를 선택하면 오른쪽 창에는 해당 갤러리 옵션이 나와 있습니다.
4. **Gallery1** 창에서 맨 위 목록을 **Population**로, 중간 목록을 **City**로, 맨 아래 목록을  **Country**로 설정합니다.


## <a name="accessibility-guidelines"></a>접근성 지침
**레이블** 컨트롤은 그 이름과 달리 다른 컨트롤의 레이블로 사용하지 않아도 되며, 텍스트의 일부를 표시하는 데 사용할 수 있습니다.

**레이블**은 **[OnSelect](properties-core.md)** 동작을 지정하여 단추 또는 링크로 사용할 수 있습니다. 이 방법을 사용하는 경우에는 단추와 유사한 접근성 고려 사항이 있습니다.

### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **[Color](properties-color-border.md)** 및 **[Fill](properties-color-border.md)**
* 기타 [표준 색 대비 요구 사항](../accessible-apps-color.md)이 적용됨(단추 또는 링크로 사용되는 경우)

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[Text](properties-core.md)** 가 있어야 합니다.

    > [!NOTE]
> 화면 읽기 프로그램은 **[TabIndex](properties-accessibility.md)** 가 0 이상이면 **레이블**을 단추로 처리합니다.

### <a name="low-vision-support"></a>저시력 사용자 지원
* **레이블**은 링크로 사용되는 경우 링크처럼 표시되어야 합니다.
    * **[Underline](properties-text.md)** 을 **true**로 설정합니다.
    * **[HoverColor](properties-color-border.md)** 는 **[Color](properties-color-border.md)** 와 달라야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 텍스트가 단추 또는 링크로 사용되는 경우 **[TabIndex](properties-accessibility.md)** 는 0 이상이어야 합니다. 이 경우 키보드 사용자가 이미지로 이동할 수 있습니다.
* 텍스트가 단추 또는 링크로 사용되는 경우 포커스 표시기는 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
