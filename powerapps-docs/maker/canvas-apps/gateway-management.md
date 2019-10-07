---
title: 캔버스 앱용 온-프레미스 데이터 게이트웨이 관리 | Microsoft Docs
description: 온-프레미스 데이터 게이트웨이 및 연결 관리
author: archnair
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/30/2016
ms.author: archanan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0f9b9c3104d407baa3cece76159d65c5be61ab79
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983400"
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
1. [Powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 왼쪽 탐색 창에서, **게이트웨이**를 클릭하거나 탭합니다.

    ![왼쪽 탐색 창의 게이트웨이](./media/gateway-management/manage-gateway.png)

2. 게이트웨이에 대한 관리 권한이 없으면, [지금 게이트웨이 설치](http://go.microsoft.com/fwlink/?LinkID=820931)(또는 오른쪽 위 모서리에서 **새 게이트웨이**)를 클릭하거나 탭한 후, 표시되는 마법사의 안내를 따릅니다.

    ![게이트웨이 설치](./media/gateway-management/no-gateway-installed.png)

    게이트웨이 설치 방법에 대한 자세한 내용은 [온-프레미스 데이터 게이트웨이 이해](gateway-reference.md)를 참조하세요.

## <a name="view-and-manage-gateway-permissions"></a>게이트웨이 권한 보기 및 관리
1. [Powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 왼쪽 탐색 창에서, **게이트웨이**를 클릭하거나 탭한 후, 게이트웨이를 클릭하거나 탭합니다.

2. **사용자**를 클릭하거나 탭하고, 사용자나 그룹을 지정한 후 권한 수준을 지정하여 게이트웨이에 사용자를 추가합니다.

   * 다음 **을 사용할 수 있습니다**. 게이트웨이에서 앱 및 흐름에 사용할 연결을 만들 수 있지만 게이트웨이를 공유할 수 없는 사용자입니다. 앱을 실행하지만 공유하지 않는 사용자에 대해 이 권한을 사용합니다.
   * **사용할 수 있는 + 공유**: 앱 및 흐름에 사용 하기 위해 게이트웨이에 대 한 연결을 만들 수 있고 앱을 공유할 때 자동으로 게이트웨이를 공유 하는 사용자입니다. 다른 사용자 또는 조직과 앱을 공유해야 하는 사용자에 대해 이 권한을 사용합니다.
   * **관리자**: 사용자 추가, 권한 설정, 사용 가능한 모든 데이터 원본에 대 한 연결 만들기 및 게이트웨이 삭제를 포함 하 여 게이트웨이에 대 한 모든 권한이 있는 관리자입니다.

**사용 가능** 및 **사용 가능 + 공유** 권한 수준의 경우 사용자가 게이트웨이를 통해 연결할 수 있는 데이터 원본을 선택합니다.

## <a name="view-and-manage-gateway-connections"></a>게이트웨이 연결 보기 및 관리
1. [Powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 왼쪽 탐색 창에서, **게이트웨이**를 클릭하거나 탭한 후, 게이트웨이를 클릭하거나 탭합니다.

2. **연결**을 클릭하거나 탭한 다음, 연결을 클릭하거나 탭하여 해당 세부 정보를 보거나 설정을 편집 또는 삭제합니다.

3. 연결을 공유하려면, **공유**를 클릭하거나 탭한 다음, 사용자를 추가하거나 제거합니다.

    > [!NOTE]
   > SQL Server와 같은 일부 형식의 연결만 공유할 수 있습니다. 자세한 정보는 [앱 리소스 공유](share-app-resources.md)를 참조하세요.

연결을 관리하는 방법에 대한 자세한 내용은 [연결 관리](add-manage-connections.md)를 참조하세요.

## <a name="troubleshooting-and-advanced-configuration"></a>문제 해결 및 고급 구성
게이트웨이 관련 문제 해결 또는 네트워크에 대한 게이트웨이 서비스 구성에 대한 자세한 내용은 [온-프레미스 데이터 게이트웨이 이해](gateway-reference.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계
* [SQL Server](connections/connection-azure-sqldatabase.md) 또는 [SharePoint](connections/connection-sharepoint-online.md)와 같은 온-프레미스 데이터 원본에 연결하는 앱을 만듭니다.
* 온-프레미스 데이터 원본에 연결하는 [앱을 공유](share-app.md)합니다.
