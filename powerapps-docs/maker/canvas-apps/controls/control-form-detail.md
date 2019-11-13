---
title: '표시 양식 및 편집 양식 컨트롤: 참조 | Microsoft Docs'
description: 표시 양식과 편집 양식 컨트롤에 대한 속성 및 예제 등을 포함한 정보
author: aneesmsft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2017
ms.author: aneesa
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0b25a22e732c96bf35f8951602e706f71b1733a7
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986718"
---
# <a name="edit-form-and-display-form-controls-in-powerapps"></a>PowerApps의 편집 양식 및 표시 양식 컨트롤
데이터 원본에서 레코드를 표시하고, 편집하고, 만듭니다.

## <a name="description"></a>설명
**표시 양식** 컨트롤을 추가하면 사용자가 레코드의 모든 필드 또는 지정한 필드만 표시할 수 있습니다. **편집 양식** 컨트롤을 추가하면 사용자가 해당 필드를 편집하고, 레코드를 만들고, 변경 내용을 데이터 원본에 저장할 수 있습니다.

![예제 양식 및 양식 보기 컨트롤](./media/control-form-detail/form-detail-intro.png)

**[갤러리](control-gallery.md)** 컨트롤을 추가하면 데이터 원본에 테이블을 표시하도록 구성한 다음 사용자가 갤러리에서 선택한 레코드를 표시하도록 양식을 구성할 수 있습니다. 사용자가 편집 저장 및 취소, 레코드 만들기를 선택할 수 있는 **[단추](control-button.md)** 컨트롤을 하나 이상 추가할 수도 있습니다. 컨트롤을 함께 사용하여 [완벽한 솔루션을 만들 수](../working-with-forms.md) 있습니다.

### <a name="record-selection"></a>레코드 선택
어떤 양식 종류에서나 **DataSource** 속성을 레코드 테이블로 설정하고 양식의 **Item** 속성은 해당 테이블의 특정 레코드를 표시하도록 설정합니다. 예를 들어 양식의 **Item** 속성은갤러리 **[ 컨트롤의 ](control-gallery.md)SelectedItem** 속성으로 설정할 수 있습니다. 갤러리에서 레코드를 선택할 때 양식이 더 많은 필드를 표시할 수 있는 경우를 제외하고 양식에 동일한 레코드가 표시됩니다. 사용자가 갤러리로 돌아와 다른 레코드를 선택하면 갤러리의 **SelectedItem** 속성이 변경됩니다. 이렇게 변경하면 양식의 **Item** 속성이 업데이트되어 최근에 선택한 레코드를 표시합니다.

**Show, edit, or add a record**(레코드 표시, 편집 또는 추가)의 설명대로 **드롭다운** 컨트롤을 사용하거나 [Lookup](../add-form.md) 또는 **First** 같은 함수를 사용하여 양식의 **Item** 속성을 설정할 수도 있습니다. 예를 들어 **항목** 속성을 이러한 수식 중 하나로 설정 하 여 Common Data Service의 **Accounts** 엔터티에 Fabrikam 항목을 표시할 수 있습니다.

```First(Accounts)```

```Lookup(Accounts, "Fabrikam" in name)```

각각의 양식 컨트롤에는 하나 이상의 **[카드](control-card.md)** 컨트롤이 포함됩니다. 카드의 **[DataField](control-card.md)** 속성을 설정하면 [해당 카드가 표시할 필드와 기타 세부 정보](../add-form.md)를 지정하게 됩니다.

### <a name="create-a-record"></a>레코드 만들기
**편집 양식** 컨트롤이 **편집** 모드이면 사용자가 양식의 **Item** 속성에서 지정된 레코드를 업데이트할 수 있습니다. 검사하면 **Mode** 속성이 **편집**을 반환합니다.

그러나 **편집 양식** 컨트롤이 **새로 만들기** 모드이면 **Item** 속성이 무시됩니다. 양식이 기존 레코드를 표시하지 않고 그 대신 각 필드의 값은 사용자가 양식을 구성한 데이터 원본의 기본값과 일치하게 됩니다. **[NewForm](../functions/function-form.md)** 함수로 인해 양식이 이 모드로 전환됩니다.

예를 들어, 단추의 **[Text](properties-core.md)** 속성을 **새로 만들기**로 표시하고 그 **[OnSelect](properties-core.md)** 속성은 **[NewForm](../functions/function-form.md)** 함수를 포함하는 수식으로 설정할 수 있습니다. 사용자가 해당 단추를 선택하면 **새로 만들기** 모드로 전환되어 사용자가 알고 있는 값으로 레코드를 만들 수 있습니다.

ResetForm **[ 함수나 ](../functions/function-form.md)** SubmitForm **[ 함수가 성공적으로 실행된 경우 양식이 다시 ](../functions/function-form.md)편집** 모드로 전환됩니다.

