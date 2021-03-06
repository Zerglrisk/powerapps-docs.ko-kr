---
title: SharePoint 목록에서 캔버스 앱 만들기 | Microsoft Docs
description: Power Apps에서 자동으로 캔버스 앱을 만들어 SharePoint 목록의 데이터를 관리 합니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 346bb27911549715b6c4fdc40f64552c524527be
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959452"
---
# <a name="create-a-canvas-app-in-power-apps-from-a-sharepoint-list"></a>SharePoint 목록에서 Power Apps의 캔버스 앱 만들기

이 항목에서는 Power Apps를 사용 하 여 SharePoint 목록의 항목을 기반으로 캔버스 앱을 만듭니다. Power Apps 또는 SharePoint Online 내에서 앱을 만들 수 있습니다. Power Apps 내에서 데이터 게이트웨이를 통해 [연결](connections/connection-sharepoint-online.md#create-a-connection) 하는 경우 온-프레미스 SharePoint 사이트의 목록에 기반 하 여 앱을 만들 수 있습니다.

사용자가 만드는 앱에는 다음 3 개의 화면이 포함 됩니다.

- 찾아보기 화면에서 목록의 모든 항목을 스크롤할 수 있습니다.
- 세부 정보 화면에서 목록의 단일 항목에 대한 모든 정보를 표시할 수 있습니다.
- 편집 화면에서 항목을 만들거나 기존 항목에 대한 정보를 업데이트할 수 있습니다.

이 항목의 개념 및 기술을 SharePoint의 모든 목록에 적용할 수 있습니다. 단계를 정확히 따르려면 다음을 수행합니다.

1. SharePoint Online 사이트에서 **SimpleApp**이라는 목록을 만듭니다.
2. 이름이 **제목**인 열에서 **바닐라**, **초콜릿** 및 **딸기**에 대한 항목을 만듭니다.

텍스트, 날짜, 숫자 및 통화와 같은 다양한 형식의 여러 열이 포함된 훨씬 더 복잡한 목록을 만들더라도 앱을 생성하는 원칙은 변경되지 않습니다.

> [!IMPORTANT]
> Power Apps는 모든 유형의 SharePoint 데이터를 지원 하지 않습니다. 자세한 내용은 [알려진 문제](connections/connection-sharepoint-online.md#known-issues)를 참조하세요.

## <a name="create-an-app-from-within-power-apps"></a>Power Apps 내에서 앱 만들기

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인 합니다.

1. **고유한 앱 만들기** 아래에서 **데이터로 시작**을 마우스로 가리킨 다음, **이 앱 만들기**를 선택합니다.

    ![앱 만들기 옵션](./media/app-from-sharepoint/start-from-data.png)

1. SharePoint 타일에서 **전화 레이아웃**을 선택합니다.

    ![앱 만들기 옵션](./media/app-from-sharepoint/sharepoint-tile.png)

1. **직접 연결** 옵션을 선택하고 **만들기**를 선택합니다.

    ![연결 만들기](./media/app-from-sharepoint/create-connection.png)

1. **SharePoint 사이트에 연결** 아래에서 SharePoint Online 사이트에 대한 URL을 입력하거나 붙여넣은 다음, **이동**을 선택합니다.

    다음 예와 같이 사이트 URL(목록 이름이 아님)만 포함합니다.<br>`https://microsoft.sharepoint.com/teams/Contoso`

1. **목록 선택** 아래에서 **SimpleApp**을 선택한 다음, **연결**을 선택합니다.

    몇 분 후에 앱이 찾아보기 화면에 열리고 목록에 만든 항목이 표시됩니다. 목록에 **Title**보다 많은 열의 데이터가 있는 경우 앱에 해당 데이터가 표시됩니다. 화면 위쪽 근처의 제목 표시줄에는 목록 새로 고침, 목록 나열 및 목록에 항목 만들기 아이콘이 표시됩니다. 제목 표시줄 아래의 검색 상자에서 입력하거나 붙여넣을 텍스트를 기준으로 목록을 필터링하는 옵션을 제공합니다. 

    ![찾아보기 화면](./media/app-from-sharepoint/browse-screen.png)

    이 앱을 사용하거나 다른 사용자와 공유하기 전에 더 많은 변경 작업을 수행하려고 할 것입니다. 가장 좋은 방법은 진행하기 전에 Ctrl-S를 눌러 지금까지의 작업을 저장하는 것입니다. 앱에 이름을 지정한 다음, **저장**을 선택합니다.

## <a name="create-an-app-from-within-sharepoint-online"></a>SharePoint Online 내에서 앱 만들기

SharePoint Online 명령 모음에서 사용자 지정 목록의 앱을 만들 경우 앱이 해당 목록의 보기로 나타납니다. 웹 브라우저뿐 아니라 iOS 또는 Android 디바이스에서도 앱을 실행할 수 있습니다.

1. SharePoint Online에서 사용자 지정 목록을 열고 명령 모음에서 **PowerApps**를 선택한 다음, **앱 만들기**를 선택합니다.

    ![앱 만들기](./media/app-from-sharepoint/generate-new-app.png)

2. 표시되는 패널에서 앱 이름을 입력한 다음, **만들기**를 선택합니다.

    ![앱 이름 지정](./media/app-from-sharepoint/app-name.png)

    SharePoint 목록에 기반 하 여 만든 앱을 표시 하는 새 탭이 웹 브라우저에 나타납니다. 앱이 앱을 사용자 지정할 수 있는 Power Apps Studio에 표시 됩니다.

    ![기본 앱](./media/app-from-sharepoint/default-app.png)

3. (선택 사항) SharePoint 목록의 브라우저 탭을 새로 고친 다음(예: F5를 눌러 선택), 다음 단계에 따라 앱을 실행하거나 관리합니다.

    - 별도의 브라우저 탭에서 앱을 실행하려면 **열기**를 선택합니다.
    - 조직의 다른 사용자가 앱을 실행할 수 있도록 하려면 **이 보기를 공개로 설정**을 선택합니다.

        다른 사용자가 앱을 편집할 수 있도록 하려면 **편집 가능** 권한을 [공유](share-app.md)합니다.

    - SharePoint에서 보기를 제거하려면 **이 보기 제거**를 선택합니다.

        앱을 Power Apps에서 제거 하려면 [앱을 삭제](delete-app.md)합니다.

> [!NOTE]
> SharePoint 목록에서 만든 앱은 현재 Power Apps 모바일에 표시 되지 않습니다.

## <a name="next-steps"></a>다음 단계
이 항목에서는 SharePoint 목록의 데이터를 관리하는 앱을 만들었습니다. 다음 단계로, 좀 더 복잡 한 목록에서 앱을 만든 다음 사용자의 요구에 맞게 앱을 사용자 지정 합니다 (찾아보기 화면으로 시작).

> [!div class="nextstepaction"]
> [기본 찾아보기 화면 사용자 지정](customize-layout-sharepoint.md)
