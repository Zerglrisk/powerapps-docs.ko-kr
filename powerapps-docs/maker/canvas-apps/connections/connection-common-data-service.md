---
title: Common Data Service에 연결 | Microsoft Docs
description: Common Data Service에 연결 하 여 PowerApps에서 앱을 빌드하기 위해 사용 하는 방법을 알아봅니다.
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: da68abeec51df102647ea32a17b3d76451f2f1aa
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456750"
---
# <a name="connect-to-common-data-service"></a>Common Data Service에 연결

안전 하 게 Common Data Service에 비즈니스 데이터를 저장 하 고 사용자가 해당 데이터를 관리할 수 있도록 PowerApps에서 다양 한 앱을 빌드할 수 있습니다. 또한 Microsoft Flow, Power BI 및 Dynamics 365 데이터를 포함 하는 솔루션에 해당 데이터를 통합할 수 있습니다.

기본적으로 Common Data Service 커넥터는 앱의 현재 환경에서 데이터에 연결합니다. 다른 환경으로 앱 이동 하면, 커넥터는 새 환경에서 데이터에 연결 합니다. 이 동작은 단일 환경 또는 테스트부터 프로덕션까지 개발에서 이동 하는 ALM 프로세스는 앱을 사용 하 여 앱에 대해 잘 작동 합니다.

Common Data Service 커넥터를 사용 하 여 데이터 원본에 추가 하면 환경을 변경할 수 있으며 하나 이상의 엔터티를 선택 합니다. 기본적으로 앱을 현재 환경에서 데이터에 연결 하 고 UI에 표시 됩니다 **(현재)** 엔터티 목록을 통해.

> [!div class="mx-imgBorder"]
> ![기본 환경](media/connection-common-data-service/common-data-service-connection-change-environment.png)

선택 하는 경우 **변경**를 지정할 수 있습니다 다른 환경 데이터를 끌어오는에서 대신 또는 현재 환경에 추가 합니다.

> [!div class="mx-imgBorder"]
> ![다른 환경](media/connection-common-data-service/common-data-service-connection-select-environment.png)

선택한 환경의 이름을 검색 상자 아래에 나타납니다.

> [!div class="mx-imgBorder"]
> ![새 환경](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Common Data Service 커넥터는 Dynamics 365 커넥터 및 근접 기능 패리티 보다 더 강력 합니다.

자세한 정보는 [Common Data Service란 무엇인가요?](../../common-data-service/data-platform-intro.md)