* 단추의 **[Text](properties-core.md)** 속성을 **취소**로 표시하고 그 **[OnSelect](properties-core.md)** 속성은 **[ResetForm](../functions/function-form.md)** 함수를 포함하는 수식으로 설정할 수 있습니다. 사용자가 해당 단추를 선택하면 진행 중인 변경 내용이 무시되며 양식의 값은 다시 데이터 원본의 기본값과 일치하게 됩니다.
* 단추의 **[Text](properties-core.md)** 속성을 **변경 내용 저장**으로 표시하고 그 **[OnSelect](properties-core.md)** 속성은 **[SubmitForm](../functions/function-form.md)** 함수를 포함하는 수식으로 설정할 수 있습니다. 사용자가 해당 단추를 선택하고 데이터 원본이 업데이트되면 양식의 값이 데이터 원본의 기본값으로 재설정됩니다.

### <a name="save-changes"></a>변경 내용 저장
앞 섹션에서 설명한 것처럼 **변경 내용 저장** 단추를 만들면 사용자가 해당 단추를 선택하여 레코드를 만들거나 업데이트한 다음 변경 내용을 데이터 원본에 저장할 수 있습니다. 또는 **[SubmitForm](control-image.md)** 함수를 사용하여 구성하기만 한다면 **[이미지](../functions/function-form.md)** 컨트롤이나 다른 컨트롤이 동일한 작업을 수행하도록 구성할 수 있습니다. 어느 경우에나 **Error**, **ErrorKind**, **OnSuccess** 및 **OnFailure** 속성은 결과에 대한 피드백을 제공합니다.

**[SubmitForm](../functions/function-form.md)** 함수가 실행되면 먼저 사용자가 제출하려는 데이터의 유효성을 검사합니다. 필수 필드에 값이 없거나 다른 값이 어떤 제약 조건에 부합하지 않는 경우 **ErrorKind** 속성이 설정되고 **OnFailure** 수식이 실행됩니다. 데이터가 올바른 경우에만(즉 양식의 **Valid** 속성이 **true**인 경우) 사용자가 선택할 수 있게 **변경 내용 저장** 단추 또는 기타 컨트롤을 구성할 수 있습니다. 사용자는 문제를 해결할 뿐 아니라 **변경 내용 저장** 단추를 다시 선택하여(또는 앞서 설명한 대로 **취소** 단추를 선택하여 변경 내용 취소) **Error** 및 **ErrorKind** 속성을 다시 설정해야 합니다.

데이터가 유효성 검사를 통과할 경우 **[SubmitForm](../functions/function-form.md)** 이 데이터를 데이터 원본에 보내며 여기서 네트워크 대기 시간에 따라 다소 시간이 걸릴 수 있습니다.

* 제출에 성공하면 **Error** 속성이 지워지고 **ErrorKind** 속성이 **ErrorKind.None**으로 설정되며 **OnSuccess** 수식이 실행됩니다. 사용자라 레코드를 만든 경우(즉 양식이 이전에 **새로 만들기** 모드였음) 양식이 **편집** 모드로 전환되어 사용자가 새로 만든 레코드나 다른 레코드를 편집할 수 있게 됩니다.
* 제출에 실패하면 **Error** 속성에 사용자에게 친숙한 데이터 원본의 오류 메시지가 표시되어 문제를 설명합니다. **ErrorKind** 속성은 문제에 따라 적합하게 설정되며 **OnFailure** 수식이 실행됩니다.

일부 데이터 원본에서 두 사람이 동시에 동일한 레코드 업데이트를 시도하는 것을 탐지할 수 있습니다. 이 경우 **ErrorKind**가 **ErrorKind.Conflict**로 설정되며 다른 사용자의 변경 내용으로 데이터 원본을 새로 고친 다음, 해당 사용자의 변경 내용을 다시 적용하는 조치를 취합니다.

> [!TIP]
> 사용자가 진행 중인 변경 내용을 취소할 수 있게 양식에 **취소** 단추를 제공할 경우, 이 속성이 화면 변경을 위한 **[Navigate](../functions/function-form.md)** 함수를 포함한다 하더라도 **[ResetForm](properties-core.md)** 함수를 단추의 **[OnSelect](../functions/function-navigate.md)** 속성에 추가합니다. 그렇지 않으면 양식이 사용자의 변경 내용을 유지합니다.

### <a name="layout"></a>레이아웃
기본적으로 카드는 전화 앱의 한 열, 테이블 앱의 세 열에 놓입니다. 양식을 구성할 때 양식에 있는 열 수와, 카드가 해당 값에 맞출지 여부를 지정할 수 있습니다. 이 설정은 카드의 **X**, **Y** 및 **Width** 속성을 설정하는 데만 사용되므로 속성으로 노출되지 않습니다.

