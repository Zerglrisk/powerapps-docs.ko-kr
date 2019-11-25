---
title: Common Data Service의 엔터티 및 메타데이터 | MicrosoftDocs
description: Common Data Service의 엔터티 및 메타데이터에 대해 알아보기
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: 88b18946-474c-4c94-8e4c-27532f930757
caps.latest.revision: 28
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3aeb07c29178570ca17426cca46dd7cbc73a2aca
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706994"
---
# <a name="entities-and-metadata-in-common-data-service"></a>Common Data Service의 엔터티 및 메타데이터

Common Data Service는 애플리케이션에 대한 데이터 모델을 쉽고 빠르게 만들 수 있도록 설계되었습니다. 일반적으로 이 항목에서 소개하는 메타데이터에 대한 세부 정보를 고려해야 합니다. 그러나 Common Data Service를 사용하는 앱의 작동 방식 또는 가능한 사항을 평가하는 방법에 대해 더 자세히 이해하고 싶다면 Common Data Service에서 사용하는 메타데이터를 이해하면 통찰력을 얻을 수 있습니다.

*메타데이터*는 데이터에 대한 데이터를 의미합니다. Common Data Service는 환경에서 사용할 데이터의 정의를 비교적 쉽게 편집할 수 있기 때문에 유연한 플랫폼을 제공합니다. Common Data Service에서 메타데이터는 엔터티의 컬렉션입니다. 엔터티는 데이터베이스에 저장되어 있는 데이터 종류를 설명합니다.  각 엔터티는 데이터베이스 테이블에 대응하고 엔터티 내 각 필드(특성으로도 알려짐)는 해당 테이블 열을 나타냅니다. 엔터티 메타데이터는 만들 수 있는 레코드 종류를 제어하고 여기에 수행할 수 있는 작업 종류입니다. 사용자 지정 도구를 사용하여 엔터티, 필드 및 엔터티 관계를 만들거나 편집할 때 이 메타데이터를 편집하는 것입니다. 
  
사용자가 환경의 데이터로 상호 작용하는 데 사용하는 다른 클라이언트는 메타데이터를 사용자 지정할 때 달라지므로 엔터티 메타데이터가 변경되면 조정됩니다. 하지만 이러한 클라이언트는 표시할 시각적 요소, 적용할 사용자 지정 논리 및 보안을 적용하는 방법을 제어하는 다른 데이터에 따라서도 달라집니다. 이 시스템 데이터는 엔터티에도 저장되지만 엔터티 자체는 사용자 지정에 사용할 수 없습니다.

[엔터티 참조](/powerapps/developer/common-data-service/reference/about-entity-reference)를 검토하여 Common Data Service에 기본적으로 포함되는 표준 엔터티, 특성 및 엔터티 관계에 대해 알아볼 수 있습니다.

