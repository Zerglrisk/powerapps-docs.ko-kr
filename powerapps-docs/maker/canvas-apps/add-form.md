---
title: 표시, 편집 또는 캔버스 앱에서 레코드를 추가 합니다. | Microsoft Docs
description: 캔버스 앱 폼을 사용하여 데이터 원본에 테이블의 레코드를 표시, 편집 또는 추가합니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/06/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e94aa48ed3fba1b4591e196e3b81d3fb0f76666f
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63321437"
---
# <a name="show-edit-or-add-a-record-in-a-canvas-app"></a>캔버스 앱에서 레코드를 표시, 편집 또는 추가합니다.

캔버스 앱에 **[표시](controls/control-form-detail.md)** 폼 컨트롤을 추가 및 구성하여 모든 필드를 표시할 수 있으며, 또한 레코드의 필드를 편집하도록 **[편집](controls/control-form-detail.md)** 폼 컨트롤을 추가 및 구성하고, 레코드를 추가하고 데이터 원본에 변경 사항을 저장할수 있습니다.

## <a name="prerequisites"></a>필수 조건

- PowerApps에서 [컨트롤을 추가하고 구성](add-configure-controls.md)하는 방법을 알아봅니다.
- 이 자습서에 대한 샘플 데이터를 포함하는 [이 Excel 파일](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)을 다운로드합니다.
- Excel 파일을 비즈니스용 OneDrive와 같은 [클라우드 저장소 계정](connections/cloud-storage-blob-connections.md)에 업로드합니다.
- 전화 앱을 열거나 만듭니다. Excel 파일에서 **FlooringEstimates** 테이블을 [연결 추가](add-data-connection.md)합니다.

    태블릿 앱에 폼을 추가할 수 있지만, 기본적으로 폼은 세 개 열을 가지므로 이 항목에서는 일치하지 않습니다.

- 기존 앱에서 여는 경우, 앱에 [화면을 추가](add-screen-context-variables.md)합니다.

## <a name="add-a-form-and-show-data"></a>폼 추가 및 데이터 표시
1. 빈 화면에 **[드롭다운](controls/control-drop-down.md)** 컨트롤을 추가하고 이름을 **ChooseProduct**로 지정합니다.

    > [!NOTE]
   > 컨트롤을 추가하거나, 이름을 바꾸거나, 속성을 설정하는 방법을 잘 모르는 경우 [컨트롤 추가 및 구성](add-configure-controls.md)을 참조하세요.

1. 오른쪽 창의 **속성** 탭에서, **항목**을 `FlooringEstimates`으로 설정하고 **Value**에 `Name`을 설정합니다.

    ![폼의 Items 속성 설정](./media/add-form/items-property.png)

    목록은 데이터 원본에서 바닥재 제품의 이름을 표시합니다.

1. **편집** 폼 컨트롤을 추가하여 **ChooseProduct** 아래로 이동한 다음, 화면의 대부분에 맞게 폼 크기를 조정합니다.

    ![양식 추가](./media/add-form/add-a-form.png)

    > [!NOTE]
   > 여기서는 **편집** 폼 컨트롤에 대해 설명하지만 **표시** 폼 컨트롤에도 비슷한 원칙이 적용됩니다.

1. 폼의 **[DataSource](controls/control-form-detail.md)** 속성을 **FlooringEstimates**로 설정하고 **[Item](controls/control-form-detail.md)** 속성을 이 수식으로 설정합니다.

    `First(Filter(FlooringEstimates, Name=ChooseProduct.Selected.Value))`

   이 수식은 폼 구성을 완료한 후 사용자가 **ChooseProduct**에서 선택한 해당 레코드를 표시하도록 지정합니다.

1. 오른쪽 창의 **속성** 탭에서 **필드 편집**을 선택합니다.

    ![필드 편집](./media/add-form/edit-fields.png)

1. **필드** 창에서 **필드 추가**를 선택하고, 각 필드에 대한 확인란을 선택한 다음, **추가**를 선택합니다.

    ![필드 추가](./media/add-form/add-fields.png)

1. **필드 추가** 옆의 줄임표(...)를 선택하고 **모두 축소**를 선택합니다. **Name** 목록을 끌어서 맨 위로 이동합니다.

    ![필드 이동](./media/add-form/move-field.png)

    **편집** 폼 컨트롤에 변경 내용이 반영됩니다.

    ![폼이 표시](./media/add-form/show-form1.png)

## <a name="set-the-card-type-for-a-field"></a>필드에 대한 카드 유형 설정
1. **필드** 창에서 아래쪽 화살표를 선택하여 **Price** 필드를 확장합니다.

1. **컨트롤 형식** 목록을 열고 난 후 **슬라이더 편집**을 선택합니다.

    ![슬라이더 편집](./media/add-form/edit-slider.png)

    폼에서 **Price** 필드는 **텍스트 입력** 컨트롤 대신 **슬라이더** 컨트롤을 표시합니다.

1. (선택 사항) **Overview** 필드 컨트롤을 **여러 줄 텍스트 편집** 컨트롤로 변경하려면 동일한 프로세스를 수행합니다.

## <a name="edit-form-only-save-changes"></a>(편집 폼에만) 변경 내용 저장

1. 폼의 이름을 **EditForm**으로 바꿉니다.

1. **[단추](controls/control-button.md)** 컨트롤을 추가하고 **[OnSelect](controls/properties-core.md)** 속성에 이 수식을 설정합니다.

   `SubmitForm(EditForm)`

1. 미리 보기를 열기 위해 F5 키를 눌러, 제품의 이름을 변경하고 위에서 추가한 단추를 선택합니다.

    **[SubmitForm](functions/function-form.md)** 함수는 데이터 원본에 변경 내용을 저장합니다.

1. (선택 사항) Esc 키를 눌러 (또는 오른쪽 위 모서리의 닫기 아이콘을 선택하여) 미리 보기를 닫습니다.

## <a name="next-steps"></a>다음 단계
[폼](working-with-forms.md), 및 [수식](working-with-formulas.md)을 사용한 작업에 대한 자세한 내용을 알아봅니다.
