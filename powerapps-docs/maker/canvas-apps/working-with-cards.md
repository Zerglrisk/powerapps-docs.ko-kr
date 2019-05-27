---
title: 데이터 카드 이해 | Microsoft Docs
description: PowerApps에서 폼 카드를 사용하여 데이터 원본에서 정보를 수집하고 표시합니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0337c7f79a81d7368128b6ef11d4d108345d3923
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216625"
---
# <a name="understand-data-cards-in-powerapps"></a>PowerApps의 데이터 카드 이해

**[카드](controls/control-card.md)** 컨트롤은 캔버스 앱에서 **[편집 폼](controls/control-form-detail.md)** 및 **[표시 폼](controls/control-form-detail.md)** 컨트롤의 구성 요소입니다. 폼은 전체 레코드를 나타내며 각 카드는 해당 레코드의 단일 필드를 나타냅니다.

디자인 작업 영역에서 폼 컨트롤을 선택하면 오른쪽 창에서 가장 쉽게 카드와 상호 작용할 수 있습니다. 해당 창에 표시할 필드, 각 필드를 표시하는 방법 및 필드를 표시할 순서를 선택할 수 있습니다. 이 예제에서는 **Assets**라고 하는 SharePoint 목록에서 빌드된 앱에 있는 **편집 폼** 컨트롤을 보여줍니다.

![첫 번째 화면](./media/working-with-cards/first-screen.png)

카드를 시작하려면 [폼 추가](add-form.md) 및 [데이터 폼 이해](working-with-forms.md)를 참조하세요. 이 항목의 나머지 부분에서는 카드 작동 방식 및 사용자 지정 또는 고유한 카드를 생성하는 방법에 대해 자세히 설명합니다.

## <a name="predefined-cards"></a>미리 정의된 카드

PowerApps는 문자열, 숫자 및 기타 데이터 형식에 미리 정의된 일련의 카드를 제공합니다. 오른쪽 창에서 사용할 수 있는 변동을 확인하고 필드에 사용되는 카드를 변경할 수 있습니다.

![](./media/working-with-cards/selected-card.png)

이 예제에서는 한 줄 텍스트 카드가 선택되었지만 URL의 텍스트는 한 줄에 나타낼 수 있는 길이보다 깁니다. 사용자에게 편집할 수 있는 더 많은 공간을 제공하도록 여러 줄 텍스트 카드로 변경하겠습니다.

![](./media/working-with-cards/multiline-edit.png)

이 데이터 원본의 일부 필드는 표시되지 않지만 해당 확인란을 선택하여 필드를 표시하거나 숨길 수 있습니다. 이 예제에서는 **SecurityCode** 필드를 표시하는 방법을 보여줍니다.

![](./media/working-with-cards/add-security-code.png)

## <a name="customize-a-card"></a>카드 사용자 지정
카드는 다른 컨트롤을 구성합니다. **편집 폼** 컨트롤에서 사용자는 **삽입** 탭에서 추가한 표준 **[텍스트 입력](controls/control-text-input.md)** 컨트롤에 데이터를 입력합니다.  

컨트롤을 제어하여 카드의 모양을 변경하는 방법의 예제를 살펴보겠습니다.

1. 먼저 **SecurityCode** 필드의 경우 가장 최근에 삽입한 카드를 다시 살펴보겠습니다. 이 카드를 한 번 클릭하거나 눌러서 선택합니다.
   
    ![](./media/working-with-cards/select-security-code.png)
2. 입력 컨트롤 자체를 클릭하거나 눌러서 카드 내의 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 선택합니다.
   
    ![](./media/working-with-cards/select-text-input.png)
3. 선택 영역 상자를 끌어와서 카드 내에서 이 컨트롤을 이동하고, 선택 영역 상자의 가장자리를 따라 핸들을 끌어와서 컨트롤의 크기를 조정합니다.
   
    ![](./media/working-with-cards/customize-text-input.png)  

