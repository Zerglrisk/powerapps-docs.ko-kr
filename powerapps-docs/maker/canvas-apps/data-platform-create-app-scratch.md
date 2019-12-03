---
title: Common Data Service를 사용하여 캔버스 앱을 처음부터 만들기 | Microsoft Docs
description: Power Apps에서 캔버스 앱을 만들어 Common Data Service에서 레코드를 추가, 업데이트 및 삭제 합니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/21/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48cd98481cff354d4e54cb54dc38865f6dfa6a14
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679687"
---
# <a name="create-a-canvas-app-from-scratch-using-common-data-service"></a>Common Data Service를 사용하여 캔버스 앱을 처음부터 만들기

표준 엔터티(기본 제공), 사용자 지정 엔터티(사용자 조직에서 만듦) 또는 모두를 사용하여 Common Data Service에 저장된 데이터를 관리하는 캔버스 앱을 빌드합니다.

Common Data Service에서 앱을 빌드하는 경우에는 SharePoint, Dynamics 365 또는 Salesforce와 같은 데이터 원본에서와 마찬가지로 Power Apps에서 연결을 만들 필요가 없습니다. 앱에서 표시, 관리하려는 엔터티를 지정하기만 하면 됩니다.

## <a name="prerequisites"></a>필수 조건

- 앱을 처음부터 만들기 전에 앱을 [생성](data-platform-create-app.md) 한 다음 해당 앱의 [갤러리](customize-layout-sharepoint.md), [양식](customize-forms-sharepoint.md)및 [카드](customize-card.md)를 사용자 지정 하 여 Power Apps 기본 사항에 익숙해져야 합니다.
- 샘플 데이터를 사용하여 데이터베이스를 만든 [환경으로 전환합니다](working-with-environments.md). 적절한 라이선스를 있는 경우 이 요구 사항이 충족되는 [환경을 만들 수 있습니다](../../administrator/create-environment.md).
- 앱을 만들려면 [Environment Maker](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles) 보안 역할에 할당되어야합니다.

## <a name="open-a-blank-app"></a>비어 있는 앱 열기