자세한 내용은 [데이터 양식 레이아웃 이해](../working-with-form-layout.md)를 참조하세요.

## <a name="key-properties"></a>주요 속성
**DataSource** – 사용자가 표시하고, 편집하거나, 만드는 레코드를 포함하는 데이터 원본입니다.

* 이 속성을 설정하지 않으면 사용자가 레코드를 표시하거나, 편집하거나, 만들 수 없고 추가적인 메타데이터나 유효성 검사가 제공되지 않습니다.

**DefaultMode** -양식 컨트롤의 최초 모드입니다.  아래 **모드**의 설명에서 허용되는 값과 의미를 참조하세요. 

**DisplayMode** - 양식 컨트롤에서 데이터 카드와 컨트롤에 사용되는 모드입니다.  

**Mode** 속성을 기준으로 파생되며 독립적으로 설정할 수 없습니다.

| 모드 | DisplayMode | 설명 |
| --- | --- | --- |
| **FormMode.Edit** |**DisplayMode.Edit** |데이터 카드 및 컨트롤은 편집이 가능하며, 레코드에 대한 변경 내용을 수락할 준비가 되어 있습니다. |
| **FormMode.New** |**DisplayMode.Edit** |데이터 카드 및 컨트롤은 편집이 가능하며,새 레코드를 수락할 준비가 되어 있습니다. |
| **FormMode.View** |**DisplayMode.View** |데이터 카드 및 컨트롤은 편집할 수 없으며 보기에 최적화되어 있습니다. |

**Error** – **[SubmitForm](../functions/function-form.md)** 함수 실패 시 이 양식에 대해 표시하는 사용자에게 친숙한 오류 메시지입니다.

* 이 속성은 **편집 양식** 컨트롤에만 적용됩니다.
* 이 속성은 **[SubmitForm](../functions/function-form.md)** , **EditForm** 또는 **[ResetForm](../functions/function-form.md)** 함수가 실행되었을 때만 변경됩니다.
* 오류가 발생하지 않으면 이 속성은 *비어* 있으며 **ErrorKind**가 **ErrorKind.None**으로 설정됩니다.
* 가능한 경우 오류 메시지는 사용자의 언어로 반환됩니다. 일부 오류 메시지는 데이터 원본에서 직접 가져오므로 사용자의 언어로 제공되지 않을 수 있습니다.

**ErrorKind** – **SubmitForm** 실행 시 오류가 발생한 경우 발생한 오류의 종류입니다.

* **편집 양식** 컨트롤에만 적용됩니다.
* 이 속성은 **[Errors](../functions/function-errors.md)** 함수와 동일한 열거형입니다. **편집 양식** 컨트롤은 다음과 같은 값을 반환할 수 있습니다.

| ErrorKind | 설명 |
| --- | --- |
| **ErrorKind.Conflict** |다른 사용자가 동일한 레코드를 변경하여 변경 충돌이 발생했습니다. **[Refresh](../functions/function-refresh.md)** 함수를 실행하여 레코드를 다시 로드한 다음 다시 변경합니다. |
| **ErrorKind.None** |알 수 없는 종류의 오류입니다. |
| **ErrorKind.Sync** |데이터 원본이 오류를 보고했습니다. 자세한 내용은 **Error** 속성을 확인합니다. |
| **ErrorKind.Validation** |일반적인 유효성 검사 문제를 발견했습니다. |

**Item** – 사용자가 표시하거나 편집할 **DataSource**의 레코드입니다.

**LastSubmit** – 서버 생성 필드를 포함하여 마지막으로 제출에 성공한 레코드입니다.

* 이 속성은 **편집 양식** 컨트롤에만 적용됩니다.
* 고유 번호를 갖는 **ID** 필드 등, 데이터 원본이 자동적으로 필드를 생성하거나 계산하는 경우, **SubmitForm**을 성공적으로 실행한 후 **LastSubmit** 속성이 이 새 값을 갖게 됩니다.
* 이 속성의 값은 **OnSuccess** 수식으로 제공됩니다.

**Mode** – 이 컨트롤은 **편집** 또는 **새로 만들기** 모드입니다.

| 모드 | 설명 |
| --- | --- |
| **FormMode.Edit** |사용자가 이 양식을 사용하여 레코드를 편집할 수 있습니다. 양식의 카드에 있는 값에는 기존 레코드가 미리 입력되며 사용자가 변경합니다. **[SubmitForm](../functions/function-form.md)** 함수가 성공적으로 실행되면 기존 레코드가 수정됩니다. |
| **FormMode.New** |사용자가 이 양식을 사용하여 레코드를 만들 수 있습니다. 폼의 컨트롤에 있는 값은 데이터 원본 레코드의 기본값으로 미리 채워집니다. **[Submitform](../functions/function-form.md)** 함수가 성공적으로 실행 되 면 레코드가 생성 됩니다. |
| **FormMode.View** |사용자가 이 양식을 사용하여 레코드를 볼 수 있습니다. 폼의 컨트롤에 있는 값은 데이터 원본 레코드의 기본값으로 미리 채워집니다. |

