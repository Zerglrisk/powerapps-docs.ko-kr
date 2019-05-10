---
title: '드롭다운 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 드롭다운 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 02e8477873adad476c65e513a470e027aee5cd5c
ms.sourcegitcommit: 8d0ba2ec0c97be91d1350180dd6881c14dec8f2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65517381"
---
# <a name="drop-down-control-in-powerapps"></a>PowerApps의 드롭다운 컨트롤
사용자가 열지 않는 한 첫 번째 항목만 표시하는 목록입니다.

## <a name="description"></a>설명
**드롭다운** 컨트롤은 특히 목록에 선택항목이 많은 경우 화면 사용 공간을 절약합니다. 이 컨트롤은 사용자가 펼침 단추를 선택하여 다른 선택을 표시하지 않으면 한 줄만 취합니다.  이 컨트롤을 사용하면 최대 500개의 항목이 표시됩니다.

## <a name="key-properties"></a>주요 속성
**[Default](properties-core.md)** - 사용자가 다른 값을 지정하기 전 컨트롤의 초기 값입니다.

**[Items](properties-core.md)** – 컨트롤에 표시되는 항목을 포함하는 데이터의 원본입니다. 원본에 여러 개의 열이 있는 경우, 컨트롤의 **Value** 속성을 표시할 데이터의 열로 설정하세요.
  
**Value** - 컨트롤에 표시할 데이터 열입니다(예를 들어 데이터 원본에 여러 열이 있는 경우).

**선택한** – 선택한 항목을 나타내는 데이터 레코드입니다.

**AllowEmptySelection** – 컨트롤이 선택 영역이 없는 항목은 선택 된 경우 표시 여부를 선택 합니다. 앱 사용자 빈 항목을 선택 하 여 선택 항목을 지울 수도 있습니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**ChevronBackground** – 드롭다운 목록에서 아래쪽 화살표의 배경색입니다.

**ChevronFill** – 드롭다운 목록에서 아래쪽 화살표의 색입니다.

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

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[HoverColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**[OnChange](properties-core.md)** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 아래쪽 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingTop](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 위쪽 가장자리 사이의 거리입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[Reset](properties-core.md)** – 컨트롤이 기본값으로 되돌아가는지 여부입니다.

**(사용 되지 않음) SelectedText** – 선택한 항목을 나타내는 하는 문자열 값입니다.

**[SelectionColor](properties-color-border.md)** – 목록에서 선택한 항목의 텍스트 색 또는 펜 컨트롤에 있는 선택 도구의 색입니다.

**[SelectionFill](properties-color-border.md)** – 목록에서 선택한 항목 또는 펜 컨트롤에서 선택한 영역의 배경색입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="example"></a>예

### <a name="simple-list"></a>간단한 목록

1. **드롭다운** 컨트롤을 추가한 다음, **[Items](properties-core.md)** 속성을 다음 수식으로 설정합니다.

    `["Seattle", "Tokyo", "London", "Johannesburg", "Rio de Janeiro"]`

    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?

1. Alt 키를 누른 채로 컨트롤의 아래쪽 화살표를 선택하여 목록에 항목을 표시합니다.

### <a name="list-from-a-data-source"></a>데이터 원본에서 나열
이 절차의 원칙은 [테이블을 제공하는 모든 데이터 원본](../connections-list.md#tables)에 적용되지만 이러한 단계를 정확하게 수행하려면, Common Data Service 데이터베이스가 생성되고 샘플 데이터가 추가된 환경이 필요합니다.

1. [빈 앱을 연](../data-platform-create-app-scratch.md#open-a-blank-app) 다음, [**계정** 엔터티를 지정](../data-platform-create-app-scratch.md#specify-an-entity)합니다.

1. **드롭다운** 컨트롤을 추가하고 **[Items](properties-core.md)** 속성을 다음 수식으로 설정합니다.

    `Distinct(Accounts, address1_city)`

    이 수식은 **계정** 엔터티의 모든 도시를 표시합니다. 두 개 이상의 레코드에 동일한 도시가 있는 경우, **[Distinct](../functions/function-distinct.md)** 함수는 드롭다운 컨트롤에 있는 중복을 숨깁니다.

1. (선택 사항) **드롭다운** 컨트롤의 이름을 **도시**로 변경하고 세로 **갤러리** 컨트롤을 추가하고 갤러리의 **[Items](properties-core.md)** 속성을 이 수식으로 설정합니다.

    `Filter(Accounts, address1_city = Cities.Selected.Value)`

    이 **[Filter](../functions/function-filter-lookup.md)** 함수는 도시가 **도시** 컨트롤에서 선택한 값과 일치하는 **계정** 엔터티의 레코드만 표시합니다.

## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **ChevronFill** 및 **ChevronBackground**
* **ChevronHoverFill** 및 **ChevronHoverBackground**
* **SelectionColor** 및 **SelectionFill**
* **SelectionFill** 및 **[Fill](properties-color-border.md)**

이는 [표준 색 대비 요구 사항](../accessible-apps-color.md)에 추가됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
