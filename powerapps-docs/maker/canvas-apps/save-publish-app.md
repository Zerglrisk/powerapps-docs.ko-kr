---
title: 캔버스 앱 저장 및 게시 | Microsoft Docs
description: 앱 작성자를 위한 캔버스 앱 저장 및 게시에 대한 단계별 지침
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/14/2017
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 19d793b879d42e9446cc8ad366bc08879162185d
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995770"
---
# <a name="save-and-publish-a-canvas-app-in-powerapps"></a>PowerApps에서 캔버스 앱 저장 및 게시
캔버스 앱에 대한 변경 내용을 저장할 때마다 사용자와 앱을 편집할 수 있는 권한이 있는 다른 모든 사람에 대해서만 자동으로 게시합니다. 변경이 끝나면 앱이 공유된 모든 사용자가 사용할 수 있도록 명시적으로 게시해야 합니다.

앱을 공유하는 방법에 대한 정보는 [공유](share-app.md)를 참조하세요.

## <a name="save-changes-to-an-app"></a>앱에 대한 변경 내용 저장
PowerApps Studio의 왼쪽 가장자리에 있는 **파일** 메뉴에서 **저장**을 클릭하거나 누르고 다음과 같은 단계를 따릅니다.

* 이전에 앱을 저장한 적이 없는 경우 이름을 지정하고 **저장**을 클릭하거나 누릅니다.

    ![새 앱 저장](./media/save-publish-app/save-as.png)
* 앱을 저장하지 않은 경우 **저장**을 클릭하거나 누릅니다.  

    ![업데이트된 앱 저장](./media/save-publish-app/save-app.png)

PowerApps는 정기적으로 2분마다 앱을 저장할 수 있습니다. 앱을 한 번 저장한 경우 PowerApps에서는 사용자가 저장 작업을 누를 필요 없이 앱의 버전을 주기적으로 저장합니다. 작성자는 **파일** 메뉴의 **계정** 탭에서 **자동 저장** 설정을 사용하거나 사용하지 않도록 설정할 수 있습니다.

![자동 저장 설정](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>앱 게시
1. PowerApps Studio의 왼쪽 가장자리에 있는 **파일** 메뉴에서 **저장**을 클릭하거나 누르고 **이 버전 게시**를 클릭하거나 누릅니다.

    ![앱 게시](./media/save-publish-app/publish-app.png)
2. **게시** 대화 상자에서 **이 버전 게시**를 누르거나 클릭하여 앱을 공유하는 모든 사용자에게 앱을 게시합니다.

   ![게시 검토](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > 캔버스 앱을 게시할 때마다 앱은 최신 버전의 PowerApps에서 실행하도록 업그레이드됩니다. 즉, 사용자가 마지막으로 게시한 이후로 추가된 모든 최신 기능 및 성능 업그레이드의 이점을 누리게 된다는 것을 의미합니다. 몇 개월 내에 업데이트를 게시하지 않은 경우 지금 다시 게시하면 즉각적인 성능 이점을 볼 수 있게 됩니다.

## <a name="identify-the-live-version"></a>라이브 버전 확인
[powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 (왼쪽 모서리에 있는) **파일** 메뉴에서 **앱**을 클릭하거나 누르고, 앱에 대한 세부 정보 아이콘을 클릭하거나 누른 다음, **버전** 탭을 클릭하거나 누릅니다.

**라이브** 버전은 앱을 공유하는 모든 사용자에게 게시됩니다. 앱의 최신 버전은 편집 사용 권한이 있는 사용자에게만 제공됩니다.

![포털에서 게시](./media/save-publish-app/publish-portal.png)

최신 버전을 게시하려면 **이 버전 게시**를 클릭하거나 누른 다음 **게시** 대화 상자에서 **이 버전 게시**를 클릭하거나 누릅니다.

## <a name="next-steps"></a>다음 단계
* [브라우저나](../../user/run-app-browser.md) [휴대폰](../../user/run-app-client.md)에서 앱을 찾아서 실행 합니다.
* powerapps.com에서 [앱 이름 바꾸기](set-name-tile.md)
* 앱의 여러 버전이 있는 경우 [앱 복원](restore-an-app.md)
