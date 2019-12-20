---
title: Common Data Service란? | Microsoft Docs
description: Common Data Service에 대한 소개, 엔터티, 서버 측 논리, 보안 및 개발자 기능.
author: clwesene
manager: kvivek
ms.service: powerapps
ms.topic: overview
ms.component: cds
ms.date: 06/21/2019
ms.reviewer: matp
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2b5a84179a4d9c6598331a6e728326a2318f9a9a
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883623"
---
# <a name="what-is-common-data-service"></a>Common Data Service란?
Common Data Service를 사용하면 비즈니스 응용 프로그램에서 사용한 데이터를 안전하게 저장하고 관리할 수 있습니다. Common Data Service 내의 데이터는 엔터티 집합 내에 저장됩니다. *엔터티*는 테이블에서 데이터베이스에 데이터를 저장하는 방식과 비슷하게 데이터를 저장하는 데 사용되는 레코드 집합입니다. Common Data Service에는 일반적인 시나리오를 포괄하는 표준 엔터티의 기본 집합이 포함되어 있지만 조직에 특정한 사용자 지정 엔터티를 만들고 파워 쿼리를 사용하여 데이터로 채울 수도 있습니다. 그런 다음 앱 제작자는 Power Apps를 사용하여 이 데이터로 풍부한 애플리케이션을 빌드할 수 있습니다.

![비즈니스 애플리케이션 플랫폼의 개요를 보여주는 스크린샷](./media/data-platform-cds-intro/platform.png "플랫폼 개요")

Common Data Service 계획을 구매하는 방법에 대한 자세한 내용은 [가격 책정 정보](../../administrator/pricing-billing-skus.md)를 참조하십시오.

## <a name="why-use-common-data-service"></a>Common Data Service를 사용하는 이유는 무엇입니까?
Common Data Service 내의 표준 및 사용자 지정 엔터티는 데이터에 대한 보안 및 클라우드 기반 저장소 옵션을 제공합니다. 엔터티를 통해 앱 내에서 사용할 조직의 데이터에 대한 비즈니스 중심의 정의를 만들 수 있습니다. 엔터티가 최선의 선택인지 확실하지 않은 경우 다음과 같은 이점을 고려하십시오.

* **관리 용이** &ndash; 메타데이터와 데이터가 모두 클라우드에 저장됩니다. 저장되는 방법에 대한 세부 사항에 대해 염려할 필요가 없습니다.
* **보안 용이**&ndash; 데이터는 사용자가 액세스 권한을 부여한 경우에만 볼 수 있도록 안전하게 저장됩니다. 역할 기반 보안을 사용하면 조직 내의 여러 사용자에 대해 엔터티에 대한 액세스를 제어할 수 있습니다.
* **Dynamics 365 데이터에 액세스** &ndash; Dynamics 365 애플리케이션의 데이터는 Common Data Service 내에도 저장되어 Dynamics 365 데이터를 활용하는 앱을 빨리 빌드하고 Power Apps를 사용하여 앱을 확장할 수 있습니다.
* **풍부한 메타데이터** &ndash; 데이터 형식 및 관계는 Power Apps 내에서 직접 활용됩니다.
* **논리 및 유효성 검사** &ndash; 데이터 품질을 보장하고 비즈니스 프로세스를 구동하기 위해 계산된 필드, 비즈니스 규칙, 워크플로 및 비즈니스 프로세스 흐름을 정의합니다.
* **생산성 도구** &ndash; 엔터티는 Microsoft Excel용 추가 기능에서 생산성을 높이고 데이터 액세스 가능성을 보장하는 데 사용할 수 있습니다.

## <a name="dynamics-365-and-common-data-service"></a>Dynamics 365 및 Common Data Service

Dynamics 365 Sales, Dynamics 365 Customer Service 또는 Dynamics 365 Talent 등의 Dynamics 365 애플리케이션 또한 Common Data Service를 사용하여 애플리케이션에서 사용하는 데이터를 저장하고 보호합니다. 이렇게 하면 통합이 필요 없이 Dynamics 365 내에서 이미 사용되는 핵심 비즈니스 데이터에 대해 직접 Power Apps 및 Common Data Service를 사용하여 앱을 빌드할 수 있습니다.

