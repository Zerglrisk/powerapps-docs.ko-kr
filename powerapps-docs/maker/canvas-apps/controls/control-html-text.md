---
title: 'HTML 텍스트 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 HTML 텍스트 컨트롤에 관한 정보
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed104f5ae4e7244e5a49b6cbc67745fd2f9e24dc
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678606"
---
# <a name="html-text-control-in-powerapps"></a>PowerApps의 HTML 텍스트 컨트롤
텍스트를 표시하고 HTML 태그를 서식 지정으로 변환하는 상자입니다.

## <a name="description"></a>설명
**HTML 텍스트** 컨트롤은 일반 텍스트와 숫자를 표시할 뿐 아니라 줄바꿈 없는 공백 같은 HTML 태그도 변환합니다.

## <a name="key-properties"></a>주요 속성
**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**HtmlText** – HTML 텍스트 컨트롤에 표시되며 HTML 태그를 포함할 수 있는 텍스트입니다.

## <a name="additional-properties"></a>추가 속성
**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 하단 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 상단 가장자리 사이의 거리입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**Find**( *FindString*, *WithinString* )](../functions/function-find.md)

## <a name="example"></a>예
1. **[레이블](control-text-box.md)** 컨트롤을 추가하고 이름을 **Source**로 지정한 다음 **[Text](properties-core.md)** 속성을 다음 문자열로 지정합니다.

"\<p&gt;본사에서는\&nbsp;매우 \&quot;심층적인\&quot; 세계화 및 지역화를 이뤄냈습니다.\<p&gt;"

[컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?

1. **HTML 텍스트** 컨트롤을 추가하고 **HtmlText** 속성을 다음 값으로 설정합니다.<br>
   **Source.Text**
   
     **HTML 텍스트** 컨트롤에 **[레이블](control-text-box.md)** 컨트롤과 같은 텍스트가 표시되나 태그가 적합한 문자로 변환됩니다.


## <a name="accessibility-guidelines"></a>접근성 지침
**HTML 텍스트**는 대화형으로 사용할 수 없습니다. 텍스트 표시에만 사용해야 합니다.

### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **[Color](properties-color-border.md)** 및 **[Fill](properties-color-border.md)**
* 사용자 지정 색 및 배경이 있는 텍스트

### <a name="screen-reader-support"></a>화면 판독기 지원
* **HtmlText**가 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* **HtmlText**는 `<button>`, `<a>` 또는 `<input>`과 같은 대화형 요소를 포함해서는 안 됩니다. Power Apps의 **[TabIndex](properties-accessibility.md)** 시스템은 **HtmlText**내부의 요소를 고려 하지 않습니다.
