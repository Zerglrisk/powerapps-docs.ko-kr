---
title: Common Data Service의 날짜 및 시간 필드의 동작 및 형식 | MicrosoftDocs
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: 73d691c7-344e-4c96-8979-c661c290bf81
caps.latest.revision: 47
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cbb327956558e57713040ec8ab1a26d3af78c6c7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711834"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>날짜 및 시간 필드의 동작 및 형식

Common Data Service에서는 많은 표준 엔터티 필드에 날짜 및 시간 데이터 형식이 사용됩니다. 필드가 나타내는 날짜의 유형에 따라 **사용자 현지 시간**, **날짜만** 또는 **표준 시간대 독립** 같은 필드 동작을 선택할 수 있습니다.  
  
<a name="Behavior"></a>   

## <a name="date-and-time-field-behavior-and-format"></a>날짜 및 시간 필드 동작 및 형식  

다음 표에는 날짜 및 시간 동작 및 형식에 대한 정보가 포함되어 있습니다.  
  
|동작|형식|설명|  
|--------------|------------|-------------------------------|  
|**사용자 현지 시간** |**날짜만**<br />- 또는 -<br />**날짜 및 시간**|사용자 지정 날짜 및 시간 필드의 기본 동작입니다.<br /><br />필드 값은 현재 사용자의 현지 시간으로 표시됩니다.<br />웹 서비스에서 이러한 값은 일반적인 UTC 표준 시간대 형식을 사용하여 반환됩니다.<br /><br />기본 동작을 선택하면 이것을 한 번 변경할 수 있습니다. 추가 정보 [사용자 현지 시간 동작 변경](#change-user-local-behavior)|  
|**날짜만**|**날짜만**|시간대 변환 없음.<br /><br />값의 시간 부분은 항상 12:00AM입니다.<br />값의 날짜 부분은 UI 및 웹 서비스에 지정된 대로 저장되고 검색됩니다.|  
|**표준 시간대 독립**|**날짜만**<br />- 또는 -<br />**날짜 및 시간**|시간대 변환 없음.<br /><br />날짜 및 시간 값은 UI 및 웹 서비스에 지정된 대로 저장되고 검색됩니다.|  

## <a name="change-user-local-behavior"></a>사용자 현지 시간 동작 변경:

관리형 솔루션의 게시자가 이를 방지하지 않는 한 기존 사용자 지정 날짜 필드의 동작을 **사용자 현지 시간**에서 **날짜만** 또는 **표준 시간대 독립**으로 변경할 수 있습니다. 이것은 일회성 변경입니다.

필드 동작을 변경하면 필드 동작을 변경한 후 추가하거나 수정한 필드 값에 영향을 미칩니다. 기존 필드 값은 데이터베이스에 UTC 시간대 형식으로 유지됩니다. 기존 필드 값의 동작을 UTC에서 날짜만으로 변경하려면 개발자의 도움을 받아 프로그래밍 방식으로 이를 수행하도록 해야 할 수 있습니다. 추가 정보:  [데이터베이스에 있는 기존 날짜 및 시간 값의 동작 변환](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#convert-behavior-of-existing-date-and-time-values-in-the-database) 

> [!WARNING]
> 기존 날짜 및 시간 필드의 동작을 변경하기 전에 비즈니스 규칙, 워크플로 및 계산 필드 또는 롤업 필드 같은 필드의 모든 종속성을 검토하여 동작 변경 결과로 문제가 발생하지 않도록 해야 합니다. 날짜 및 시간 필드의 동작을 변경한 후에는 변경된 필드에 종속되는 각 비즈니스 규칙, 워크플로, 계산 필드 및 롤업 필드를 열고 정보를 검토하고 저장하여 최신 날짜 및 시간 필드의 동작 및 값을 사용할 수 있도록 해야 합니다. 

### <a name="change-behavior-during-a-solution-import"></a>솔루션 가져오기 중 동작 변경

**사용자 현지 시간** 동작을 사용하여 날짜 필드가 포함된 솔루션을 가져올 때는 동작을 **날짜만** 또는 **표준 시간대 독립**으로 변경하는 옵션이 있을 수 있습니다.  

### <a name="prevent-changing-behavior"></a>동작 변경 방지

관리형 솔루션에서 사용자 지정 날짜 필드를 배포하는 경우 **CanChangeDateTimeBehavior** 관리 속성을 **False**로 설정하여 솔루션을 사용하는 사용자가 동작을 변경 하지 못하게 할 수 있습니다. 자세한 내용은 [필드 관리 속성](set-managed-properties-metadata.md#field-managed-properties)을 참조하십시오.
  
## <a name="use-cases"></a>사용 사례

**날짜만** 및 **표준 시간대 독립** 동작에 대한 다음 사용 사례를 고려하십시오.

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>날짜만의 시나리오: 생일과 기념일

날짜만 동작은 생일이나 기념일 같이 시간과 시간대에 대한 정보가 필요하지 않은 경우 적합합니다. 이 옵션을 선택하면 전세계 모든 앱 사용자에게 정확히 같은 날짜 값만 표시됩니다.  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>표준 시간대 독립의 시나리오: 호텔 체크 인

호텔 체크인 시간 등 표준 시간대 정보가 필요 없을 때 이 동작을 사용할 수 있습니다. 이 옵션을 선택하면 전세계 모든 앱 사용자에게 정확히 같은 날짜와 시간 값이 표시됩니다.  


## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>날짜만 동작에서 지원되지 않는 날짜 및 시간 쿼리 연산자  

다음 날짜 및 시간 관련 쿼리 연산자는 **날짜만** 동작에 유효하지 않습니다. 이러한 연산자 중 하나가 쿼리에 사용되면 잘못된 연산자 예외 오류가 throw됩니다.  
  
- X분 이상 경과  
- X시간 이상 경과  
- 지난 X시간  
- 다음 X시간  

  
### <a name="see-also"></a>참조

[필드 만들기 및 편집](create-edit-fields.md)<br />
[계산 필드를 정의하여 수동 계산 자동화](define-calculated-fields.md)<br />
[필드 관리 속성](set-managed-properties-metadata.md#field-managed-properties)<br />
[관리 속성](solutions-overview.md#managed-properties)

