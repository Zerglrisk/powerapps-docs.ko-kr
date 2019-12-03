---
title: '등급 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 등급 컨트롤에 관한 정보
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
ms.openlocfilehash: a5e91f8ff3b760e173ac01b32a68c7f60a488014
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732119"
---
# <a name="rating-control-in-power-apps"></a>Power Apps의 등급 제어
1과 사용자가 지정하는 최대 숫자 사이의 값을 나타낼 수 있는 컨트롤입니다.

## <a name="description"></a>설명
이 컨트롤에서 사용자는 몇 개의 별을 선택하여 좋아하는 정도 등을 나타낼 수 있습니다.

## <a name="key-properties"></a>주요 속성
**[Default](properties-core.md)** – 사용자가 컨트롤을 변경하기 전의 초기 값입니다.

**Max** – 사용자가 슬라이더 또는 등급을 설정할 수 있는 최대값입니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[OnChange](properties-core.md)** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**RatingFill** – 등급 컨트롤에서 별의 색입니다.

**ReadOnly** – 사용자가 슬라이더 또는 등급 컨트롤의 값을 변경할 수 있는지 여부입니다.

**[Reset](properties-core.md)** – 컨트롤을 기본값으로 되돌릴지 여부를 선택합니다.

**ShowValue** – 사용자가 해당 값을 변경하거나 컨트롤을 마우스로 가리킬 때 슬라이더 또는 등급의 값이 나타나는지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**평균**(*Value1*, *Value2,* ... )](../functions/function-aggregates.md)

## <a name="example"></a>예
1. **등급** 컨트롤을 추가하고 **Quantitative**로 이름을 지정합니다.
   
    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. **[텍스트 입력](control-text-input.md)** 컨트롤을 추가하고 **Qualitative**로 이름을 지정한 후 **등급** 컨트롤 아래로 이동합니다.
3. **[텍스트 입력](control-text-input.md)** 의 **[Default](properties-core.md)** 속성을 **""** 로 설정하고 **HintText**를 다음 수식으로 설정합니다.
   <br>**If(Quantitative.Value > 3, "특별히 무엇을 하는 것이 좋았나요?", "개선하려면 어떻게 하나요?")**
   
    **[If](../functions/function-if.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
4. F5 키를 누르거나 **등급** 컨트롤에서 4개 또는 5개의 별을 클릭하거나 탭합니다.
   
    **[텍스트 입력](control-text-input.md)** 컨트롤의 힌트 텍스트가 변경되어 높은 등급을 반영합니다.
5. **Quantitative**에서 4개 미만의 별을 클릭하거나 탭합니다.
   
    **[텍스트 입력](control-text-input.md)** 컨트롤의 힌트 텍스트가 변경되어 낮은 등급을 반영합니다.
6. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **RatingFill** 및 **[Fill](properties-color-border.md)**

이는 [표준 색 대비 요구 사항](../accessible-apps-color.md)에 추가됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

    > [!NOTE]
  > 화면 읽기 프로그램은 **등급** 컨트롤을 라디오 단추로 처리합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
* 별이 너무 많은 경우에는 다른 컨트롤을 사용하는 것이 좋습니다. 키보드로 탐색하는 것은 지루하고 터치 스크린으로 정확하게 선택하는 것은 어려울 수 있습니다.

    > [!NOTE]
  > **등급**에서 라디오 단추에 대해 동일한 키보드 조작을 사용할 수 있습니다.
