---
title: '확인란 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 확인란 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3504c80cbf2414959cadc218339d959d168d15ba
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61559452"
---
# <a name="check-box-control-in-powerapps"></a>PowerApps의 확인란 컨트롤
사용자가 값을 **true** 또는 **false**로 설정하기 위해 선택 또는 지울 수 있는 컨트롤입니다.

## <a name="description"></a>설명
사용자는 수십 년 동안 GUI에 사용해 온 이 유사한 컨트롤을 사용하여 부울 값을 지정할 수 있습니다.

## <a name="key-properties"></a>주요 속성
**[Default](properties-core.md)** – 사용자가 컨트롤을 변경하기 전의 초기 값입니다.

**[Text](properties-core.md)** – 컨트롤에 표시되는 텍스트 또는 사용자가 컨트롤에 입력하는 텍스트입니다.

**[Value](properties-core.md)** – 입력 컨트롤의 값입니다.

## <a name="additional-properties"></a>추가 속성
**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**CheckboxBackgroundFill** – 확인란 컨트롤에서 확인 표시를 둘러싼 박스의 배경색입니다.

**CheckboxBorderColor** – 확인란 컨트롤에서 확인 표시를 둘러싼 테두리의 색입니다.

**CheckboxSize** – 확인란 컨트롤에서 확인 표시를 둘러싼 박스의 너비와 높이입니다.

**CheckmarkFill** – 확인란 컨트롤에 있는 확인 표시의 색입니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**[FontWeight](properties-text.md) ** – 컨트롤의 텍스트의 가중치: **굵게**, **Semibold**, **정상**, 또는 **밝은**.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[HoverColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**OnCheck** - 확인란의 값이나 토글이 **true**로 변경되었을 때 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**OnUncheck** - 확인란의 값이나 토글이 **false**로 변경되었을 때 앱이 응답하는 방식입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 아래쪽 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingTop](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 위쪽 가장자리 사이의 거리입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[Reset](properties-core.md)** – 컨트롤이 기본값으로 되돌아가는지 여부입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[VerticalAlign](properties-text.md)** – 컨트롤의 세로 가운데를 기준으로 한 텍스트의 위치입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>예
1. **확인란** 컨트롤을 추가하고 이름을 **chkReserve**로 지정한 다음, **Reserve now**를 표시하도록 **[Text](properties-core.md)** 속성을 설정합니다.
   
    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. **[날짜 선택기](control-date-picker.md)** 컨트롤을 추가하고 다음 수식으로 **[Visible](properties-core.md)** 속성을 설정합니다.
   <br>**If(chkReserve.Value = true, true)**
   
    **[If](../functions/function-if.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
3. F5 키를 누르고 **chkReserve**를 클릭하거나 탭하여 **[Value](properties-core.md)** 속성을 **true**로 설정한 다음, **chkReserve**를 다시 클릭하거나 탭하여 **[Value](properties-core.md)** 속성을 **false**로 설정합니다.
   
    **[날짜 선택기](control-date-picker.md)** 는 **chkReserve**의 **[Value](properties-core.md)** 속성이 **false**가 아닌 **true**인 경우에 나타납니다.
4. 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **CheckmarkFill** 및 **CheckboxBackgroundFill**
* **CheckboxBackgroundFill** 및 **[Fill](properties-color-border.md)**
* **CheckboxBackgroundFill** 및 **[PressedFill](properties-color-border.md)**
* **CheckboxBackgroundFill** 및 **[HoverFill](properties-color-border.md)**

이는 [표준 색 대비 요구 사항](../accessible-apps-color.md)에 추가됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[Text](properties-core.md)** 가 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
 
