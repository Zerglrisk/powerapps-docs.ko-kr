---
title: '도형 컨트롤 및 아이콘 모양을: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯하여 도형 컨트롤과 아이콘 컨트롤에 관한 정보
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
ms.openlocfilehash: f46199d0265cf042ebae5dd27ae308fad7eca8e6
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732036"
---
# <a name="shape-controls-and-icon-controls-in-power-apps"></a>Power Apps의 셰이프 컨트롤 및 아이콘 컨트롤
모양 및 동작 속성을 구성할 수 있는 그래픽입니다.

## <a name="description"></a>설명
이러한 컨트롤에는 fill, size 및 location 등의 속성을 구성할 수 있는 화살표, 기하학적 도형, 작업 아이콘 및 기호가 있습니다. 사용자가 컨트롤을 선택 하는 경우 앱이 응답 하도록 **[Onselect](properties-core.md)** 속성을 구성할 수도 있습니다.

## <a name="key-properties-icons-and-shapes"></a>키 속성 (아이콘 및 셰이프)
**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Onselect](properties-core.md)** – 사용자가 컨트롤을 선택할 때 앱이 응답 하는 방식입니다.

## <a name="key-properties-icons-only"></a>키 속성 (아이콘만 해당)

**Icon** -표시할 아이콘의 유형 (예: **ArrowDown** 또는 **ShoppingCart**)입니다. 

**회전** -아이콘을 회전할 각도입니다. 

**Color** -이름 또는 RGBA 값을 기준으로 아이콘의 색입니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤을 선택 하는 경우 컨트롤의 테두리 색입니다.

**[보도 Sedfill](properties-color-border.md)** – 사용자가 컨트롤을 선택 하는 경우 컨트롤의 배경색입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수

[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>예

1. 기본 **[화면](control-screen.md)** 컨트롤의 이름을 **Target**으로 지정하고 **[레이블](control-text-box.md)** 컨트롤을 추가하며 **[Text](properties-core.md)** 속성을 **Target**을 표시하도록 설정합니다.

    [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 방법을 모르시나요?

1. **[화면](control-screen.md)** 컨트롤을 추가하고 이름을 **Source**로 지정합니다.

1. **Source**에서 **도형** 컨트롤을 추가하고 다음 수식에 **[OnSelect](properties-core.md)** 속성을 설정합니다.

  `Navigate(Target, ScreenTransition.Fade)`
  
1. F5 키를 누른 다음 **셰이프** 컨트롤을 선택 합니다.

    **Target** 화면이 나타납니다.

1. (선택 사항) Esc 키를 눌러 기본 작업 영역으로 돌아가고 **도형** 컨트롤을 **Target**에 추가한 다음, **도형** 컨트롤의 **[OnSelect](properties-core.md)** 속성을 다음 서식으로 설정합니다.

  `Navigate(Source, ScreenTransition.Fade)`

## <a name="accessibility-guidelines"></a>접근성 지침

### <a name="color-contrast"></a>색 대비

다음은 단추로 사용되거나 장식용으로만 사용되지 않는 그래픽에만 적용됩니다.

아이콘:
- **[Color](properties-color-border.md)** 및 **[Fill](properties-color-border.md)**
- 기타 [표준 색 대비 요구 사항](../accessible-apps-color.md)이 적용됨(단추로 사용되는 경우)

테두리가 있는 셰이프:
- **[BorderColor](properties-color-border.md)** 및 컨트롤 외부 색
- **[FocusedBorderColor](properties-color-border.md)** 및 컨트롤 외부 색(단추로 사용되는 경우)

테두리가 없는 셰이프:
- **[Fill](properties-color-border.md)** 및 컨트롤 외부 색
- **[PressedFill](properties-color-border.md)** 및 컨트롤 외부 색(단추로 사용되는 경우)
- **[HoverFill](properties-color-border.md)** 및 컨트롤 외부 색(단추로 사용되는 경우)

### <a name="screen-reader-support"></a>화면 reader 지원
- 그래픽이 단추로 사용 되는 경우 **[AccessibleLabel](properties-accessibility.md)** 는 비어 있지 않은 문자열로 설정 해야 하며 그렇지 않은 경우에는 장식이 아닌 문자열로 설정 해야 합니다.

- 그래픽이 중복 정보를 제공 하거나 장식에만 해당 되는 경우 **[AccessibleLabel](properties-accessibility.md)** 은 비어 있거나 빈 문자열 **""** 이어야 합니다. 이 값을 설정 하면 화면 판독기에서 그래픽을 무시 합니다.

예를 들어 **설정 아이콘의** **[AccessibleLabel](properties-accessibility.md)** 속성을 **설정**으로 설정할 수 있습니다. 이 아이콘은 단추로 사용 되지 않습니다. **설정**이라는 **[레이블](control-text-box.md)** 옆에 있습니다. 화면 읽기 권한자는 아이콘 및 레이블을 모두 불필요 한 자세한 정보 표시로 **설정**합니다. 이 경우 아이콘에는 **[AccessibleLabel](properties-accessibility.md)** 필요 하지 않습니다.

> [!IMPORTANT]
> **[AccessibleLabel](properties-accessibility.md)** 이 빈 문자열로 설정 되 고 **[TabIndex](properties-accessibility.md)** 가 0 이상으로 설정 된 경우 화면 판독기는 아이콘이 나 모양을 **단추로** 읽습니다. 이러한 아이콘이 나 도형은 단추로 렌더링 됩니다. 

### <a name="keyboard-support"></a>키보드 지원
- 그래픽이 단추로 사용 되는 경우 **[TabIndex](properties-accessibility.md)** 는 0 이상 이어야 합니다. 아이콘 또는 모양에 대해이 값을 설정 하면 키보드 사용자가이 값을 탐색할 수 있습니다.

- 그래픽이 단추로 사용 되는 경우 포커스 표시기를 명확 하 게 표시 해야 합니다. 이 결과를 얻으려면 **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용 합니다.

    > [!NOTE]
    > **[TabIndex](properties-accessibility.md)** 가 0 이상이면 아이콘 또는 셰이프가 단추로 렌더링됩니다. 모양은 변경 되지 않지만 화면 판독기는 이미지를 단추로 올바르게 식별 합니다. **[TabIndex](properties-accessibility.md)** 가 0보다 작으면 아이콘 또는 셰이프가 이미지로 식별됩니다.
