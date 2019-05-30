---
title: Excel 데이터를 기반으로 처음부터 캔버스 앱 만들기 | Microsoft Docs
description: 이 자습서에서는 사용자가 Excel 파일에서 레코드를 생성, 편집 및 삭제할 수 있도록 두 화면 캔버스 앱을 만듭니다.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/26/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ee9ea62280b06b75bf71885c532659f0381e6d9a
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61555504"
---
# <a name="create-a-canvas-app-from-scratch-based-on-excel-data"></a>Excel 데이터를 기반으로 처음부터 캔버스 앱 만들기

표 형식의 Excel 데이터를 기반으로 처음부터 고유한 캔버스 앱을 만든 다음, 원하는 경우 다른 원본의 데이터를 추가합니다. 이 자습서를 따라 두 화면을 포함하는 앱을 만듭니다. 한 화면에서 사용자는 일련의 레코드를 찾아볼 수 있습니다. 다른 화면에서 사용자는 한 레코드를 만들거나, 한 레코드에서 하나 이상의 필드를 업데이트하거나, 전체 레코드를 삭제할 수 있습니다. 이 접근 방식은 [앱을 자동으로 생성](get-started-create-from-data.md)하는 것보다 시간이 더 걸리지만 숙련된 앱 제작자는 이 방법으로 요구 사항에 맞는 최고의 앱을 빌드할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

이 자습서의 단계를 정확하게 수행하려면 먼저 이 샘플 데이터를 사용하여 Excel 파일을 만듭니다.

1. 이 데이터를 복사한 다음 Excel 파일에 붙여넣습니다.

    | StartDay | StartTime | 자원 봉사자 | Backup |
    | --- | --- | --- | --- |
    | 토요일 |오전 10시 정오 |Vasquez |Kumashiro |
    | 토요일 |정오~오후 2시 |Ice |Singhal |
    | 토요일 |오후 2시~오후 4시 |Myk |Mueller |
    | 일요일 |오전 10시 정오 |Li |Adams |
    | 일요일 | 정오~오후 2시 |Singh |Morgan |
    | 일요일 | 오후 2시~오후 4시 |Batye |Nguyen |

2. PowerApps에서 정보를 구문 분석할 수 있도록 해당 데이터를 **Schedule**이라는 테이블로 형식을 지정합니다.

    자세한 내용은 [Excel에서 테이블 형식 지정](how-to-excel-tips.md)을 참조합니다.

3. 파일을 **eventsignup.xls** 이름으로 저장한 다음, OneDrive와 같은 [클라우드 저장소 계정](connections/cloud-storage-blob-connections.md)에 업로드합니다.

> [!IMPORTANT]
> 사용자의 Excel 파일을 사용할 수 있으며 일반 개념에 대해서만 이 자습서를 검토할 수 있습니다. 그러나 Excel 파일의 데이터는 테이블로 형식이 지정돼야 합니다. 자세한 내용은 [Excel에서 테이블 형식 지정](how-to-excel-tips.md)을 참조합니다.

## <a name="open-a-blank-app"></a>비어 있는 앱 열기

