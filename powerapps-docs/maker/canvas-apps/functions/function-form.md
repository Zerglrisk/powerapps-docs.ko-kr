---
title: EditForm, NewForm, SubmitForm, ResetForm 및 ViewForm 함수 | Microsoft Docs
description: Power Apps의 EditForm, NewForm, SubmitForm, ResetForm 및 ViewForm 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8cb2acc15d7d82e2c0935133ffdaf5e4f5284f0c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730885"
---
# <a name="editform-newform-submitform-resetform-and-viewform-functions-in-power-apps"></a>Power Apps의 EditForm, NewForm, SubmitForm, ResetForm 및 ViewForm 함수
**[편집 양식](../controls/control-form-detail.md)** 컨트롤의 항목을 보거나 편집하거나 생성하고 콘텐츠를 저장하고 컨트롤을 다시 설정합니다.

## <a name="overview"></a>개요
다음 함수는 **편집 양식** 컨트롤의 상태를 변경합니다.  양식 컨트롤은 다음 모드 중 하나입니다.

| 모드 | 설명 |
| --- | --- |
| **FormMode.Edit** |양식에 기존 레코드가 채워지고 사용자가 필드 값을 수정할 수 있습니다.  완료되면 사용자가 변경 내용을 레코드에 저장할 수 있습니다. |
| **FormMode.New** |양식에 기본값이 채워지고 사용자가 필드 값을 수정할 수 있습니다.  완료되면 사용자가 레코드를 데이터 원본에 추가할 수 있습니다. |
| **FormMode.View** |양식에 기존 레코드가 채워지지만 사용자가 필드 값을 수정할 수 없습니다. |

## <a name="description"></a>설명
이러한 함수는 사용자가 편집 내용을 저장하거나 편집 내용을 취소하거나 레코드를 만들 수 있도록 **[Button](../controls/control-button.md)** 이나 **[Image](../controls/control-image.md)** 컨트롤의 **[OnSelect](../controls/properties-core.md)** 수식에서 호출됩니다. [컨트롤과 이러한 함수를 함께 사용](../working-with-forms.md)하여 완벽한 솔루션을 만들 수 있습니다.

이 함수는 값을 반환하지 않습니다.

### <a name="submitform"></a>SubmitForm
Form 컨트롤의 변경 내용을 데이터 원본에 저장하려면 Button 컨트롤의 **[OnSelect](../controls/properties-core.md)** 속성에 **SubmitForm** 함수를 사용합니다.

이 함수는 변경 내용을 제출하기 전에 필수로 표시되었거나 값에 하나 이상의 제약 조건이 있는 필드에서 유효성 검사 문제를 확인합니다. 이 동작은 **[Validate](function-validate.md)** 함수의 동작과 일치합니다.

**SubmitForm**은 Form 컨트롤에 포함된 **[Card](../controls/control-card.md)** 컨트롤의 **[Valid](../controls/control-card.md)** 속성을 모두 집계한 Form의 **[Valid](../controls/control-form-detail.md)** 속성을 검사합니다. 문제가 발생하면 데이터가 제출되지 않고 Form 컨트롤의 **[Error](../controls/control-form-detail.md)** 및 **[ErrorKind](../controls/control-form-detail.md)** 속성이 그에 맞게 설정됩니다.

유효성 검사를 통과하면 **SubmitForm**은 변경 내용을 데이터 원본에 제출합니다.

* 성공하면 Form의 **[OnSuccess](../controls/control-form-detail.md)** 동작이 실행되고 **[Error](../controls/control-form-detail.md)** 및 **[ErrorKind](../controls/control-form-detail.md)** 속성이 지워집니다.  양식이 **FormMode.New** 모드에 있었다면 **FormMode.Edit** 모드로 돌아갑니다.
* 실패할 경우 Form의 **[OnFailure](../controls/control-form-detail.md)** 동작이 실행되고 **[Error](../controls/control-form-detail.md)** 및 **[ErrorKind](../controls/control-form-detail.md)** 속성이 그에 맞게 설정됩니다.  양식의 모드는 변경되지 않습니다.  

### <a name="editform"></a>EditForm
**EditForm** 함수는 Form 컨트롤의 모드를 **FormMode.Edit**으로 변경합니다. 이 모드에서는 Form 컨트롤의 **[Item](../controls/control-form-detail.md)** 속성 내용을 사용하여 양식을 채웁니다.  양식이 이 모드에 있을 때 **SubmitForm** 함수가 실행되면 레코드가 변경되고 생성되지 않습니다.  **FormMode.Edit**은 Form 컨트롤의 기본값입니다.

### <a name="newform"></a>NewForm
**NewForm** 함수는 Form 컨트롤의 모드를 **FormMode.New**로 변경합니다. 이 모드에서는 Form 컨트롤의 **[Item](../controls/control-form-detail.md)** 속성 콘텐츠가 무시되고 Form의 **[DataSource](../controls/control-form-detail.md)** 속성 기본값으로 양식이 채워집니다. 양식이 이 모드에 있을 때 **SubmitForm** 함수가 실행되면 레코드가 생성되고 변경되지 않습니다.

