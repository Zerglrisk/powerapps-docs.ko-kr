---
title: 보고 고려 사항 | MicrosoftDocs
ms.custom: ''
ms.date: 09/27/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
- powerapps
ms.assetid: cb1bb002-8300-43bb-ab75-99e7a9c9c35d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: d3600ad3c1f0953ff3aef5786c62afebca43b4c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755054"
---
# <a name="reporting-considerations"></a>보고 고려 사항

모델 기반 앱에는 고객이 신속하게 의사 결정을 하고 고객과 보다 효과적으로 상호 작용하는 데 도움이 되는 비즈니스 데이터를 사용할 수 있는 많은 기능이 있습니다.  사용할 수 있는 기능은 보기, 차트, 대시보드 및 SQL Server Reporting Services 보고서를 포함합니다. 또한 Power BI 기능 [PowerView](https://support.office.com/article/power-view-overview-and-learning-5380e429-3ee0-4be2-97b7-64d7930020b6), [PowerPivot](https://support.office.com/article/power-pivot-overview-and-learning-f9001958-7901-4caa-ad80-028a6d2432ed), [PowerQuery](https://support.office.com/article/power-query-overview-and-learning-ed614c81-4b00-4291-bd3a-55d80767f81d)를 사용하여 자체 서비스 보고서를 손쉽게 구축할 수 있는 Microsoft Excel이 통합되었습니다. 앱 데이터베이스 내에 저장되는 데이터의 양이 계속 증가하면서 BI 전략에 대해 고려하고 대규모 데이터 집합을 보고하고 시각화하기 위한 가장 효과적인 메커니즘을 결정하는 것이 전보다 더 중요해지고 있습니다.  
  
 환경에서는 보고 인프라는 데이터베이스와 공유되고 별도로 유지됩니다. 이 아키텍처에서는 고객이 보고서를 실행하는 데 필요한 리소스를 공유하지만 각 보고서는 고객의 개별 데이터베이스 인스턴스에서 실행됩니다.  뿐만 아니라 비즈니스 목표를 충족하기 위해 실행하고 싶을 때마다 필요한 만큼 많은 보고서를 실행할 수 있습니다.  보고서에 대해서는 시간 제한을 두지 않습니다.  
  
 Common Data Service에 내장된 보고 기능은 더 짧은 기간 동안 데이터 집합에 대한 보고서를 실행할 수 있도록 설계되었습니다. 이를 고려하여 다음과 같은 고정된 설정이 있습니다.  
  
- 보고서와 쿼리는 최대 5분 동안 실행할 수 있습니다. 최대 기간에 도달하면 보고서는 시간 초과되며 사용자에게 메시지가 반환됩니다. 5분의 기간 내에 보고서와 쿼리는 대부분의 운영 보고 요구를 충족하는 상당한 융통성을 제공하는 레코드가 50,000개 이상인 대규모 데이터 집합에 걸쳐 있을 수 있습니다.  
  
- 쿼리 응답을 개선하려면 세부적인 보고서는 많은 레코드 표시를 최소화하는 것이 좋습니다. 이렇게 하려면 적절한 필터링을 적용하여 반환되는 레코드 수를 줄입니다. 집계 또는 요약된 보고서를 만들 때는 보고서에서 집계를 수행하기 위해 세부적인 레코드를 반입하는 대신 쿼리에 집계를 푸시해야 합니다.  이는 Fetch XML 집계를 사용하여 수행할 수 있습니다. <!-- More information: [Use FetchXML aggregation](../developer/use-fetchxml-aggregation.md)  -->
  
- 대시보드에 차트와 표를 표시하는 경우 귀하의 앱으로 행이 50,000개 미만인 데이터 집합을 갖는 쿼리를 실행할 수 있습니다. 행이 50,000개 이상인 대시보드 쿼리를 실행하는 경우 “최대 레코드 한도를 초과했습니다. 레코드 수를 줄이십시오.”라는 메시지가 반환됩니다.  데이터 집합 설정을 사용하면 앱의 최적 성능이 보장됩니다.  
 
  
<a name="BKMK_ReportTips"></a>   
## <a name="tips-and-solutions-for-reporting"></a>보고를 위한 팁과 솔루션  
 일반적으로 조직 대부분의 보고 요구를 충족하기 위해서는 이러한 설정이 적합합니다. 사용자가 이러한 설정을 초과하지 않도록 하고 일반적인 보고서 쿼리 성능을 개선하기 위해서는 다음과 같은 최상의 방법을 고려하십시오.  
  
- 사용자 지정 보고서나 대시보드를 만들 때는 현재 월 또는 분기 같이 결과를 제한하기 위해 보고서에 시간 기반 필터를 추가하여 더 짧은 기간 동안 더 작은 데이터 집합을 쿼리하도록 설계하십시오.  
  
- 따라서 결과를 반환하는 데 필요한 엔터티 수를 제한하는 것이 좋습니다. 그러면 쿼리를 실행하고 결과 집합을 반환하는 데 필요한 시간이 줄어듭니다.  
  
- 세부적인 보고서에 표시되는 레코드 수는 줄이는 것이 좋습니다. 적절한 필터링을 사용하면 시간 초과를 줄이기 위해 쿼리에서 반환되는 레코드 수를 줄일 수 있습니다.  
  
- 집계 또는 요약된 보고서의 경우 SQL Server Reporting Services 보고서에서 집계를 데이터베이스에 푸시하여 세부적인 레코드를 반입하지 않고 집계를 수행하도록 해야 합니다.  
  
- 비즈니스에 적합한 경우 사용자는 기본(기본 제공) 보고서와 대시보드를 실행해야 합니다. 이러한 보고서와 대시보드는 일반적으로 사용자 데이터 집합 당 쿼리를 수행하도록 설계되므로 대부분의 경우 데이터 집합 제한을 초과하지 않습니다.  
  
  사용자가 이러한 설정을 초과하는 보고서를 실행해야 하는 경우 복잡한 보고 요구를 지원하기 위해 다음과 같은 옵션을 검토하는 것이 좋습니다. 두 옵션 모두 데이터 통합 솔루션을 사용하여 보고 작업 부하를 Common Data Service에서 다른 데이터 저장소로 효과적으로 오프로드합니다.  
  
- [어댑터](reporting-considerations.md#BKMK_ThirdPartyAdapt)는 SQL Server Integration Services(SSIS)와 함께 사용되어 귀하의 앱 데이터와의 통합 기능을 확장합니다.  
  
- [추출 변환 로드(ETL) 도구](reporting-considerations.md#BKMK_ETL)는 여러 데이터 소스를 결합하거나 SSIS를 사용하지 않는 경우 데이터 웨어하우스 솔루션으로 데이터를 추출하여 데이터의 분석을 만들기 위한 새로운 도구 집합을 제공합니다. ETL 도구는 데이터를 이동하기 위해 Common Data Service와 연결하는 포괄적인 솔루션을 제공합니다.  
  
> [!IMPORTANT]
>  이러한 도구를 사용할 때는 비업무 시간 동안 데이터를 이동하거나 동기화하는 것이 좋습니다.  
  
 필요한 경우 큰 보고서를 실행하기 위해 특별히 사용되는 데이터의 오프라인 사본 만들기 같이 특정 보고 요구를 위한 솔루션을 제공할 수 있는 많은 Microsoft 파트너가 있습니다.  이러한 파트너는 데이터 통합 도구 사용에 익숙합니다. 추가 정보: [Dynamics 365 파트너 찾기](https://dynamics.microsoft.com/partners/find-a-partner/)  
  
<a name="BKMK_ThirdPartyAdapt"></a>   
## <a name="third-party-adapters-for-ssis"></a>SSIS용 타사 어댑터  
  
-   [Dynamics 365/CRM용 CozyRoc SSIS+ 구성 요소](https://www.cozyroc.com/ssis/dynamics-crm)  
  
-   [Dynamics 365용 KingswaySoft SSIS 통합 도구 키트](https://www.kingswaysoft.com/products/ssis-integration-toolkit-for-microsoft-dynamics-365)  
  
-   [Dynamics 365용 CData SSIS 구성 요소](https://www.cdata.com/ssis/components/)  
  
-   [Dynamics 365용 Team4 SSIS 커넥터](https://www.team4.de/microsoft-dynamics-365-crm/)  
  
<!--    [PragmaticWorks TaskFactory SSIS Source/Destination for Dynamics CRM](https://pragmaticworks.com/Products/Task-Factory/Features/DynamicsCRMSource.aspx)  -->
  
<a name="BKMK_ETL"></a>   
## <a name="etl-tools"></a>ETL 도구  
  
-   [TIBCO Dynamics 365 통합](https://www.tibco.com/solutions/microsoft-dynamics-365-integration)  <br />
  
<!--   [Productivity tools from Informatica](https://community.informatica.com/community/search.jspa?peopleEnabled=true&userID=&containerType=14&container=2002&spotlight=true&resultTypes=solution&q=dynamics+CRM)  -->
  
### <a name="see-also"></a>참조  
 [Report Authoring Extension(SQL Server Data Tools 지원 포함)](https://www.microsoft.com/download/details.aspx?id=45013) <br />
  
 [Excel용 Microsoft Power Query 소개](https://office.microsoft.com/en-ca/excel-help/introduction-to-microsoft-power-query-for-excel-HA104003940.aspx?CTT=5&origin=HA104003813)   <br />
 [Dynamics 365 for Customer Engagement OData 피드 및 파워 쿼리: [레코드]는 무엇입니까?](https://community.dynamics.com/crm/b/survivingcrm/archive/2014/02/16/dynamics-crm-odata-feeds-and-power-query-what-s-the-record.aspx)   <br />
 

