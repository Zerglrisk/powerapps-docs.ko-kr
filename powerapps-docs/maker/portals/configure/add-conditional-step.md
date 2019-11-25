---
title: 포털에 대한 조건부 단계 유형 구성 | MicrosoftDocs
description: 포털의 조건부 단계 유형을 추가 및 구성하는 방법에 대해 설명합니다.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760727"
---
# <a name="add-a-conditional-step-type"></a>조건부 단계 유형 추가

웹 양식 단계는 단계가 식을 평가해야 함을 나타내는 '조건' 형식일 수 있습니다. 식이 true로 평가되는 경우 다음 단계가 표시 됩니다. 식이 false로 평가되고 '조건이 fail인 경우 다음 단계'가 지정된 경우 해당 단계가 표시됩니다. 현재 엔터티는 식을 평가하는 데 사용되는 대상입니다. 이전 단계의 레코드 원본에 대한 레코드 원본 기본값입니다.

## <a name="attributes"></a>특성

| 이름                         | 설명                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 조건                    | 평가할 조건식                                                                                                                                                                                           |
| 조건이 실패하면 다음 단계 | 다른 모든 유형과 달리 조건부 단계 유형은 두 다음 단계 조회를 가집니다. 조건이 true로 평가되면 기본 다음 단계 조회가 적용됩니다. 이 속성은 조건이 false로 평가되는 경우 다음 단계를 설정합니다. |

다음의 피연산자를 사용할 수 있습니다.

| 피연산자    | 타입                   |
|---------------|------------------------|
| =, ==         | 같음                 |
| !=            | 같지 않음             |
| &gt;          | 보다 큼           |
| &lt;          | 보다 작음              |
| &gt;=         | 보다 크거나 같음 |
| &lt;=         | 보다 작거나 같음    |
| &             | 논리곱                    |
| \|             | 논리합                     |
| 에서 받으세요!             | 제외                    |
| =\*, ==\*, -= | 같음                   |
| !=\*          | 같지 않음               |

## <a name="format"></a>형식

식의 형식은 다음과 같습니다.

\[엔터티 특성 논리 이름\] \[피연산자\] \[값\]

예제:

new\_categorycode = 750101

조건 하나가 다수의 식을 가질 수 있습니다. 괄호를 사용하여 중첩된 식을 그룹화할 수 있습니다. 예:

new\_categorycode = 750101 & gendercode = 2

-   new\_categorycode = 750101 & (gendercode = 2 | gendercode = 3)

-   new\_name = Jane Doe

-   new\_twooptionfield = true

-   new\_twooptionfield = false

### <a name="see-also"></a>참조

[포털 구성](configure-portal.md)  
[엔터티 양식 정의](entity-forms.md)  
[포털에 대한 웹 양식 단계](web-form-steps.md)  
[포럼 불러오기/탭 단계 유형 불러오기](load-form-step.md)  
[리디렉션 단계 유형](add-redirect-step.md)  
[맞춤 JavaScript 추가](add-custom-javascript.md)  

