---
title: 포함된 캔버스 앱 공유 | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8c4b56d78b4c7337a9baf442231636e3d35ee27c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884063"
---
# <a name="share-an-embedded-canvas-app"></a>포함된 캔버스 앱 공유
이 항목에서는 이미 만든 포함된 캔버스 앱을 공유하는 방법에 대해 설명합니다.

포함된 캔버스 앱을 만들고 모델 기반 양식에 추가한 후에는 모델 기반 양식에 대한 액세스 권한이 있는 모든 사용자가 캔버스 앱 및 사용 하는 데이터에 액세스할 수 있는지 확인하는 단계를 수행해야 합니다. 다음 지침을 참조하십시오.
-   포함된 캔버스 앱을 조직 또는 보안 그룹이나 특정 사용자의 모든 사람과 공유합니다. 자세한 내용: [앱 공유](../canvas-apps/share-app.md#share-an-app)
-   사용자가 포함된 캔버스 앱에서 사용하는 Common Data Service 엔터티에 대한 적절한 권한이 있는지 확인합니다. 추가 정보: [엔터티 권한 관리](../canvas-apps/share-app.md#manage-entity-permissions)
-   SharePoint 또는 OneDrive 같이 포함된 캔버스 앱에서 사용하는 클라우드 서비스의 데이터에 대해 적절한 권한을 사용자에게 부여해야 합니다. 공유 단계는 Power Apps의 범위를 벗어나는 각 클라우드 서비스에만 적용됩니다.

> [!NOTE]
> 현재, 앱 사용자에게 포함된 또는 독립형 캔버스 앱에 대한 액세스 권한을 부여하기 위해 보안 역할의 **캔버스 앱** 권한을 사용할 수 없습니다.

포함된 캔버스 앱도 솔루션을 인식합니다. 기본적으로 포함된 캔버스 앱은 호스트 모델 기반 양식과 동일한 솔루션에 만들어집니다. 포함된 캔버스 앱을 한 환경에서 다른 환경으로 이동하려면 포함된 캔버스 앱을 다른 구성 요소와 마찬가지로 솔루션의 일부로 내보내고 가져옵니다.

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 추가](embedded-canvas-app-add-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 편집](embedded-canvas-app-edit-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱의 화면 크기 및 방향 사용자 지정](embedded-canvas-app-customize-screen.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 컨트롤의 속성 및 동작](embedded-canvas-app-properties-actions.md) <br />
[포함된 캔버스 앱 작업 지침](embedded-canvas-app-guidelines.md) <br />
[공개 미리 보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 엡을 최신 버전으로 마이그레이션](embedded-canvas-app-migrate-from-preview.md) <br />