다음과 같은 변경 중 하나가 발생하면 양식이 **새로 만들기** 모드에서 **편집** 모드로 전환됩니다.

* 양식을 성공적으로 제출하고 레코드가 만들어졌습니다. 갤러리가 이 새 레코드로 선택을 자동으로 이동하도록 설정된 경우, 만들어진 레코드에 대해 양식이 **편집** 모드로 지정되어 사용자가 추가적인 변경을 수행할 수 있게 됩니다.
* **[EditForm](../functions/function-form.md)** 함수가 실행됩니다.
* **[ResetForm](../functions/function-form.md)** 함수가 실행됩니다. 예를 들어, 사용자가 이 함수를 통해 구성된 **취소** 단추를 선택할 수 있습니다.

**OnFailure** – 데이터 작업에 실패했을 때 앱이 응답하는 방식입니다.

* 이 속성은 **편집 양식** 컨트롤에만 적용됩니다.

**OnReset** – **편집 양식** 컨트롤이 재설정되었을 때 앱이 응답하는 방식입니다.

* 이 속성은 **편집 양식** 컨트롤에만 적용됩니다.

**OnSuccess** – 데이터 작업에 성공했을 때 앱이 응답하는 방식입니다.

* 이 속성은 **편집 양식** 컨트롤에만 적용됩니다.

**Unsaved** – **편집 양식** 컨트롤에 저장하지 않은 사용자 변경 내용이 있으면 True입니다.

* 이 속성은 **편집 양식** 컨트롤에만 적용됩니다.
* 저장되지 않은 변경 내용이 사라지기 전에 이 속성을 사용하여 사용자에게 경고합니다.  사용자가 현재 레코드에 변경 내용을 저장하기 전에 **[갤러리](control-gallery.md)** 의 다른 레코드를 선택하지 않게 하려면 갤러리의 **[Disabled](properties-core.md)** 속성을 **Form.Unsaved**로 설정하고 새로 고침 작업도 사용하지 않게 설정합니다.

**Updates** – 양식 컨트롤에 로드한 레코드에 대한 데이터 원본에 다시 쓸 값입니다.  

* 이 속성은 **편집 양식** 컨트롤에만 적용됩니다.
* 이 속성을 사용하여 컨트롤 내의 카드에서 필드 값을 추출합니다.  그런 다음 이 값을 사용하여 **[Patch](../functions/function-patch.md)** 함수 호출이나 연결에서 노출된 다른 메서드로 데이터 원본을 수동으로 업데이트할 수 있습니다.  **[SubmitForm](../functions/function-form.md)** 함수를 사용하는 경우 이 속성이 필요하지 않습니다.
* 이 속성은 값 레코드를 반환합니다.  예를 들어 양식 컨트롤에 **Name** 및 **Quantity** 필드의 카드 컨트롤이 있고 이 카드에 대한 **[Update](control-card.md)** 속성이 각각 "Widget"과 10이라면 양식 컨트롤에 대한 **Updates** 속성은 **{ Name: "Widget", Quantity: 10 }** 를 반환합니다.

**Valid** – **[Card](control-card.md)** 또는 **Edit form** 컨트롤에 올바른 항목이 있고 데이터 원본에 제출할 수 있는지의 여부입니다.

* 이 속성은 **편집 양식** 컨트롤에만 적용됩니다.
* **양식** 컨트롤의 **Valid** 속성은 양식의 모든카드 **[ 컨트롤에 있는 ](control-card.md)Valid** 속성을 집계합니다. 양식의 **Valid** 속성은 양식의 모든 카드에 있는 데이터가 올바른 경우에만 **true**이며 그 밖의 경우 양식의 **Valid** 속성은 **false**입니다.
* 양식의 데이터가 올바르지만 아직 제출되지 않았을 때만 변경 내용을 저장하는 단추를 사용하려면 단추의 **DisplayMode** 속성을 다음 수식으로 설정합니다.
  
    **SubmitButton.DisplayMode = If(IsBlank( Form.Error ) || Form.Valid, DisplayMode.Edit, DisplayMode.Disabled)**

## <a name="additional-properties"></a>추가 속성
**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="more-information"></a>자세한 정보
양식이 작동하는 방법에 대한 포괄적인 개요는 [데이터 양식 이해](../working-with-forms.md)를 참조하세요.

## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="screen-reader-support"></a>화면 판독기 지원
* **[레이블](control-text-box.md)** 을 사용하여 양식에 제목을 추가해 보세요.
