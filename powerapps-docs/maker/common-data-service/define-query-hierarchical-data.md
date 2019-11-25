---
title: Common Data Service의 계층적 데이터 정의 및 쿼리 | MicrosoftDocs
description: 계층적으로 관련된 데이터를 정의하고 쿼리하는 방법 알아보기
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c829665baf2688c755bdfba7debb19d7b69a1c46
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758683"
---
# <a name="define-and-query-hierarchically-related-data"></a>계층적으로 관련된 데이터를 정의하고 쿼리하기

관련 데이터를 계층적으로 정의 및 쿼리하여 귀중한 비즈니스 통찰력을 얻을 수 있습니다. 계층 구조 모델링 및 가상화 기능을 사용하면 많은 이점이 있습니다.  
  
- 복잡한 계층 구조 정보를 보고 탐색합니다.  
- 계층 구조의 컨텍스트 보기에서 핵심 성과 지표(KPI)를 봅니다.  
- 웹 및 태블릿을 통해 주요 정보를 시각적으로 분석합니다.  
  
일부 표준 엔터티에는 이미 정의된 계층이 있습니다. 사용자 지정 엔터티를 포함하여 다른 엔터티를 계층 구조에 사용할 수 있으며 이에 대한 시각화를 만들 수 있습니다. 

## <a name="define-hierarchical-data"></a>계층적 데이터 정의

Common Data Service에서 계층 구조 데이터 구조는 관련 레코드의 *자체 참조* 일대다(1:N) 관계에서 지원됩니다. 

> [!NOTE]
> *자체 참조*는 엔터티가 자신과 관련되어 있음을 의미합니다. 예를 들어 거래처 엔터티에는 다른 거래처 엔터티 레코드를 사용하는 조회 필드가 있습니다.

자체 참조 일대다(1: N) 관계가 존재할 때 관계 정의에서 **계층적** 옵션을 **예**로 설정할 수 있습니다.

![관계 정의의 계층 설정](media/self-referential-relationship-car-solution-explorer.png)

데이터를 계층 구조로 쿼리하려면 엔터티의 일대다(1:N) 자체 참조 관계를 계층적으로 설정해야 합니다. 이 작업은 솔루션 탐색기를 통해서만 수행할 수 있습니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

계층 구조를 켜려면:  
  
1. [1:N 관계](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships)를 보는 동안 편집하려는 자체 참조 관계를 선택합니다.
2. **관계 정의**에서 **계층**을 **예**로 설정합니다.  
  
> [!NOTE]
> - 일부 기본(1:N) 관계는 사용자 지정할 수 없습니다. 이는 이러한 관계를 계층적으로 설정하는 것이 방지됩니다.  
> - 시스템 자체 참조 관계를 위한 계층적 관계를 지정할 수 있습니다. 여기에는 "contact_master_contact" 관계 같은 시스템 유형의 1:N 자체 참조 관계가 포함됩니다.  

> [!IMPORTANT]
> 자체 참조 관계를 여러 개 가질 수 있지만 엔터티당 하나의 관계만 계층적 관계로 정의할 수 있습니다. 한 번 적용된 설정을 변경하려고 하면 경고가 표시됩니다.
>
> - **비활성화할 때:** 이 관계에 대해 계층 구조 설정을 끄면 이 계층 구조를 사용하는 모든 롤업 정의, 프로세스 및 보기가 작동하지 않습니다. 계속하시겠습니까? 
> - **활성화할 때:** 이 관계에 계층 구조 설정을 사용하면 기존 계층 구조를 사용하는 모든 롤업 정의가 무효화됩니다. 계속하시겠습니까?
>
> 기존 계층 구조에 다른 종속성이 없음을 확신할 수 없는 경우에는 배포에 대한 설명서를 검토하거나 다른 사용자 지정자와 의논하여 기존 계층적 관계가 어떻게 사용되는지 이해해야 합니다.

<a name="BKMK_Querydata"></a> 
  
## <a name="query-hierarchical-data"></a>계층적 데이터 쿼리  

계층적 데이터를 검색하려면 정의된 계층이 없으면 관련 레코드를 반복적으로 쿼리해야 합니다. 정의된 계층이 있는 경우 현재 한 단계에서 관련 데이터를 계층 구조로 쿼리할 수 있습니다. **이하** 및 **이상** 논리를 사용하여 레코드를 쿼리할 수 있습니다. **이하** 및 **이상** 계층적 연산자는 상세하게 찾기 및 워크플로 편집기에 표시됩니다. 이러한 연산자를 사용하는 방법에 대한 자세한 내용은 [워크플로 단계 구성](/flow/configure-workflow-steps#setting-conditions-for-workflow-actions)을 참조하십시오. 상세하기 찾기에 대한 자세한 내용은 [상세하게 찾기 검색 만들기, 편집 또는 저장](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)을 참조하십시오.  

> [!NOTE]
> 개발자는 또한 코드에서 이러한 연산자를 사용할 수 있습니다. 추가 정보: [개발자 설명서: 계층적 데이터 쿼리](/dynamics365/customer-engagement/developer/org-service/query-hierarchical-data)
  
다음 예제에서는 계층 구조를 쿼리하는 시나리오를 보여줍니다.  
  
### <a name="query-account-hierarchy"></a>거래처 계층 구조 쿼리  
  
![거래처 계층 구조의 쿼리 거래처](media/query-accounts.png)  
  
### <a name="query-account-hierarchy-including-related-activities"></a>관련 활동을 포함하는 거래처 계층 구조를 쿼리합니다.  
  
![계정의 관련 작업 쿼리](media/query-account-related-activities.png)  
  
###  <a name="query-account-hierarchy-including-related-opportunities"></a>관련 영업 기회를 포함하는 거래처 계층 구조를 쿼리합니다.  
  
![쿼리 계정의 관련 영업 기회](media/query-account-related-opportunities.png)  
  
## <a name="see-also"></a>참조 
[1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships.md)<br />
[솔루션 탐색기를 사용하여 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-solution-explorer.md)<br />
[모델 기반 앱을 사용하여 계층적 데이터 시각화](visualize-hierarchical-data.md)<br />
[비디오: 계층적 보안 모델링 설정](https://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)<br />
[비디오: 계층 구조 시각화](https://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
