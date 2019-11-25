---
title: 모델 기반 앱에 보고 기능 추가
ms.custom: ''
ms.date: 08/16/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: aba6196680d674b8ee42096e340a105b19ac8d07
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752382"
---
# <a name="add-reporting-features-to-your-model-driven-app"></a>모델 기반 앱에 보고 기능 추가

PowerApps 앱에 사용자에게 유용한 비즈니스 정보를 제공하는 보고서를 포함할 수 있습니다. 이러한 보고서는 SQL Server Reporting Services를 기반으로 하며 일반적인 SQL Server Reporting Services 보고서에서 사용할 수 있는 기능과 동일한 기능을 제공합니다.

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "Progress against goals standard report")

시스템 보고서는 모든 사용자가 사용할 수 있는 반면, 보고서를 만들거나 소유한 개별 사용자는 특정 동료 또는 팀과 공유하거나 조직의 모든 사용자가 실행할 수 있도록 제공합니다. 이러한 보고서는 Common Data Service 고유의 FetchXML 쿼리를 사용하며 데이터를 검색하여 보고서를 빌드합니다. PowerApps 앱에서 작성한 보고서는 Fetch 기반 보고서입니다.

> [!NOTE]
> 태블릿 및 휴대폰과 같은 모바일 장치에서 실행되는 캔버스 앱 또는 모델 기반 앱에서는 보고서 기능이 작동하지 않습니다. 

<!-- Reports can be built in either of the following ways.

- From a model-driven app using the report wizard. More information: [Create or edit a report using the Report Wizard](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
- Create custom reports using SQL Server Data Tools and Report Authoring Extensions. More information: [Reporting and Analytics Guide](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)  -->


## <a name="add-reporting-to-a-unified-interface-app"></a>통합 인터페이스 앱에 보고 추가
사용자가 보고서를 실행, 공유, 작성 및 수정할 수 있도록 Fetch 기반 보고 기능을 앱에 추가할 수 있습니다. 이렇게 하려면 앱의 사이트 맵에 보고서 항목을 추가합니다. 

1. [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인하고 편집을 위해 기존 앱을 엽니다. 
2. 앱 디자이너에서 **사이트 맵** 옆의 ![사이트 맵 편집을 위한 연필 아이콘](media/ccf-pencil-icon.png)을 선택합니다. 
3. 사이트 맵 디자이너에서 **추가**를 선택한 다음 **영역**을 선택합니다. 
4. **제목** 상자에서 *보고서* 같은 영역 제목의 이름을 입력합니다. 
5. 이전 단계에서 이름을 지정한 영역을 선택하고 **추가**를 선택하고, **그룹**을 선택한 다음 **제목** 상자에 *보고서*와 같은 그룹 제목의 이름을 입력합니다. 
6. 이전 단계에서 이름을 지정한 그룹을 선택하고 **추가**를 선택한 다음 **하위 영역**을 선택하고 다음 속성을 포함시킵니다. 

   - **유형**. **엔터티**를 선택합니다.
   - **엔터티**. 엔터티 목록에서 **보고서** 엔터티를 선택합니다.  
   - **제목**. *보고서* 같은 설명이 포함된 제목을 입력합니다.

      ![사이트 맵에 보고서 엔터티 추가](media/report-entity-sitemap.png)

7. **저장 후 닫기**를 선택하여 앱 디자이너로 돌아갑니다. 


8. 앱 디자이너에서 **저장**을 선택한 다음 **게시**를 선택합니다.

이제 앱에 사용자가 권한이 있는 보고서를 보고, 실행하고, 할당하고, 공유하고 편집할 수 있으며 보고서 마법사를 사용하여 새 보고서를 만들 수 있는 **보고서** 영역이 표시됩니다. 

> [!div class="mx-imgBorder"] 
> ![](media/report-feature-in-app.png "Report view")

## <a name="options-for-creating-new-reports"></a>새 보고서 만들기 옵션
다음 중 한 가지 방법으로 새 보고서를 만들 수 있습니다.
- 보고서 마법사를 사용합니다. 보고가 활성화된 모델 중심 앱을 열고 보고서 마법사를 실행하여 새 보고서를 만듭니다. 보고서 마법사에서는 드릴스루 보고서 및 상위 N 보고서를 포함하여 테이블 및 차트 보고서를 만들 수 있습니다. 추가 정보: [보고서 마법사를 사용하여 보고서 만들기 또는 편집](../../user/create-report-with-wizard.md) 
- Report Authoring Extension 사용. Visual Studio, SQL Server Data Tools, Report Authoring Extension을 사용하여 가져오기 기반 보고 서비스 보고서를 새로 작성하거나 기존 보고서를 사용자 지정할 수 있습니다. 추가 정보 : [SQL Server Data Tools을 사용하여 새 보고서 작성](/dynamics365/customer-engagement/analytics/create-a-new-report-using-sql-server-data-tools)

## <a name="report-visibility"></a>보고서 표시 영역
거래처 엔터티에 대한 거래처 요약 보고서와 같은 표준 엔터티 보고서는 모든 앱 사용자가 사용할 수 있습니다. 보고서를 담당하는 사용자는 특정 동료 또는 팀과 보고서를 공유할 수 있습니다. 시스템 관리자 및 시스템 사용자 지정자는 조직 전체가 볼 수 있는 보고서를 제공하여 모든 사용자가 사용할 수 있도록 합니다. 보고서를 공유하는 방법에 대한 자세한 내용은 [다른 사용자 및 팀과 보고서 공유](../../user/work-with-reports.md#share-a-report-with-other-users-or-teams)를 참조하십시오. 

## <a name="reports-in-solutions"></a>솔루션의 보고서
보고서는 솔루션에 따라 달라집니다. 솔루션에 보고서를 구성 요소로 추가하면 PowerApps 기능 및 사용자 인터페이스를 확장하는 단일 소프트웨어 단위가 됩니다. 조직에 표시되는 보고서만 솔루션에 추가할 수 있습니다.

조직에서 볼 수 있는 보고서를 찾으려면 보고서 목록에서 모델 기반 앱을 열고 보고서를 선택한 다음 **편집**을 선택합니다. **관리** 탭에서 **볼 수 있는 대상**이 **조직**으로 설정되었는지 확인합니다. 

> [!div class="mx-imgBorder"] 
> ![](media/report-scope.png "Organization level report visibility")

보고서의 스냅숏을 솔루션의 일부로 추가하거나, 가져오거나, 내보낼 수 있습니다. 모델 기반 앱에서 보고서, 하위 보고서, 보고서 범주, 보고서 표시 영역 및 보고서 관련 레코드 종류는 보고서 집합의 구성 요소로 간주됩니다. 덮어쓰지 않는 모드에서 솔루션 업데이트를 가져올 때 보고서 집합의 어느 한 구성 요소라도 사용자 지정된 경우 솔루션에 의한 보고서 업데이트가 무시됩니다.

## <a name="related-topics"></a>관련 항목
[보고서 작업](/powerapps/user/work-with-reports)<br/>
[보고서 마법사를 사용하여 보고서 만들기](/powerapps/user/create-report-with-wizard)<br/>
[PowerApps 외부에서 보고서 추가](/powerapps/user/add-existing-report)<br/>
[보고서의 기본 필터 편집](/powerapps/user/edit-report-filter)<br/>
[보고서 문제 해결](/powerapps/user/troubleshoot-reports)
