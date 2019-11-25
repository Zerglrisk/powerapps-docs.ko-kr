---
title: Power Platform 데이터 흐름에서 온-프레미스 데이터 게이트웨이 사용 | MicrosoftDocs
description: Power Platform 데이터 흐름에서 온-프레미스 데이터 게이트웨이를 사용하는 방법 알아보기
ms.custom: ''
ms.date: 08/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4a47f082520b4680c9045209f85c26beb3586875
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752245"
---
# <a name="using-an-on-premises-data-gateway-in-power-platform-dataflows"></a>Power Platform 데이터 흐름에서 온-프레미스 데이터 게이트웨이 사용
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

온-프레미스 데이터 게이트웨이를 설치하여 Power Platform 데이터 흐름과 온-프레미스 SQL Server 데이터베이스 또는 온-프레미스 SharePoint 사이트와 같이 클라우드에 없는 데이터 원본 간에 데이터를 빠르고 안전하게 전송할 수 있습니다.
관리 권한이 있는 모든 게이트웨이를 보고 해당 게이트웨이에 대한 권한 및 연결을 관리할 수 있습니다.

게이트웨이를 사용하면 다음 연결을 통해 온-프레미스 데이터에 연결할 수 있습니다.

-   SharePoint

-   SQL Server

-   Oracle

-   Informix

-   파일 시스템

-   DB2

## <a name="prerequisites"></a>필수 구성 요소

-   PowerApps 계정. 계정이 없으신가요? [30일 무료 평가판에 등록하세요](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps).

-   게이트웨이에 대한 관리 권한. 이러한 권한은 기본적으로 설치한 게이트웨이에 제공됩니다. 관리자는 다른 사람에게 게이트웨이에 대한 권한을 부여할 수 있습니다. 

