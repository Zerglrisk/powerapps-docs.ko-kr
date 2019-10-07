---
title: '콤보 박스 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 콤보 박스 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/13/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dbbff1f85ccc104a1a0f88c6b9670c45c0528592
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993484"
---
# <a name="combo-box-control-in-powerapps"></a>PowerApps의 콤보 박스 컨트롤
사용자가 제공된 선택 항목 중에서 선택할 수 있습니다.  검색과 다중 선택을 지원합니다.

## <a name="description"></a>설명
**콤보 상자** 컨트롤 선택 항목을 검색할 수 있습니다.  검색은 SearchField 속성의 서버 측에서 수행되므로 성능은 매우 큰 데이터 원본에 의해 영향을 받지 않습니다.  

단일 또는 다중 선택 모드는 SelectMultiple 속성을 통해 구성됩니다.

선택할 항목을 검색할 때 각 항목에 대해 데이터 창의 레이아웃 설정을 수정하여 단일 데이터 값, 두 개의 값 또는 그림과 두 개의 값(사람)을 표시하도록 선택할 수 있습니다.

## <a name="people-picker"></a>상대 선택
**콤보 상자**를 상대 선택으로 사용하려면, 데이터 창의 레이아웃 설정에서 **사람** 템플릿을 선택하고, 아래 사람에게 표시할 관련 데이터 속성을 구성합니다.

## <a name="key-properties"></a>주요 속성
**[Items](properties-core.md)**  – 선택 항목을 만들 수 있는 데이터의 원본입니다.

**DefaultSelectedItems** – 사용자가 컨트롤과 상호 작용 하기 전의 초기 선택 된 항목입니다.

**SelectedItems** – 사용자 상호 작용을 통해 선택된 항목의 목록입니다.

**SelectMultiple** – 사용자가 단일 항목 또는 여러 항목을 선택할 수 있는지 여부입니다.

**IsSearchable** – 사용자가 선택하기 전에 항목을 검색할 수 있는지 선택합니다.

**SearchFields** - 사용자가 텍스트를 입력할 때 검색되는 데이터 원본의 데이터 필드입니다.  여러 필드를 검색하려면 ComboBox1.SearchFields = ["MyFirstColumn", "MySecondColumn"]으로 설정하세요.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**DisplayFields** – 검색에서 반환된 각 항목에 대해 표시되는 필드의 목록입니다.  속성 옵션 탭에서 데이터 창을 통해 구성하는 것이 가장 쉬운 방법입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**InputTextPlaceholder** – 선택된 항목이 없을 경우 최종 사용자에게 표시되는 지침 텍스트입니다.

**OnChange** – 사용자가 선택 항목을 변경할 때 앱이 응답하는 방법입니다.

**OnNavigate** - 사용자가 항목을 클릭할 때 앱이 응답하는 방법입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="example"></a>예
1. **삽입** 탭에서 **컨트롤** 메뉴를 열고 **콤보 상자**를 선택 합니다.  

1. 오른쪽 창의 **속성** 탭에서 **데이터 원본 선택** 목록 ( **항목**옆에 있는)을 연 다음 데이터 원본을 추가 하거나 선택 합니다.

1. 동일한 탭에서 **편집** ( **필드**옆에 있는)을 선택 합니다.

1. **데이터** 창에서 **주 텍스트** 목록을 연 다음 **콤보 상자** 컨트롤에 표시 하려는 열을 선택 합니다.

1. Alt 키를 누른 채 아래쪽 화살표를 선택 하 여 **콤보 상자** 컨트롤을 엽니다.

    컨트롤은 사용자가 지정한 데이터 원본에서 지정한 열의 데이터를 표시 합니다.
    
1. 필드 기본적으로 첫 번째 레코드를 표시 하려면 **DefaultSelectedItems** 속성을이 식으로 설정 하 고 *DataSource* 를 데이터 원본 이름으로 바꿉니다.

    `First(DataSource)`

## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **ChevronFill** 및 **ChevronBackground**
* **ChevronHoverFill** 및 **ChevronHoverBackground**
* **SelectionColor** 및 **SelectionFill**
* **SelectionFill** 및 **[Fill](properties-color-border.md)**
* **SelectionTagColor** 및 **SelectionTagFill**

이는 [표준 색 대비 요구 사항](../accessible-apps-color.md)에 추가됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

    > [!NOTE]
  > 터치 스크린에서 화면 읽기 프로그램 사용자는 콤보 상자의 콘텐츠를 순차적으로 탐색할 수 있습니다. 콤보 상자는 선택 시 해당 콘텐츠를 표시하거나 숨기는 단추 역할을 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.

    > [!NOTE]
  > Tab 키는 콤보 상자로 이동하거나 멀어지도록 이동합니다. 화살표 키는 콤보 상자의 콘텐츠를 탐색합니다. Esc 키는 열려 있는 드롭다운을 닫습니다.
