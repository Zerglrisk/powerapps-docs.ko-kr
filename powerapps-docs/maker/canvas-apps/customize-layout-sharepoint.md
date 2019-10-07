---
title: 자습서 - 생성된 앱에서 갤러리 사용자 지정 | Microsoft Docs
description: 이 자습서에서는 갤러리에 표시되는 데이터와 PowerApps에 자동으로 생성된 앱의 다른 요소를 사용자 지정합니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: tutorial
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d12f667c1ff1fbf8424840b887e0f9394197ee2c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986047"
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>자습서 PowerApps에서 갤러리 사용자 지정

이 자습서에서는 갤러리라고 하는 레코드의 목록을 사용자 지정하고 Microsoft PowerApps에서 자동으로 생성된 앱의 다른 내용을 변경합니다. 이러한 변경 내용이 없어도 사용자는 앱에서 데이터를 관리할 수 있지만 조직의 요구 사항에 맞게 사용자 지정하면 앱을 더 쉽게 사용할 수 있습니다.

예를 들어 이 자습서에 나온 갤러리는 기본적으로 다음 그래픽과 일치합니다. 이메일 주소는 다른 데이터 유형에 비해 더 두드러지게 나타나며, 사용자는 해당 주소의 텍스트에 따라 갤러리를 정렬 및 필터링할 수 있습니다.

![기본 갤러리](./media/customize-layout-sharepoint/gallery-before.png)

그러나 사용자가 이메일 주소보다 계정 이름에 더 관심이 있을 수도 있으므로 조직에 대한 핵심 데이터를 기준으로 강조 표시, 정렬 및 필터링하도록 갤러리를 다시 구성할 수 있습니다. 또한 앱의 다른 화면과 구분되도록 기본 화면의 제목을 변경할 수도 있습니다.

![최종 갤러리](./media/customize-layout-sharepoint/gallery-after.png)

또한 터치 스크린 또는 마우스 휠이 없는 사용자가 전체 갤러리를 탐색할 수 있도록 스크롤 막대를 추가할 수 있습니다.

> [!div class="checklist"]
> * 갤러리 레이아웃 변경
> * 갤러리에 표시되는 데이터 형식 변경
> * 사용자가 데이터를 정렬 및 검색할 수 있는 기준 열 변경
> * 화면 제목 변경
> * 스크롤 막대 표시

이 자습서는 특정 데이터 원본에서 생성된 앱으로 시작합니다. 그러나 SharePoint 목록, Excel 테이블 또는 다른 데이터 원본을 기반으로 PowerApps에서 생성하는 모든 앱에는 동일한 개념이 적용됩니다.