카드 내에서 컨트롤의 크기를 조정하고, 이동하고, 다른 내용을 수정할 수 있지만 먼저 잠금을 해제하지 않으면 삭제할 수 없습니다.

## <a name="unlock-a-card"></a>카드 잠금 해제
컨트롤을 포함하는 것 외에도 카드 자체가 다른 컨트롤과 마찬가지로 속성 및 수식을 포함하는 컨트롤입니다. 양식에 필드를 표시하려는 경우 오른쪽 창에서는 자동으로 카드를 만들고 필요한 수식을 생성합니다.  오른쪽 창의 **고급** 탭에서 이러한 수식을 볼 수 있습니다.

![](./media/working-with-cards/advanced-locked.png)

즉시 카드의 가장 중요한 속성 중 하나인 **[DataField](controls/control-card.md)** 속성을 확인합니다. 이 속성은 사용자가 확인하고 이 카드에서 편집할 수 있는 데이터 원본의 필드를 나타냅니다.  

**고급** 탭에서 상단의 배너는 이 카드의 속성이 잠겨있음을 나타냅니다. 또한 잠금 아이콘은 **[DataField](controls/control-card.md)**, **[DisplayName](controls/control-card.md)** 및 **[Required](controls/control-card.md)** 속성 옆에 나타납니다. 오른쪽 창에서는 이러한 수식을 생성했다면 잠금은 이러한 속성을 실수로 변경하지 않도록 방지합니다.

![](./media/working-with-cards/lock-icons.png)

이러한 속성을 수정할 수 있도록 위쪽의 배너를 클릭하거나 눌러서 카드의 잠금을 해제합니다.

![](./media/working-with-cards/unlocked-card.png)

**[DisplayName](controls/control-card.md)** 을 수정하여 **Asset**과 **ID** 간에 공백을 만들겠습니다. 이렇게 변경하여 생성된 내용을 변경하고 있습니다.  오른쪽 창의 이 카드에는 다른 레이블이 있습니다.

![](./media/working-with-cards/change-display-name.png)

이제 이 카드를 제어하고 요구에 맞도록 추가로 수정할 수 있습니다. 하지만 이전과 같이 카드의 표현을 변경할 수 있는 기능(예: 한 줄 텍스트를 여러 줄 텍스트로 변경)이 상실되었습니다. 미리 정의된 카드를 지금 제어하는 "사용자 지정 카드"로 변환했습니다.  

> [!IMPORTANT]
> 카드의 잠금을 해제하는 경우 카드를 다시 잠글 수 없습니다. 카드를 잠긴 상태로 다시 돌리려면 해당 카드를 제거하고 오른쪽 창에서 다시 삽입합니다.

다양한 방법으로 잠금이 해제된 카드의 모양 및 동작을 변경할 수 있습니다(예: 내부에서 컨트롤 추가 및 삭제). 예를 들어 **삽입** 탭의 **아이콘** 메뉴에서 별 모양을 추가할 수 있습니다.

![](./media/working-with-cards/add-star.png)

별은 이제 카드의 일부이기 때문에 예를 들어 양식 내에서 카드의 순서를 바꾸는 경우에도 함께 이동됩니다.

또 다른 예제로 **ImageURL** 카드의 잠금을 해제한 다음 **이미지** 컨트롤을 **삽입** 탭의 해당 카드에 추가합니다.

![](./media/working-with-cards/add-image.png)

수식 입력줄에서 이 컨트롤의 **Image** 속성을 *TextBox*.**Text**로 설정합니다. 여기서 *TextBox*는 URL을 포함하는 **텍스트 입력** 컨트롤의 이름입니다.

![](./media/working-with-cards/show-image.png)

이제 이미지를 확인하고 해당 URL을 편집할 수 있습니다. **Parent.Default**를 **Image** 속성으로 사용했지만 사용자가 URL을 변경한 경우 업데이트되지 않습니다.

