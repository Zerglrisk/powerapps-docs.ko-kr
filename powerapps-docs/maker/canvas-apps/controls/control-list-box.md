---
title: '목록 상자 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 목록 상자 컨트롤에 관한 정보
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
ms.openlocfilehash: d211af5c34874a0ea0afe80af91c2f65495a7a60
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650496"
---
# <a name="list-box-control-in-powerapps"></a>PowerApps의 목록 상자 컨트롤
사용자가 하나 또는 여러 개의 항목을 선택할 수 있는 목록입니다.

## <a name="description"></a>설명
**목록 상자** 컨트롤은 항상 사용 가능한 선택 항목을 모두 표시하며( **[드롭다운](control-drop-down.md)** 컨트롤과 다름) 이중에서 사용자가 한번에 둘 이상의 항목을 선택할 수 있습니다( **[라디오](control-radio.md)** 컨트롤과 다름).

## <a name="key-properties"></a>주요 속성
**[Default](properties-core.md)** – 사용자가 컨트롤을 변경하기 전의 초기 값입니다.

**[Items](properties-core.md)** – 갤러리, 목록 또는 차트와 같은 컨트롤에 표시되는 데이터 원본입니다.

**Selected** – 선택한 항목을 나타내는 데이터 레코드입니다.

갤러리, 목록 또는 차트를 추가할 경우 속성 목록은 새 컨트롤이 표시해야 하는 데이터를 쉽게 지정할 수 있는 **항목**을 기본적으로 보여줍니다. 예를 들어 갤러리의 **Items** 속성을 Salesforce의 **Account** 테이블, Excel에서 만들어 클라우드에 업로드한 **Inventory** 테이블 또는 **ConferenceSpeakers** SharePoint 목록 테이블로 설정할 수 있습니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

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

**[FontWeight](properties-text.md)** - 컨트롤의 텍스트 굵기입니다. **Bold**, **Semibold**, **Normal** 또는 **Lighter**로 설정합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[HoverColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**ItemPaddingLeft** – 목록 상자의 텍스트와 왼쪽 가장자리 사이의 거리입니다.

**[LineHeight](properties-text.md)** - 텍스트 선 또는 목록의 항목 등, 항목 사이의 거리입니다.

**[OnChange](properties-core.md)** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 하단 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 상단 가장자리 사이의 거리입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[Reset](properties-core.md)** – 컨트롤을 기본값으로 되돌릴지 여부를 선택합니다.

**Selectedtext (사용 되지 않음)** – 선택한 항목을 나타내는 문자열 값입니다.

**[SelectionColor](properties-color-border.md)** – 목록에서 선택한 항목의 텍스트 색 또는 펜 컨트롤에서 선택 도구의 색입니다.

**[SelectionFill](properties-color-border.md)** – 펜 컨트롤의 목록 또는 선택한 영역에서 선택한 항목 또는 항목의 배경색입니다.

**SelectMultiple** – 사용자는 목록 상자에서 여러 항목을 선택할 수 있는지 여부를 선택합니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>예
1. **목록 상자** 컨트롤을 추가하고 이름을 **CategoryList**로 지정한 다음, **[Items](properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
   **["Carpet","Hardwood","Tile"]**
   
    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
   
    ![목록 상자의 바닥재 범주](./media/control-list-box/category-listbox.png)
2. 3개의 **[드롭다운](control-drop-down.md)** 컨트롤을 추가하고 **CategoryList** 아래로 이동한 다음, 이름을 **CarpetList**, **HardwoodList** 및 **TileList**로 지정합니다.
3. 각 **[드롭다운](control-drop-down.md)** 컨트롤의 **[Items](properties-core.md)** 속성을 다음 값 중에 하나로 설정합니다.
   
   * CarpetList: **["Caserta Stone Beige","Ageless Beauty Clay", "Lush II Tundra"]**
   * HardwoodList: **["Golden Teak","Natural Hickory", "Victoria Mahogany"]**
   * TileList: **["Honey Onyx Marble","Indian Autumn Slate", "Panaria Vitality Ceramic"]**
     
     ![드롭다운 목록의 바닥재 이름](./media/control-list-box/flooring-names.png)
4. 각 **[드롭다운](control-drop-down.md)** 컨트롤의 **[Visible](properties-core.md)** 속성을 다음 값 중에 하나로 설정합니다.
   
   * CarpetList: **If("Carpet" in CategoryList.SelectedItems.Value, true)**
   * HardwoodList: **If("Hardwood" in CategoryList.SelectedItems.Value, true)**
   * TileList: **If("Tile" in CategoryList.SelectedItems.Value, true)**
     
     **[If](../functions/function-if.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
5. F5 키를 누르고 **CategoryList**에서 여러 개의 항목을 선택합니다.
   
    선택 항목에 따라 적절한 **[드롭다운](control-drop-down.md)** 컨트롤이 나타납니다.
   
    ![드롭다운 목록의 바닥재 이름](./media/control-list-box/selected-lists.png)
6. (선택 사항) 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **SelectionColor** 및 **SelectionFill**
* **SelectionFill** 및 **[Fill](properties-color-border.md)**
* **[HoverFill](properties-color-border.md)** 및 **[Fill](properties-color-border.md)**
* **[PressedFill](properties-color-border.md)** 및 **[Fill](properties-color-border.md)**

이는 [표준 색 대비 요구 사항](../accessible-apps-color.md)에 추가됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.

    > [!NOTE]
  > Tab 키는 **목록 상자**로 이동하거나 멀어지도록 이동합니다. 화살표 키는 **목록 상자**의 콘텐츠를 탐색합니다.
