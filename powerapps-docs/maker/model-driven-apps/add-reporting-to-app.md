---
title: 모델 기반 앱에 보고 추가
ms.custom: ''
ms.date: 06/24/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-reporting-to-your-model-driven-app"></a>모델 기반 앱에 보고 추가

PowerApps 앱은 사용자에게 유용한 비즈니스 정보를 제공하는 보고서를 포함할 수 있습니다. 이러한 보고서는 SQL Server Reporting Services를 기반으로 하며 일반적인 SQL Server Reporting Services 보고서에서 사용할 수 있는 기능과 동일한 기능을 제공합니다.

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "목표 달성률 표준 보고서")

시스템 보고서는 모든 사용자가 사용할 수 있는 반면, 보고서를 만들거나 소유한 개별 사용자는 특정 동료 또는 팀과 공유하거나 조직의 모든 사용자가 실행할 수 있도록 제공합니다. 이 보고서는 Common Data Service 및 Dynamics 365 for Customer Engagement 앱에 대해 독점적인 FetchXML 쿼리를 사용하고 데이터를 검색하여 보고서를 작성합니다. PowerApps 앱에서 작성한 보고서는 Fetch 기반 보고서입니다.

> [!NOTE]
> 태블릿 및 휴대폰과 같은 모바일 장치에서 실행되는 캔버스 앱 또는 모델 기반 앱에서는 보고서 기능이 작동하지 않습니다. 

다음 방법 중 하나로 보고서를 작성할 수 있습니다.

- 보고서 마법사를 사용하는 모델 기반 앱에서. 추가 정보: [보고서 마법사를 사용하여 보고서 만들기 또는 편집](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
<!-- From a model-driven app using an advanced find query. To do this, you build an advanced find query and then select **Download as FetchXML**. Next, from the reports area select **New**, for **Report Type** select **Existing File**, select **Choose File** open the xml file, fill in the required fields, and save the report. More information: [Add a report](/dynamics365/customer-engagement/basics/add-existing-report) -->
- SQL Server Data Tools 및 Report Authoring Extensions를 사용하여 사용자 지정 보고서를 만듭니다. 추가 정보: [보고 및 분석 가이드](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)


## <a name="add-reporting-to-a-unified-interface-app"></a>통합 인터페이스 앱에 보고 추가
사용자가 보고서를 실행, 공유, 작성 및 수정할 수 있도록 Fetch 기반 보고 기능을 앱에 추가할 수 있습니다. 이렇게 하려면 앱의 사이트 맵에 보고서 항목을 추가합니다. 

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인하고 편집을 위해 기존 앱을 엽니다. 
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


이제 앱에 사용자가 권한이 있는 보고서를 보고, 실행하고, 할당하고, 공유하고 편집할 수 있으며 보고서 마법사를 사용하여 새 보고서를 만들 수있는 **보고서** 영역이 표시됩니다. 

> [!div class="mx-imgBorder"] 
> ![](media/report-feature-in-app.png "보고서 보기")

### <a name="see-also"></a>참조
[보고서 실행](/dynamics365/customer-engagement/basics/run-report)
