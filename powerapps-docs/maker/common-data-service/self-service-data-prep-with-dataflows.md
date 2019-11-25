---
title: PowerApps에서 데이터 흐름을 통한 셀프 서비스 데이터 준비 | MicrosoftDocs
description: PowerApps에서 데이터 흐름을 사용하여 데이터를 준비하는 방법 알아보기
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
ms.openlocfilehash: 32fb0c402fce458f728b44c63e337fe07b36fd76
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754658"
---
<!--note from editor: I think "dataflows" should be lowercase based on this entry in the Microsoft style guide (scroll down to find dataflows): https://styleguides.azurewebsites.net/Styleguide/Read?id=2696&topicid=42299 -->



# <a name="self-service-data-prep-with-dataflows"></a>데이터 흐름을 통한 셀프 서비스 데이터 준비
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

데이터의 양이 계속 증가함에 따라 해당 데이터를 체계적이고 실행 가능한 정보로 셰이핑해야 하는 문제가 발생합니다. 대량의 데이터를 신속하게 실행 가능한 통찰력으로 전환할 수 있도록 앱, AI 워크로드 또는 분석을 위해 준비된 데이터를 원합니다. PowerApps 포털에서 셀프 서비스 데이터를 준비하면 몇 번의 클릭만으로 데이터를 변환하고 Common Data Service 또는 조직의 Azure Data Lake Storage Gen2 계정에 로드할 수 있습니다.

조직이 서로 다른 소스의 데이터를 통합하고 소비를 준비할 수 있도록 데이터 흐름이 도입되었습니다. 친숙한 셀프 서비스 도구를 사용하여 빅 데이터를 수집, 변환, 통합 및 보강할 수 있는 데이터 흐름을 쉽게 만들 수 있습니다. 데이터 흐름을 만들 때 데이터 원본 연결, ETL(추출, 변환, 로드) 논리 및 결과 데이터를 로드할 대상을 정의합니다. 생성된 데이터 흐름의 새로 고침 일정을 구성하여 실행 빈도를 표시할 수 있습니다. 또한 새로운 모델 중심의 계산 엔진을 사용하면 데이터 흐름 고객에게 데이터 준비 프로세스를 보다 관리가 용이하고 명확하며 덜 성가신 것으로 만들 수 있습니다. 데이터 흐름을 통해 데이터 IT 조직에서 생성 및 감독이 필요하며 완료하는 데 몇 시간 또는 며칠이 걸렸던 작업이 이제 앱 제작자, 비즈니스 분석가 및 보고서 제작자 등 데이터 과학자가 아닌 개인이 클릭 몇 번만으로 처리할 수 있습니다.


데이터 흐름은 엔터티에 데이터를 저장합니다. 엔터티는 테이블에서 데이터베이스에 데이터를 저장하는 방식과 비슷하게 데이터를 저장하는 데 사용되는 레코드 집합입니다. 고객은 사용자 지정 엔터티 스키마를 정의하거나 Common Data Model의 표준 엔터티를 활용할 수 있습니다.
Common Data Model은 비즈니스 및 분석 애플리케이션이 사용할 공유 데이터 언어입니다. Common Data Model 메타데이터 시스템은 Common Data Model에 따라 데이터를 저장하는 PowerApps, Power BI, 일부 Dynamics 365 앱(모델 기반 앱) 및 Azure와 같은 애플리케이션 및 비즈니스 프로세스에서 데이터와 그 의미의 일관성을 유지합니다. 그런 다음 데이터 흐름의 결과 엔터티를 다음 중 하나에 저장할 수 있습니다.

-   **Common Data Service.** PowerApps 및 Microsoft Flow를 사용하여 비즈니스 애플리케이션에서 사용되는 데이터를 안전하게 저장하고 관리할 수 있습니다.

