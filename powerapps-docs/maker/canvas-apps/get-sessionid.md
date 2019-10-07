---
title: 세션 ID 또는 캔버스 앱 ID 가져오기 | Microsoft Docs
description: PowerApps의 문제를 해결하기 위해 세션 ID 또는 캔버스 앱 ID를 가져오는 방법
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 11f749f241f978ebd94e460833e98cca894fe7fa
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71990194"
---
# <a name="get-a-session-id-or-a-canvas-app-id"></a>세션 ID 또는 캔버스 앱 ID 가져오기
PowerApps에 만든 캔버스 앱에 문제가 발생하는 경우 해당 문제에 대한 세션 ID, 앱 ID 또는 둘 다를 제공하여 Microsoft에서 훨씬 더 효과적으로 문제를 해결할 수 있도록 도울 수 있습니다.

## <a name="get-the-session-id"></a>세션 ID 가져오기

### <a name="when-editing-an-app"></a>앱을 편집 중인 경우
1. 왼쪽 위 모서리에서 **파일**을 선택합니다.

1. **계정**을 선택합니다.

1. **진단**에서 **세션 세부 정보**를 선택합니다.

    ![PowerApps Studio에서 세션 ID 가져오기](media/get-sessionid/studio.png)

### <a name="when-running-an-app-in-a-browser"></a>브라우저에서 앱을 실행 중인 경우
1. 오른쪽 위 모서리에서 기어 아이콘을 선택합니다.

1. **세션 세부 정보**를 선택합니다.

    ![브라우저에서 세션 ID 가져오기](media/get-sessionid/browser.png)

### <a name="when-running-an-app-on-a-phone-or-a-tablet"></a>휴대폰이나 태블릿에서 앱을 실행 중인 경우
1. 오른쪽으로 살짝 밉니다.

1. **세션 세부 정보**를 탭합니다.

    ![브라우저에서 세션 ID 가져오기](media/get-sessionid/mobile.png)

### <a name="when-running-an-embedded-app-or-form"></a>포함 앱 또는 폼을 실행 중인 경우
1. 다음 단계 중 하나를 수행합니다.

    - Alt 키를 누른 상태에서 앱 또는 폼을 마우스 오른쪽 단추로 클릭합니다.
    - 두 손가락으로 앱 또는 폼을 1~2초 동안 탭한 다음, 손가락을 놓습니다.

1. **세션 세부 정보**를 선택합니다.

    ![포함 앱에서 세션 ID 가져오기](media/get-sessionid/embedded.png)

## <a name="get-an-app-id"></a>앱 ID 가져오기
1. [PowerApps에 로그인](https://powerapps.microsoft.com)합니다.

1. 왼쪽 모서리 근처에 있는 **앱**을 선택합니다.

1. 문제 해결 중인 앱에 대해 줄임표( **. . .** )를 선택하고 **세부 정보**를 선택합니다.

    ![앱 세부 정보로 이동](./media/get-sessionid/details.png)

    해당 앱의 **세부 정보** 창 하단에 앱 ID가 표시됩니다.

    ![세부 정보에서 앱 ID 복사](./media/get-sessionid/app-id.png)
