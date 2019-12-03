---
title: '카드 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 카드 컨트롤에 관한 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: gregli
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7f0d4268700b8c46a15fe74da4a4825395dcfe5b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74722929"
---
# <a name="card-control-in-power-apps"></a>Power Apps의 카드 컨트롤
**[표시 폼](control-form-detail.md)** 또는 **[편집 폼](control-form-detail.md)** 컨트롤의 단일 필드에 대한 표시 및 편집 환경을 제공합니다.

## <a name="description"></a>설명
**[표시 폼](control-form-detail.md)** 및 **[편집 폼](control-form-detail.md)** 컨트롤은 레코드 전체를 표시하고 볼 수 있는 컨테이너의 역할을 합니다. 각 컨테이너는 개별 필드를 표시하거나 이러한 필드를 업데이트할 방법을 제공하는 **카드** 컨트롤 집합을 포함할 수 있습니다. 각 카드에는 작동하는 레코드의 필드를 지정하는 **DataField** 속성이 있습니다.  

미리 정의된 카드는 다양한 데이터 형식과 사용자 경험에 대해 정의됩니다.  예를 들어, 키보드와 함께 사용하기 좋은 **[텍스트 입력](control-text-input.md)** 컨트롤로 숫자 필드를 편집하기 위한 카드가 있을 수 있으며, **[슬라이더](control-slider.md)** 컨트롤을 사용하여 숫자 편집을 지원하는 카드가 있을 수도 있습니다. 양식 컨트롤을 선택하면 오른쪽 창에서 필드에 따라 카드를 쉽게 선택할 수 있습니다.

카드 자체에 컨트롤이 있습니다. 카드의 컨트롤은 단일 필드를 표시하고 편집하기 위한 경험을 구성합니다. 예를 들어, 숫자 카드는 필드의 표시 이름을 제공하는 **[레이블](control-text-box.md)** 컨트롤, 필드의 값에 편집기를 제공하는 **[텍스트 입력](control-text-input.md)** 컨트롤로 구성될 수 있습니다. 또한, 카드에는 발생하는 유효성 검증 오류를 보여주는 **[레이블](control-text-box.md)** 컨트롤, 필드가 필수 항목임을 나타내기 위한 일반 별표에 대한 **[레이블](control-text-box.md)** 컨트롤이 있을 수 있습니다.

크기를 조정하고 숨기고 컨트롤을 추가하고 다른 변경 사항을 적용하여 미리 정의된 카드의 컨트롤을 사용자 지정할 수 있습니다. 또한, 처음부터 컨트롤을 추가하도록 완전히 비어 있는 카드, "사용자 지정 카드"로 시작할 수도 있습니다.

미리 정의된 카드는 기본적으로 *잠겨* 있습니다. 잠긴 카드에서는 카드의 일부 속성 또는 카드 내부의 컨트롤만 수정할 수 있으며 잠긴 카드는 삭제할 수 없습니다. **고급** 보기의 **보기** 탭에서 카드 잠금 및 잠금 해제를 볼 수 있습니다. 속성이 잠겨 있고 수정할 수 없는 경우 해당 이름 옆에 자물쇠 아이콘이 나타납니다. 해당 카드에 대해 자동 수식이 더 이상 생성되지 않으므로, 카드 잠금 해제는 주의하여 수행해야 하는 고급 작업이며 카드를 다시 잠글 수 없습니다.

폼의 컨테이너 내부에서 **ThisItem** 레코드가 사용 가능하며 해당 레코드의 모든 필드를 포함합니다.  예를 들어, 카드의 **[Default](properties-core.md)** 속성은 **ThisItem**.*FieldName*으로 설정되는 경우가 많습니다.

**부모** 참조를 사용하여 카드의 속성을 참조하도록 컨트롤을 구성할 수 있습니다.  예를 들어, 컨트롤은 **Parent.Default**를 사용하여 데이터 원본에서 필드의 초기 상태를 읽어야 합니다. 원하는 정보에 직접 액세스하는 대신 **부모**를 사용하면 카드의 암호화가 개선되며, 내부 서식을 깨지 않고도 다른 필드로 바꿀 수 있습니다.

카드를 사용자 지정, 잠금 해제 및 만드는 방법에 대한 예는 [데이터 카드 이해](../working-with-cards.md)를 참조하세요.

## <a name="key-properties"></a>주요 속성
**DataField** - 이 카드가 표시하고 편집하는 레코드 내부의 필드 이름입니다.

* 이름을 수식이 아닌 큰따옴표로 묶은 단일 정적 문자열로 지정합니다(예: **"Name"** ).
* **DataField** 속성을 *blank*로 설정하여 카드의 바인딩을 해제합니다. **Valid** 및 **Update** 속성은 바인딩 해제된 카드에는 무시됩니다.

