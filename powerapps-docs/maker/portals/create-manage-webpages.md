---
title: 웹 페이지 만들기 및 관리 | MicrosoftDocs
description: 포털에서 웹 페이지를 만들고 관리하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 09/16/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-and-manage-webpages"></a>웹 페이지 만들기 및 관리

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

웹 페이지는 웹 사이트에서 고유한 URL로 식별되는 문서입니다. 웹 사이트의 핵심 개체 중 하나이며 다른 웹 페이지에 대한 부모 및 자식 관계를 통해 웹 사이트의 계층 구조를 만듭니다.

> [!NOTE]
> 포털 디자이너를 사용하여 포털을 사용자 지정하면 웹 사이트 사용자가 성능 효과를 체감할 수 있습니다. 사용량이 많지 않은 시간 동안 실시간 포털에서 변경을 수행하는 것이 좋습니다.

## <a name="create-webpage"></a>웹 페이지 만들기

1.  [포털을 편집](manage-existing-portals.md#edit)하여 포털 디자이너에서 열 수 있습니다.  

2.  명령 모음에서 **새 페이지**를 선택하고 페이지 템플릿을 선택하십시오.

    > [!div class=mx-imgBorder]
    > ![새 웹 페이지 만들기](media/create-webpage.png "새 웹 페이지 만들기")

3.  화면 오른쪽의 속성 창에서 다음 정보를 입력합니다.

    - **이름**: 페이지의 이름입니다. 이 값은 페이지 제목으로도 사용됩니다.

    - **부분 URL**: 이 페이지의 포털 URL을 빌드하기 위해 사용되는 URL 경로 세그먼트입니다.

    - **템플릿**: 포털에 이 페이지를 렌더링하기 위해 사용되는 페이지 템플릿입니다. 필요한 경우 목록에서 다른 템플릿을 선택할 수 있습니다.

        > [!div class=mx-imgBorder]
        > ![웹 페이지 속성](media/webpage-props.png "웹 페이지 속성")

생성한 웹 페이지가 추가되고 해당 계층 구조가 **페이지** 창에 표시됩니다. **페이지** 창을 보려면 화면 왼쪽의 툴 벨트에서 **페이지** ![페이지 아이콘](media/pages-icon.png "페이지 아이콘")를 선택합니다.  

포털을 위해 몇 개의 웹 페이지를 작성했다고 가정해 봅시다. 페이지 계층 구조는 다음과 같습니다.

> [!div class=mx-imgBorder]
> ![페이지 창](media/pages-pane.png "페이지 창")  

웹 사이트의 기본 메뉴는 웹 페이지의 계층 구조에 따라 자동으로 생성됩니다. 이를 **기본** 메뉴라고 합니다. 웹 사이트에 표시할 사용자 지정 메뉴를 만들 수도 있습니다. 추가 정보: [사용자 지정 메뉴 추가](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![웹 사이트 탐색](media/website-navigation.png "웹 사이트 탐색")

Dynamics 365 포털에서 작업하고 메뉴가 페이지 계층 구조와 동일하게 하려면 **탐색 메뉴** 목록에서 **기본**을 선택해야 합니다.

> [!div class=mx-imgBorder]
> ![기본 탐색 메뉴](media/navigation-menu-default.png "기본 탐색 메뉴")

## <a name="manage-webpage"></a>웹 페이지 관리

1.  [포털을 편집](manage-existing-portals.md#edit)하여 포털 디자이너에서 열 수 있습니다.  

2.  화면 왼쪽의 툴 벨트에서 **페이지** ![페이지 아이콘](media/pages-icon.png "페이지 아이콘")를 선택합니다.  

3.  관리하려는 페이지 위로 마우스를 가져간 다음 관리하려는 웹 페이지의 **줄임표** 버튼(…)을 선택합니다. 또는, 관리하려는 페이지를 마우스 오른쪽 버튼으로 클릭할 수 있습니다.

4.  상황에 맞는 메뉴에서 필요한 작업을 선택하십시오.

    - **기본 메뉴에서 숨기기**: 기본 메뉴를 통해 페이지가 사이트 맵에 표시되지 않도록 숨깁니다.

    - **기본 메뉴에 표시**: 기본 메뉴를 통해 사이트 맵에 페이지를 표시합니다.

    - **자식 페이지 추가**: 자식 페이지를 선택한 페이지에 추가합니다. 자식 페이지는 부모 페이지의 페이지 템플릿을 상속합니다.

    - **홈 페이지로 설정**: 페이지를 홈 페이지로 설정합니다. 새 홈 페이지의 URL은 웹 사이트의 루트로 설정되고 이전 페이지의 URL은 그에 따라 업데이트됩니다.

    - **위로 이동**: 페이지를 계층 구조의 위로 이동합니다.

    - **아래로 이동**: 페이지를 계층 구조의 아래로 이동합니다.

        > [!NOTE]
        > 동일한 수준의 페이지 간에 페이지를 위나 아래로 이동하는 것이 지원됩니다.

    - **하위 페이지 승격**: 들여쓰기를 줄이고 자식 페이지를 계층 구조의 이전 페이지 수준으로 만듭니다.

    - **하위 페이지 만들기**: 들여쓰기를 늘리고 페이지를 계층 구조의 이전 페이지의 자식 페이지로 만듭니다.

    - **삭제**: 페이지를 삭제합니다.

        > [!div class=mx-imgBorder]
        > ![웹 페이지 관리 옵션](media/webpage-manage-options.png "웹 페이지 관리 옵션")  




