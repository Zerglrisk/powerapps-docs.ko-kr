---
title: 캔버스 앱 폼 이해 | Microsoft Docs
description: PowerApps에서 캔버스 앱에 폼을 추가하면 데이터 원본에서 정보를 수집하고 표시할 수 있습니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/27/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 476964166a57bea23469baf0c1e7497be10ab73f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541660"
---
# <a name="understand-canvas-app-forms-in-microsoft-powerapps"></a>Microsoft PowerApps의 캔버스 앱 폼 이해

캔버스 앱에 세 가지 유형의 컨트롤을 추가하여 사용자가 레코드를 찾아보고, 해당 레코드에 대한 세부 정보를 표시하고, 레코드를 편집하거나 만들 수 있습니다.

| 작업 | 컨트롤 | 설명 |
| --- | --- | --- |
| **레코드 찾아보기** |**[갤러리](controls/control-gallery.md)** 컨트롤 |데이터 원본의 레코드를 필터링, 정렬, 검색 및 스크롤하고 특정 레코드를 선택합니다. 작은 화면에서도 한 번에 여러 레코드를 표시할 수 있도록 각 레코드의 일부 필드만 표시합니다. |
| **레코드 세부 정보 표시** |**[표시 폼](controls/control-form-detail.md)** 컨트롤 |단일 레코드의 경우 해당 레코드에 여러 또는 모든 필드를 표시합니다. |
| **레코드 만들기 또는 편집** |**[편집 폼](controls/control-form-detail.md)** 컨트롤 |단일 레코드에서 하나 이상의 필드를 업데이트(또는 기본값으로 시작하는 레코드 만들기)하고, 변경 내용을 기본 데이터 원본에 다시 저장합니다. |

더 쉽게 구분할 수 있도록 각 컨트롤을 다른 화면에 배치합니다.

![3개 화면에 걸쳐 있는 레코드 찾아보기, 보기 및 편집](./media/working-with-forms/three-screens.png)

이 항목에서 설명한 대로 이러한 컨트롤을 수식과 결합하여 전체 사용자 환경을 만듭니다.

## <a name="prerequisites"></a>필수 조건

* PowerApps에 [등록](../signup-for-powerapps.md)한 다음, 등록에 사용한 동일한 자격 증명을 입력하여 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
* PowerApps에서 [컨트롤 구성](add-configure-controls.md)을 어떻게 하는지 알아봅니다.

## <a name="explore-a-generated-app"></a>생성된 앱 탐색
PowerApps는 지정한 데이터 원본을 기반으로 하는 앱을 자동으로 생성할 수 있습니다. 각 앱에는 앞에서 설명한 컨트롤과 이를 연결하는 수식이 포함된 3개의 화면이 있습니다. 이러한 앱을 "기본적으로(out of the box)" 실행하고, 특정 목표에 맞게 사용자 지정하거나 작동 방식을 검토하여 자신의 앱에 적용되는 유용한 개념을 알아봅니다. 다음 섹션에서는 생성된 앱을 구동하는 화면, 컨트롤 및 수식을 검사합니다.  

### <a name="browse-screen"></a>찾아보기 화면
![찾아보기 화면 컨트롤](./media/working-with-forms/afd-browse-screen-basic.png)

이 화면에는 다음과 같은 주요 수식이 있습니다.

| 컨트롤 | 지원되는 동작 | 수식 |
| --- | --- | --- |
| **BrowseGallery1** |**Assets** 데이터 원본의 레코드를 표시합니다. |갤러리의 **[Items](controls/properties-core.md)** 속성이 **Assets** 데이터 원본을 기반으로 하는 수식으로 설정됩니다. |
| **ImageNewItem1** |사용자가 레코드를 쉽게 만들 수 있도록 각 필드가 기본값으로 설정된 **편집 및 만들기** 화면을 표시합니다. |이미지의 **[OnSelect](controls/properties-core.md)** 속성이 다음 수식으로 설정됩니다.<br> **NewForm( EditForm1 );<br>Navigate( EditScreen1, None )** |
| **NextArrow1**(갤러리에서) |현재 선택한 레코드의 여러 또는 모든 필드를 볼 수 있도록 **세부 정보** 화면을 표시합니다. |화살표의 **[OnSelect](controls/properties-core.md)** 속성이 다음 수식으로 설정됩니다.<br>**Navigate( DetailScreen1, None )** |

이 화면의 기본 컨트롤인 **BrowseGallery1**은 화면의 영역 대부분을 포함합니다. 사용자는 갤러리를 스크롤하여 더 많은 필드를 표시하거나 업데이트할 특정 레코드를 찾을 수 있습니다.

데이터 원본의 레코드를 표시하도록 갤러리의 **[Items](controls/properties-core.md)** 속성을 설정합니다. 예를 들어 해당 속성을 **Assets**로 설정하여 해당 이름의 데이터 원본에 있는 레코드를 표시합니다.

> [!NOTE]
> 생성된 앱에서 사용자가 레코드를 정렬하고 검색할 수 있도록 **[Items](controls/properties-core.md)** 가 기본적으로 훨씬 더 복잡한 수식으로 설정됩니다. 이 항목의 뒷부분에서 해당 수식을 작성하는 방법을 알아보겠지만, 지금은 간단한 버전으로도 충분합니다.