이 앱의 두 번째 화면에서 동일한 작업을 수행할 수 있습니다. 여기서 **표시 폼** 컨트롤을 사용하여 레코드의 세부 정보를 표시합니다. 이 경우에 사용자가 해당 화면에서 URL을 편집하지 않기 때문에 레이블을 숨기는 것이 좋습니다(카드가 아닌 레이블의 **Visible** 속성을 **false**로 설정).

![](./media/working-with-cards/show-image-display.png)

## <a name="interact-with-a-form"></a>폼 사용
카드의 잠금을 해제한 후에 이를 포함하는 폼을 사용하는 방법을 변경할 수 있습니다.

컨트롤이 해당 카드를 사용하는 방법 및 카드가 폼을 사용하는 방법에 대한 몇 가지 지침은 다음과 같습니다. 이들은 지침일 뿐입니다. PowerApps의 모든 컨트롤과 마찬가지로 PowerApps에 있는 다른 컨트롤을 참조하고 카드 및 카드 내의 컨트롤에서 true인 수식을 만들 수 있습니다. 창의적인 여러 가지 방법으로 앱을 만들 수 있습니다.  

### <a name="datafield-property"></a>DataField 속성
카드의 가장 중요한 속성은 **[DataField](controls/control-card.md)** 속성입니다.  이 속성은 유효성 검사, 업데이트되는 필드 및 카드의 기타 측면을 생성합니다.

### <a name="information-flowing-in"></a>들어오는 정보
폼은 컨테이너로써 **ThisItem**을 내부의 모든 카드에 사용할 수 있습니다. 이 레코드는 현재 사용 중인 레코드에 대한 모든 필드를 포함합니다.  

모든 카드의 **[Default](controls/properties-core.md)** 속성을 **ThisItem**.*FieldName*으로 설정해야 합니다.  특정 상황에서 중간에 이 값을 변환할 수 있습니다. 예를 들어 문자열을 포맷하거나 값을 다른 언어로 변환하려고 합니다.

카드 내의 각 컨트롤은 **Parent.Default**를 참조하여 필드의 값을 가져와야 합니다. 이 전략에서는 카드의 내부 수식을 변경하지 않고 카드의 **[Default](controls/properties-core.md)** 속성을 변경할 수 있도록 카드에 대한 캡슐화의 수준을 제공합니다.

기본적으로 **DefaultValue** 및 **[Required](controls/control-card.md)** 속성은 **[DataField](controls/control-card.md)** 속성에 따라 데이터 원본의 메타데이터에서 가져옵니다. 고유한 논리로 이러한 수식을 재정의하고 **[DataSourceInfo](functions/function-datasourceinfo.md)** 함수를 사용하여 데이터 원본의 메타데이터를 통합할 수 있습니다.

### <a name="information-flowing-out"></a>내보내는 정보
사용자가 카드에서 컨트롤을 사용하여 레코드를 수정한 후에 **[SubmitForm](functions/function-form.md)** 함수는 데이터 원본에 해당 변경 내용을 저장합니다. 해당 함수가 실행되면 양식 컨트롤은 각 카드의 **[DataField](controls/control-card.md)** 속성 값을 읽고 변경할 필드에 대해 알아봅니다.  

또한 폼 컨트롤은 각 카드의 **[Update](controls/control-card.md)** 속성 값을 읽습니다. 이 값을 이 필드에 대한 데이터 원본에 저장합니다. 카드의 **[Default](controls/properties-core.md)** 수식에서 적용된 변환을 되돌리려면 여기에서 다른 변환을 적용하면 됩니다.

**Valid** 속성은 **[DataField](controls/control-card.md)** 속성에 따라 데이터 원본의 메타데이터에서 생성됩니다. 또한 **[Required](controls/control-card.md)** 속성 및 **[Update](controls/control-card.md)** 속성이 값을 포함하는지 여부에 기반합니다. **[Update](controls/control-card.md)** 속성의 값이 유효하지 않으면 **Error** 속성은 사용자에게 친숙한 오류 메시지를 제공합니다.

