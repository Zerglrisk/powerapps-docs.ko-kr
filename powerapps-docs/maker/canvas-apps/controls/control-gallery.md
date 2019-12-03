---
title: '갤러리 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 갤러리 컨트롤에 관한 정보
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2019
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 449948efb53fd5fdc3b0f65f5277d50b6a831dc7
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74709377"
---
# <a name="gallery-control-in-canvas-apps"></a>Canvas 앱의 갤러리 컨트롤

다른 컨트롤을 포함하고 데이터 집합을 보여주는 컨트롤입니다.

## <a name="description"></a>설명

**갤러리** 컨트롤은 데이터 원본에서 여러 개의 레코드를 표시할 수 있으며, 각 레코드는 여러 형식의 데이터를 포함할 수 있습니다. 예를 들어, **갤러리** 컨트롤은 여러 연락처를 보여줄 수 있으며, 각 항목은 각 연락처에 대한 이름, 주소, 전화 번호를 포함한 연락처 정보를 보여줍니다. 각 데이터 필드는 **갤러리** 컨트롤 내에서 별도의 컨트롤로 나타나며, 해당 템플릿에서 이러한 컨트롤을 구성할 수 있습니다. 템플릿은 가로/세로 방향으로 **갤러리** 컨트롤의 왼쪽 가장자리, 그리고 세로/가로 방향로 **갤러리** 컨트롤의 상단에 갤러리 내부의 첫 번째 항목으로 나타냅니다. 템플릿에 적용한 변경 사항은 **갤러리** 컨트롤 전체에서 반영됩니다.

갤러리에서 이미지 및 텍스트를 표시 하기 위한 미리 정의 된 템플릿 및 가변 높이 항목에 대 한 갤러리를 사용할 수 있습니다.

## <a name="limitations"></a>제한 사항

모든 항목이 로드 되기 전에 사용자가 **유연한 높이** 갤러리 컨트롤을 스크롤하면 데이터 로드가 완료 되 면 현재 보기 상태인 항목이 푸시 다운 되 고 표시 되지 않을 수 있습니다. 이 문제를 방지 하려면 **유연한 높이** 변형 대신 표준 **갤러리** 컨트롤을 사용 합니다.

## <a name="key-properties"></a>주요 속성

**[Default](properties-core.md)**  – 앱이 시작하면 갤러리에서 선택할 데이터 원본의 항목 또는 레코드입니다.

**[Items](properties-core.md)** – 갤러리, 목록 또는 차트와 같은 컨트롤에 표시되는 데이터 원본입니다.

**Selected** – 선택한 항목입니다.

## <a name="additional-properties"></a>추가 속성

**[AccessibleLabel](properties-accessibility.md)** – 화면 판독기에 대 한 갤러리의 레이블 (포함 된 항목이 아님)입니다. 항목 목록의 개념을 설명해야 합니다.

**AllItems** – 갤러리의 템플릿에 속해 있는 추가 컨트롤 값을 포함하는 갤러리에 있는 모든 항목입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**ItemAccessibleLabel** – 화면 판독기에 대 한 각 갤러리 항목의 레이블입니다. 각 항목의 정의를 설명 해야 합니다.

**NavigationStep** – **ShowNavigation** 속성이 **true**로 설정되어 있고 사용자가 해당 갤러리 한쪽 끝에서 탐색 화살표를 선택할 경우 갤러리를 스크롤하는 정도입니다.

**선택 가능 – 갤러리** 항목을 선택할 수 있는지 여부를 선택 합니다. **True**로 설정 되 면 화면 읽기 프로그램은 갤러리를 선택 가능 목록으로 식별 하 고 클릭 하거나 탭 하 여 항목을 선택 합니다. **False**로 설정 하면 화면 읽기 프로그램에서 갤러리를 일반 목록으로 식별 하 고 항목을 클릭 하거나 탭 하지 않습니다.

**ShowNavigation** – 사용자가 화살표를 클릭하거나 탭하여 갤러리에서 항목을 스크롤할 수 있도록 갤러리의 각 끝에 화살표를 나타낼지 여부를 선택합니다.

**ShowScrollbar** – 사용자가 갤러리를 마우스로 가리킬 때 스크롤바를 나타낼지 여부를 선택합니다.

**Snap** – 사용자가 갤러리를 스크롤할 때 다음 항목이 전체 화면으로 나타나도록 자동으로 맞출지 여부를 선택합니다.

**TemplateFill** – 갤러리의 배경색입니다.

**TemplatePadding** – 갤러리에서 항목 사이의 거리입니다.