> [!TIP]
> 메타데이터를 편집하는 데 사용할 수 있는 디자이너는 메타데이터에 있는 모든 세부 정보를 표시할 수 없습니다. 시스템에서 발견되는 모든 엔터티와 메타데이터 속성을 볼 수 있는 **메타데이터 브라우저**라는 모델 기반 앱을 설치할 수 있습니다. 자세한 내용: [환경에 대한 메타데이터 찾아보기](https://docs.microsoft.com/dynamics365/customer-engagement/developer/browse-your-metadata)
  
<a name="BKMK_CreateNewOrUseExistingMetadata"></a>

## <a name="create-new-metadata-or-use-existing-metadata"></a>새 메타데이터 만들거나 기존 메타데이터를 사용하십니까?

Common Data Service에는 핵심 비즈니스 애플리케이션 기능을 지원하는 여러 표준 엔터티가 포함되어 있습니다. 예를 들어 고객 또는 잠재적인 고객에 대한 데이터는 거래처 또는 연락처 엔터티를 사용하여 저장됩니다.  
  
이러한 각 엔터티에는 시스템에서 해당 엔터티에 대해 저장해야 하는 일반적인 데이터를 나타내는 여러 필드가 포함되어 있습니다.  
  
대부분의 조직의 경우 제공된 목적에 맞게 표준 엔터티와 특성을 사용하면 유용합니다. 
  
솔루션을 설치는 경우 솔루션 개발자가 표준 엔터티와 특성을 활용한다고 가정할 수 있습니다. 시스템 엔터티와 특성을 바꾸는 새 사용자 지정 엔터티를 만들면 사용 가능한 솔루션이 조직에 대해 작동하지 않을 수 있습니다.  
  
이러한 이유로 조직에 맞게 제공된 표준 엔터티, 필드 및 엔터티 관계를 찾아 사용하는 것이 좋습니다. 타당하지 않고 사용자 요구에 맞게 편집할 수 없는 경우 새 엔터티, 필드 및 엔터티 관계를 만들어야 하는지 평가해야 합니다. 

<!--  Can we say this yet? 
    
> [!NOTE]
> The [Common Data Model](/powerapps/common-data-model/overview) will provide a capability to add additional standard entities. 

-->

조직에서 사용하는 명명 규칙에 맞게 엔터티의 표시 이름을 변경할 수 있습니다. 예를 들어 사용자를 위해 *회사*의 거래처 엔터티나 *개인*의 연락처 엔터티의 표시 이름을 변경하는 것은 매우 일반적입니다. 이는 엔터티의 동작을 변경하지 않고 엔터티나 특성에 수행할 수 있습니다. 엔터티 이름을 바꾸는 방법에 대한 자세한 내용은 [엔터티 이름 변경](edit-entities.md#change-the-name-of-an-entity)을 참조하십시오.
  
표준 엔터티, 필드 또는 엔터티 관계는 삭제할 수 없습니다. 시스템 솔루션의 일부로 간주되고 각 조직에 있어야 합니다. 표준 엔터티를 숨기려면 조직의 보안 역할 권한을 변경하여 해당 엔터티에 대한 읽기 권한을 제거합니다. 그러면 응용 프로그램의 대부분에서 엔터티가 제거됩니다. 필요 없는 시스템 필드가 있을 경우 양식 및 이를 사용하는 보기에서 제거합니다. 상세하기 찾기에 표시되지 않도록 필드 및 엔터티 관계 정의의 **검색 가능** 값을 변경합니다. 
  
<a name="BKMK_LimitationsOnMetadata"></a>   

## <a name="limitations-on-creating-metadata-items"></a>메타데이터 항목 만들기에 대한 제한 사항  

만들 수 있는 엔터티 수에 제한이 있습니다. 배포의 사용 중인 **[설정](../model-driven-apps/advanced-navigation.md#settings)** > **관리** > **사용 중인 리소스** 페이지에서 최대 수에 대한 정보를 찾을 수 있습니다. 더 많은 사용자 지정 엔터티가 필요한 경우 기술 지원에 문의하십시오. 최고 한도는 조정할 수 있습니다.  
  
각 엔터티 내 만들 수 있는 필드 수에는 상한값이 있습니다. 이러한 제한은 데이터베이스 테이블의 행에 저장될 수 있는 데이터 양에 기술적인 제한을 기반으로 합니다. 각 필드 유형은 다른 양의 공간을 사용할 수 있기 때문에 특정 수를 제공하는 것이 어렵습니다. 상한값은 엔터티에 대한 모든 필드에 사용되는 총 공간에 따라 달라집니다.  
  
대부분의 사용자는 상한값에 도달하도록 충분한 사용자 지정 필드를 만들지 않지만 엔터티에 수백 개의 사용자 지정 필드를 추가할 예정이라면 이것이 최상의 디자인인지 고려해야 합니다. 추가하려는 모든 필드가 해당 엔터티의 레코드에 대한 속성을 설명합니까? 조직을 사용하는 사용자가 그렇게 많은 필드를 포함하는 양식에서 관리할 수 있다고 생각합니까? 양식에 추가하는 필드 수는 레코드를 편집할 때마다 전송되어야 하는 데이터 양을 증가시키고 시스템 성능에 영향을 줍니다. 사용자 지정 필드를 엔터티에 추가할 때 이러한 요소를 고려해야 합니다.  
  
옵션 집합 필드는 상세하기 찾기를 사용할 때 양식의 드롭다운 컨트롤 또는 선택 컨트롤에 표시되는 옵션 집합을 제공합니다. 환경은 옵션 집합 내에 수천 개의 옵션을 지원할 수 있지만 이를 상한값으로 고려하지 않아야 합니다. 유용성에 관한 연구를 보면 드롭다운 컨트롤에 옵션이 많을 경우 문제가 있는 경우가 많다고 합니다. 옵션 집합 필드를 사용하여 데이터의 범주를 정의합니다. 실제로 데이터의 개별 항목을 나타내는 범주를 선택하기 위해 옵션 집합 필드를 사용하지 마십시오. 예를 들어 가능한 수백 개의 장비 제조업체를 저장하는 옵션 집합 필드를 유지하는 것보다 옵션 집합 대신 각 제조업체에 대한 참조를 저장하고 조회 필드를 사용하는 엔터티를 만들 것을 고려해 보십시오.  
  
## <a name="next-steps"></a>다음 단계 

[엔터티 만들기 또는 편집(레코드 종류)](create-edit-entities.md)<br />
[엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)

