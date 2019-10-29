---
title: 솔루션에서 캔버스 앱 만들기 | Microsoft Docs
description: PowerApps에서 앱을 다른 환경에 배포할 수 있도록 솔루션에서 캔버스 앱을 만듭니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c908e3d25530b52b103ef58989545e46b931e791
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "71987719"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>솔루션 내에서 캔버스 앱 만들기

예를 들어 앱을 다른 환경에 배포 하려는 경우 솔루션 내에서 앱을 만듭니다. 솔루션에는 앱 뿐만 아니라 사용자 지정 된 엔터티, 옵션 집합 및 기타 구성 요소가 포함 될 수 있습니다. 솔루션 내에서 앱 및 기타 구성 요소를 만들고, 솔루션을 내보낸 다음 다른 환경으로 가져오는 방법으로 다양 한 방법으로 환경을 신속 하 게 사용자 지정할 수 있습니다.

솔루션에 대 한 자세한 내용은 [솔루션 개요](../common-data-service/solutions-overview.md)를 참조 하세요.

## <a name="prerequisite"></a>필수 조건

이 항목의 단계를 따르려면 Common Data Service 데이터베이스를 포함 하는 환경으로 전환 해야 합니다.

## <a name="create-a-solution"></a>솔루션 만들기

앱을 만들거나 앱을 연결 하려는 솔루션이 이미 있는 경우이 절차를 건너뛸 수 있습니다.

1. PowerApps에 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 한 다음 필요한 경우 적절 한 환경으로 전환 합니다.

    - 솔루션 내에서 앱을 만들려는 경우 Common Data Service 데이터베이스를 포함 하는 환경으로 전환 합니다.
    - 솔루션에 기존 앱을 연결 하려는 경우 해당 앱을 포함 하는 환경으로 전환 합니다.

1. 왼쪽 탐색 모음에서 **솔루션**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![왼쪽 탐색 모음의 솔루션 옵션](./media/add-app-solution/left-nav.png "왼쪽 탐색 모음의 솔루션 옵션")

1. 제목 표시줄 아래의 배너에서 **새 솔루션**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![배너의 New-solution 옵션](./media/add-app-solution/banner-new-solution.png "배너의 New-solution 옵션")

1. 표시 되는 창에서 솔루션에 대 한 표시 이름, 게시자 및 버전을 지정 합니다.

    > [!div class="mx-imgBorder"]
    > ![새 솔루션에 대 한 옵션](./media/add-app-solution/configure-new-solution.png "새 솔루션에 대 한 옵션")

    지정 하는 표시 이름에 따라 이름 (공백 없음)이 자동으로 생성 되지만, 원하는 경우 생성 된 이름을 사용자 지정할 수 있습니다. 사용자 환경에 대 한 기본 게시자를 지정 하 고 해당 영역에 특정 요구 사항이 없는 경우 버전 **1.0** 을 지정할 수 있습니다.

1. 왼쪽 위 모서리 근처에서 **저장 후 닫기**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![새 솔루션 저장](./media/add-app-solution/save-new-solution.png "새 솔루션 저장")

## <a name="create-a-canvas-app-in-a-solution"></a>솔루션에서 캔버스 앱 만들기

솔루션 내에서 빈 캔버스 앱을 만들 수 있습니다. 3 화면 앱을 자동으로 생성 하거나 솔루션 내에서 템플릿 또는 샘플 앱을 사용자 지정할 수 없습니다.

1. PowerApps에 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 합니다.

1. 필요한 경우 캔버스 앱을 만들려는 솔루션을 포함 하는 환경으로 전환 합니다.

1. 왼쪽 탐색 모음에서 **솔루션**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![왼쪽 탐색 모음의 솔루션 옵션](./media/add-app-solution/left-nav.png "왼쪽 탐색 모음의 솔루션 옵션")

1. 솔루션 목록에서 캔버스 앱을 만들려는 솔루션을 선택 합니다.

1. 제목 표시줄 아래의 배너에서 **새로** 만들기  > **app**  > **Canvas 앱**을 선택한 다음 만들려는 앱의 폼 팩터 (전화 또는 태블릿)를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![솔루션에서 앱을 만드는 옵션](./media/add-app-solution/new-option.png "솔루션에서 앱을 만드는 옵션")

    PowerApps Studio 다른 브라우저 탭에서 빈 캔버스로 열립니다.

1. 앱을 만들고 하나 이상의 변경을 수행한 다음 변경 내용을 저장 합니다.

1. 솔루션을 선택한 브라우저 탭에서 **완료** 를 선택 하 여 솔루션의 구성 요소 목록을 새로 고칩니다.

    > [!div class="mx-imgBorder"]
    > ![완료 단추](./media/add-app-solution/done-button.png "완료 단추")

    해당 솔루션의 구성 요소 목록에 새 앱이 표시 됩니다. 앱에 대 한 변경 내용을 저장 하면 솔루션에 있는 버전에 반영 됩니다.

## <a name="link-an-existing-canvas-app-to-a-solution"></a>기존 캔버스 앱을 솔루션에 연결

솔루션에 앱을 연결 하려는 경우 둘 다 동일한 환경에 있어야 하 고 솔루션 내에서 앱을 만들어야 합니다.

1. PowerApps에 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 합니다.

1. 필요한 경우 앱을 연결 하려는 솔루션을 포함 하는 환경으로 전환 합니다.

1. 왼쪽 탐색 모음에서 **솔루션**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![왼쪽 탐색 모음의 솔루션 옵션](./media/add-app-solution/left-nav.png "왼쪽 탐색 모음의 솔루션 옵션")

1. 솔루션 목록에서 앱을 연결 하려는 솔루션을 선택 합니다.

1. 제목 표시줄 아래의 배너에서 기존  > **앱** **추가**  > **Canvas 앱**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![기존 앱을 연결 하는 배너 옵션](./media/add-app-solution/add-existing.png "기존 앱을 연결 하는 배너 옵션")

    이 환경에서 솔루션 내에 생성 된 캔버스 앱 목록이 표시 됩니다.

1. 앱 목록에서 솔루션에 연결 하려는 앱을 선택 하 고 **추가**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![단추 추가](./media/add-app-solution/add-button.png "단추 추가")

## <a name="known-limitations"></a>알려진 제한 사항

알려진 제한 사항에 대 한 자세한 내용은 [PowerApps에서 솔루션 사용](../common-data-service/use-solution-explorer.md#known-limitations)을 참조 하세요. 

## <a name="next-steps"></a>다음 단계

- 솔루션에 더 많은 앱 및 [기타 구성 요소](../common-data-service/use-solution-explorer.md)(예: 엔터티, 흐름 및 대시보드)를 만들거나 연결 합니다.
- 다른 환경, AppSource 등에 배포할 수 있도록 [솔루션을 내보냅니다](../common-data-service/import-update-export-solutions.md) .
