---
title: '콤보 박스 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 콤보 박스 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/13/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e6d1b1083fcc7e865fa7c9cfe3f8966e20ed86a5
ms.sourcegitcommit: c52c1869510a9a37d9f7b127e06f07583529588b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670914"
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

**DefaultSelectedItems** -초기 사용자 컨트롤과 상호 작용 하기 전에 항목을 선택 합니다.

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
1. 에 **삽입** 탭을 열고 합니다 **컨트롤** 메뉴를 선택한 후 **콤보 상자**합니다.  

1. 에 **속성** 탭을 열고 오른쪽 창을 **데이터 원본을 선택** 목록 (옆에 **항목**), 한 다음 추가 하거나 데이터 원본을 선택 합니다.

1. 동일한 탭에서 선택 **편집할** (옆 **필드**).

1. 에 **데이터** 창 열기를 **기본 텍스트** 목록 및 다음에 표시 하려는 열을 선택 합니다 **콤보 상자** 컨트롤입니다.

1. Alt 키를 누른 채를 열려면 아래쪽 화살표를 선택 합니다 **콤보 상자** 제어 합니다.

    컨트롤에서는 지정한 데이터 원본에 지정 된 열에서 데이터를 보여 줍니다.
    
1. (선택 사항) 기본적으로 첫 번째 레코드를 표시 하려면 설정 합니다 **DefaultSelectedItems** 속성을이 식으로 대체 *DataSource* 데이터 원본의 이름:

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