사용자는 표시하거나 편집할 레코드를 찾는 대신 갤러리 위쪽에 있는 "+" 기호를 선택하여 레코드를 만들 수 있습니다. 이 효과는 **[이미지](controls/control-image.md)** 컨트롤을 추가하고, 그 안에 "+" 기호를 표시하고, **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정하여 만듭니다.
<br>**NewForm( EditForm1 ); Navigate( EditScreen1, None )**

이 수식은 **EditForm1**이라는 **[편집 양식](controls/control-form-detail.md)** 컨트롤이 있는 **편집 및 만들기** 화면을 엽니다. 또한 이 수식은 해당 양식을 **New** 모드로 전환합니다. 이 모드에서는 양식에서 데이터 원본의 기본값을 표시하므로 사용자가 처음부터 레코드를 쉽게 만들 수 있습니다.

**BrowseGallery1**에서 표시되는 모든 컨트롤을 검사하려면 해당 갤러리의 첫 번째 섹션에서 다른 섹션의 템플릿으로 사용되는 컨트롤을 선택합니다. 예를 들어 왼쪽 가장자리에서 가운데 **[레이블](controls/control-text-box.md)** 컨트롤을 선택합니다.

![찾아보기 화면 컨트롤](./media/working-with-forms/afd-browse-gallery-controls.png)

이 예제에서는 컨트롤의 **[Text](controls/properties-core.md)** 속성이 **Assets** 데이터 원본의 필드인 **ThisItem.AssignedTo**로 설정됩니다. 갤러리의 다른 세 **[레이블](controls/control-text-box.md)** 컨트롤의 **[Text](controls/properties-core.md)** 속성은 비슷한 수식으로 설정되며, 각 컨트롤은 데이터 원본의 다른 필드를 표시합니다.  

**[도형](controls/control-shapes-icons.md)** 컨트롤(화살표)을 선택하고, **[OnSelect](controls/properties-core.md)** 속성이 다음 수식으로 설정되어 있는지 확인합니다.
<br>**Navigate( DetailScreen1, None )**

사용자가 **BrowseGallery1**에서 레코드를 찾으면 해당 레코드의 화살표를 선택하여 **DetailScreen1**에 대한 세부 정보를 표시할 수 있습니다. 화살표를 선택하여 사용자는 **BrowseGallery1**의 **Selected** 속성 값을 변경합니다. 이 앱에서 해당 속성은 **DetailScreen1**뿐만 아니라 사용자가 레코드를 업데이트하도록 결정한 경우 **편집 및 만들기** 화면에도 표시할 레코드를 결정합니다.

### <a name="detail-screen"></a>세부 정보 화면
![세부 정보 화면 컨트롤](./media/working-with-forms/afd-detail-screen-basic.png)

이 화면에는 다음과 같은 주요 수식이 있습니다.

