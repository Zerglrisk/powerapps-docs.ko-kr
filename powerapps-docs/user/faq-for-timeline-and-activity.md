---
title: 활동 및 타임라인 월에 대한 질문과 대답 | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 08859f70e047d1c53379e8a79f56997d6beedc58
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67457017"
---
# <a name="frequently-asked-questions-about-activities-and-the-timeline-wall"></a>활동 및 타임라인 월에 대한 질문과 대답  

## <a name="is-a-title-required-when-adding-a-new-note"></a>새 메모를 추가할 때 제목이 필요한가요?

아니요. 활동에 메모를 추가할 때 제목 필드는 필수 필드로 표시되지만 필수가 아닙니다. 이 문제는 레거시 Web Client의 알려진 문제입니다.

## <a name="for-an-appointment-when-i-choose-the-option-to-save-as-draft-it-doesnt-show-that-the-appointment-has-been-saved-as-a-draft"></a>약속의 경우, *초안으로 저장* 옵션을 선택해도 약속이 초안으로 저장되었다고 표시되지 않습니다.

약속 레거시 Web Client의 약속을 초안으로 저장할 경우 제목에 약속이 초안으로 저장되었음을 나타내는 **[초안]** 이 표시되지 않습니다.다.

## <a name="can-i-add-activities-to-read-only-records"></a>읽기 전용 레코드에 활동을 추가할 수 있나요?

예. 메모, 전화 통화, 작업 등과 같은 읽기 전용 엔터티에 활동을 추가할 수 있습니다. 

## <a name="are-html-tags-supported-in-notes"></a>HTML 태그가 **메모**에서 지원되나요?

아니요. 레코드 또는 엔터티에 대한 메모 활동을 만들 때 HTML 태그는 지원되지 않습니다. 예를 들어 메모 필드에 `<TAG> </TAG>` 를 추가 하는 경우에는로 `<TAG_XXX="XX"> </TAG>`표시 됩니다.

## <a name="how-can-i-improve-performance-on-timeline-wall"></a>타임라인 월의 성능을 향상시키려면 어떻게 하나요?

타임라인 월 성능은 특정 엔터티 레코드에서 반환하는 데이터의 양을 최적화하여 향상시킬 수 있습니다. 

1.  엔터티 양식을 사용 중인 활동만 표시하도록 구성합니다.  양식 수준에서 이 작업을 수행하여 유용한 활동만 표시할 수 있습니다.  예를 들어, 사례에 작업을 사용하지 않는 경우 작업을 표시하지 않도록 사례 양식의 타임라인 월을 구성할 수 있습니다.
2.  타임라인 월이 표시하는 기본 레코드의 수를 줄입니다.  기본적으로 10을 반환하도록 설정한 경우 레코드 수가 10개보다 많으면 성능 문제가 발생할 수 있습니다.  기본값을 초과하지 않는 것이 좋습니다. 

## <a name="activity-wall-is-not-supported-in-print-preview"></a>활동 월은 인쇄 미리 보기에서 지원되지 않습니다.

Dynamics 365에서 **인쇄 미리 보기** 옵션을 선택하면 사용 가능 목록에 **타임라인 월**이 표시되지 않습니다. **메모**는 표시되지만 작업 또는 이메일은 표시되지 않습니다.





