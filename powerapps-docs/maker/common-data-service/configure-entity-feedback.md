---
title: Power Apps에서 피드백을 위해 엔터티 구성 | MicrosoftDocs
description: 엔터티에 대한 피드백을 활성화하는 방법 알아보기
ms.custom: ''
ms.date: 05/18/2018
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
ms.assetid: 5b25cf09-d43b-4165-9eaa-7549f4855e7c
caps.latest.revision: 13
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0ccf81df57754d6b111e3769d45d8398a9907eb2
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861654"
---
# <a name="configure-an-entity-for-feedbackratings"></a>피드백/등급에 대한 엔터티 구성

피드백에 대한 엔터티를 활성화하여 고객 또는 직원이 엔터티 레코드에 대한 피드백을 작성하거나 정의된 범위 내에서 엔터티 레코드를 평가할 수 있도록 합니다.  

이 기능은 일반적으로 포털 또는 설문 조사를 통해 고객의 데이터를 캡처하는 시스템과 함께 사용됩니다. 서비스 또는 제품 만족도에 대한 데이터는 해당 종류의 데이터를 나타내는 엔터티와 함께 적용할 수 있습니다.

피드백은 직원들이 공동 작업에 대한 피드백을 제공하기 위해 사용할 수도 있습니다.

> [!NOTE]
> 다음 단계를 수행하려면 시스템 관리자 또는 시스템 사용자 지정자 보안 역할이나 이와 동급의 권한이 있는지 확인해야 합니다.
  
## <a name="enable-feedback"></a>피드백 활성화  
  
엔터티를 편집하여 **피드백**을 활성화합니다. 추가 정보: [엔터티 편집](edit-entities.md)
  
## <a name="add-a-subgrid-for-feedback-on-the-entity-form"></a>엔터티 양식의 피드백에 대한 하위 표 추가  

기본적으로 피드백을 추가하려는 레코드의 관련 레코드 목록으로 이동해야 합니다. 보다 쉽게 사용자가 피드백을 추가할 수 있도록 피드백을 활성화하려는 엔터티 양식에 피드백 하위 표 추가를 원할 수 있습니다.  

<!-- This is the closest I could find to a topic about adding an subgrid to a form. -->
추가 정보: [하위 표 속성 개요](../model-driven-apps/sub-grid-properties-legacy.md)

## <a name="add-a-rollup-field--to-the-entity-form-to-show-the-ratings"></a>평가를 표시하려면 엔터티 양식에 롤업 필드 추가  

사용을 원하는 엔터티에 대한 평가 계산 방식에 따라 평가를 계산하는 롤업 필드를 만들어 피드백에 사용하려는 엔터티 양식에 추가합니다. 추가 정보: [값을 집계하는 롤업 필드 정의](define-rollup-fields.md)
  
### <a name="see-also"></a>참조  
 [Dynamics 365 레코드에 대한 피드백 또는 평점 제출](/dynamics365/customer-engagement/basics/submit-feedback-ratings)
