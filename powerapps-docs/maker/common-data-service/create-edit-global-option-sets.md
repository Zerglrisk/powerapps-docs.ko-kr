---
title: Common Data Service용 전역 옵션 집합(선택 목록) 만들기 및 편집 개요 | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: f06b8941-8dca-4601-b965-341cfb6fc3b2
caps.latest.revision: 11
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 746f3b1677df7eb89ce35ef1161a291bfdb7d2be
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865878"
---
# <a name="create-and-edit-global-option-sets-overview"></a>전역 옵션 집합 만들기 또는 편집 개요 

옵션 집합(선택 목록)은 엔터티에 포함될 수 있는 필드 유형으로, 옵션 집합을 정의합니다. 옵션 집합이 양식에 표시될 경우에는 드롭다운 목록 컨트롤을 사용하고, **상세하게 찾기**에 표시될 경우 *선택 목록 컨트롤*을 사용합니다. 때때로 옵션 집합은 개발자의 선택 목록이라고 합니다.  
  
로컬에 정의된 옵션 집합을 사용하거나 다른 옵션 집합 필드에 사용될 수 있는 전역으로 정의된 옵션 집합을 사용하도록 옵션 집합을 정의할 수 있습니다. 

전역 옵션 집합은 둘 이상의 필드에 적용할 수 있는 표준 범주 집합이 있을 경우 유용합니다. 두 개의 다른 옵션 집합을 동일한 값으로 유지하는 것은 힘들므로 동기화되지 않을 경우, 특히 엔터티 필드를 일대다 엔터티 관계로 매핑한 경우에는 오류 메시지가 표시될 수 있습니다. 추가 정보:  [엔터티 필드 매핑](map-entity-fields.md)

> [!NOTE]
> 모든 옵션 집합을 전역 옵션 집합으로 정의하는 경우 전역 옵션 집합의 목록이 증가하고 관리하기가 어려울 수 있습니다. 옵션 집합이 한 위치에서만 사용된다는 것을 알고 있는 경우에는 로컬 옵션 집합을 사용합니다.

전역 옵션 집합을 만들거나 편집하는 데 사용할 수 있는 디자이너는 두 가지가 있습니다.

|디자이너| 설명|
|--|--|
|[Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|쉽게 간소화된 환경을 제공하지만 일부 특수 설정은 사용할 수 없습니다.<br />추가 정보: [옵션 집합 만들기](custom-picklists.md) |
|솔루션 탐색기|쉽지 않지만 덜 일반적인 요구 사항에 대한 더 많은 유연성을 제공합니다. <br />추가 정보: [솔루션 탐색기를 사용하여 Common Data Service에 대한 전역 옵션 집합 만들기 및 편집](create-edit-global-option-sets-solution-explorer.md) |

> [!NOTE]
> 다음을 사용하여 환경에서 전역 옵션 집합을 만들 수도 있습니다.
> - 전역 옵션 집합의 정의가 포함된 솔루션을 가져옵니다.
> - 개발자는 프로그램을 작성하여 만들 수 있습니다. <br />추가 정보: [개발자 설명서: 전역 옵션 집합](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)을 사용자 지정합니다.

이 항목의 정보는 사용할 수 있는 디자이너를 선택하는 데 도움이 됩니다. 

다음 요구 사항 중 하나를 해결 해야 하는 경우가 아니면 [Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 사용하여 전역 옵션 집합을 작업해야 합니다.

- 옵션에 색상 할당
- 옵션의 순서 변경
- Common Data Service 기본 솔루션 이외의 솔루션에 전역 옵션 집합 만들기
- 관리 속성 설정
- 가상 엔터티에 사용되는 속성 설정
- 종속성 보기

## <a name="see-also"></a>참조

[옵션 집합 만들기](custom-picklists.md)<br />
[솔루션 탐색기를 사용하여 Common Data Service에 대한 전역 옵션 집합 만들기 및 편집](create-edit-global-option-sets-solution-explorer.md)<br />
[개발자 설명서: 전역 옵션 집합 사용자 지정](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)
  

 
