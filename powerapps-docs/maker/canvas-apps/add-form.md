---
title: Canvas 앱에서 레코드 표시, 편집 또는 추가 | Microsoft Docs
description: 캔버스 앱 양식을 사용하여 데이터 원본에 테이블의 레코드를 표시, 편집 또는 추가합니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/06/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed7493dcc9c2ef5f0b84052a11dbadb0947af38e
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994126"
---
# <a name="show-edit-or-add-a-record-in-a-canvas-app"></a>Canvas 앱에서 레코드 표시, 편집 또는 추가

Canvas 앱에서 **[표시](controls/control-form-detail.md)** 양식 컨트롤을 추가 하 고 구성 하 여 레코드의 모든 필드를 표시 하 고, **[편집](controls/control-form-detail.md)** 양식 컨트롤을 추가 및 구성 하 여 레코드의 모든 필드를 편집 하 고, 레코드를 추가 하 고, 변경 내용을 데이터 원본에 다시 저장할 수도 있습니다.

## <a name="prerequisites"></a>필수 조건

- PowerApps에서 [컨트롤을 추가하고 구성](add-configure-controls.md)하는 방법을 알아봅니다.
- 이 자습서에 대한 샘플 데이터를 포함하는 [이 Excel 파일](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)을 다운로드합니다.
- Excel 파일을 비즈니스용 OneDrive와 같은 [클라우드 스토리지 계정](connections/cloud-storage-blob-connections.md)에 업로드합니다.
- 휴대폰에 대 한 앱을 만들거나 열고 Excel 파일의 **FlooringEstimates** 테이블에 대 한 [연결을 추가](add-data-connection.md) 합니다.

    양식을 태블릿 앱에 추가할 수 있지만이 항목에는 기본적으로 세 개의 열이 있으므로이 항목은 일치 하지 않습니다.

- 기존 앱을 여는 경우 해당 앱에 [화면을 추가](add-screen-context-variables.md) 합니다.

## <a name="add-a-form-and-show-data"></a>폼 추가 및 데이터 표시
1. 빈 화면에서 **[드롭다운](controls/control-drop-down.md)** 컨트롤을 추가 하 고 이름을 **ChooseProduct**로 설정 합니다.

    > [!NOTE]
   > 컨트롤을 추가하거나, 이름을 바꾸거나, 속성을 설정하는 방법을 잘 모르는 경우 [컨트롤 추가 및 제어](add-configure-controls.md)를 참조하세요.

1. 오른쪽 창의 **속성** 탭에서 **항목** 을 `FlooringEstimates`로 설정 하 고 **값** 을 `Name`로 설정 합니다.

    ![양식의 Items 속성 설정](./media/add-form/items-property.png)

    목록은 데이터 원본에서 바닥재 제품의 이름을 표시합니다.

1. **편집** 양식 컨트롤을 추가 하 고 **ChooseProduct**아래로 이동한 다음 폼의 크기를 조정 하 여 화면 대부분을 포함 합니다.

    ![양식 추가](./media/add-form/add-a-form.png)

    > [!NOTE]
   > 이 항목에서는 **편집** 양식 컨트롤에 대해 설명 하지만, 유사한 원칙이 **표시** 양식 컨트롤에도 적용 됩니다.

1. 양식의 **[DataSource](controls/control-form-detail.md)** 속성을 **FlooringEstimates** 로 설정 하 고 **[Item](controls/control-form-detail.md)** 속성을 다음 수식으로 설정 합니다.

    `First(Filter(FlooringEstimates, Name=ChooseProduct.Selected.Value))`

   이 수식은 폼 구성을 완료한 후 사용자가 **ChooseProduct**에서 선택한 해당 레코드를 표시하도록 지정합니다.

1. 오른쪽 창의 **속성** 탭에서 **필드 편집**을 선택 합니다.

    ![필드 편집](./media/add-form/edit-fields.png)

1. **필드** 창에서 **필드 추가**를 선택하고, 각 필드에 대한 확인란을 선택한 다음, **추가**를 선택합니다.

    ![필드 추가](./media/add-form/add-fields.png)

1. **필드 추가**옆에 있는 줄임표 (...)를 선택 하 고 **모두 축소**를 선택한 다음 **이름** 을 목록 맨 위로 끌어 옵니다.

    ![필드 이동](./media/add-form/move-field.png)

    **편집** 양식 컨트롤에 변경 내용이 반영 됩니다.

    ![폼 표시](./media/add-form/show-form1.png)

## <a name="set-the-card-type-for-a-field"></a>필드에 대한 카드 유형 설정
1. **필드** 창에서 아래쪽 화살표를 선택 하 여 **Price** 필드를 확장 합니다.

1. **컨트롤 형식** 목록을 연 다음 **편집 슬라이더**를 선택 합니다.

    ![슬라이더 편집](./media/add-form/edit-slider.png)

    양식에서 **Price** 필드는 **텍스트 입력** 컨트롤 대신 **슬라이더** 컨트롤을 표시 합니다.

1. 필드 동일한 프로세스를 따라 **개요** 필드의 컨트롤을 **여러 줄 텍스트 편집** 컨트롤로 변경 합니다.

## <a name="edit-form-only-save-changes"></a>(폼 편집에만) 변경 내용 저장

1. 형식 **Editform**의 이름을 바꿉니다.

1. **[단추](controls/control-button.md)** 컨트롤을 추가하고 이 수식에 **[OnSelect](controls/properties-core.md)** 속성을 설정합니다.

   `SubmitForm(EditForm)`

1. F5 키를 눌러 미리 보기를 열고 제품 이름을 변경한 다음 만든 단추를 선택 합니다.

    **[Submitform](functions/function-form.md)** 함수는 변경 내용을 데이터 원본에 저장 합니다.

1. 필드 Esc 키를 누르거나 오른쪽 위 모서리의 닫기 아이콘을 선택 하 여 미리 보기를 닫습니다.

## <a name="next-steps"></a>다음 단계
[폼](working-with-forms.md), 및 [수식](working-with-formulas.md)을 사용한 작업에 대한 자세한 내용을 알아봅니다.