### <a name="resetform"></a>ResetForm
**ResetForm** 함수는 사용자가 변경하기 전에 양식의 콘텐츠를 초기 값으로 다시 설정합니다. 양식이 **FormMode.New** 모드에 있으면, 양식이 **FormMode.Edit** 모드로 다시 설정됩니다. 양식 컨트롤의 **[OnReset](../controls/control-form-detail.md)** 동작도 실행됩니다.  **[Reset](function-reset.md)** 함수를 사용하여 개별 컨트롤을 다시 설정할 수도 있지만 양식 내에서만 가능합니다.

### <a name="viewform"></a>ViewForm
**ViewForm** 함수는 Form 컨트롤의 모드를 **FormMode.View**로 변경합니다. 이 모드에서는 Form 컨트롤의 **[Item](../controls/control-form-detail.md)** 속성 내용을 사용하여 양식을 채웁니다.  **Submitform** 및 **resetform** 함수는이 모드에서 영향을 주지 않습니다.

### <a name="displaymode-property"></a>DisplayMode 속성
현재 모드는 **Mode** 속성을 통해 읽을 수 있습니다.  모드는 양식 컨트롤 내 데이터 카드 및 컨트롤에 사용할 수 있는 **DisplayMode** 속성의 값도 결정합니다.  데이터 카드의 **DisplayMode** 속성은 데이터 카드를 참조 하는 컨트롤의 **DisplayMode** 속성에 따라 **DisplayMode** (양식 참조)로 설정 됩니다. 

| 모드 | DisplayMode | 설명 |
| --- | --- | --- |
| **FormMode.Edit** |**DisplayMode.Edit** |데이터 카드 및 컨트롤은 편집이 가능하며, 레코드에 대한 변경 내용을 수락할 준비가 되어 있습니다. |
| **FormMode.New** |**DisplayMode.Edit** |데이터 카드 및 컨트롤은 편집이 가능하며,새 레코드를 수락할 준비가 되어 있습니다. |
| **FormMode.View** |**DisplayMode.View** |데이터 카드 및 컨트롤은 편집할 수 없으며 보기에 최적화되어 있습니다. |

## <a name="syntax"></a>구문
**SubmitForm**( *FormName* )

* *FormName* - 필수 항목입니다. 데이터 원본을 제출할 Form 컨트롤입니다.

**EditForm**( *FormName* )

* *FormName* - 필수 항목입니다.  **FormMode.Edit** 모드로 전환할 Form 컨트롤입니다.

**NewForm**( *FormName* )

* *FormName* - 필수 항목입니다. **FormMode.New** 모드로 전환할 Form 컨트롤입니다.

**ResetForm**( *FormName* )

* *FormName* - 필수 항목입니다. 초기 값으로 다시 설정할 Form 컨트롤입니다. 또한 **FormMode.New** 모드에서 **FormMode.Edit** 모드로 양식을 전환합니다.

**ViewForm**( *FormName* )

* *FormName* - 필수 항목입니다.  **FormMode.View** 모드로 전환할 Form 컨트롤입니다.

## <a name="examples"></a>예
전체 예제는 [데이터 폼 이해](../working-with-forms.md)를 참조하세요.

1. Button 컨트롤을 추가하고 **저장**이 표시되도록 **[Text](../controls/properties-core.md)** 속성을 설정하고 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **SubmitForm( EditForm )**
2. Form 컨트롤의 **[OnFailure](../controls/control-form-detail.md)** 속성을 비워두고 **[OnSuccess](../controls/control-form-detail.md)** 속성을 다음 수식으로 설정합니다.
   
    **Back()**
3. **[Label](../controls/control-text-box.md)** 컨트롤의 이름을 **ErrorText**로 지정하고 **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **EditForm.Error**
   
    사용자가 **저장** 단추를 선택하면 Form 컨트롤의 모든 변경 내용이 기본 데이터 원본에 제출됩니다.
   
   * 제출이 성공하면 변경 내용이 저장되거나 Form 컨트롤이 **New** 모드에 있으면 레코드가 생성됩니다. **ErrorText**가 *비어* 있고 이전 화면이 다시 나타납니다.
   * 제출이 실패하면 **ErrorText**가 친숙한 오류 메시지를 표시하고, 사용자가 문제를 해결하고 다시 시도할 수 있도록 현재 화면이 계속 표시됩니다.
4. Button 컨트롤을 추가하고 **취소**가 표시되도록 **[Text](../controls/properties-core.md)** 속성을 설정하고 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **ResetForm( EditForm ); Back()**
   
    사용자가 **취소** 단추를 선택하면 Form 컨트롤의 값이 사용자가 편집을 시작하기 전 상태로 재설정되고 이전 화면이 다시 나타나고 Form 컨트롤이 **New** 모드이면 **Edit** 모드로 돌아갑니다.
5. Button 컨트롤을 추가하고 **새로 만들기**가 표시되도록 **[Text](../controls/properties-core.md)** 속성을 설정하고 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **NewForm( EditForm ); Navigate( EditScreen, None )**
   
    사용자가 **새로 만들기** 단추를 선택하면 Form 컨트롤이 **New** 모드로 전환되고 Form 컨트롤의 데이터 원본 기본값으로 해당 컨트롤이 채워지고 Form 컨트롤이 포함된 화면이 나타납니다. **SubmitForm** 함수가 실행되면 레코드가 업데이트되는 대신 만들어집니다.

