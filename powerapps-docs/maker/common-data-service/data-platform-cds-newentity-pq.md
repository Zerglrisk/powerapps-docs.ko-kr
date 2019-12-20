---
title: 파워 쿼리를 사용하여 Common Data Service에서 엔터티에 데이터 추가 | Microsoft Docs
description: 파워 쿼리를 사용하여 다른 데이터 원본의 Common Data Service의 새 엔터티나 기존 엔터티에 데이터를 추가하는 방법에 대한 단계별 지침입니다.
author: mllopis
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 03/21/2018
ms.author: millopis
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cc5ce204047810704f01562a9a00668e51784769
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2872916"
---
# <a name="add-data-to-an-entity-in-common-data-service-by-using-power-query"></a>파워 쿼리를 사용하여 Common Data Service의 엔터티에 데이터 추가
이 절차에서는 [Common Data Service](data-platform-intro.md)에서 엔터티를 만들고 파워 쿼리를 사용하여 OData 피드의 데이터로 해당 엔터티를 채웁니다. 동일한 기술을 사용하여 이러한 온라인 및 온-프레미스 소스의 데이터를 통합할 수 있습니다.

* SQL Server
* Salesforce
* IBM DB2
* 액세스
* Excel
* 웹 API
* OData 피드
* 텍스트 파일

또한 새 엔터티 또는 기존 엔터티에 로드하기 전에 데이터를 필터링, 변환 및 결합할 수 있습니다.

Power Apps 라이선스가 없는 경우 [무료로 가입](../signup-for-powerapps.md)할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소
이 항목을 수행하려면 엔터티를 만들 수 있는 [환경](../canvas-apps/working-with-environments.md) 으로 전환해야 합니다.

## <a name="specify-the-source-data"></a>원본 데이터 지정

1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인한 다음 왼쪽 가장자리 근처에 있는 **데이터**의 아래쪽 화살표를 클릭하거나 탭합니다.

    ![Power Apps 홈 페이지](./media/data-platform-cds-newentity-pq/sign-in.png)

1. 표시되는 목록에서 **데이터 통합**을 클릭하거나 탭한 다음 창의 오른쪽 위 근처에 있는 **새 프로젝트**를 클릭하거나 탭합니다.

1. 데이터 원본 목록에서 **OData**를 클릭하거나 탭합니다.

    ![OAuth 커넥터 선택](./media/data-platform-cds-newentity-pq/choose-odata.png)

1. **연결 설정**에서 이 URL을 입력하거나 붙여넣고 **다음**을 선택합니다.<br>
`https://services.odata.org/V4/Northwind/Northwind.svc/`

1. 테이블 목록에서 **고객** 확인란을 선택하고 **다음**을 클릭하거나 탭합니다.

    ![고객 테이블을 선택합니다.](./media/data-platform-cds-newentity-pq/select-table.png)

1. (선택 사항) 포함할 열을 선택하거나, 하나 이상의 방법으로 테이블을 변환하거나, 색인나 조건부 열을 추가하거나, 기타 변경 작업을 수행하여 필요에 맞게 스키마를 수정합니다.

1. 오른쪽 아래에서 **다음**을 클릭하거나 탭합니다.

## <a name="specify-the-target-entity"></a>대상 엔터티 지정
1. **부하 설정**에서 **새 엔터티에 로드**를 선택합니다.

    ![새 엔터티의 이름을 지정합니다.](./media/data-platform-cds-newentity-pq/new-entity-name.png)

    새 엔터티에 다른 이름 또는 표시 이름을 지정할 수 있지만 이 자습서를 정확히 따르도록 기본값을 그대로 둡니다.

1. **기본 이름 필드** 목록에서 **ContactName**을 클릭하거나 탭한 후 오른쪽 아래에서 **다음**을 클릭하거나 탭합니다.

    다른 기본 이름 필드를 지정 하거나, 원본 테이블의 다른 열을 만들려는 엔터티의 각 필드 또는 둘 다에 매핑할 수 있습니다. 또한 쿼리 출력의 텍스트 열을 Common Data Service에서 여러 줄 텍스트 또는 단일 행 텍스트로 생성할지 여부도 지정할 수 있습니다. 이 자습서를 정확하게 따르려면 기본 열 매핑을 그대로 둡니다.

1. **로드 상태**가 **완료**되면 오른쪽 아래에서 **완료**를 선택합니다.

1. **데이터**(왼쪽 가장자리 근처)에서 **엔터티**를 선택하여 데이터베이스의 엔터티 목록을 표시합니다.

    OData 피드에서 만든 **고객** 엔터티가 사용자 지정 엔터티로 나타납니다.

    ![표준 및 사용자 지정 엔터티 목록](./media/data-platform-cds-newentity-pq/entity-list.png)

> [!WARNING]
> 파워 쿼리를 사용하여 기존 엔터티에 데이터를 추가하는 경우 해당 엔터티의 모든 데이터를 덮어쓰게 됩니다.

**기존 엔터티에 로드**를 선택하는 경우 **고객** 테이블에서 데이터를 추가할 엔터티를 지정할 수 있습니다. 예를 들어 Common Data Service와 함께 제공되는 **거래처** 엔터티에 데이터를 추가할 수 있습니다. **원본 열**에서 **고객** 테이블의 **ContactName** 열에 있는 데이터를 **거래처** 엔터티의 **이름** 열에 추가하도록 지정할 수 있습니다.

![새 엔터티의 이름을 지정합니다.](./media/data-platform-cds-newentity-pq/existing-entity.png)

이 기능에 대해 기쁘게 생각하며 사용자 의견을 들을 수 있길 기대하고 있습니다. 이 기능에 대해 [귀하의 제안 및 피드백을 보내주십시오](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)!

[사용 권한에 대한 오류 메시지](data-platform-cds-newentity-troubleshooting-mashup.md)가 나타나면 관리자에 게 문의하십시오.

> [!WARNING]
> 이 기능을 사용하여 로드할 수 있는 실행 및 프로젝트당 50만 행의 제한이 있습니다.
