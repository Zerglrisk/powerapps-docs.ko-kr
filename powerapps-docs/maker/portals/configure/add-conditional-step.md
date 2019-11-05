---
title: 포털에 대 한 조건부 단계 유형 구성 | MicrosoftDocs
description: 포털에 대 한 조건부 단계 유형을 추가 하 고 구성 하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ec3e568b239bf66c0d4554e244d5afef2d5ef673
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553673"
---
# <a name="add-a-conditional-step-type"></a>조건부 단계 유형 추가

웹 폼 단계는 단계에서 식을 계산 해야 함을 나타내는 ' Condition ' 형식일 수 있습니다. 식이 true로 평가 되 면 다음 단계가 표시 됩니다. 식이 false로 평가 되 고 ' 다음 단계가 실패 하는 경우 '가 지정 된 경우 해당 단계가 표시 됩니다. 현재 엔터티는 식을 계산 하는 데 사용 되는 대상입니다. 레코드 원본의 기본값은 이전 단계의 레코드 원본입니다.

## <a name="attributes"></a>특성

| 이름                         | 설명                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 조건                    | 평가할 조건 식입니다.                                                                                                                                                                                           |
| 조건이 실패 하는 경우 다음 단계 | 다른 모든 것과 달리 조건부 단계 유형에는 두 개의 다음 단계 조회가 있습니다. 조건이 true로 평가 되는 경우 기본 다음 단계 조회가 적용 됩니다. 이 속성은 조건이 false로 평가 되는 다음 단계를 설정 합니다. |

사용 가능한 피연산자는 다음과 같습니다.

| 피연산자    | 유형                   |
|---------------|------------------------|
| =, ==         | 같거나                 |
| !=            | 같지 않음             |
| &gt;          | 보다 큼           |
| &lt;          | 보다 작음              |
| &gt;=         | 크거나 같음 |
| &lt;=         | 작거나 같음    |
| &             | And                    |
| \|             | Or                     |
| !             | Not                    |
| =\*, = =\*,-= | 이와                   |
| ! =\*          | 좋아요 안 함               |

## <a name="format"></a>서식

식의 형식은 다음과 같습니다.

엔터티 특성 논리적 이름\] \[피연산자\] \[값을 \[\]

예 들어

새\_categorycode = 750101

조건에는 여러 식이 있을 수 있습니다. 괄호를 사용 하 여 중첩 식을 그룹화 할 수 있습니다. 예를 들면 다음과 같습니다.

새\_categorycode = 750101 & gendercode = 2

-   새\_categorycode = 750101 & (gendercode = 2 | gendercode = 3)

-   새\_이름 = Jane Doe

-   새\_twooptionfield = true

-   새\_twooptionfield = false

### <a name="see-also"></a>참고 항목

[포털 구성](configure-portal.md)  
[엔터티 양식 정의](entity-forms.md)  
[포털에 대 한 웹 양식 단계](web-form-steps.md)  
[양식 로드/로드 탭 단계 유형](load-form-step.md)  
[단계 유형 리디렉션](add-redirect-step.md)  
[사용자 지정 JavaScript 추가](add-custom-javascript.md)  

