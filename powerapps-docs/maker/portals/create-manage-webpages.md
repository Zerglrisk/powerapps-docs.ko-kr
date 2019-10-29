---
title: 웹 페이지 만들기 및 관리 | Microsoft Docs
description: 포털에서 웹 페이지를 만들고 관리 하는 방법에 대 한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b62f6a811d2f2e6c5218ef601f18d69357d15ba9
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977016"
---
# <a name="create-and-manage-webpages"></a>웹 페이지 만들기 및 관리

웹 페이지는 웹 사이트에서 고유한 URL로 식별 되는 문서입니다. 웹 사이트의 핵심 개체 중 하나 이며 다른 웹 페이지에 대 한 부모 및 자식 관계를 통해 웹 사이트의 계층 구조를 작성 합니다.

> [!NOTE]
> PowerApps portal Studio를 사용 하 여 포털을 사용자 지정 하는 경우 웹 사이트 사용자가 성능에 영향을 줄 수 있습니다. 라이브 포털에서 사용량이 많지 않은 시간에 변경 내용을 적용 하는 것이 좋습니다.

## <a name="create-webpage"></a>웹 페이지 만들기

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  명령 모음에서 **새로 만들기 페이지** 를 선택 하 고 **레이아웃** 또는 **고정 레이아웃**에서 페이지를 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![새 웹 페이지 만들기](media/create-webpage.png "새 웹 페이지") 만들기

    > [!NOTE]
    > - **레이아웃** 을 사용 하 여 페이지를 만들면 전체 페이지를 유연 하 게 편집할 수 있습니다. **고정 레이아웃** 에는 포털 프로 비전의 일부로 설치 되는 페이지 템플릿과 [포털 관리 앱](configure/configure-portal.md)을 사용 하 여 만든 사용자 지정 페이지 템플릿이 포함 되어 있습니다.
    > - **레이아웃** 옵션을 사용 하 여 페이지를 만들려는 경우 새 **기본 studio 템플릿** 페이지 템플릿이 설치 됩니다.

3.  화면 오른쪽에 있는 속성 창에서 다음 정보를 입력 합니다.

    - **이름**: 페이지의 이름입니다. 이 값은 페이지의 제목으로도 사용 됩니다.

    - **부분 url**:이 페이지의 포털 url을 작성 하는 데 사용 되는 url 경로 세그먼트입니다.

    - **템플릿**: 포털에서이 페이지를 렌더링 하는 데 사용 되는 페이지 템플릿입니다. 필요한 경우 목록에서 다른 템플릿을 선택할 수 있습니다.

        > [!div class=mx-imgBorder]
        > ![웹 페이지 속성](media/webpage-props.png "웹 페이지 속성")

만든 웹 페이지가 추가 되 고 해당 계층 구조가 **페이지** 창에 표시 됩니다. **페이지** 창을 보려면 화면 왼쪽의 도구 창에서 페이지 ![페이지 아이콘](media/pages-icon.png "페이지 아이콘") **을 선택 합니다** .  

포털에 대 한 몇 가지 웹 페이지를 만들었다고 가정해 보겠습니다. 페이지 계층 구조는 다음과 같습니다.

> [!div class=mx-imgBorder]
> ![페이지 창](media/pages-pane.png "페이지 창")  

웹 사이트의 주 메뉴는 웹 페이지의 계층 구조에 따라 자동으로 만들어집니다. **기본** 메뉴 라고 합니다. 웹 사이트에 표시할 사용자 지정 메뉴를 만들 수도 있습니다. 추가 정보: [사용자 지정 메뉴 추가](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![웹 사이트 탐색](media/website-navigation.png "웹 사이트 탐색")

Dynamics 365 환경을 사용 하 여 만든 포털에서 작업 중이 고 메뉴가 페이지 계층 구조와 동일 하 게 하려면 **탐색 메뉴** 목록에서 **기본값** 을 선택 해야 합니다.

> [!div class=mx-imgBorder]
> ![기본 탐색 메뉴](media/navigation-menu-default.png "기본 탐색 메뉴")

## <a name="manage-webpage"></a>웹 페이지 관리

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  화면 왼쪽의 toolbelt에서 **페이지** ![페이지 아이콘](media/pages-icon.png "페이지 아이콘") 을 선택 합니다.  

3.  관리 하려는 페이지를 마우스로 가리키고 관리할 웹 페이지에 대 한 **줄임표** 단추 (...)를 선택 합니다. 차례로. 관리 하려는 페이지를 마우스 오른쪽 단추로 클릭할 수 있습니다.

4.  상황에 맞는 메뉴에서 필요한 작업을 선택 합니다.

    - **기본 메뉴에서 숨기기**: 기본 메뉴를 통해 사이트 맵 페이지에 표시 되지 않도록 페이지를 숨깁니다.

    - **기본 메뉴에 표시**: 기본 메뉴를 통해 사이트 맵 페이지에 페이지를 표시 합니다.

    - **자식 페이지 추가**: 선택한 페이지에 자식 페이지를 추가 합니다. 자식 페이지는 부모 페이지의 페이지 템플릿을 상속 합니다.

    - **홈 페이지로 설정**: 페이지를 홈 페이지로 설정 합니다. 새 홈 페이지의 URL이 웹 사이트의 루트로 설정 되 고 이전 페이지의 URL이 그에 따라 업데이트 됩니다.

    - **위로 이동**: 계층에서 페이지를 위로 이동 합니다.

    - **아래로 이동**: 계층에서 페이지를 아래로 이동 합니다.

        > [!NOTE]
        > 페이지를 위아래로 이동 하는 것은 같은 수준에 있는 페이지 간에 지원 됩니다.

    - 하위 페이지 수준 **올리기**: 들여쓰기를 줄이고 계층의 이전 페이지 수준에서 자식 페이지를 만듭니다.

    - 하위 페이지 **만들기**: 들여쓰기를 늘리고 페이지를 계층 구조에서 이전 페이지의 자식 페이지로 만듭니다.

    - **삭제**: 페이지를 삭제 합니다.

        > [!div class=mx-imgBorder]
        > ![웹 페이지 관리 옵션](media/webpage-manage-options.png "웹 페이지 관리 옵션")  