**[Default](properties-core.md)** – 사용자가 컨트롤을 변경하기 전의 초기 값입니다.

* 카드의 각 컨트롤은 데이터 원본에 따라 필드의 기본값을 참조하도록 이 속성을 **Parent.Default**로 설정하세요. 예를 들어, 사용자가 해당 슬라이더에 대한 일반 값으로 시작할 수 있도록 슬라이더의 **[Default](properties-core.md)** 속성을 **Parent.Default**로 설정합니다.

**DisplayMode** – 값은 **Edit, View,** 또는 **Disabled**가 될 수 있습니다. 카드 내부의 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 구성합니다.  

* 단일 카드를 기본적으로 양식의 동작에 연결되어 있는 이 속성을 구성하여 편집 및 보기 양식 모두에 사용할 수 있도록 허용합니다.
* **보기** 모드에서 **[텍스트 입력](control-text-input.md)** , **[드롭다운](control-drop-down.md)** , **[날짜 선택기](control-date-picker.md)** 등의 자식 컨트롤은 텍스트 값만 표시하고 다른 대화형 요소 또는 장식을 렌더링하지 않습니다.

**DisplayName** – 데이터 원본의 필드에 대한 사용자에게 친숙한 이름입니다.

* **[DataSourceInfo](../functions/function-datasourceinfo.md)** 함수는 데이터 원본에서 이 메타데이터를 제공합니다.
* 카드 내부의 컨트롤은 필드의 이름을 참조하도록 **Parent.DisplayName**을 사용해야 합니다.

**Error** - 유효성 검사가 실패할 때 이 필드에 표시할 사용자에게 친숙한 오류 메시지입니다.

* 이 속성은 **SubmitForm**이 호출되면 설정됩니다.  
* 메시지는 데이터 원본의 메타데이터에 따라 유효성 검사 문제를 설명하고 카드의 **Required** 속성을 확인합니다.

**Required** – 데이터 원본의 필드를 편집하는 카드에 값을 포함해야 하는지 여부를 선택합니다.

* **[DataSourceInfo](../functions/function-datasourceinfo.md)** 함수는 데이터 원본에서 필요한 메타데이터를 제공합니다.
* 카드 내 컨트롤은 **Parent.Required**를 사용하여 카드의 필드가 필요한지 여부를 결정합니다.

**Update** – 필드에 대한 데이터 원본에 다시 쓸 값입니다.

* 데이터 원본에 다시 쓰려면 이 속성의 서식을 사용하여 카드의 편집 컨트롤에서 값을 가져옵니다. 예를 들어, 카드의 **Update** 속성을 **Slider.Value**로 설정하여 해당 카드에 있는 슬라이더의 값으로 데이터 원본을 업데이트합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[WidthFit](properties-size-location.md)** – **[편집 양식](control-form-detail.md)** 컨트롤처럼 컨테이너 컨트롤의 빈 공간을 채우기 위해 컨트롤의 가로가 자동으로 커지는지 여부입니다. 여러 카드에서 이 속성이 **true**로 설정되면 카드 사이에 공간이 나뉩니다. 자세한 내용은 [데이터 양식 레이아웃 이해](../working-with-form-layout.md)를 참조하세요.

## <a name="additional-properties"></a>추가 속성
**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**Valid** – **카드** 또는 **[편집 양식](control-form-detail.md)** 컨트롤에 올바른 항목이 있고 데이터 원본에 제출할 수 있는지의 여부입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다. 여러 열이 있는 컨테이너의 **[카드](control-card.md)** 컨트롤의 경우 이 속성은 카드가 표시되는 열을 결정합니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다. 여러 행이 있는 컨테이너의 **[카드](control-card.md)** 컨트롤의 경우 이 속성은 카드가 표시되는 행을 결정합니다.

## <a name="examples"></a>예
[데이터 카드 이해](../working-with-cards.md) 및 [데이터 양식 레이아웃 이해](../working-with-form-layout.md)에서 예를 참조하세요.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **[Fill](properties-color-border.md)** 및 자식 컨트롤. 예를 들어 카드에 **[레이블](control-text-box.md)** 이 포함되어 있고 레이블에 투명한 채우기가 있는 경우 카드의 **[Fill](properties-color-border.md)** 은 효과적으로 레이블의 배경색이 됩니다. 따라서 카드의 **[Fill](properties-color-border.md)** 과 레이블의 **[Color](properties-color-border.md)** 사이에 적절한 대비가 있어야 합니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **DisplayName**이 있어야 합니다.