카드의 **[DataField](controls/control-card.md)** 속성이 *비어* 있는 경우 카드는 컨트롤의 컨테이너일 뿐입니다. 양식이 전송될 때 해당 **Valid** 및 **[Update](controls/control-card.md)** 속성이 사용되지 않습니다.

## <a name="dissecting-an-example"></a>예제 분석
기본 데이터 항목 카드를 구성하는 컨트롤을 살펴보겠습니다. 컨트롤 간의 공백이 늘어나서 각각을 보다 명확하게 표시합니다.

![](./media/working-with-cards/dissect-card1.png)

이 그래픽에서 데이터 카드 내의 컨트롤 레이블이 지정 되어 있습니다.

![](./media/working-with-cards/dissect-card2.png)

네 가지 컨트롤은 이 카드를 작동시킵니다.

| 이름 | 유형 | 설명 |
| --- | --- | --- |
| **TextRequiredStar** |**[레이블](controls/control-text-box.md)** 컨트롤 |필수 필드를 나타내기 위해 일반적으로 데이터 항목 양식에서 사용되는 별을 표시합니다. |
| **TextFieldDisplayName** |**[레이블](controls/control-text-box.md)** 컨트롤 |이 필드의 사용자 친화적 이름을 표시합니다. 이 이름은 데이터 원본의 스키마에 포함된 내용과 다를 수 있습니다. |
| **InputText** |**입력 텍스트** 컨트롤 |필드의 초기 값을 표시하고 해당 값을 변경할 수 있습니다. |
| **TextErrorMessage** |**[레이블](controls/control-text-box.md)** 컨트롤 |유효성 검사에서 문제가 발생한 경우 사용자에게 친숙한 오류 메시지가 표시됩니다. 또한 필요한 경우 필드에 값이 있는지 확인합니다. |

이러한 컨트롤을 데이터로 채우려면 해당 속성은 이러한 주요 수식을 통해 카드의 속성에서 생성될 수 있습니다. 이러한 수식은 특정 필드를 참조하지 않습니다. 대신 모든 정보는 카드에서 가져옵니다.

| 컨트롤 속성 | 수식 | 설명 |
| --- | --- | --- |
| **TextRequiredStar.Visible** |**Parent.Required** |별은 필드가 필요한 경우에만 나타납니다. 사용자 또는 데이터 원본의 메타데이터에 의해 작성된 수식이 필요합니다. |
| **TextFieldDisplayName.Text** |**Parent.DisplayName** |텍스트 상자 컨트롤은 데이터 원본의 메타데이터에서 제공하는 사용자 친화적인 이름을 보여주며 카드의 **[DisplayName](controls/control-card.md)** 속성에서 설정됩니다. |
| **InputText.Default** |**Parent.Default** |카드의 기본값에서 제공한 대로 텍스트 입력 컨트롤은 처음부터 데이터 원본의 필드 값을 보여줍니다. |
| **TextErrorMessage.Text** |**Parent.Error** |유효성 검사 문제가 발생한 경우 카드의 **오류** 속성은 해당 오류 메시지를 제공합니다. |

이러한 컨트롤에서 정보를 끌어오고 다시 데이터 원본에 푸시하기 위해 다음 키 수식이 필요합니다.

| 컨트롤 이름 | 수식 | 설명 |
| --- | --- | --- |
| **DataCard.DataField** |**"ApproverEmail"** |사용자가 이 카드에서 표시하고 편집할 수 있는 필드의 이름입니다. |
| **DataCard.Update** |**InputText.Text** |**[SubmitForm](functions/function-form.md)** 을 실행할 때 유효성을 검사하고 데이터 원본에 다시 푸시할 값입니다. |