1. [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

1. **고유한 앱 만들기**에서 **빈 페이지의 캔버스 앱**을 선택합니다.

    ![비어 있는 앱 타일](./media/data-platform-create-app-scratch/blank-app.png)

1. 앱의 이름을 지정하고, **휴대폰**을 선택한 다음, **만들기**를 선택합니다.

    태블릿용 앱을 처음부터 만들 수 있지만 이 항목에서는 전화용 앱을 만드는 방법을 설명합니다.

## <a name="specify-an-entity"></a>엔터티 지정

1. 화면 가운데에서 **데이터에 연결**을 선택합니다.

1. **데이터** 창에서 **Common Data Service**를 선택하고, **계정** 확인란을 선택한 다음, **연결**을 선택합니다.

1. 오른쪽 위 모서리에 있는 닫기 아이콘을 선택하여 **데이터** 창을 닫습니다.

## <a name="add-a-list-screen"></a>목록 추가 화면

1. **홈** 탭에서 **새 화면**에 대한 아래쪽 화살표를 선택한 다음, **목록**을 선택합니다.

    ![목록 추가 화면](./media/data-platform-create-app-scratch/list-screen.png)

1. 왼쪽 탐색 모음에서 **BrowseGallery1**을 선택한 다음, **Items** 속성의 값을 다음 수식으로 설정합니다.

    `SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))`

    이 수식에서 지정한 작업은 다음과 같습니다.

   - 갤러리에서 **거래처** 엔터티의 데이터를 표시합니다.
   - 사용자가 정렬 단추를 선택하여 정렬 순서를 토글할 때까지 데이터를 오름차순으로 정렬합니다.
   - 사용자가 검색 창(**TextSearchBox1**)에 하나 이상의 문자를 입력하거나 붙여넣으면 목록에서 사용자가 지정한 문자가 **이름** 필드에 포함된 계정만 표시합니다.

     [이러한 함수와 다른 많은 함수](formula-reference.md)를 사용하여 앱의 표시 방식과 작동 방식을 지정할 수 있습니다.

     ![갤러리의 Items 속성 설정](./media/data-platform-create-app-scratch/gallery-items.png)

1. 각 계정의 이름만 표시하도록 갤러리의 레이아웃을 설정하고, [갤러리 사용자 지정](customize-layout-sharepoint.md)에서 설명한 대로 **찾아보기** 단어를 표시하도록 제목 표시줄을 구성합니다.

    ![찾아보기 화면](./media/data-platform-create-app-scratch/final-browse.png)

1. 왼쪽 탐색 모음에서 **Screen1** 위를 마우스로 가리키고, 줄임표(...)를 선택한 다음, **삭제**를 선택합니다.

1. 왼쪽 탐색 모음에서 **Screen2** 위를 마우스로 가리키고, 줄임표(...)를 선택한 다음, **이름 바꾸기**를 선택합니다.

1. **BrowseScreen**을 입력하거나 붙여넣은 다음, 해당 화면의 갤러리 이름을 **BrowseGallery**로 바꿉니다.

    ![찾아보기 화면 및 갤러리 이름 바꾸기](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>양식 화면 추가

1. 이전 절차의 첫 번째 단계를 반복합니다. 단, **목록** 화면 대신 **양식** 화면을 추가합니다.

1. 오른쪽 창의 **고급** 탭에 표시된 대로 양식의 **DataSource** 속성을 **계정**, 해당 **항목** 속성을 **BrowseGallery.Selected**로 설정합니다.

    ![양식의 Datasource 및 Item 속성 설정](./media/data-platform-create-app-scratch/form-datasource.png)

1. 오른쪽 창의 **속성** 탭에서 **필드 편집** 을 선택 하 여 **필드** 창을 엽니다.

1. **필드 추가**를 선택하고, 다음 필드에 대한 확인란을 선택합니다.

    - **계정 이름**
    - **주소 1: 번 지 1**
    - **주소 1: 도시**
    - **주소 1: 우편 번호**
    - **직원 수**
    - **연간 수익**

    > [!NOTE]
    > 이 시나리오 외에서는 **새 필드**를 선택 하 고 필요한 정보를 제공한 다음 **완료**를 선택 하 여 사용자 지정 필드를 만들 수 있습니다. 추가 정보: [필드 만들기](../common-data-service/create-edit-field-portal.md#create-a-field)<br><br>![](media/data-platform-create-app-scratch/choose-or-add-fields.png "Select and add a field")

1. **추가**를 선택합니다.

1. **만들기/편집**을 표시하도록 제목 표시줄의 **Text** 속성을 설정합니다.

    화면에 변경 내용이 반영됩니다.

    ![양식의 Datasource 및 Item 속성 설정](./media/data-platform-create-app-scratch/field-list.png)

1. 이 화면의 이름을 **FormScreen**으로 변경합니다.

## <a name="configure-icons"></a>아이콘 구성

1. **BrowseScreen**에서 화면 위쪽 근처에서 원형 아이콘을 선택하고, **OnSelect** 속성을 다음 수식으로 설정합니다.

    `Refresh(Accounts)`

    ![새로 고침 아이콘](./media/data-platform-create-app-scratch/refresh-icon.png)

1. 더하기 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `NewForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![추가 아이콘](./media/data-platform-create-app-scratch/plus-icon.png)

1. 오른쪽을 가리키는 첫 번째 화살표의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `EditForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![다음 아이콘](./media/data-platform-create-app-scratch/next-icon.png)

1. **FormScreen**에서 취소 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `ResetForm(EditForm1);Navigate(BrowseScreen, ScreenTransition.None)`

    ![취소 아이콘](./media/data-platform-create-app-scratch/cancel-icon.png)

1. 확인 표시 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    `SubmitForm(EditForm1); Navigate(BrowseScreen, ScreenTransition.None)`

    ![확인 표시 아이콘](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. **삽입** 탭에서 **아이콘**을 선택한 다음, **휴지통** 아이콘을 선택합니다.

1. **휴지통** 아이콘의 **Color** 속성을 **White**로 설정하고, **OnSelect** 속성을 다음 수식으로 설정합니다.

    `Remove(Accounts, BrowseGallery.Selected); Navigate(BrowseScreen, ScreenTransition.None)`

    ![휴지통 아이콘](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>앱 테스트

1. 왼쪽 탐색 모음에서 **BrowseScreen**을 선택한 다음, F5 키를 누르거나 오른쪽 위 모서리 근처에서 재생 아이콘을 선택하여 미리 보기를 엽니다.

    ![미리 보기 열기](./media/data-platform-create-app-scratch/open-preview.png)

1. 목록을 오름차순 또는 내림차순으로 정렬한 다음, 계정 이름에 있는 하나 이상의 문자를 기준으로 필터링합니다.

1. 계정을 추가하고, 추가한 계정을 편집하고, 계정 업데이트를 시작하지만, 변경 내용을 취소한 다음, 계정을 삭제합니다.

## <a name="next-steps"></a>다음 단계

- 예를 들어 [이 앱을 솔루션에 연결](add-app-solution.md)하여 다른 환경에 배포하거나 AppSource에 게시할 수 있습니다.
- [하나 이상의 샘플 앱을 열고](open-and-run-a-sample-app.md), 만들 수 있는 다양한 유형의 앱을 살펴봅니다.
