---
title: PowerBI 보고서 만들기 | Microsoft Docs
description: Common Data Service 커넥터를 사용하여 PowerBI Desktop에서 데이터에 연결합니다.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 24972d4c159db30c4abb142adf258a5930c8ace9
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758951"
---
# <a name="create-a-power-bi-report"></a>Power BI 보고서 생성
Common Data Service에서는 Power BI Desktop을 사용하여 데이터에 직접 연결하고 보고서를 생성하여 이를 Power BI에 게시할 수 있습니다. Power BI에서 보고서는 다른 사용자와 공유되고 Power BI 모바일 앱에서 액세스되는 교차 플랫폼으로 대시보드에 사용될 수 있습니다.

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>필수 구성 요소

Common Data Service와 함께 Power BI를 사용하려면 다음이 필요합니다.

* 로컬 컴퓨터에서 실행되는 무료 애플리케이션인 Power BI Desktop을 다운로드하여 설치합니다. [여기](https://powerbi.microsoft.com/desktop/)에서 Power BI Desktop을 다운로드할 수 있습니다.
* 포털에 액세스할 수 있는 메이커 권한 및 데이터에 액세스하기 위한 읽기 권한이 있는 앱 환경에 대한 Common Data Service입니다.

## <a name="finding-your-common-data-service-environment-url"></a>Common Data Service 환경 URL 찾기

1. [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)를 열고 연결하려는 환경을 선택하고 오른쪽 위 모서리에 있는 **설정 기어**를 클릭한 다음 **고급 사용자 지정**을 클릭합니다.

    ![Common Data Service 환경](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "Common Data Service 환경")

2. 새 탭을 열 개발자 리소스 섹션에서 **리소스**를 클릭합니다.

    ![Common Data Service 환경](./media/data-platform-cds-powerbi-connector/CDSEnv2.png "Common Data Service 환경")

3. 새 탭에서 URL의 루트를 복사하면 사용자 환경에 대한 고유한 URL이 됩니다. URL은 **https://yourenvironmentid.crm.dynamics.com/** 형식이며 URL의 나머지 부분을 복사하지 않도록 해야 합니다. PowerBI 보고서를 만들 때 사용할 수 있도록 이 위치를 편리하게 유지합니다.

    > [!div class="mx-imgBorder"] 
    > ![Common Data Service 환경](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "Common Data Service 환경")

## <a name="connecting-to-common-data-service-from-power-bi-desktop"></a>Power BI Desktop에서 Common Data Service에 연결

1. **Power BI Desktop**을 시작하고 시작 화면에서 처음으로 메시지를 받거나 빈 캔버스로 바로 이동하는 경우 두 경우 모두 **데이터 가져오기**를 클릭하고 **자세히**를 선택하여 Power BI Desktop에 사용할 수 있는 데이터 원본 전체 목록을 엽니다.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop")

2. 커넥터 목록에서 **온라인 서비스** 및 **Common Data Service(베타)** 를 클릭합니다. **연결**을 클릭합니다.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop")

3. **Common Data Service 환경 URL**을 **서버 URL** 필드에 붙여 넣고 **확인**을 클릭합니다. 처음에는 PowerApps 및 Common Data Service에 연결하는 데 사용하는 것과 동일한 자격 증명을 사용하여 로그인하라는 메시지가 표시됩니다.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop")

4. 탐색기에는 사용자 환경에서 사용할 수 있는 모든 엔터티가 세 개의 폴더로 그룹화되어 표시됩니다. **Common Data Model** 폴더를 확장합니다.

    * Common Data Model - Common Data Model의 일부로 모든 환경에서 일반적으로 사용되고 사용할 수 있는 표준 엔터티입니다.
    * 사용자 지정 엔터티 - 환경에서 만들거나 가져온 엔터티입니다.
    * 시스템 - Common Data Model 및 사용자 지정 엔터티를 포함하여 사용자 환경의 모든 엔터티가 포함됩니다.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop")

5. **거래처** 엔터티를 선택하여 오른쪽 창에서 데이터 미리 보기를 표시하고 **로드**를 클릭합니다.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport5.png "Power BI Desktop")

6. 이제 엔터티가 보고서에 로드되 고 보고서 작성을 시작하거나 이 프로세스를 반복하여 엔터티를 더 추가할 수 있습니다.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport6.png "Power BI Desktop")

7. 필드 패널에서 **이름** 필드를 클릭하여 보고서 캔버스에 새 시각화를 추가합니다. 이제 이 프로세스를 반복하고 시각화를 변경하여 보고서를 작성할 수 있습니다.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop")


## <a name="using-option-sets"></a>옵션 집합 사용

옵션 집합은 앱 및 흐름에서 사용자에게 값의 드롭다운 목록을 제공하기 위해 엔터티에 사용됩니다. Power BI 커넥터 옵션 집합 필드를 사용하는 경우 고유 값과 표시 값을 모두 표시하는 두 개의 열로 표시됩니다.

예를 들어 ApprovalStatus라는 엔터티에 옵션을 설정한 경우 Power BI에서 두 필드를 볼 수 있습니다.

* ApprovalStatus - 이 옵션 집합의 각 항목에 대한 고유 정수 값을 표시합니다, 이것은 필터를 적용 할 때 도움이 되기 때문에 표시 이름을 나중에 변경할 경우 영향을 받지 않습니다.
* ApprovalStatus_display - 이 항목의 친숙한 표시 이름을 표시하고 테이블 또는 차트에서 옵션을 표시할 때 가장 일반적으로 사용됩니다.

    |ApprovalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|제출됨
    2|검토 중
    3|승인됨
    4|거부됨

## <a name="navigating-relationships"></a>관계 탐색

Common Data Service의 관계는 GUID 필드를 사용하여 두 엔터티 사이에 PowerBI Desktop 내에서 관계를 생성해야 합니다, 이것은 시스템이 생성한 고유 식별자가 어디에 생성 레코드에 대한 관계가 생성되도록 다른 필드에 모호성 또는 중복이 존재할 수 있습니다. Power BI Desktop에서의 관계 관리에 대한 자세한 내용은 [여기](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships)를 참조하십시오.

일부 관계는 자동으로 만들어질 수 있지만 보고서를 만들 때 올바른 관계를 검토하고 확인하는 것도 가능합니다.

* 엔터티의 조회 필드에는 관련 엔터티에 있는 레코드의 GUID가 포함됩니다.
* 관련 엔터티는 예를 들어 Accountid 또는 MyCustomEntityid 등 GUID를 포함하는 "[EntityName]id" 형식의 필드를 갖게 됩니다.
* PowerBI Desktop 관계 관리 기능을 사용하면 조회 필드와 관련 엔터티의 id 필드 간에 새 관계를 만들 수 있습니다.


## <a name="next-steps"></a>다음 단계
* [엔터티의 필드 관리](data-platform-manage-fields.md)
* [엔터티 간 관계 정의](data-platform-entity-lookup.md)