| 컨트롤 | 지원되는 동작 | 수식 |
| --- | --- | --- |
| **DetailForm1** |**Assets** 데이터 원본의 레코드를 표시합니다. |**[DataSource](controls/control-form-detail.md)** 속성을 **Assets**로 설정합니다. |
| **DetailForm1** |표시할 레코드를 결정합니다. 생성된 앱에서 사용자가 갤러리에서 선택한 레코드를 표시합니다. |이 컨트롤의 **[Item](controls/control-form-detail.md)** 속성을 다음 값으로 설정합니다.<br>**BrowseGallery1.Selected** |
| **[카드](controls/control-card.md)** 컨트롤 |**[표시 폼](controls/control-form-detail.md)** 컨트롤에서 레코드의 단일 필드를 표시합니다. |**[DataField](controls/control-card.md)** 속성을 큰따옴표로 묶은 필드 이름으로 설정합니다(예: **"Name"** ). |
| **ImageBackArrow1** |사용자가 이 컨트롤을 선택하면 **BrowseScreen1**이 열립니다. |**[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>**Back()** |
| **ImageDelete1** |사용자가 이 컨트롤을 선택하면 레코드를 삭제합니다. |**[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>**Remove( Assets, BrowseGallery1.Selected )** |
| **ImageEdit1** |사용자가 이 컨트롤을 선택하면 현재 레코드에 대한 **편집 및 만들기** 화면이 열립니다. |**[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>**Navigate( EditScreen1, None )** |

화면 위쪽에서 세 개의 이미지가 **DetailForm1** 외부에 있으며 단추로 작동하여 앱의 세 화면을 오케스트레이션합니다.

**DetailForm1**은 이 화면을 지배하고 사용자가 갤러리에서 선택한 레코드를 표시합니다(양식의 **[Item](controls/control-form-detail.md)** 속성이 **BrowseGallery1.Selected**로 설정되었기 때문). 양식의 **[DataSource](controls/control-form-detail.md)** 속성은 각 필드의 사용자에게 친숙한 표시 이름과 같은 데이터 원본에 대한 메타데이터도 제공합니다.

**DetailForm1**에는 여러 **[카드](controls/control-card.md)** 컨트롤이 포함되어 있습니다. **[카드](controls/control-card.md)** 컨트롤 자체 또는 포함된 컨트롤을 선택하여 추가 정보를 검색할 수 있습니다.

![제작 환경에서 선택한 세부 정보 카드 및 카드 컨트롤](./media/working-with-forms/afd-detail-card-controls.png)

**[카드](controls/control-card.md)** 컨트롤의 **[DataField](controls/control-card.md)** 속성은 카드에서 표시하는 필드를 결정합니다. 이 경우 해당 속성은 **AssetID**로 설정됩니다. 카드에는 **[Text](controls/properties-core.md)** 속성이 **Parent.Default**로 설정된 **[레이블](controls/control-text-box.md)** 컨트롤이 있습니다. 이 컨트롤은 카드에 대한 **Default** 값을 표시하며, 이 값은 **[DataField](controls/control-card.md)** 속성을 통해 설정됩니다.

생성된 앱에서 **[카드](controls/control-card.md)** 컨트롤은 기본적으로 잠겨 있습니다. 카드가 잠겨 있으면 **[DataField](controls/control-card.md)** 와 같은 일부 속성을 수정할 수 없으며 해당 속성에는 수식 입력줄을 사용할 수 없습니다. 이 제한은 사용자 지정이 생성된 앱의 기본 기능을 손상시키지 않도록 합니다. 그러나 오른쪽 창에서 카드 및 해당 컨트롤의 속성 일부를 변경할 수 있습니다.

![옵션 창이 열려 있는 세부 정보 화면](./media/working-with-forms/detail-screen-new.png)

오른쪽 창에서 표시할 필드와 각 필드에서 표시하는 컨트롤의 종류를 선택할 수 있습니다.

### <a name="editcreate-screen"></a>편집/만들기 화면
![편집 화면 컨트롤](./media/working-with-forms/afd-edit-screen-basic.png)

이 화면에는 다음과 같은 주요 수식이 있습니다.

| 컨트롤 | 지원되는 동작 | 수식 |
| --- | --- | --- |
| **EditForm1** |**Assets** 데이터 원본의 레코드를 표시합니다. |**[DataSource](controls/control-form-detail.md)** 속성을 **Assets**로 설정합니다. |
| **EditForm1** |표시할 레코드를 결정합니다. 생성된 앱에서 사용자가 **BrowseScreen1**에서 선택한 레코드를 표시합니다. |**[Item](controls/control-form-detail.md)** 속성을 다음 값으로 설정합니다.<br>**BrowseGallery1.Selected** |
| **[카드](controls/control-card.md)** 컨트롤 |**[편집 양식](controls/control-form-detail.md)** 컨트롤에서 사용자가 레코드의 필드를 하나 이상 편집할 수 있도록 컨트롤을 제공합니다. |**[DataField](controls/control-card.md)** 속성을 큰따옴표로 묶은 필드 이름으로 설정합니다(예: **"Name"** ). |
| **ImageCancel1** |사용자가 이 컨트롤을 선택하면 진행 중인 변경 내용을 삭제하고 **세부 정보** 화면이 열립니다. |**[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>**ResetForm( EditForm1 ); Back()** |
| **ImageAccept1** |사용자가 이 컨트롤을 선택하면 변경 내용을 데이터 원본에 제출합니다. |**[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>**SubmitForm( EditForm1 )** |
| **EditForm1** |변경 내용이 승인되면 이전 화면으로 돌아갑니다. |**[OnSuccess](controls/control-form-detail.md)** 속성을 다음 수식으로 설정합니다.<br>**Back()** |
| **EditForm1** |변경 내용이 승인되지 않으면 사용자가 문제를 해결하고 다시 제출할 수 있도록 현재 화면에 남아 있습니다. |**[OnFailure](controls/control-form-detail.md)** 속성을 비워둡니다. |
| **LblFormError1** |변경 내용이 승인되지 않으면 오류 메시지를 표시합니다. |**[Text](controls/properties-core.md)** 속성을 다음 값으로 설정합니다.<br>**EditForm1.Error** |

**세부 정보** 화면에서처럼 **EditForm1**이라는 양식 컨트롤이 **편집 및 만들기** 화면을 지배합니다. 또한 **EditForm1**의 **[Item](controls/control-form-detail.md)** 속성이 **BrowseGallery1.Selected**로 설정되므로 사용자가 **BrowseScreen1**에서 선택한 레코드가 양식에 표시됩니다 . **세부 정보** 화면은 각 필드를 읽기 전용으로 표시하지만, 사용자는 **EditForm1**의 컨트롤을 사용하여 하나 이상의 필드 값을 업데이트할 수 있습니다. 또한 **[DataSource](controls/control-form-detail.md)** 속성을 사용하여 각 필드의 사용자에게 친숙한 표시 이름과 변경 내용을 저장해야 하는 위치와 같은 이 데이터 원본에 대한 메타데이터에 액세스합니다.

사용자가 업데이트를 취소하기 위해 "X" 아이콘을 선택하면 **[ResetForm](functions/function-form.md)** 함수에서 저장되지 않은 변경 내용을 삭제하고, **[Back](functions/function-navigate.md)** 함수에서 **세부 정보** 화면을 엽니다. 사용자가 **BrowseScreen1**에서 다른 레코드를 선택할 때까지 **세부 정보** 화면과 **편집 및 만들기** 화면 모두에서 동일한 레코드를 표시합니다. 해당 레코드의 필드는 사용자가 변경한 다음 중단한 변경 내용이 아니라 가장 최근에 저장된 값으로 설정된 상태로 유지됩니다.

사용자가 폼에서 하나 이상의 값을 변경한 다음 "확인 표시" 아이콘을 선택하면 **[SubmitForm](functions/function-form.md)** 함수에서 사용자의 변경 내용을 데이터 원본으로 보냅니다.

* 변경 내용이 성공적으로 저장되면, 폼의 **[OnSuccess](controls/control-form-detail.md)** 수식이 실행되고 **Back()** 함수에서 세부 정보 화면을 열어 업데이트된 레코드를 표시합니다.
* 변경 내용이 성공적으로 저장되지 않으면, 양식의 **[OnFailure](controls/control-form-detail.md)** 수식이 실행되지만 '공백'이므로 아무 것도 변경되지 않습니다. 사용자가 변경을 취소하거나 오류를 해결할 수 있도록 **편집 및 만들기** 화면이 열려 있습니다. **LblFormError1**은 양식의 **Error** 속성이 설정된 사용자에게 친숙한 오류 메시지를 표시합니다.

**[표시 폼](controls/control-form-detail.md)** 컨트롤과 마찬가지로 **[편집 폼](controls/control-form-detail.md)** 컨트롤에는 레코드의 다른 필드를 표시하는 다른 컨트롤이 포함된 **[카드](controls/control-card.md)** 컨트롤이 포함되어 있습니다.

![제작 환경에서 선택한 편집 카드 및 카드 컨트롤](./media/working-with-forms/afd-edit-card-controls.png)

이전 이미지에서 선택한 카드는 **AssetID** 필드를 표시하고 사용자가 해당 필드의 값을 편집할 수 있도록 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 포함하고 있습니다. 이와 대조적으로 세부 정보 화면에는 읽기 전용 **[레이블](controls/control-text-box.md)** 컨트롤의 동일한 필드가 표시 됩니다. **[텍스트 입력](controls/control-text-input.md)** 컨트롤에는 **Parent. default**로 설정 된 **[기본](controls/properties-core.md)** 속성이 있습니다. 사용자가 레코드를 편집하는 대신 레코드를 만든 경우 해당 컨트롤은 사용자가 새 레코드에 대해 변경할 수 있는 초기 값을 표시합니다.

오른쪽 창에서 각 카드를 표시하거나, 숨기거나, 다시 정렬하거나, 다른 유형의 컨트롤에 있는 필드를 표시하도록 구성할 수 있습니다.

![옵션 창이 열려 있는 편집 화면](./media/working-with-forms/edit-screen.png)

## <a name="build-an-app-from-scratch"></a>앱을 처음부터 빌드
PowerApps에서 앱을 생성하는 방법을 이해하면 이 항목의 앞부분에서 설명한 것과 동일한 구성 요소와 수식을 사용하여 앱을 직접 빌드할 수 있습니다.

## <a name="identify-test-data"></a>테스트 데이터 식별
이 항목을 최대한 활용하려면 실험할 수 있는 데이터 원본으로 시작합니다. 걱정할 필요 없이 읽고 업데이트할 수 있는 테스트 데이터가 있어야 합니다.

> [!NOTE]
> 공백이 있는 열 이름이 데이터 원본으로 포함된 SharePoint 목록 또는 Excel 테이블을 사용하는 경우 PowerApps는 공백을 **"\_x0020\_"** 으로 바꿉니다. 예를 들어 SharePoint 또는 Excel의 **"Column Name"** 은 데이터 레이아웃에 표시되거나 수식에 사용될 때 PowerApps에 **"Column_x0020_Name"** 으로 나타납니다.

이 항목의 나머지 부분을 정확하게 수행하려면 다음 데이터가 포함된 "아이스크림"이라는 SharePoint 목록을 만듭니다.

![아이스크림 SharePoint 목록](./media/working-with-forms/sharepointlist-icecream.png)

* 비어 있는 전화 앱을 만들고 [데이터 원본에 연결합니다](add-data-connection.md).
  
    > [!NOTE]
  > 태블릿 앱은 매우 비슷하지만, 추가 화면 공간을 최대한 활용하기 위해 별도의 [화면 레이아웃](#screen-design)이 필요할 수 있습니다.
  
    항목의 나머지 부분에 있는 예제는 **Ice Cream**이라는 데이터 원본을 기반으로 합니다.

## <a name="browse-records"></a>레코드 찾아보기
찾아보기 화면에 있는 갤러리에서 레코드를 찾아서 해당 레코드에 대한 정보 부분을 빠르게 가져옵니다.

1. **세로** 갤러리를 추가하고 레이아웃을 **제목**으로 변경합니다.
   
    ![아이스크림 데이터 원본에 연결된 갤러리](./media/working-with-forms/new-gallery.png)
2. 갤러리의 **[Items](controls/properties-core.md)** 속성을 **Ice Cream**으로 설정합니다.
3. 갤러리에 있는 첫 번째 레이블의 **[Text](controls/properties-core.md)** 속성을 **ThisItem.Title**로 설정합니다(다르게 설정된 경우).
   
    레이블은 이제 각 레코드의 **제목** 필드에 값을 표시합니다.
   
    ![아이스크림 데이터 원본에 연결된 갤러리](./media/working-with-forms/new-gallery-2.png)
4. 화면을 채우도록 갤러리의 크기를 조정하고 **[TemplateSize](controls/control-gallery.md)** 속성을 **60**으로 설정합니다.
   
    이 화면은 데이터 원본의 모든 레코드를 표시하는 다음 예제와 비슷합니다.
   
    ![아이스크림 데이터 원본에 연결된 갤러리](./media/working-with-forms/new-gallery-icecream.png)

## <a name="view-details"></a>세부 정보 보기
갤러리에서 원하는 정보가 표시되지 않으면 레코드의 화살표를 선택하여 세부 정보 화면을 엽니다. 해당 화면의 **[표시 폼](controls/control-form-detail.md)** 컨트롤은 선택한 레코드의 더 많은, 아마도 모든 필드를 표시합니다.

**[표시 폼](controls/control-form-detail.md)** 컨트롤은 다음 두 가지 속성을 사용하여 레코드를 표시합니다.

* **[DataSource](controls/control-form-detail.md)** 속성 -  레코드를 보유하고 있는 데이터 원본의 이름입니다. 이 속성은 오른쪽 패널을 필드로 채우고 각 필드의 표시 이름 및 데이터 형식(문자열, 숫자, 날짜 등)을 결정합니다.  
* **[Item](controls/control-form-detail.md)** 속성 -  표시할 레코드입니다.  이 속성은 종종 **[갤러리](controls/control-gallery.md)** 컨트롤의 **Selected** 속성에 연결되므로 사용자가 **[갤러리](controls/control-gallery.md)** 컨트롤에서 레코드를 선택한 다음 해당 레코드로 드릴할 수 있습니다.

**[DataSource](controls/control-form-detail.md)** 속성이 설정되면 오른쪽 창에서 필드를 추가 및 제거하고 표시 방법을 변경할 수 있습니다.

이 화면에서 사용자는 레코드의 값을 의도적이거나 실수로 변경할 수 없습니다. **[표시 폼](controls/control-form-detail.md)** 컨트롤은 읽기 전용이므로 레코드를 수정하지 않습니다.

**[표시 폼](controls/control-form-detail.md)** 컨트롤을 추가하려면 다음을 수행합니다.

1. 화면을 추가한 다음 이 화면에 **[표시 폼](controls/control-form-detail.md)** 컨트롤을 추가합니다
2. 양식 컨트롤의 **[DataSource](controls/control-form-detail.md)** 속성을 **'아이스크림'** 으로 설정합니다.

오른쪽 창에서 화면에 표시할 필드와 각 필드에 표시할 카드 유형을 선택할 수 있습니다. 오른쪽 창에서 변경하면 각 **[카드](controls/control-card.md)** 컨트롤의 **[DataField](controls/control-card.md)** 속성이 사용자가 상호 작용할 필드로 설정됩니다. 화면은 다음 예제와 비슷합니다.

![아이스크림 데이터 원본에 대한 표시 양식](./media/working-with-forms/ice-cream-new.png)

마지막으로 특정 레코드의 세부 정보를 볼 수 있도록 **[표시 폼](controls/control-form-detail.md)** 컨트롤을 **[갤러리](controls/control-gallery.md)** 컨트롤에 연결해야 합니다.  **[Item](controls/control-form-detail.md)** 속성 설정이 완료되는 즉시 갤러리의 첫 번째 레코드가 폼에 표시됩니다.

* **[표시 양식](controls/control-form-detail.md)** 컨트롤의 **[Item](controls/control-form-detail.md)** 속성을 **Gallery1.Selected**로 설정합니다.
   
    선택한 항목의 세부 정보가 양식에 표시됩니다.
   
    ![갤러리 컨트롤에 연결된 아이스크림 데이터 원본에 대한 표시 양식](./media/working-with-forms/view-form-select-coconut.png)

잘 했습니다!  이제 사용자가 갤러리 화면에서 세부 정보 화면을 열고, 세부 정보 화면에서 갤러리 화면을 여는 방법을 탐색해 볼 시간입니다.

* **[단추](controls/control-button.md)** 컨트롤을 화면에 추가하고, **[뒤로](functions/function-navigate.md)** 를 표시하도록 **[Text](controls/properties-core.md)** 속성을 설정하고, **[OnSelect](controls/properties-core.md)** 속성을 **Back()** 으로 설정합니다.
   
    이 수식은 사용자가 세부 정보 보기를 마치면 갤러리로 돌아갑니다.

    ![뒤로 단추가 있는 아이스크림 데이터 원본에 대한 표시 양식](./media/working-with-forms/viewform-icecream-back.png)

이제 **[갤러리](controls/control-gallery.md)** 컨트롤로 돌아가서 세부 정보 화면에 일부 탐색을 추가해 보겠습니다.

1. **[갤러리](controls/control-gallery.md)** 컨트롤을 호스팅하는 첫 번째 화면으로 전환하고 갤러리의 첫 번째 항목에 있는 화살표를 선택합니다.

2. 도형의 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Navigate( Screen2, None )**
   
    ![뒤로 단추가 있는 아이스크림 데이터 원본에 대한 표시 양식](./media/working-with-forms/gallery-icecream-nav-new.png)

3. F5 키를 누른 다음 갤러리에 있는 화살표를 선택하여 항목에 대한 세부 정보를 표시합니다.

4. **[뒤로](functions/function-navigate.md)** 단추를 선택하여 제품 갤러리로 돌아간 다음 Esc 키를 누릅니다.

## <a name="editing-details"></a>세부 정보 편집
마지막으로 최종적인 핵심 작업은 사용자가 **[편집 폼](controls/control-form-detail.md)** 컨트롤에서 수행한 레코드의 내용을 변경하는 것입니다.

**[편집 폼](controls/control-form-detail.md)** 컨트롤은 다음 두 가지 속성을 사용하여 레코드를 표시하고 편집합니다.

* **[DataSource](controls/control-form-detail.md)** 속성 -  레코드를 보유하고 있는 데이터 원본의 이름입니다.  **[표시 폼](controls/control-form-detail.md)** 컨트롤과 마찬가지로 이 속성은 오른쪽 패널을 필드로 채우고 각 필드의 표시 이름 및 데이터 형식(문자열, 숫자, 날짜 등)을 결정합니다. 또한 이 속성은 기본 데이터 원본에 제출하기 전에 각 필드의 값이 유효한지 여부를 결정합니다.
* **[Item](controls/control-form-detail.md)** 속성 -  편집할 레코드이며, 종종 **[갤러리](controls/control-gallery.md)** 컨트롤의 **Selected** 속성에 연결됩니다. 이렇게 하면 **[갤러리](controls/control-gallery.md)** 컨트롤에서 레코드를 선택하고, 세부 정보 화면에 표시하고, **편집 및 만들기** 화면에서 편집할 수 있습니다.

**[편집 폼](controls/control-form-detail.md)** 컨트롤을 추가하려면 다음을 수행합니다.

1. 화면을 추가하고, **[편집 양식](controls/control-form-detail.md)** 컨트롤을 추가한 다음, 양식의 **[DataSource](controls/control-form-detail.md)** 속성을 **'아이스크림'** 으로 설정합니다.
2. **[Item](controls/control-form-detail.md)** 속성을 **Gallery1.Selected**로 설정합니다.

이제 화면에 표시할 필드를 선택할 수 있습니다. 또한 각 필드에 표시할 카드 유형도 선택할 수 있습니다. 오른쪽 창에서 변경하면 각 **[카드](controls/control-card.md)** 컨트롤의 **[DataField](controls/control-card.md)** 속성이 사용자가 상호 작용할 필드로 설정됩니다.  화면은 다음 예제와 비슷합니다.

![아이스크림 데이터 원본에 대한 표시 양식](./media/working-with-forms/icecream-edit.png)

이러한 두 속성은 **[표시 폼](controls/control-form-detail.md)** 컨트롤의 속성과 동일합니다.  그리고 이러한 속성만으로도 레코드의 세부 정보를 표시할 수 있습니다.  

**[편집 폼](controls/control-form-detail.md)** 컨트롤은 **[SubmitForm](functions/function-form.md)** 함수를 제공하여 데이터 원본에 대한 변경 내용을 쓰기 저장하면서 진행됩니다. 단추 또는 이미지 컨트롤과 함께 사용하여 사용자의 변경 내용을 저장합니다.

* **[단추](controls/control-button.md)** 컨트롤을 추가하고, **저장**을 표시하도록 **[Text](controls/properties-core.md)** 속성을 설정하고, **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
  **SubmitForm( Form1 )**

![아이스크림 데이터 원본에 대한 편집 양식](./media/working-with-forms/edit-icecream-save.png)

이 화면에서 탐색을 추가하려면 다음을 수행합니다.

1. 다른 **[단추](controls/control-button.md)** 컨트롤을 추가하고, **취소**를 표시하도록 **[Text](controls/properties-core.md)** 속성을 설정하고, **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다. <br>**ResetForm( Form1 ); Back()**
   
    이 수식은 저장되지 않은 편집 내용을 삭제하고 이전 화면을 엽니다.
   
    ![아이스크림 데이터 원본에 대한 표시 양식](./media/working-with-forms/edit-icecream-cancel.png)
2. 양식의 **[OnSuccess](controls/control-form-detail.md)** 속성을 **Back()** 으로 설정합니다.
   
    업데이트가 성공적으로 저장되면 이전 화면(이 경우 세부 정보 화면)이 자동으로 열립니다.
   
    !["OnSuccess" 규칙이 추가된 편집 양식](./media/working-with-forms/edit-icecream-onsuccess.png)
3. **표시** 화면에서 단추를 추가하고, **편집**을 표시하도록 **[Text](controls/properties-core.md)** 속성을 설정하고, **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br> **Navigate( Screen3, None )**
   
    !["편집" 단추가 추가된 표시 양식](./media/working-with-forms/viewform-icecream-edit.png)

데이터를 보고 입력하는 3개의 화면이 있는 기본 앱을 빌드했습니다.  이 앱을 사용해 보려면 갤러리 화면을 표시한 다음, F5 키를 누르거나 화면의 왼쪽 위 모서리 근처에 있는 앞으로 화살표 "미리 보기" 단추를 선택합니다. 분홍색 점은 사용자가 각 단계에서 화면을 클릭하거나 탭하는 위치를 나타냅니다.

![아이스크림 앱 사용해 보기](./media/working-with-forms/try-icecream.png)

## <a name="create-a-record"></a>레코드 만들기
사용자는 동일한 **편집** 폼과 상호 작용하여 레코드를 업데이트하고 만듭니다. 사용자가 레코드를 만들려고 할 때 **[NewForm](functions/function-form.md)** 함수는 폼을 **New** 모드로 전환합니다.

폼이 **New** 모드에 있으면 각 필드의 값은 데이터 원본의 기본값으로 설정됩니다. 폼의 **[Item](controls/control-form-detail.md)** 속성에 제공된 레코드는 무시됩니다.  

사용자가 새 레코드를 저장할 준비가 되면 **[SubmitForm](functions/function-form.md)** 이 실행됩니다. 양식이 성공적으로 제출되면 양식은 **EditMode**로 다시 전환됩니다.  

첫 번째 화면에서 **새로 만들기** 단추가 추가됩니다.

1. 갤러리가 있는 화면에서 **[단추](controls/control-button.md)** 컨트롤을 추가합니다.
2. 단추의 **[Text](controls/properties-core.md)** 속성을 **New**로 설정하고, **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
   **NewForm( Form1 ); Navigate( Screen3, None )**
   
    이 수식은 **Screen3**의 **[편집 양식](controls/control-form-detail.md)** 컨트롤을 **New** 모드로 전환하고 사용자가 채울 수 있도록 해당 화면을 엽니다.

!["편집" 단추가 추가된 표시 양식](./media/working-with-forms/gallery-icecream-new.png)

편집 및 만들기 화면이 열리면 사용자가 항목을 추가할 준비가 된 폼이 비어 있습니다. 사용자가 **저장** 단추를 선택하면 **[SubmitForm](functions/function-form.md)** 함수는 레코드를 업데이트하는 대신 만들도록 합니다. 사용자가 **취소** 단추를 선택하면, **[ResetForm](functions/function-form.md)** 함수는 폼을 **Edit** 모드로 다시 전환하고, **[Back](functions/function-navigate.md)** 함수는 갤러리를 탐색하기 위한 화면을 엽니다.

## <a name="delete-a-record"></a>레코드 삭제
1. **표시** 화면에서 단추를 추가하고, **삭제**를 표시하도록 **[Text](controls/properties-core.md)** 속성을 설정합니다.
2. 단추의 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Remove( 'Ice Cream', Gallery1.Selected ); Back()**
   
    !["편집" 단추가 추가된 표시 양식](./media/working-with-forms/viewform-icecream-remove.png)

## <a name="handling-errors"></a>오류 처리
이 앱에서 필드의 값이 유효하지 않거나, 필수 필드가 비어 있거나, 네트워크 연결이 끊어졌거나, 다른 문제가 발생하면 오류가 발생합니다.  

어떤 이유로든 **[SubmitForm](functions/function-form.md)** 이 실패하면 **[편집 양식](controls/control-form-detail.md)** 컨트롤의 **Error** 속성에 사용자에게 표시할 오류 메시지가 포함됩니다. 이 정보를 사용하면 사용자는 문제를 해결하고 변경 내용을 다시 제출하거나 업데이트를 취소할 수 있습니다.

1. 편집 및 만들기 화면에서 **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고 **저장** 단추 바로 아래로 이동합니다. 사용자가 이 컨트롤을 선택하여 변경 내용을 저장한 후에는 모든 오류를 쉽게 확인할 수 있습니다.

2. **Form1.Error**를 표시하도록 **[레이블](controls/control-text-box.md)** 컨트롤의 **[Text](controls/properties-core.md)** 속성을 설정합니다.

    !["편집" 단추가 추가된 표시 양식](./media/working-with-forms/edit-icecream-error.png)

PowerApps가 데이터에서 생성하는 앱에서 이 컨트롤의 **[AutoHeight](controls/control-text-box.md)** 속성이 *true*로 설정되므로 오류가 발생하지 않으면 공백이 사용되지 않습니다. 또한 **[편집 양식](controls/control-form-detail.md)** 컨트롤의 **[Height](controls/properties-size-location.md)** 및 **[Y](controls/properties-size-location.md)** 속성은 오류가 발생할 때 이 컨트롤의 증가를 고려하여 동적으로 조정됩니다. 자세한 내용을 알아보려면 기존 데이터에서 앱을 생성하고 이러한 속성을 검사합니다. 오류가 발생하지 않은 경우 오류의 텍스트 상자 컨트롤은 매우 짧습니다. **고급** 보기(**보기** 탭에서 사용 가능)를 열어 이 컨트롤을 선택해야 할 수도 있습니다.

![오류 텍스트 컨트롤이 선택된 데이터 편집 양식의 앱](./media/working-with-forms/edit-assets-error1.png)

![양식 컨트롤이 선택된 데이터 편집 양식의 앱](./media/working-with-forms/edit-assets-error2.png)

## <a name="refresh-data"></a>데이터 새로 고침
사용자가 앱을 열 때마다 데이터 원본을 새로 고치지만, 사용자가 앱을 닫지 않고 갤러리의 레코드를 새로 고쳐야 할 수도 있습니다. 사용자가 수동으로 데이터를 새로 고칠 수 있도록 **새로 고침** 단추를 추가합니다.

1. **[갤러리](controls/control-gallery.md)** 컨트롤이 있는 화면에서 **[단추](controls/control-button.md)** 컨트롤을 추가하고, **새로 고침**을 표시하도록 **[Text](controls/properties-core.md)** 속성을 설정합니다.

2. 이 컨트롤의 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br> **Refresh( 'Ice Cream' )**

    ![데이터 원본 새로 고침](./media/working-with-forms/browse-icecream-refresh.png)

## <a name="search-and-sort-the-gallery"></a>갤러리 검색 및 정렬
PowerApps가 데이터에서 생성한 앱에서 찾아보기 화면의 위쪽에 있는 두 가지 컨트롤에 대해 논의하지 않았습니다. 사용자는 이러한 컨트롤을 사용하여 하나 이상의 레코드를 검색하거나 레코드 목록을 오름차순 또는 내림차순으로 정렬하거나 둘 다 정렬할 수 있습니다.

![찾아보기 화면에서 컨트롤 정렬 및 검색](./media/working-with-forms/afd-browse-search-sort.png)

사용자가 정렬 단추를 선택하면 갤러리의 정렬 순서가 반대로 바뀝니다. 이 동작을 만들려면 '컨텍스트 변수'를 사용하여 갤러리가 정렬되는 방향을 추적합니다. 사용자가 단추를 선택하면 변수가 업데이트되고 방향이 반대로 바뀝니다. 정렬 단추의 **[OnSelect](controls/properties-core.md)** 속성이 **UpdateContext( {SortDescending1: !SortDescending1} )** 수식으로 설정됩니다.

**SortDescending1** 컨텍스트 변수가 아직 없으면 **[UpdateContext](functions/function-updatecontext.md)** 함수에서 이 변수를 만듭니다. 이 함수는 변수의 값을 읽고 **!** 연산자를 사용하여 논리적 반대로 설정합니다. 액세스합니다. 값이 'true'이면 'false'가 됩니다. 값이 'false'이면 'true'가 됩니다.

**[갤러리](controls/control-gallery.md)** 컨트롤의 **[Items](controls/properties-core.md)** 속성에 대한 수식은 **TextSearchBox1** 컨트롤의 텍스트와 함께 이 컨텍스트 변수를 사용합니다.

```powerapps-dot
Sort( 
    If( IsBlank(TextSearchBox1.Text),
        Assets,
        Filter( Assets, TextSearchBox1.Text in Text(ApproverEmail) ) 
    ),
    ApproverEmail,
    If(SortDescending1, Descending, Ascending) 
)
```

이 수식을 분석해 보겠습니다.

* 외부에는 **[Sort](functions/function-sort.md)** 함수가 있습니다. 이 함수는 테이블, 정렬할 필드 및 정렬할 방향의 세 가지 인수를 사용합니다.  
  
  * 정렬 방향은 사용자가 **ImageSortUpDown1** 컨트롤을 선택할 때 전환되는 컨텍스트 변수에서 가져옵니다. 'true'/'false' 값은 상수 **내림차순**과 **오름차순**으로 변환됩니다.
  * 정렬할 필드는 **ApproverEmail**로 고정됩니다. 갤러리에서 표시되는 필드를 변경하면 이 인수도 변경해야 합니다.
* 내부에는 **[Filter](functions/function-filter-lookup.md)** 함수가 있습니다. 이 함수는 테이블을 인수로 사용하고, 식을 사용하여 각 레코드에 대해 평가합니다.
  
  * 테이블은 원시 **Assets** 데이터 원본이며, 필터링하거나 정렬하기 전의 시작점입니다.
  * 이 식은 **ApproverEmail** 필드 내에서 **TextSearchBox1**에 있는 문자열의 인스턴스를 검색합니다.  다시 말하지만 갤러리에서 표시되는 필드를 변경하면 이 인수도 업데이트해야 합니다.
  * **TextSearchBox1**이 비어 있으면 사용자가 모든 레코드를 표시하려고 하며 **[Filter](functions/function-filter-lookup.md)** 함수가 무시됩니다.

이는 한 가지 예입니다. 앱의 요구 사항에 따라 **[Filter](functions/function-filter-lookup.md)** , **[Sort](functions/function-sort.md)** 및 다른 함수와 연산자를 함께 구성하여 **[Items](controls/properties-core.md)** 속성에 대한 고유의 수식을 만들 수 있습니다.    

## <a name="screen-design"></a>화면 디자인
지금까지 화면에 컨트롤을 분산하는 다른 방법에 대해서는 설명하지 않았습니다. 이는 다양한 옵션이 있기 때문이며, 최상의 선택은 앱의 특정 요구 사항에 따라 다릅니다.

전화 화면에서 부동산은 이렇게 제한되므로 다른 화면에서 찾아보고, 표시하고, 편집하고, 만들려고 합니다. 이 항목에서는 **[Navigate](functions/function-navigate.md)** 및 **[Back](functions/function-navigate.md)** 함수에서 각 화면을 엽니다.  

태블릿에서 두 화면 또는 한 화면에서도 찾아보기, 표시 및 편집/만들기를 수행할 수 있습니다. 후자의 경우 **[Navigate](functions/function-navigate.md)** 또는 **[Back](functions/function-navigate.md)** 함수가 필요하지 않습니다.

사용자가 동일한 화면에서 작업하는 경우 **[갤러리](controls/control-gallery.md)** 에서 선택 항목을 변경할 수 없으며, **[편집 양식](controls/control-form-detail.md)** 컨트롤에서 편집 내용을 잃을 수 있으므로 주의해야 합니다.  다른 레코드 변경 내용이 아직 저장되지 않은 경우 사용자가 다른 레코드를 선택하지 못하게 하려면 갤러리의 **[Disabled](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
**EditForm.Unsaved**