1. [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

1. **고유한 앱 만들기**에서 **빈 페이지의 캔버스 앱**을 선택합니다.

    > [!div class="mx-imgBorder"]
    >![빈 캔버스 앱 만들기](./media/get-started-create-from-blank/blank-app.png)

1. 앱의 이름을 지정하고, **휴대폰**을 선택한 다음, **만들기**를 선택합니다.

    전화 또는 다른 디바이스(예: 태블릿)에 사용할 앱을 처음부터 디자인할 수 있습니다. 이 항목에서는 전화용 앱 디자인에 대해 중점적으로 설명합니다.

    > [!div class="mx-imgBorder"]
    >![앱의 이름 및 형식 지정](./media/get-started-create-from-blank/excel-demo.png)

    PowerApps Studio에서는 빈 전화용 앱을 만듭니다.

1. **PowerApps Studio 시작** 대화 상자가 열리면 **건너뛰기**를 선택합니다.

## <a name="connect-to-data"></a>데이터에 연결

1. 화면 가운데에서 **데이터에 연결**을 선택합니다.

1. **데이터** 창에서 연결이 표시되면 클라우드 저장소 계정에 대한 연결을 선택합니다. 연결이 표시되지 않으면 다음 단계에 따라 연결을 추가합니다.

    1. **새 연결**을 선택하고 클라우드 저장소 계정의 타일을 선택한 다음, **만들기**를 선택합니다.
    2. 메시지가 표시되면 해당 계정에 대한 자격 증명을 입력합니다.

1. **Excel 파일 선택**에서 **eventsignup**의 첫 문자를 입력하거나 붙여넣어 목록을 필터링한 다음, 업로드한 파일을 선택합니다.

1. **테이블 선택**에서 **Schedule** 확인란을 선택한 다음, **연결**을 선택합니다.

1. **데이터** 창의 오른쪽 위 모서리에서 닫기 아이콘(X)을 선택하여 창을 닫습니다.

## <a name="create-the-view-screen"></a>보기 화면 만들기

1. **홈** 탭에서 **새 화면** 옆에 있는 아래쪽 화살표를 선택하여 화면 유형 목록을 연 다음, **목록**을 선택합니다.

    화면에는 검색 상자와 **[갤러리](controls/control-gallery.md)** 컨트롤 등의 여러 기본 컨트롤이 추가됩니다. 갤러리는 검색 상자에서 전체 화면을 처리합니다.

1. 새 화면 위쪽에서 **[레이블](controls/control-text-box.md)** 컨트롤을 선택한 다음, **[제목]** 을 **레코드 보기**로 바꿉니다.

     ![제목 표시줄 변경](./media/get-started-create-from-blank/change-title-bar.png)

1. 왼쪽 탐색 표시줄에서 **BrowseGallery1**을 선택합니다.

    핸들이 있는 선택 상자가 갤러리를 둘러쌉니다.

    ![목록 추가 화면](./media/get-started-create-from-blank/select-gallery.png)

1. 오른쪽 창의 **속성** 탭에서 **레이아웃** 메뉴의 아래쪽 화살표를 선택합니다.

    ![레이아웃 메뉴를 엽니다.](./media/get-started-create-from-blank/select-layout.png)

1. **제목, 부제목 및 본문**을, 선택합니다.

1. 수식 입력줄에서 **CustomGallerySample**을 **일정**으로 바꾸고, **SampleText**의 두 인스턴스를 **자원 봉사자**로 바꿉니다.

1. 수식 입력줄의 오른쪽 가장자리에서 아래쪽 화살표를 선택한 다음, **텍스트 서식 지정**을 선택합니다.

    수식은 다음 예제와 일치합니다.

    ```powerapps-dot
    SortByColumns(
        Search(
            Schedule,
            TextSearchBox1.Text,
            "Volunteer"
        ),
        "Volunteer",
        If(
            SortDescending1,
            SortOrder.Descending,
            SortOrder.Ascending
        )
    )
    ```

1. 오른쪽 창의 **속성** 탭에서 **필드** 레이블 옆에 있는 **편집**을 선택합니다.

1. **Title2** 상자에서 **자원 봉사자**를 선택합니다.

1. **데이터** 창의 오른쪽 위 모서리에서 닫기 아이콘(X)을 선택하여 창을 닫습니다.

사용자는 해당 수식의 **SortByColumns** 및 **Search** 함수를 기반으로 갤러리를 자원봉사자의 이름별로 정렬 및 필터링할 수 있습니다.

- 사용자가 검색 상자에 하나 이상의 문자를 입력하면 갤러리에는 **Volunteer** 필드에 사용자가 입력한 텍스트를 포함하는 레코드만 표시됩니다.
- 사용자가 제목 표시줄에서 새로 고침 단추와 더하기 단추 사이에 있는 정렬 단추를 선택하면 갤러리에는 **자원 봉사자** 필드를 기준으로 (사용자가 단추를 선택한 횟수에 따라) 오름차순 또는 내림차순으로 레코드가 표시됩니다.

이러한 함수 및 다른 함수에 대한 자세한 내용은 [수식 참조](formula-reference.md)를 참조하세요.

## <a name="create-the-change-screen"></a>변경 화면 만들기

1. **홈** 탭에서 **새 화면** 옆에 있는 아래쪽 화살표를 선택한 다음, **양식**을 선택합니다.

1. 왼쪽 탐색 모음에서 **EditForm1**을 선택합니다.

1. 오른쪽 창의 **속성** 탭에서 **데이터 원본** 옆에 있는 아래쪽 화살표를 선택한 다음, 나타나는 목록에서 **일정**을 선택합니다.

1. 방금 지정한 데이터 원본에서 **필드 편집**을 선택합니다.

1. **필드** 창에서 **필드 추가**를 선택하고, 각 필드에 대한 확인란을 선택한 다음, **추가**를 선택합니다.

1. 각 필드의 이름 옆에 있는 화살표를 선택하여 축소한 다음, **자원 봉사자** 필드를 위로 끌어와서 필드 목록의 위쪽에 표시되도록 합니다.

     ![필드 순서 바꾸기](./media/get-started-create-from-blank/reorder-fields.png)

1. **필드** 창의 오른쪽 위 모서리에서 닫기 아이콘(X)을 선택하여 창을 닫습니다.

1. 수식 입력줄에 이 식을 입력하거나 붙여넣어 양식의 **Item** 속성을 해당 식으로 설정합니다.

    `BrowseGallery1.Selected`

1. 화면 위쪽에서 **[레이블](controls/control-text-box.md)** 컨트롤을 선택한 다음, **[제목]** 을 **레코드 변경**으로 바꿉니다.

    ![제목 표시줄 변경](./media/get-started-create-from-blank/change-title-bar2.png)

## <a name="delete-and-rename-screens"></a>화면 삭제 및 이름 바꾸기

1. 왼쪽 탐색 모음에서 **Screen1**을 선택한 다음, **삭제**를 선택합니다.

    ![삭제 화면](./media/get-started-create-from-blank/delete-screen.png)

1. **Screen2**에 대한 줄임표(...)를 선택하고 **이름 바꾸기**를 선택한 다음, **ViewScreen**을 입력하거나 붙여넣습니다.

1. **Screen3**에 대한 줄임표(...)를 선택하고 **이름 바꾸기**를 선택한 다음, **ChangeScreen**을 입력하거나 붙여넣습니다.

## <a name="configure-icons-on-the-view-screen"></a>보기 화면에서 아이콘 구성

1. **ViewScreen** 위쪽 근처에 있는 원형 화살표 아이콘을 선택합니다.

    ![레코드 추가](./media/get-started-create-from-blank/refresh-icon.png)

1. 해당 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `Refresh(Schedule)`

    사용자가 이 아이콘을 선택하면 **Schedule**의 데이터가 Excel 파일에서 새로 고쳐집니다.

    이 함수와 다른 함수에 대한 자세한 내용은 [수식 참조](formula-reference.md)를 참조하세요.

1. **ViewScreen**의 오른쪽 위 모서리에서 더하기 아이콘을 선택합니다.

    ![레코드 추가](./media/get-started-create-from-blank/add-record.png)

1. 해당 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `NewForm(EditForm1);Navigate(ChangeScreen,ScreenTransition.None)`

    사용자가 이 아이콘을 선택하면 **ChangeScreen**은 비어 있는 각 필드를 표시하며, 사용자는 레코드를 보다 쉽게 만들 수 있습니다.

1. 갤러리의 첫 번째 레코드에 대해 오른쪽 방향 화살표를 선택합니다.

    ![화살표 선택](./media/get-started-create-from-blank/select-arrow.png)

1. 화살표의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `EditForm(EditForm1); Navigate(ChangeScreen, ScreenTransition.None)`

    사용자가 이 아이콘을 선택하면 **ChangeScreen**은 선택된 레코드의 데이터를 보여주는 각 필드를 표시하며, 사용자는 레코드를 보다 쉽게 편집 또는 삭제할 수 있습니다.

## <a name="configure-icons-on-the-change-screen"></a>변경 화면에서 아이콘 구성

1. **ChangeScreen**의 오른쪽 위 모서리에서 "X" 아이콘을 선택합니다.

    ![취소 아이콘](./media/get-started-create-from-blank/cancel-icon.png)

1. 해당 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `ResetForm(EditForm1);Navigate(ViewScreen, ScreenTransition.None)`

    사용자가 이 아이콘을 선택하면 이 화면에서 사용자가 변경한 모든 내용이 무시되고 보기 화면이 열립니다.

1. 오른쪽 위 모서리에서 확인 표시 아이콘을 선택합니다.

    ![확인 표시 아이콘](./media/get-started-create-from-blank/checkmark-icon.png)

1. 확인 표시의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `SubmitForm(EditForm1); Navigate(ViewScreen, ScreenTransition.None)`

    사용자가 이 아이콘을 선택하면 이 화면에서 사용자가 변경한 모든 내용이 저장되고 보기 화면이 열립니다.

1. **삽입** 탭에서 **아이콘**을 선택한 다음, **휴지통** 아이콘을 선택합니다.

1. 새 아이콘의 **Color** 속성을 **White**로 설정하고 새 아이콘을 확인 표시 아이콘 옆에 표시되도록 이동합니다.

    ![휴지통 아이콘](./media/get-started-create-from-blank/trash-icon.png)

1. 휴지통 아이콘의 **Visible** 속성을 다음 수식으로 설정합니다.

    `EditForm1.Mode = FormMode.Edit`

    양식이 **새로 만들기** 모드가 아닌 **편집** 모드인 경우에만 이 아이콘이 표시됩니다.

1. 휴지통 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `Remove(Schedule, BrowseGallery1.Selected); Navigate(ViewScreen, ScreenTransition.None)`

    사용자가 이 아이콘을 선택하면 선택된 레코드가 데이터 원본에서 삭제되고 보기 화면이 열립니다.

## <a name="test-the-app"></a>앱 테스트

1. **ViewScreen**을 선택한 다음, F5 키를 누르거나 오른쪽 위 모서리 근처의 **미리 보기** 아이콘을 선택하여 미리 보기를 엽니다.

    ![미리 보기 모드 열기](./media/get-started-create-from-blank/open-preview.png)

1. 검색 상자에 하나 이상의 문자를 입력하거나 붙여넣어서 자원 봉사자의 이름을 기반으로 목록을 필터링합니다.

1. 정렬 아이콘을 한 번 이상 선택하여 자원 봉사자의 이름에 따라 오름차순 또는 내림차순으로 데이터를 표시합니다.

1. 레코드를 추가합니다.

1. 추가한 레코드를 업데이트한 다음, 변경 내용을 저장합니다.

1. 추가한 레코드를 업데이트한 다음, 변경 내용을 취소합니다.

1. 추가한 레코드를 삭제합니다.

1. Esc 키를 누르거나 오른쪽 위 모서리의 닫기 아이콘을 선택하여 미리 보기 모드를 닫습니다.

## <a name="next-steps"></a>다음 단계

- 다른 디바이스에서 실행할 수 있도록 앱을 클라우드에 저장하려면 Ctrl-S를 누릅니다.
- 다른 사용자가 앱을 실행할 수 있도록 [앱을 공유](share-app.md)하세요.
- 표준 양식을 만들지 않고 데이터를 관리하는 데 사용할 수 있는 **Patch**와 같은 [함수](working-with-formulas.md)를 자세히 알아보세요.
- 예를 들어 [이 앱을 솔루션에 연결](add-app-solution.md)하여 다른 환경에 배포하거나 AppSource에 게시할 수 있습니다.
