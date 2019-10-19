---
title: 캔버스 앱용 온-프레미스 데이터 게이트웨이 관리 | Microsoft Docs
description: 온-프레미스 데이터 게이트웨이 및 연결 관리
author: arthiriyer
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2019
ms.author: arthii
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 90a0bd777e808bb3aaab10b249d4fd765fbad654
ms.sourcegitcommit: 6984ce43cc5653ccb957219d2a687907ebb5520c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72560923"
---
# <a name="manage-an-on-premises-data-gateway-in-powerapps"></a>PowerApps의 온-프레미스 데이터 게이트웨이를 관리합니다.

온-프레미스 게이트웨이를 설치하여 PowerApps에 빌드된 캔버스 앱 및 온-프레미스 SQL Server 데이터베이스 또는 온-프레미스 SharePoint 사이트와 같이 클라우드에 없는 데이터 원본 간에 데이터를 빠르고 안전하게 전송합니다. 관리 권한이 있는 모든 게이트웨이를 보고 해당 게이트웨이에 대한 권한과 연결을 관리합니다.

게이트웨이를 사용하여 이러한 연결을 통해 온-프레미스 데이터에 연결할 수 있습니다.

* SharePoint
* SQL Server
* Oracle
* Informix
* Filesystem
* 용

## <a name="prerequisites"></a>필수 조건

* PowerApps에 [등록](../signup-for-powerapps.md)하는 데 사용된 사용자 이름과 암호
* 게이트웨이 대한 관리 권한 설치한 각 게이트웨이에 대해 기본적으로 이 권한을 가지며, 다른 게이트웨이의 관리자가 해당 게이트웨이에 대한 이러한 권한을 사용자에게 부여할 수 있습니다.
* 온-프레미스 게이트웨이를 사용하여 온-프레미스 데이터 액세스를 지원하는 라이선스 자세한 내용은 [가격 책정 페이지](https://powerapps.microsoft.com/pricing/)의 "연결" 섹션을 참조하세요.
* 게이트웨이 및 온-프레미스 연결은 사용자의 [기본 환경](working-with-environments.md)에서만 생성하고 사용할 수 있습니다.

## <a name="install-a-gateway"></a>게이트웨이 설치

게이트웨이를 설치 하려면 [온-프레미스 데이터 게이트웨이 설치](/data-integration/gateway/service-gateway-install)의 단계를 따릅니다. _온-프레미스 데이터 게이트웨이 (개인 모드)_ 를 Power BI에만 사용할 수 있기 때문에 게이트웨이를 표준 모드로 설치 합니다.

## <a name="view-and-manage-gateway-permissions"></a>게이트웨이 권한 보기 및 관리

1. [Powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 왼쪽 탐색 창에서, **게이트웨이**를 클릭하거나 탭한 후, 게이트웨이를 클릭하거나 탭합니다.

2. **사용자**를 클릭하거나 탭하고, 사용자나 그룹을 지정한 후 권한 수준을 지정하여 게이트웨이에 사용자를 추가합니다.

   * **사용 가능**:앱 및 흐름에 사용하기 위해 게이트웨이에 대한 연결을 만들 수 있지만, 해당 게이트웨이를 공유할 수 없는 사용자입니다. 앱을 실행하지만 공유하지 않는 사용자에 대해 이 권한을 사용합니다.
   * **사용 가능 + 공유**: 앱 및 흐름에 사용하기 위해 게이트웨이에 대한 연결을 만들어 앱을 공유할 때 게이트웨이를 자동으로 공유할 수 있는 사용자입니다. 다른 사용자 또는 조직과 앱을 공유해야 하는 사용자에 대해 이 권한을 사용합니다.
   * **관리자**: 사용자 추가, 권한 설정, 모든 사용 가능한 데이터 원본에 대한 연결 만들기 및 게이트웨이 삭제를 포함해 게이트웨이를 완전히 제어할 수 있는 관리자입니다.

**사용 가능** 및 **사용 가능 + 공유** 권한 수준의 경우 사용자가 게이트웨이를 통해 연결할 수 있는 데이터 원본을 선택합니다.

## <a name="view-and-manage-gateway-connections"></a>게이트웨이 연결 보기 및 관리

1. [Powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 왼쪽 탐색 창에서, **게이트웨이**를 클릭하거나 탭한 후, 게이트웨이를 클릭하거나 탭합니다.

2. **연결**을 클릭하거나 탭한 다음, 연결을 클릭하거나 탭하여 해당 세부 정보를 보거나 설정을 편집 또는 삭제합니다.

3. 연결을 공유하려면, **공유**를 클릭하거나 탭한 다음, 사용자를 추가하거나 제거합니다.

    > [!NOTE]
   > SQL Server와 같은 일부 형식의 연결만 공유할 수 있습니다. 자세한 정보는 [앱 리소스 공유](share-app-resources.md)를 참조하세요.

연결을 관리하는 방법에 대한 자세한 내용은 [연결 관리](add-manage-connections.md)를 참조하세요.

## <a name="troubleshooting-and-advanced-configuration"></a>문제 해결 및 고급 구성

게이트웨이와 관련 된 문제를 해결 하는 방법에 대 한 자세한 내용은 [온-프레미스 데이터 게이트웨이 문제 해결](/data-integration/gateway/service-gateway-tshoot)을 참조 하세요. 구성에 대 한 자세한 내용은 [온-프레미스 데이터 게이트웨이 앱 사용](/data-integration/gateway/service-gateway-app)을 참조 하세요.

## <a name="next-steps"></a>다음 단계

* [온-프레미스 데이터 게이트웨이를 설치](/data-integration/gateway/service-gateway-install)합니다.
* [SQL Server](connections/connection-azure-sqldatabase.md) 또는 [SharePoint](connections/connection-sharepoint-online.md)와 같은 온-프레미스 데이터 원본에 연결하는 앱을 만듭니다.
* 온-프레미스 데이터 원본에 연결하는 [앱을 공유](share-app.md)합니다.