* **Dynamics 365 데이터로 앱 빌드** &ndash; Power Apps 내에서 또는 Pro Developer SDK를 사용하여 비즈니스 데이터로 신속하게 앱을 빌드합니다.
* **다시 사용할 수 있는 비즈니스 논리 및 규칙 관리** &ndash; 이미 Dynamics 365 엔터티에서 이미 정의된 규칙 관리 및 논리는 Power Apps에 적용되어 사용자의 데이터 액세스 방법에 관계없이 데이터 일관성을 유지합니다.
* **Dynamics 365 및 Power Apps에서 다시 사용할 수 있는 기술** &ndash; 이전에 Power Apps 또는 Dynamics 365에서 기술을 보유했던 사용자는 이제 새 Common Data Service 플랫폼 전체에서 그러한 기술을 활용할 수 있습니다. 이제 응용 프로그램 전체에서 엔터티, 양식, 차트 등을 만드는 것이 일반적입니다.

    > [!NOTE]
    > Common Data Service에서 사용할 수 있는 Finance and Operations 앱의 비즈니스 데이터를 사용하려면 현재 Finance and Operations 앱에서 [데이터 통합자](/power-platform/admin/data-integrator)를 구성해야 합니다.

## <a name="integrating-data-into-the-common-data-service"></a>데이터를 Common Data Service에 통합

앱을 빌드하는 작업에는 일반적으로 둘 이상의 소스에 있는 데이터가 포함되지만 응용 프로그램 수준에서 데이터를 통합하는 경우도 있으며 이 데이터를 공통 저장소로 결합 하여 앱 구축 환경을 쉽게 만들 수 있고 단일 집합의 데이터를 통해 유지 관리하고 작동하는 논리입니다. Common Data Service를 사용하면 데이터를 여러 소스에서 단일 저장소로 통합하여 Dynamics 365 애플리케이션에서 이미 사용할 수 있는 데이터와 함께 Power Apps, Flow 및 Power BI에서 사용할 수 있습니다.

* **다른 시스템과의 예약 통합** &ndash; 보관되는 다른 시스템 데이터와의 예약 통합은 Power Apps에서 다른 애플리케이션 데이터를 활용할 수 있도록 Common Data Service와 정기적으로 동기화할 수 있습니다.
* **PowerQuery를 사용한 데이터 변환 및 가져오기** &ndash; Common Data Service로 가져올 때 데이터를 변환하는 것은 여러 온라인 데이터 원본에서 Excel과 Power BI 전체에서 사용되는 일반 도구인 PowerQuery를 통해서 할 수 있습니다.
* **한 번 데이터 가져오기** &ndash; Excel 및 CSV 파일의 단순한 가져오기 및 내보내기는 Common Data Service.에 한 번 또는 자주 데이터를 가져오는 데 사용할 수 있습니다.

데이터를 Common Data Service에 통합하는 방법에 대한 자세한 내용은 [파워 쿼리를 사용하여 Common Data Service의 엔터티에 데이터 추가](data-platform-cds-newentity-pq.md)를 참조하십시오.

## <a name="interacting-with-entities"></a>엔터티와의 상호 작용
앱을 개발할 때 표준 엔터티, 사용자 지정 엔터티 또는 둘 다 사용할 수 있습니다. Common Data Service는 기본적으로 표준 엔터티를 제공합니다. 이는 모범 사례에 따라 조직 내에서 가장 일반적인 개념과 시나리오를 캡처하기 위해 설계되었습니다.

![엔터티 목록을 보여 주는 스크린샷.](./media/data-platform-cds-intro/entitylist.png "엔터티 목록")

엔터티의 전체 목록은 [엔터티 참조](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference)를 참조하십시오.

조직에 고유한 정보를 저장하기 위해 하나 이상의 사용자 지정 엔터티를 만들어 표준 엔터티의 기능을 확장할 수 있습니다. 자세한 내용은 [사용자 지정 엔터티 만드는 방법](create-custom-entity.md)을 참조하십시오.

## <a name="logic-and-validation"></a>논리 및 유효성 검사
Common Data Service 내의 엔터티는 다양한 서버측 논리 및 유효성 검사를 활용하여 데이터 품질을 보장하고 엔터티 내에서 데이터를 만들고 사용하는 각 앱의 반복적인 코드를 줄일 수 있습니다.

