---
title: Power Apps에서 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 개요 | MicrosoftDocs
description: 1:N(일대다) 또는 N:1(다대일) 엔터티 관계를 만드는 방법 알아보기
ms.custom: ''
ms.date: 05/27/2018
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
ms.assetid: 52c00707-b2bc-4950-abec-89baefd94f6e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 07e173dff08a10de5354c08d3530605f530e512d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866142"
---
# <a name="create-one-to-many-or-many-to-one-entity-relationships-overview"></a>1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 개요

Common Data Service에서 1:N(일대다) 또는 N:1(다대일) 관계는 두 엔터티가 서로 관련되는 방식을 정의합니다. 
  
사용자 지정 엔터티 관계를 만들려면 먼저 기존 엔터티 관계를 사용하여 요구 사항을 충족하는지 평가합니다. <br />추가 정보: [새 메타데이터를 만들거나 기존 메타데이터를 사용하시겠습니까?](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

1: N(일대다) 또는 n:1(다대일) 관계를 만들고 편집하는 데 사용할 수 있는 두 개의 디자이너가 있습니다.

|디자이너| 설명|
|--|--|
|[Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|쉽게 간소화된 환경을 제공하지만 일부 특수 설정은 사용할 수 없습니다.<br />추가 정보: [Power Apps 포털에서 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-portal.md)|
|솔루션 탐색기|쉽지 않지만 덜 일반적인 요구 사항에 대한 더 많은 유연성을 제공합니다. <br />추가 정보: [솔루션 탐색기를 사용하여 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-solution-explorer.md) |

> [!NOTE]
> 다음을 사용하여 환경에서 새 엔터티 관계를 만들 수도 있습니다.
> - 모델 기반 앱의 경우 양식 편집기 에서 **새 필드**를 선택하고 *조회* 필드를 만듭니다. <br />추가 정보: [양식에 필드 추가](../model-driven-apps/add-field-form.md)
> - 관련 엔터티에 대한 새 조회 필드를 만듭니다. <br />추가 정보: [필드 만들기 및 편집](create-edit-fields.md)
> - 엔터티 관계의 정의가 포함된 솔루션을 가져옵니다. <br />추가 정보: [솔루션 가져오기, 업데이트 및 내보내기](import-update-export-solutions.md)
> - 파워 쿼리를 사용하여 새 엔터티를 만들고 데이터로 채웁니다. <br />추가 정보: [파워 쿼리를 사용하여 Common Data Service의 엔터티에 데이터 추가](data-platform-cds-newentity-pq.md).
> - 개발자는 [메타데이터 서비스 ](../../developer/common-data-service/metadata-services.md)를 사용하여 엔터티 관계를 만들고 업데이트하는 프로그램을 작성할 수 있습니다. <br />추가 정보: [엔터티 관계 메타데이터 사용자 지정](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

이 항목의 정보는 사용할 수 있는 디자이너를 선택하는 데 도움이 됩니다. 

다음 요구 사항 중 하나를 해결해야 하는 경우가 아니면 Power Apps 포털을 사용하여 1: N(일대다) 또는 N:1(다대일) 엔터티 관계를 만들고 편집해야 합니다.

- 필드 매핑 구성
- 모델 기반 앱에 대한 탐색 창 옵션 구성
- 관계 동작 구성
- 상세하게 찾기에서 관계가 숨겨지는지 여부를 정의합니다.
- 계층적 관계 만들기


## <a name="community-tools"></a>커뮤니티 도구

**[엔터티 관계 다이어그램 작성자](https://www.xrmtoolbox.com/plugins/JourneyIntoCRM.XrmToolbox.ERDPlugin/)** 는 XrmToolbox 커뮤니티가 Common Data Service용으로 개발한 도구입니다. 커뮤니티 개발 도구에 대한 자세한 내용은 [Common Data Service용 개발자 도구](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) 항목을 참조하십시오.

> [!NOTE]
> 커뮤니티 도구는 Microsoft의 제품이 아니며 커뮤니티 도구에 대해 지원을 확장하지 않습니다. 도구와 관련된 질문이 있으면 게시자에게 문의하십시오. 추가 정보: [XrmToolBox](https://www.xrmtoolbox.com)

### <a name="see-also"></a>참조

[엔터티 간 관계 만들기 및 편집](create-edit-entity-relationships.md)<br />
[Power Apps 포털에서 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-portal.md)<br />
[솔루션 탐색기를 사용하여 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-solution-explorer.md)<br />
[개발자 설명서: 엔터티 관계 메타데이터 사용자 지정](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[개발자 설명서: 엔터티 관계 자격](/dynamics365/customer-engagement/developer/entity-relationship-eligibility)