PowerApps에 등록하지 않은 경우 시작하기 전에 [체험판으로 등록합니다](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="prerequisites"></a>필수 조건

Common Data Service의 **계정** 엔터티에서 [앱을 생성](data-platform-create-app.md) 합니다.

## <a name="open-the-generated-app"></a>생성된 앱 열기

1. [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인한 다음, 왼쪽 가장자리 근처에서 **앱**을 선택합니다.

1. 생성한 앱을 찾고, 앱에 대한 줄임표 아이콘( **...** )을 선택한 다음, **편집**을 선택합니다.

    ![편집할 앱 열기](./media/customize-layout-sharepoint/open-app.png)

1. **PowerApps Studio 시작** 대화 상자에서 **건너뛰기**를 선택합니다.

## <a name="change-the-layout"></a>레이아웃 변경

1. 왼쪽 탐색 창에서 **BrowseGallery1**을 선택합니다.

    갤러리가 선택되면 핸들이 있는 선택 상자가 갤러리를 둘러쌉니다.

    ![갤러리 선택](media/customize-layout-sharepoint/select-gallery-1.png)

1. 오른쪽 창의 **속성** 탭에서 **레이아웃**아래의 옵션 목록을 연 다음 제목만 표시 하는 옵션을 선택 합니다.

    ![제목 전용 레이아웃 선택](./media/customize-layout-sharepoint/choose-layout.png)

1. **필드**옆에서 **편집**을 선택 하 고 제목 상자에 대해 아래쪽 화살표를 선택 합니다.

    이 컨트롤의 이름은 **Title1**과 같이 숫자로 끝납니다. 단, 숫자는 사용자가 수행한 다른 작업에 따라 달라질 수 있습니다.

1. 옵션 목록에서 **계정 이름**을 선택 하 고 **데이터** 창을 닫습니다.

    갤러리에 각 계정의 이름이 표시됩니다.

    ![최종 갤러리](./media/customize-layout-sharepoint/final-gallery.png)

## <a name="change-sort-and-search-columns"></a>열 정렬 및 검색 변경

1. 이전 섹션에서 설명한 대로 갤러리를 선택합니다.

    ![갤러리 선택](./media/customize-layout-sharepoint/select-gallery-title.png)

1. 왼쪽 위 모서리 근처에서 속성 목록에 **항목**이 표시되는지 확인합니다.

    ![항목 속성](./media/customize-layout-sharepoint/items-property.png)

    이 속성의 값은 수식 입력줄에 표시됩니다. 이 속성을 설정하여 갤러리의 데이터 원본뿐 아니라 사용자가 데이터를 정렬하고 검색할 수 있는 기준 열도 지정합니다.

1. 이 수식을 복사한 다음, 수식 입력줄에 붙여넣습니다.

    ```SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, Descending, Ascending))```

    이 수식을 사용하여 다음을 확인할 수 있습니다.

    * 검색 창에 하나 이상의 문자가 있는 경우 갤러리에는 사용자가 입력한 텍스트가 포함된 계정 이름만 표시됩니다.
    * 사용자가 정렬 아이콘을 선택하면 갤러리는 사용자가 아이콘을 선택하는 횟수에 따라 오름차순 또는 내림차순의 계정 이름별로 사전순으로 정렬됩니다.

     이러한 함수 및 다른 함수에 대한 자세한 내용은 [수식 참조](formula-reference.md)를 참조하세요.

### <a name="test-sorting-and-searching"></a>정렬 및 검색 테스트

1. F5 키를 누르거나 오른쪽 위 모서리 근처에 있는 [재생] 단추를 선택하여 미리 보기 모드를 엽니다.

    ![미리 보기 모드 열기](./media/customize-layout-sharepoint/open-preview.png)

1. 브라우저 화면의 오른쪽 위 모서리 근처에서 정렬 아이콘을 한 번 이상 선택하여 사전순 정렬 순서를 오름차순과 내림차순 중에서 변경합니다.

    ![정렬 아이콘 테스트](./media/customize-layout-sharepoint/sort-button.png)

1. 검색 상자에 **k**를 입력하여 입력한 문자를 포함하는 계정 이름만 표시합니다.

    ![검색 표시줄 테스트](./media/customize-layout-sharepoint/test-filter.png)

1. 검색 창에서 모든 텍스트를 제거한 다음, Esc 키를 누르거나 오른쪽 위 모서리 근처에서 닫기 아이콘을 선택하여 미리 보기 모드를 닫습니다.

## <a name="change-the-screen-title"></a>화면 제목 변경

1. 화면의 제목을 클릭하거나 탭하여 선택합니다.

    ![화면 제목 선택](./media/customize-layout-sharepoint/select-title.png)

1. 속성 목록에 **텍스트**가 표시되는지 확인하고 수식 입력줄에서 **계정**을 **찾아보기**(큰따옴표 유지)로 바꿉니다.

    ![화면 제목 업데이트](./media/customize-layout-sharepoint/change-screen-title.png)

    화면은 변경 내용을 반영합니다.

    ![새 화면 제목](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scrollbar"></a>스크롤 막대 표시

사용자가 터치 스크린 및 마우스 휠을 가지고 있지 않은 경우 사용자가 갤러리를 마우스로 가리키면 스크롤 막대가 표시되도록 갤러리를 구성합니다. 이렇게 하면 화면에 모든 계정을 한 번에 표시할 수 없는 경우에도 모든 계정을 표시할 수 있습니다.

1. 첫 번째 절차에서 설명한 대로 갤러리를 선택합니다.

    ![갤러리 선택](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. 갤러리의 **Scrollbar 표시** 속성을 **true**로 설정 합니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 갤러리를 사용자 지정하고 생성된 앱에서 레코드를 찾아보기 위한 기본 화면의 다른 내용을 변경했습니다. 세부 정보를 표시하고 계정을 만들거나 업데이트하는 기본 화면을 사용자 지정할 수도 있습니다. 찾아보기 화면에는 갤러리가 포함되는 것처럼 앱의 다른 두 화면에는 양식이 포함됩니다. 예를 들어 양식이 표시하는 데이터 형식 및 순서를 변경할 수 있습니다.

> [!div class="nextstepaction"]
> [양식 사용자 지정](customize-forms-sharepoint.md)
