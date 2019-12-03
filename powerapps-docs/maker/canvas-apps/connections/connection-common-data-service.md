---
title: Common Data Service에 연결 | Microsoft Docs
description: Common Data Service에 연결 하 고이를 사용 하 여 Power Apps에서 앱을 빌드하는 방법을 알아봅니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2473f445839b774ecc28fe007912511095d9316d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723820"
---
# <a name="connect-to-common-data-service"></a>Common Data Service에 연결

사용자가 해당 데이터를 관리할 수 있도록 Common Data Service에 비즈니스 데이터를 안전 하 게 저장 하 고 Power Apps에서 다양 한 앱을 빌드할 수 있습니다. 또한 Dynamics 365의 전원 자동화, Power BI 및 데이터를 포함 하는 솔루션에 해당 데이터를 통합할 수 있습니다.

기본적으로 Common Data Service 커넥터는 앱의 현재 환경에 있는 데이터에 연결 됩니다. 앱이 다른 환경으로 이동 하는 경우 커넥터는 새 환경의 데이터에 연결 됩니다. 이 동작은 개발에서 테스트로 이동 하기 위한 ALM 프로세스를 따르는 단일 환경 또는 앱을 사용 하는 응용 프로그램에서 효과적으로 작동 합니다.

Common Data Service 커넥터를 사용 하 여 데이터 원본을 추가 하는 경우 환경을 변경한 다음 하나 이상의 엔터티를 선택할 수 있습니다. 기본적으로 앱은 현재 환경의 데이터에 연결 하 고, UI는 엔터티 목록에 대해 **(현재)** 를 표시 합니다.

> [!div class="mx-imgBorder"]
> ![기본 환경](media/connection-common-data-service/common-data-service-connection-change-environment.png)

**변경**을 선택 하는 경우에는 현재 환경 뿐만 아니라 다른 환경을 지정 하 여 데이터를 가져올 수 있습니다.

> [!div class="mx-imgBorder"]
> 다른 환경 ![](media/connection-common-data-service/common-data-service-connection-select-environment.png)

선택한 환경의 이름이 검색 상자 아래에 나타납니다.

> [!div class="mx-imgBorder"]
> 새 환경 ![](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Common Data Service 커넥터는 Dynamics 365 커넥터 보다 더 강력 하 고 기능 패리티에 근접 합니다.

추가 정보: [Common Data Service 이란?](../../common-data-service/data-platform-intro.md)
