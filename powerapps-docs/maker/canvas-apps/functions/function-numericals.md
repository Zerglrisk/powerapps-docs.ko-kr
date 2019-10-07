---
title: Abs, Exp, Ln, Power 및 Sqrt 함수 | Microsoft Docs
description: PowerApps에서 Abs, Sqrt 및 기타 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/13/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6e559f482c8ad151eb04057f3178b141150acc7d
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984414"
---
# <a name="abs-exp-ln-power-and-sqrt-functions-in-powerapps"></a>Microsoft PowerApps의 Abs, Exp, Ln, Power 및 Sqrt 함수
절대 값, 자연 로그, 제곱근 및 *e* 또는 지정된 숫자로 거듭제곱했을 때 결과를 계산합니다.

## <a name="description"></a>설명
**Abs** 함수는 해당 인수의 음수가 아닌 값을 반환합니다. 숫자가 음수이면 **Abs** 함수는 해당 양수를 반환합니다.

**Exp** 함수는 해당 인수를 *e*로 거듭제곱한 값을 반환합니다.  초월수 *e*는 2.7182818...로 시작합니다.

**Ln** 함수는 해당 인수의 자연 로그(밑 *e*)를 반환합니다.

**Power** 함수는 숫자를 거듭제곱한 값을 반환합니다.  이 함수는 [ **^** 연산자](operators.md)와 동일합니다.

**Sqrt** 함수는 해당 인수의 양의 제곱근을 계산하여 반환합니다.

단일 숫자를 전달하면 반환 값은 호출된 함수에 따라 단일 결과입니다.  숫자가 포함된 단일 열 [테이블](../working-with-tables.md)을 전달하면 반환 값은 해당 인수 테이블의 각 레코드에 대해 하나의 결과가 있는 단일 열 테이블입니다. 여러 열 테이블이 있는 경우 [테이블 작업](../working-with-tables.md)에 설명된 대로 단일 열 테이블로 만들 수 있습니다.  

인수의 결과가 정의되지 않은 값인 경우 결과는 *빈 값*으로 표시됩니다.  예를 들어 제곱근와 음수 로그가 함께 있을 때 발생할 수 있습니다.

## <a name="syntax"></a>구문
**Abs**( *Number* )<br>**Exp**( *Number* )<br>**Ln**( *Number* )<br>**Sqrt**( *Number* )

* *Number* - 필수 항목입니다. 작동할 숫자입니다.

**Power**( *Base*, *Exponent* )

* *Base* - 필수 항목입니다. 거듭 제곱할 밑 수입니다.
* *Exponent* - 필수 항목입니다. 밑 수를 거듭 제곱하기 위한 지수입니다.

**Abs**( *SingleColumnTable* )<br>**Exp**( *SingleColumnTable* )<br>**Ln**( *SingleColumnTable* )<br>**Sqrt**( *SingleColumnTable* )

* *SingleColumnTable* - 필수 항목입니다. 작동할 숫자의 단일 열 테이블입니다.

## <a name="examples"></a>예
### <a name="single-number"></a>단일 숫자

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Abs( -55 )** |음수 기호 없이 숫자를 반환합니다. |55 |
| **Exp( 2 )** |2로 거듭제곱한 *e* 또는 *e* \* *e*를 반환합니다. |7.389056... |
| **Ln( 100 )** |숫자 100의 자연 로그(밑 *e*)를 반환합니다. |4.605170... |
| **Power( 5, 3 )** |3으로 거듭제곱한 5 또는 5 \* 5 \* 5를 반환합니다. |125 |
| **Sqrt( 9 )** |제곱근했을 때 9가 나오는 숫자를 반환합니다. |3 |

### <a name="single-column-table"></a>단일 열 테이블
이 섹션의 예제에서는 **ValueTable**이라는 [데이터 원본](../working-with-data-sources.md)을 사용하며 이 데이터에는 다음이 포함되어 있습니다.

![](media/function-numericals/values.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Abs(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 절대값을 반환합니다. |<style> img { max-width: none } </style> ![](media/function-numericals/values-abs.png) |
| **Exp(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자를 거듭제곱한 *e*를 반환합니다. |<style> img { max-width: none } </style> ![](media/function-numericals/values-exp.png) |
| **Ln(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 자연 로그를 반환합니다. |<style> img { max-width: none } </style> ![](media/function-numericals/values-ln.png) |
| **Sqrt(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 제곱근을 반환합니다. |![](media/function-numericals/values-sqrt.png) |

### <a name="step-by-step-example"></a>단계별 예제
1. **[텍스트 입력](../controls/control-text-input.md)** 컨트롤을 추가하고 이름을 **Source**로 지정합니다.
2. **Label** 컨트롤을 추가하고 **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>
   **Sqrt( Value( Source.Text ) )**
3. **Source**에 숫자를 입력하고 **레이블** 컨트롤에서 입력한 숫자의 제곱근이 표시되는지 확인합니다.

