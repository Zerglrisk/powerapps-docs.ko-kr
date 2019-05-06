---
title: 솔루션에서 캔버스 앱 만들기 | Microsoft Docs
description: PowerApps에서 캔버스 앱 솔루션에서 다른 환경으로 앱을 배포할 수 있도록 만들기
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dcb6a9c69e602b739d58afde2242d18b60e6f477
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61540528"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>솔루션 내에서 캔버스 앱 만들기

예를 들어, 다른 환경으로 앱을 배포하려는 경우 솔루션 내에서 앱을 만듭니다. 솔루션은 앱 뿐만 아니라 사용자 지정된 엔터티, 옵션 집합 및 기타 구성 요소를 포함할 수 있습니다. 솔루션 내에서 앱과 다른 구성 요소를 만들고, 솔루션을 내보낸 다음, 다른 환경으로 가져와서 다양한 방식으로 환경을 신속하게 사용자 지정할 수 있습니다.

솔루션은 Dynamics 365 for Customer Engagement와 동일한 플랫폼을 기반으로 합니다. 자세한 내용은 [솔루션 개요](../common-data-service/solutions-overview.md)를 확인합니다.

## <a name="prerequisite"></a>필수 조건

이 항목의 단계를 수행 하려면 Common Data Service 데이터베이스를 포함 하는 환경으로 전환 해야 합니다.

## <a name="create-a-solution"></a>솔루션 만들기

앱을 생성하기 원하거나 앱을 연결하려는 솔루션이 이미 있는 경우라면 다음 절차를 건너뛸 수 있습니다.

1. PowerApps에 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)한 다음 (필요한 경우) 적절한 환경으로 전환합니다.

    - 솔루션 내에서 앱을 만들려는 경우 Common Data Service 데이터베이스를 포함하는 환경으로 전환합니다.
    - 기존 앱을 솔루션에 연결하려는 경우 해당 앱이 포함된 환경으로 전환합니다.

1. 왼쪽된 탐색 모음에서 **솔루션**을 선택합니다

    > [!div class="mx-imgBorder"]
    > ![왼쪽된 탐색 모음에서 솔루션 옵션](./media/add-app-solution/left-nav.png "왼쪽된 탐색 모음에서 솔루션 옵션")

1. 제목 표시줄 아래의 배너에서 **새 솔루션**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![배너에서 새 솔루션 옵션](./media/add-app-solution/banner-new-solution.png "배너에서 새 솔루션 옵션")

1. 표시되는 창에서 표시 이름, 게시자 및 솔루션의 버전을 지정합니다.

    > [!div class="mx-imgBorder"]
    > ![새 솔루션에 대 한 옵션](./media/add-app-solution/configure-new-solution.png "새 솔루션에 대 한 옵션")

    이름(공백 없음)은 지정하는 표시 이름에 따라 자동으로 생성되지만 원하는 경우 생성된 이름을 사용자 지정할 수 있습니다. 특별한 요구사항이 없다면 사용자 환경에 대한 기본 게시자와 버전 **1.0**을 지정할 수 있습니다.

1. 왼쪽 위 모서리 근처의 **저장 후 닫기**를 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![새 솔루션을 저장할](./media/add-app-solution/save-new-solution.png "새 솔루션을 저장 합니다.")

## <a name="create-a-canvas-app-in-a-solution"></a>솔루션에서 캔버스 앱 만들기

솔루션 내에서 빈 캔버스 앱을 만들 수 있습니다. 자동으로 3개 화면 앱을 생성하거나 솔루션 내에서 템플릿 또는 샘플 앱을 사용자 지정할 수 없습니다.

1. PowerApps로 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.

1. 필요한 경우, 캔버스 앱을 만들려는 솔루션을 포함하는 환경으로 전환합니다.

1. 왼쪽 탐색 모음에서 **솔루션**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![왼쪽된 탐색 모음에서 솔루션 옵션](./media/add-app-solution/left-nav.png "왼쪽된 탐색 모음에서 솔루션 옵션")

1. 솔루션의 목록에서 캔버스 앱을 만들려면 원하는 솔루션을 선택 합니다.

1. 제목 표시줄 아래의 배너에서 **새로 만들기** > **응용 프로그램** > **캔버스 앱**을 선택한 다음, 만들려고 하는 앱의 폼 팩터(휴대폰 또는 태블릿)를 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![솔루션에서 앱을 만드는 옵션을](./media/add-app-solution/new-option.png "솔루션에서 앱을 만드는 옵션")

    다른 브라우저 탭에서 빈 캔버스를 사용하는 PowerApps Studio가 열립니다.

1. 앱을 생성(또는 하나 이상을 변경)한 다음, 변경 내용을 저장합니다.

1. 솔루션을 선택한 브라우저 탭에서, 솔루션의 구성 요소 목록을 새로 고치기 위해 **완료**를 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![완료 단추](./media/add-app-solution/done-button.png "완료 단추")

    솔루션의 구성 요소 목록에 새 앱이 나타납니다. 앱에 어떤 변경 내용을 저장하면, 솔루션에 있는 버전에 반영됩니다.

## <a name="link-an-existing-canvas-app-to-a-solution"></a>솔루션에 기존 캔버스 앱 연결

솔루션에 앱을 연결하려는 경우, 모두 동일한 환경이어야 하고 앱은 솔루션 내에서 생성된 것이어야 합니다.

1. PowerApps로 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.

1. 필요한 경우 앱을 연결 하려는 솔루션을 포함 하는 환경으로 전환 합니다.

1. 왼쪽 탐색 모음에서 **솔루션**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![왼쪽된 탐색 모음에서 솔루션 옵션](./media/add-app-solution/left-nav.png "왼쪽된 탐색 모음에서 솔루션 옵션")

1. 솔루션의 목록에서 앱을 연결 하려는 솔루션을 선택 합니다.

1. 제목 표시줄 아래의 배너에서 **기존 항목 추가** > **응용 프로그램** > **캔버스 앱**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![기존 앱을 연결 하는 옵션을 배너](./media/add-app-solution/add-existing.png "배너 기존 앱을 연결 하는 옵션")

    이 환경에서 솔루션 내에서 만든 캔버스 앱 목록이 표시 됩니다.

1. 앱 목록에서, 솔루션에 연결하려는 앱을 선택한 다음 **추가**를 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![추가 단추](./media/add-app-solution/add-button.png "추가 단추")

## <a name="known-limitations"></a>알려진 제한 사항

알려진 제한 사항에 대한 자세한 내용은 [PowerApps에서 솔루션 사용](../common-data-service/use-solution-explorer.md#known-limitations)을 확인합니다. 

## <a name="next-steps"></a>다음 단계

- 더 많은 앱 및 엔터티, 흐름 및 솔루션 대시보드 등과 같은 [다른 구성 요소](../common-data-service/use-solution-explorer.md)를 연결하거나 새로 만듭니다.
- [솔루션 내보내기](../common-data-service/import-update-export-solutions.md)로 AppSource 등의 다른 환경에 배포할 수 있습니다.