-   **Azure Data Lake Storage Gen2.** Power BI, Azure Data, AI 서비스 또는 레이크에서 데이터를 읽는 사용자 지정 빌드된 LOB(기간 업무) 애플리케이션을 사용하여 조직의 사람들과 협업할 수 있습니다. Azure Data Lake Storage Gen2 계정에 데이터를 로드하는 데이터 흐름은 [Common Data Model 폴더](https://go.microsoft.com/fwlink/?linkid=2045304)에 데이터를 저장합니다. **Common Data Model 폴더**에는 표준화된 형식으로 스키마화된 데이터 및 메타데이터를 포함하여 데이터 교환을 용이하게 하고 조직의 Azure Data Lake Storage 계정에 데이터에 저장된 데이터를 공유 스토리지 계층으로 생성 또는 소비하는 서비스 간의 완벽한 상호 운용성을 가능하게 합니다.

데이터 흐름을 사용하여 to ingest data from a large and growing set of supported on-premises and cloud-based data sources including Excel, Azure SQL 데이터베이스, SharePoint, Azure Data Explorer, Salesforce, Oracle Database 등을 포함하여 점점 증가하는 대규모 지원 온-프레미스 및 클라우드 기반 데이터 원본 세트의 데이터를 수집할 수 있습니다.

데이터 원본을 선택한 후 파워 쿼리 하위 코드/코드 없음 경험을 사용하여 데이터를 변환하고 Common Data Model의 표준 엔터티에 매핑하거나 사용자 지정 엔터티를 만들 수 있습니다. 고급 사용자는 데이터 흐름의 M 언어를 직접 편집하여 수백만의 Power BI Desktop 및 Excel 사용자가 이미 알고 있는 파워 쿼리 환경과 유사하게 데이터 흐름을 완전히 사용자 지정할 수 있습니다.

데이터 흐름을 생성하고 저장한 후에는 클라우드에서 데이터 흐름을 실행해야 합니다.
데이터 흐름을 수동으로 실행하도록 트리거하거나 Power Platform 데이터 흐름 서비스가 이를 실행하도록 빈도를 예약할 수 있습니다. 데이터 흐름이 실행을 완료하면 해당 데이터를 사용할 수 있습니다. 데이터 흐름 데이터를 Common Data Service로 로드하기 위해 PowerApps, Microsoft Flow, Excel 및 Common Data Service 커넥터를 지원하는 기타 모든 애플리케이션에서 Common Data Service 커넥터를 사용할 수 있습니다. 조직의 Azure Data Lake Storage Gen2 계정에 저장된 데이터 흐름에서 가져오려면 Power BI Desktop에서 Power Platform 데이터 흐름 커넥터를 사용하거나 레이크에서 직접 파일에 액세스할 수 있습니다.

## <a name="how-to-use-dataflows"></a>데이터 흐름 사용 방법
이전 섹션에서는 데이터 흐름 기술에 대한 배경 지식을 제공했습니다. 이 섹션에서는 조직에서 데이터 흐름을 사용하는 방법에 대해 설명합니다.

> [!NOTE]
> 데이터 흐름을 사용을 사용하려면 유료 PowerApps 플랜이 있어야 하지만 데이터 흐름 사용에 대한 요금은 별도로 청구되지 않습니다. 

### <a name="load-data-to-common-data-service"></a>Common Data Service에 데이터 로드
데이터 흐름을 사용하여 [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)에 엔터티를 채운 다음, PowerApps 애플리케이션에서 사용할 수 있습니다. 몇 번의 클릭만으로 온라인 및 온-프레미스 소스 데이터 원본의 데이터를 통합할 수 있습니다.

<!--from editor: In the last sentence above, should it change to "...on-premises data sources." ? -->


### <a name="extend-the-common-data-model-for-your-business-needs"></a>비즈니스 요구에 맞게 Common Data Model 확장
Common Data Model을 기반으로 하여 확장하려는 조직의 비즈니스 인텔리전스 전문가는 데이터 흐름을 통해 표준 엔터티를 사용자 지정하거나 새 엔터티를 만들 수 있습니다. 그런 다음 데이터 모델을 사용자 지정하는 이 셀프 서비스 방식을 데이터 흐름과 함께 사용하여 조직에 맞는 Power BI 대시보드를 빌드할 수 있습니다.

### <a name="extend-your-capabilities-with-azure-data-and-ai-services"></a>Azure Data 및 AI 서비스로 기능 확장
Power Platform 데이터 흐름을 조직의 Azure Data Lake Storage Gen2 계정에 데이터 흐름 데이터를 저장하도록 구성할 수 있습니다. 환경이 조직의 데이터 레이크에 연결되면 데이터 과학자와 개발자는 Azure Machine Learning, Azure Databricks, Azure Data Factory 등과 같은 강력한 Azure 제품을 활용할 수 있습니다.

조직의 Azure Data Lake에 상주하는 데이터 흐름을 만드는 방법을 포함하여 Azure Data Lake Storage Gen2 및 데이터 흐름 통합에 대한 자세한 내용은 [데이터 흐름 저장소에 Azure Data Lake Storage Gen2 연결](connect-azure-data-lake-storage-for-dataflow.md)을 참조하십시오.

## <a name="summary-of-self-service-data-prep-for-big-data-in-powerapps"></a>PowerApps의 빅 데이터에 대한 셀프 서비스 데이터 준비 요약
데이터 흐름을 통해 비즈니스 데이터를 보다 효과적으로 제어하고 더욱 빠르게 통찰력을 얻을 수 있는 여러 가지 시나리오와 예가 있습니다. 조직의 다른 사람들이 Common Data Service 또는 Power BI의 Power Platform 데이터 흐름 커넥터를 통해, 또는 조직의 Azure Data Lake Storage Gen2 계정에 있는 데이터 흐름의 **Common Data Service** 폴더에 직접 액세스하여 데이터 흐름을 활용할 수 있습니다. Common Data Model에 의해 정의된 표준 데이터 모델(스키마)을 사용하여 비즈니스 애플리케이션은 엔터티의 스키마에 의존할 수 있으며 데이터 생성 방법 또는 데이터 원본에서 추상화될 수 있습니다. 데이터 흐름이 예약된 실행을 완료하면 데이터를 생성하는 데 몇 개월 이상이 걸리던 것에 비해 매우 짧은 기간에 앱, 흐름 또는 BI 통찰력을 모델링하고 만들 수 있습니다.

Common Data Model의 표준화된 형식을 사용하면 조직의 사람들이 빠르고 쉬운 자동 시각화 및 보고서를 생성하는 앱을 만들 수 있습니다. 여기에는 다음이 포함되지만 이에 국한되지 않습니다.

-   Common Data Model에서 다양한 소스의 데이터를 표준 엔터티로 매핑하여 데이터를 통합하고 알려진 스키마를 활용하여 즉시 사용 가능한 애플리케이션을 구동할 수 있습니다.

-   고유한 사용자 지정 엔터티를 만들어 조직 전체에서 데이터를 통합할 수 있습니다.

-   데이터 흐름 데이터를 활용하는 Power BI 보고서 및 대시보드를 만듭니다.

-   조직의 Azure Data Lake Storage Gen2 계정을 통해 Azure Data 및 AI 서비스와의 통합을 만듭니다.

## <a name="next-steps"></a>다음 단계

이 문서에서는 PowerApps 포털에서 셀프 서비스 데이터 준비에 대한 개요 및 이를 사용할 수 있는 방법을 설명했습니다. 다음 항목에서는 데이터 흐름의 일반적인 사용 시나리오에 대해 자세히 설명합니다.

-   [PowerApps에서 데이터 흐름 만들기 및 사용](https://go.microsoft.com/fwlink/?linkid=2100076)

-   [Common Data Service에서 엔터티에 데이터 추가](https://go.microsoft.com/fwlink/?linkid=2100075)

-   [데이터 흐름 저장소에 Azure Data Lake Storage Gen2 연결](https://go.microsoft.com/fwlink/?linkid=2099973)

-   [온-프레미스 데이터 원본과 함께 데이터 흐름 사용](https://go.microsoft.com/fwlink/?linkid=2100077)

파워 쿼리 및 예약된 새로 고침에 대한 자세한 내용은 다음 문서를 참조하십시오.

-   [Power BI Desktop의 쿼리 개요](/power-bi/desktop-query-overview)

-   [예약된 새로 고침 구성](/power-bi/refresh-scheduled-refresh)

Common Data Model에 대한 자세한 정보는 개요 문서를 읽어 보십시오.

-   [Common Data Model - 개요](/powerapps/common-data-model/overview)

