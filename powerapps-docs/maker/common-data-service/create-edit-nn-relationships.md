---
title: Common Data Service에서 다대다 엔터티 관계 만들기 개요 | MicrosoftDocs
description: 다대다 관계를 만드는 방법 알아보기
ms.custom: ''
ms.date: 05/29/2018
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
ms.assetid: 248cecfd-c9e8-430b-b4b0-860669866084
caps.latest.revision: 33
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 90658adac8f04ea131968816a6004b4789ff42e4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757771"
---
# <a name="create-many-to-many-entity-relationships-overview"></a>다대다 엔터티 관계 만들기 개요

일대다(1:N) 엔터티 관계는 레코드 간의 계층 구조를 설정합니다. 다대다(N:N) 관계에는 명시적 계층 구조가 없습니다. 구성할 조회 필드 또는 동작이 없습니다. 다대다 관계를 사용하여 만들어진 레코드는 동일한 수준으로 간주할 수 있으며 관계는 상호적입니다.  
  
다대다 관계의 경우 관계(또는 교차) 엔터티는 엔터티를 연결하는 데이터를 저장합니다. 이 엔터티에는 관련 엔터티 둘 다와의 일대다 엔터티 관계가 있으며 관계를 정의하는 데 필요한 값만 저장합니다. 관계 엔터티에는 사용자 지정 필드를 추가할 수 없으며 사용자 인터페이스에는 표시되지 않습니다. 
  
다대다 관계를 만들려면 관계에 참여하려는 두 엔터티를 선택해야 합니다. 모델 기반 앱의 경우 각 엔터티의 탐색에서 해당 목록을 사용할 수 있는 방법을 결정할 수 있습니다. 이들은 1:N 관계의 기본 엔터티에 사용되는 동일한 옵션입니다. 추가 정보:  [기본 엔터티에 대한 탐색 창 항목](create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)
  
다대다 관계에 모든 엔터티를 사용할 수 있는 것은 아닙니다. 엔터티를 디자이너에서 선택할 수 없는 경우 이 엔터티와 함께 다대다 관계를 새로 만들 수 없습니다. 추가 정보: [개발자 설명서: 엔터티 관계 자격](https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-relationship-eligibility)

1: N(일대다) 또는 n:1(다대일) 관계를 만들고 편집하는 데 사용할 수 있는 두 개의 디자이너가 있습니다.

|디자이너| 설명|
|--|--|
|[PowerApps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|쉽게 간소화된 환경을 제공하지만 일부 특수 설정은 사용할 수 없습니다.<br />추가 정보: [PowerApps 포털을 사용하여 Common Data Service에서 다대다 엔터티 관계 만들기](create-edit-nn-relationships-portal.md)|
|솔루션 탐색기|쉽지 않지만 덜 일반적인 요구 사항에 대한 더 많은 유연성을 제공합니다.<br />추가 정보: [솔루션 탐색기를 사용하여 Common Data Service에서 N:N(다대다) 엔터티 관계 만들기](create-edit-nn-relationships-solution-explorer.md) |

> [!NOTE]
> 다음을 사용하여 환경에서 새 다대다(N:N) 엔터티 관계를 만들 수도 있습니다.
> - 관계의 정의가 포함된 솔루션을 가져옵니다. 추가 정보: [솔루션 가져오기, 업데이트 및 내보내기](import-update-export-solutions.md)
> - 개발자는 [메타데이터 서비스 ](../../developer/common-data-service/metadata-services.md)를 사용하여 엔터티 관계를 만들고 업데이트하는 프로그램을 작성할 수 있습니다. 추가 정보: [개발자 설명서: 엔터티 관계 메타데이터 사용자 지정](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

이 항목의 정보는 사용할 수 있는 디자이너를 선택하는 데 도움이 됩니다. 

다음 요구 사항 중 하나를 해결해야 하는 경우가 아니면 PowerApps 포털을 사용하여 다대다(N:N) 엔터티 관계를 만들고 편집해야 합니다.

- 모델 기반 앱에 대한 탐색 창 옵션을 구성합니다.
- 모델 기반 앱의 상세하게 찾기에서 관계를 숨깁니다.

## <a name="see-also"></a>참조

[엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)<br />
[PowerApps 포털을 사용하여 Common Data Service에서 다대다 엔터티 관계 만들기](create-edit-nn-relationships-portal.md)<br />
[솔루션 탐색기를 사용하여 Common Data Service에서 N:N(다대다) 엔터티 관계 만들기](create-edit-nn-relationships-solution-explorer.md)<br />
[개발자 설명서: 엔터티 관계 메타데이터 사용자 지정](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[개발자 설명서: 엔터티 관계 자격](https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-relationship-eligibility)