**TemplateSize** -세로 방향으로 갤러리에 대한 템플릿의 높이 또는 가로 방향으로 갤러리에 대한 템플릿의 너비입니다.

**Transition** – 사용자가 갤러리의 항목을 가리킬 때 나타나는 시각 효과입니다(**팝**, **푸시** 또는 **없음**).

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**WrapCount** – 가로 또는 세로 레이아웃에 따라 각 행 또는 열당 표시되는 항목 수입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수

[**Filter**( *DataSource*, *Formula* )](../functions/function-filter-lookup.md)

[ **Reset**( *Control* )](../functions/function-reset.md) -갤러리를 초기 상태로 다시 설정 합니다. 초기 상태에는 첫 번째 항목으로 스크롤하고 첫 번째 항목을 선택 하는 작업이 포함 되며, 있는 경우 기본값입니다. 

  > [!NOTE]
  > 컨트롤 **다시 설정** 은 갤러리의 모든 자식을 재귀적으로 다시 설정 하지 않습니다.

## <a name="examples"></a>예

### <a name="show-and-filter-data"></a>데이터 표시 및 필터링

* [텍스트 표시](control-text-box.md#show-data-in-a-gallery)
* [이미지 표시](control-image.md#show-a-set-of-images-from-a-data-source)
* [목록 옵션을 선택하여 데이터 필터링](control-drop-down.md#example)
* [슬라이더를 조정하여 데이터 필터링](control-slider.md#example)

### <a name="get-data-from-the-user"></a>사용자로부터 데이터 가져오기

* [텍스트 가져오기](control-text-input.md#collect-data)
* [이미지 가져오기](control-add-picture.md#add-images-to-an-image-gallery-control)
* [사진 가져오기](control-camera.md#example)
* [사운드 가져오기](control-microphone.md#example)
* [드로잉 가져오기](control-pen-input.md#create-a-set-of-images)

## <a name="accessibility-guidelines"></a>접근성 지침

### <a name="color-contrast"></a>색 대비

갤러리 항목의 아무 곳이나 클릭하면 선택되어야 하는 경우 다음 사이에 적절한 색 대비가 있어야 합니다.

* **[BorderColor](properties-color-border.md)** 및 갤러리 외부 색(테두리가 있는 경우)
* **[Fill](properties-color-border.md)** 및 갤러리 외부 색(테두리가 없는 경우)

### <a name="screen-reader-support"></a>화면 판독기 지원

* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

    > [!NOTE]
    > 갤러리의 항목이 변경 되 면 화면 판독기에서이를 알립니다. **AccessibleLabel**도 언급됩니다. 이 언급은 알림에 대한 컨텍스트를 제공하고 동일한 화면에 여러 개의 갤러리가 있는 경우 더욱 중요합니다.

* 갤러리 항목에 여러 컨트롤이 포함 되어 있는 경우 **ItemAccessibleLabel** 를 사용 하 여 갤러리 항목의 내용을 요약 합니다.

* 사용자가 갤러리 항목을 선택 하도록 하려면 선택 **항목의 값을** **true** 로 설정 합니다. 그렇지 않으면 해당 값을 **false**로 설정 합니다.

* 갤러리 항목에 여러 컨트롤이 포함 되어 있는 경우 **ItemAccessibleLabel** 를 사용 하 여 갤러리 항목의 내용에 대 한 요약을 제공 합니다.

* 사용자가 갤러리 항목을 선택 하는지 여부에 따라 선택 **가능한** 항목을 적절 하 게 설정 해야 합니다.

### <a name="keyboard-support"></a>키보드 지원

* **ShowScrollbar**를 **true**로 설정하는 것이 좋습니다. 대부분의 터치 스크린 디바이스에서 스크롤 막대는 스크롤이 시작될 때까지 표시되지 않습니다.
* 갤러리 항목의 아무 곳이나 클릭하면 선택되어야 하는 경우에는 키보드 사용자가 갤러리 항목을 선택할 수 있는 방법도 있어야 합니다. 예를 들어 **OnSelect** 속성이 **Select(Parent)** 로 설정된 **[단추](control-button.md)** 를 추가합니다.

    > [!NOTE]
  > 갤러리 외부의 컨트롤은 갤러리 내의 키보드 탐색 순서에서 고려되지 않습니다. 갤러리 내부 컨트롤의 **[TabIndex](properties-accessibility.md)** 는 범위가 지정됩니다. 자세한 내용은 [접근성 속성](properties-accessibility.md)을 참조하세요.
