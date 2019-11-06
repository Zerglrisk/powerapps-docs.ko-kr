---
title: '슬라이더 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 슬라이더 컨트롤에 관한 정보
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
ms.openlocfilehash: 45314238783e4cbf53332e8531bc0d76c679265f
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73649855"
---
# <a name="slider-control-in-powerapps"></a>PowerApps의 슬라이더 컨트롤
사용자가 핸들을 끌어 값을 지정할 수 있는 컨트롤입니다.

## <a name="description"></a>설명
사용자는 사용자가 선택하는 방향에 따라 슬라이더의 핸들을 좌우 또는 상하로 끌어 지정하는 최소 값과 최대 값 사이의 값을 나타낼 수 있습니다.

## <a name="key-properties"></a>주요 속성
**[Default](properties-core.md)** – 사용자가 컨트롤을 변경하기 전의 초기 값입니다.

**Max** – 사용자가 슬라이더 또는 등급을 설정할 수 있는 최대값입니다.

**Min** – 사용자가 슬라이더를 설정할 수 있는 최소 값입니다.

**[Value](properties-core.md)** – 입력 컨트롤의 값입니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**HandleActiveFill** – 사용자가 값 변경 시 슬라이더에 대한 핸들의 색입니다.

**HandleFill** – 토클 또는 슬라이더 컨트롤에서 핸들(위치를 바꾸는 요소)의 색입니다.

**HandleHoverFill** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 슬라이더의 핸들 색입니다.

**HandleSize** - 핸들의 지름입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**Layout** – 사용자가 위에서 아래로(**Vertical**) 또는 왼쪽에서 오른쪽으로(**Horizontal**) 갤러리를 스크롤하거나 슬라이더를 조정할지 여부입니다.

**[OnChange](properties-core.md)** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**RailFill** – 토글 컨트롤의 값이 **false**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 오른쪽의 선 색입니다.

**RailHoverFill** – 토글 컨트롤 또는 슬라이더에 마우스를 가져가는 경우, 토글 컨트롤의 값이 **false**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 오른쪽의 선 색입니다.

**ReadOnly** – 사용자가 슬라이더 또는 등급 컨트롤의 값을 변경할 수 있는지 여부입니다.

**[Reset](properties-core.md)** – 컨트롤을 기본값으로 되돌릴지 여부를 선택합니다.

**ShowValue** – 사용자가 해당 값을 변경하거나 컨트롤을 마우스로 가리킬 때 슬라이더 또는 등급의 값이 나타나는지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**ValueFill** – 토글 컨트롤의 값이 **true**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 왼쪽의 선 색입니다.

**ValueHoverFill** – 토글 컨트롤이나 슬라이더에 마우스 포인터를 두고 있으면 값이 **true**일 때 토글 컨트롤의 직사각형 배경색이거나 슬라이더 컨트롤에서 핸들 왼쪽의 라인 색입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**Sum**( *Value1*, *Value2* )](../functions/function-aggregates.md)

## <a name="example"></a>예
1. 단추 하나를 추가하고 **[OnSelect](properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
   
    **[ClearCollect](../functions/function-clear-collect-clearcollect.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
2. F5 키를 누르고 단추를 선택한 다음, Esc 키를 누릅니다.
3. 슬라이더를 추가하고 단추 아래로 이동한 다음 슬라이더의 이름을 **MinPopulation**으로 지정합니다.
4. 슬라이더의 **Max** 속성을 **5000000**, **Min** 속성을 **1000000**으로 설정합니다.
5. 텍스트 갤러리를 세로 방향으로 추가하고 슬라이더 아래로 이동한 다음, 갤러리의 **[Items](properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
   **Filter(CityPopulations, Population > MinPopulation)**
6. 갤러리의 첫 항목에서 맨 위 레이블의 **[Text](properties-core.md)** 속성을 **ThisItem.City**로 설정하고 맨 아래 레이블의 **[Text](properties-core.md)** 속성을 다음 수식으로 설정합니다.<br> **Text(ThisItem.Population, "##,###")**
7. F5 키를 누르고 사용자가 지정한 값보다 큰 인구가 있는 도시만 표시하도록 **MinPopulation**을 조정합니다.
8. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **ValueFill** 및 **RailFill**
* **ValueHoverFill** 및 **RailHoverFill**
* **[FocusedBorderColor](properties-color-border.md)** 및 컨트롤 외부 색
* **ValueFill** 및 배경색
* **RailFill** 및 배경색
* **ValueHoverFill** 및 배경색
* **RailHoverFill** 및 배경색

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
* 슬라이더 값은 키보드를 조작할 때 표시되어야 합니다. 이 작업은 다음 방법 중 하나로 수행할 수 있습니다.
    * **ShowValue**를 **true**로 설정합니다.
    * 슬라이더에 인접한 **[레이블](control-text-box.md)** 을 추가합니다. 레이블의 **[Text](properties-core.md)** 를 슬라이더의 **[Value](properties-core.md)** 로 설정합니다.