* **비즈니스 규칙**은 데이터를 만드는 데 사용되는 앱에 관계없이 여러 필드 및 엔터티에 대한 데이터의 유효성을 검사하고 경고 및 오류 메시지를 제공합니다. 자세한 내용은 [비즈니스 규칙 만들기](./data-platform-create-business-rule.md)를 참조하십시오.
* **비즈니스 프로세스 흐름**은 사용자가 데이터를 일관되게 입력하고 매번 동일한 단계를 수행하도록 안내합니다. 비즈니스 프로세스 흐름은 현재 모델 기반 앱에 대해서만 지원됩니다. 자세한 내용은 [비즈니스 프로세스 흐름 개요](/dynamics365/customer-engagement/customize/business-process-flows-overview)를 참조하십시오.
* **워크플로**는 사용자 상호 작용 없이 비즈니스 프로세스를 자동화합니다. 자세한 내용은 [워크플로 개요](/dynamics365/customer-engagement/customize/workflow-processes)를 참조하십시오.
* **코드를 사용하는 비즈니스 논리**는 고급 개발자 시나리오를 지원하여 코드를 통해 응용 프로그램을 직접 확장합니다. 자세한 내용은 [코드를 사용하는 비즈니스 논리 적용](../../developer/common-data-service/apply-business-logic-with-code.md)을 참조하십시오.

## <a name="security"></a>보안
Common Data Service는 효율적인 데이터 액세스 및 공동 작업을 촉진하면서 사용자의 데이터 무결성 및 개인 정보를 보호하는 풍부한 보안 모델을 제공합니다. 사업부, 역할 기반 보안, 레코드 기반 보안 및 필드 기반 보안을 조합하여 사용자가 Common Data Service 환경에서 보유하는 정보에 대한 전체 액세스 권한을 정의할 수 있습니다. 추가 정보: [Common Data Service의 보안](/power-platform/admin/wp-security) 

## <a name="developer-capabilities"></a>개발자 기능
[Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 포털을 통해 사용할 수 있는 기능 외에도 Common Data Service에는 프로그래밍 방식으로 메타데이터 및 데이터에 액세스하여 엔터티와 비즈니스 논리를 만들고, 데이터가 상호 작용할 수 있는 기능이 포함되어 있습니다. 자세한 내용은 [Common Data Service 개발자 개요](../../developer/common-data-service/overview.md)를 참조하십시오.

## <a name="next-steps"></a>다음 단계
Common Data Service 시작 준비:
- [Common Data Service 데이터베이스를 사용하여 캔버스 앱을 만듭니다](../canvas-apps/data-platform-create-app-scratch.md).
- [사용자 지정 엔터티를 만든](create-custom-entity.md) 다음 [엔터티를 사용하는 캔버스 앱을 만듭니다](../canvas-apps/data-platform-create-app.md).
- Common Data Service에서 작성된 [모델 기반 앱을 만듭니다](/powerapps/maker/model-driven-apps/build-first-model-driven-app).
- [파워 쿼리를 사용](./data-platform-cds-newentity-pq.md)하여 온라인 또는 온-프레미스 데이터 원본에 연결하고 Common Data Service에 직접 데이터를 가져옵니다.

## <a name="privacy-notice"></a>개인 정보 취급 방침
Microsoft PowerApps Microsoft Power Apps 공통 데이터 모델을 사용하면 Microsoft는 진단 시스템에서 사용자 지정 엔터티 및 필드 이름을 수집하고 저장합니다. 이 점을 파악하여 고객을 위해 일반적인 데이터 모델을 개선합니다. 앱 작성자가 만드는 엔터티 및 필드 이름은 Microsoft Power Apps 커뮤니티에서 공통적인 시나리오를 이해하고 조직과 관련된 스키마와 같은 서비스의 표준 엔터티 적용 범위에서 차이를 확인하는 데 도움이 됩니다. 이러한 엔터티와 연결된 데이터베이스 테이블의 데이터는 Microsoft에서 액세스하거나 사용하거나 데이터베이스가 프로비전되는 지역 외부에서 복제되지 않습니다. 그러나 사용자 지정 엔터티와 필드 이름은 여러 지역에 걸쳐 복제될 수 있으며 데이터 보존 정책에 따라 삭제됩니다. Microsoft는 [보안 센터](https://www.microsoft.com/trustcenter/Privacy/default.aspx)에서 추가로 설명한 대로 사용자의 개인 정보를 보호하기 위해 최선을 다하고 있습니다.