-   온-프레미스 게이트웨이를 사용하여 온-프레미스 데이터 액세스를 지원하는 라이선스. 자세한 내용은 [올바른 PowerApps 플랜 찾기 페이지](https://powerapps.microsoft.com/pricing/)의 "데이터 및 시스템에 연결" 섹션을 참조하십시오.

-   게이트웨이와 온-프레미스 연결은 사용자의 기본 환경에서만 만들고 사용할 수 있습니다. 추가 정보: [환경 및 Microsoft PowerApps에서 작업](../canvas-apps/working-with-environments.md).

## <a name="install-a-gateway"></a>게이트웨이 설치
1.  [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 왼쪽 탐색 창에서 **게이트웨이**를 선택합니다.

    ![왼쪽 탐색 모음의 게이트웨이](media/nav-pane-gateways.png)

2.  목록에서 게이트웨이를 선택하십시오. 게이트웨이에 대한 관리 권한이 없는 경우 [지금 게이트웨이 설치](https://go.microsoft.com/fwlink/?LinkID=820931)를 선택한 다음 마법사의 지시를 따릅니다.

     ![게이트웨이 설치](media/install-gateway-now.png)

     게이트웨이 설치 방법에 대한 자세한 내용은 [온-프레미스 데이터 게이트웨이 이해](../canvas-apps/gateway-reference.md)를 참조하십시오.

## <a name="use-an-on-premises-data-source-in-a-dataflow"></a>데이터 흐름에 온-프레미스 데이터 원본 사용
1. 데이터 원본 목록에서 온-프레미스 데이터 원본을 선택하십시오.

   ![온-프레미스 데이터 원본 선택](media/on-premises-data-sources.png)

2. 온-프레미스 데이터에 액세스하는 데 사용될 엔터프라이즈 게이트웨이에 대한 연결 세부 사항을 제공하십시오. 게이트웨이 자체를 선택하고 선택된 게이트웨이에 대한 자격 증명을 제공해야 합니다. 자신이 관리자인 게이트웨이만 목록에 나타납니다.

    ![연결 세부 정보 제공](media/connection-creds.png)

지정된 데이터 흐름에 사용된 엔터프라이즈 게이트웨이를 변경하고 데이터 흐름 작성 도구를 사용하여 모든 쿼리에 할당된 게이트웨이를 변경할 수 있습니다.

> [!NOTE]
> 데이터 흐름은 새 게이트웨이를 사용하여 필요한 데이터 원본을 찾거나 만들려고 합니다. 그렇게 할 수 없으면 선택한 게이트웨이에서 필요한 모든 데이터 흐름을 사용할 수 있을 때까지 게이트웨이를 변경할 수 없습니다.


## <a name="view-and-manage-gateway-permissions"></a>게이트웨이 권한 보기 및 관리
1.  [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 왼쪽 탐색 창에서 **게이트웨이**를 선택한 다음 원하는 게이트웨이를 선택하십시오.

2.  게이트웨이에 사용자를 추가하려면 **사용자**를 선택하고 사용자 또는 그룹을 지정한 다음 권한 수준을 지정하십시오.

    -   **사용할 수 있음.** 이 권한이 있는 사용자는 앱 및 흐름에 사용하기 위해 게이트웨이에서 연결을 만들 수 있지만 게이트웨이를 공유할 수는 없습니다. 앱을 실행하지만 공유하지는 않는 사용자에게 이 권한을 사용하십시오.

    -   **사용 + 공유할 수 있음.** 이 권한이 있는 사용자는 앱 및 흐름에 사용하기 위해 게이트웨이에서 연결을 만들 수 있으며 앱을 공유할 때 게이트웨이를 자동으로 공유할 수 있습니다. 다른 사용자 또는 조직과 앱을 공유해야 하는 사용자에게 이 권한을 사용하십시오.

    -   **관리자.** 관리자는 사용자 추가, 권한 설정, 사용 가능한 모든 데이터 원본에 대한 연결 생성 및 게이트웨이 삭제를 포함하여 게이트웨이를 완전히 제어할 수 있습니다.

      **사용할 수 있음**과 **사용 + 공유할 수 있음** 권한 수준에서 사용자가 게이트웨이를 통해 연결할 수 있는 데이터 원본을 선택하십시오.

## <a name="view-and-manage-gateway-connections"></a>게이트웨이 연결 보기 및 관리
1.  *powerapps.com*의 왼쪽 탐색 모음에서 **게이트웨이**를 선택한 다음 원하는 게이트웨이를 선택하십시오.

2.  원하는 작업을 수행합니다. 
    - 세부 사항을 보거나, 설정을 편집하거나, 게이트웨이를 삭제하려면 **연결**을 선택한 다음 연결을 선택하십시오.
    - 연결을 공유하려면 **공유**를 선택한 다음 사용자를 추가하거나 제거하십시오.

      > [!NOTE]
      > SQL Server 연결과 같은 일부 연결 유형만 공유할 수 있습니다. 자세한 내용은 [PowerApps에서 캔버스와 앱 리소스 공유](../canvas-apps/share-app-resources.md)를 참조하십시오. <br />
      >
      > 연결을 관리하는 방법에 대한 자세한 내용은 [PowerApps에서 캔버스와 앱 연결 관리](../canvas-apps/add-manage-connections.md)를 참조하십시오.


## <a name="limitations"></a>제한 사항
엔터프라이즈 게이트웨이 및 데이터 흐름을 사용할 때는 몇 가지 알려진 제한 사항이 있습니다.

-   각 데이터 흐름은 하나의 게이트웨이만 사용할 수 있습니다. 따라서 모든 쿼리는 동일한 게이트웨이를 사용하여 구성해야 합니다.

-   게이트웨이를 변경하면 전체 데이터 흐름에 영향을 줍니다.

-   여러 게이트웨이가 필요한 경우 가장 좋은 방법은 여러 데이터 흐름(각 게이트웨이마다 하나씩)을 작성하고 계산 또는 엔터티 참조 기능을 사용하여 데이터를 통합하는 것입니다.

-   데이터 흐름은 엔터프라이즈 게이트웨이를 통해서만 지원됩니다. 드롭다운 목록 및 설정 화면에서 개인 게이트웨이를 선택할 수 없습니다.

게이트웨이 문제 해결 또는 네트워크의 게이트웨이 서비스 구성에 대한 정보는 [온-프레미스 데이터 게이트웨이 이해](../canvas-apps/gateway-reference.md)를 참조하십시오.

## <a name="next-steps"></a>다음 단계

- [PowerApps에서 데이터 흐름 생성 및 사용](create-and-use-dataflows.md)

- [파워 쿼리를 사용하여 Common Data Service의 엔터티에 데이터 추가](data-platform-cds-newentity-pq.md)

- [데이터 흐름 저장소에 Azure Data Lake Storage Gen2 연결](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)


