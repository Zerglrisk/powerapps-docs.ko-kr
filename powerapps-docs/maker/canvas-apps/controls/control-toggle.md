---
title: '토글 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 토글 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4ec115eecc676a7ec5bea3b04b135eeb63268449
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993260"
---
# <a name="toggle-control-in-powerapps"></a>PowerApps의 토글 컨트롤
핸들을 움직여 사용자가 켜거나 끌 수 있는 컨트롤입니다.

## <a name="description"></a>설명
토글은 최근 GUI용으로 설계되었으나 확인란과 동일한 방식으로 작동합니다.

## <a name="key-properties"></a>주요 속성
**[Default](properties-core.md)** – 사용자가 컨트롤을 변경하기 전의 초기 값입니다.

**[Value](properties-core.md)** – 입력 컨트롤의 값입니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**FalseFill** – 토글이 꺼진 경우 토글 채우기 색입니다.

**FalseHoverFill** – 토글이 꺼진 경우 가리킨 항목의 채우기 색입니다.

**FalseText** – 토글이 꺼진 경우 표시되는 텍스트입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**HandleFill** - 토글 핸들의 채우기 색입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[OnChange](properties-core.md)** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

**OnCheck** - 확인란의 값이나 토글이 **true**로 변경되었을 때 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**OnUncheck** - 확인란의 값이나 토글이 **false**로 변경되었을 때 앱이 응답하는 방식입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**RailFill** – 토글 컨트롤의 값이 **false**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 오른쪽의 선 색입니다.

**RailHoverFill** – 토글 컨트롤 또는 슬라이더에 마우스를 가져가는 경우, 토글 컨트롤의 값이 **false**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 오른쪽의 선 색입니다.

**[Reset](properties-core.md)** – 컨트롤이 기본값으로 되돌아가는지 여부입니다.

**ShowLabel** – 토글 컨트롤 옆에 텍스트 레이블을 표시할지 여부입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**TextPosition** – 레이블을 토클 컨트롤의 왼쪽에 둘지 또는 오른쪽에 둘지 여부입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**TrueFill** – 토글 켜진 경우 토글 채우기 색입니다.

**TrueHoverFill** – 토글이 켜진 경우 가리킨 항목의 채우기 색입니다.

**TrueText** – 토글이 켜진 경우 표시되는 텍스트입니다.

**ValueFill** – 토글 컨트롤의 값이 **true**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 왼쪽의 선 색입니다.

**ValueHoverFill** – 토글 컨트롤 또는 슬라이더 위에 마우스 포인터를 두고 있는 경우, 토글 컨트롤의 값이 **true**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 왼쪽의 선 색입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>예
1. 토글을 추가하고 이름을**MemberDiscount**로 지정합니다.

    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. 레이블을 추가하고 **[Text](properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**If(MemberDiscount.Value = true, "Price: $75", "Price: $100")**

    **[If](../functions/function-if.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
3. F5 키를 누르고 **MemberDiscount**의 값을 변경합니다.

    레이블에 **MemberDiscount**의 설정 여부에 따라 다른 가격이 표시됩니다.
4. 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **HandleFill** 및 **FalseFill**
* **HandleFill** 및 **FalseHoverFill**
* **HandleFill** 및 **TrueFill**
* **HandleFill** 및 **TrueHoverFill**
* **FalseFill** 및 컨트롤 외부 색
* **FalseHoverFill** 및 컨트롤 외부 색
* **TrueFill** 및 컨트롤 외부 색
* **TrueHoverFill** 및 컨트롤 외부 색

이는 [표준 색 대비 요구 사항](../accessible-apps-color.md)에 추가됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.
* **FalseText**가 있어야 합니다.
* **TrueText**가 있어야 합니다.

### <a name="low-vision-support"></a>저시력 사용자 지원
* 사용자가 토글 값을 빠르게 확인할 수 있도록 **ShowLabel**을 **true**로 설정하는 것이 좋습니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
