---
title: And, Or 및 Not 함수 | Microsoft Docs
description: PowerApps의 And, Or 및 Not 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4eb020d854549b6dc8878f07ae26390523a1bc03
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66215973"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>PowerApps의 And, Or 및 Not 함수

일반적으로 비교 및 테스트 결과를 조작하는 데 사용되는 부울 논리 함수입니다.

## <a name="description"></a>설명

**And** 함수는 모든 인수가 **true**인 경우 **true**를 반환합니다.

**Or** 함수는 인수 중 **true**인 항목이 있으면 **true**를 반환합니다.

**Not** 함수는 인수가 **false**이면 **true**를 반환하고 인수가 **true**이면 **false**를 반환합니다.

이러한 함수는 Excel에서와 동일한 방식으로 작동 합니다. 사용할 수도 있습니다 [연산자](operators.md) Visual Basic 또는 JavaScript 구문을 사용 하 여 이러한 동일한 작업을 수행 하려면:

| 함수 표기법 | Visual Basic 연산자 표기법 | JavaScript 연산자 표기법 |
| -------------|------------|--------|
| **And( x, y )** | **x 및 y** | **x & & y** |
| **Or( x, y )** | **x 또는 y** | **x &#124;&#124; y** |
| **Not( x )** | **X 없습니다** | **! x** |

이러한 함수는 논리 값에 작동합니다. 전달할 수 없습니다 하 숫자나 문자열로 직접; 대신 비교 또는 테스트 해야 합니다. 예를 들어이 논리 수식 **x > 1** 부울 값으로 평가 **true** 경우 **x** 보다 크면 **1**합니다. 하는 경우 **x** 는 보다 작은 **1**, 수식으로 계산 되 **false**합니다.

## <a name="syntax"></a>구문

**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* - 필수 항목입니다.  계산 및 연산의 대상이 되는 논리식입니다.

## <a name="examples"></a>예

이 섹션의 예에서는 이러한 전역 변수를 사용합니다.

- **a** = *false*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** = "Hello World"

앱에서 이러한 전역 변수를 만들려면 삽입을 [ **단추** ](../controls/control-button.md) 설정 해당 **OnSelect** 속성을 다음이 수식:

```powerapps-dot
Set( a, false ); Set( b, true ); Set( x, 10 ); Set( y, 100 ); Set( s, "Hello World" )
```

(클릭 하 여 하는 동안 Alt 키를 누른), 단추를 선택한 다음 설정 합니다 **텍스트** 의 속성을 [ **레이블** ](../controls/control-text-box.md) 다음 테이블의 첫 번째 열에서 수식에 컨트롤입니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **및 (a, b)** | 값을 테스트 **는** 하 고 **b**합니다.  인수 중 하나인 *false*이므로 반환 *false*합니다. | *false* |
| **And b** | Visual Basic 표기법을 사용 하 여 이전 예제와 동일 합니다. | *false* |
| **a && b** | JavaScript 표기법을 사용 하 여 이전 예제와 동일 합니다. | *false* |
| **Or( a, b )** | 값을 테스트 **는** 하 고 **b**합니다. 인수 중 하나인 *true*이므로 반환 *true*합니다. | *true* |
| **Or b** | Visual Basic 표기법을 사용 하 여 이전 예제와 동일 합니다. | *true* |
| **a &#124;&#124; b** | JavaScript 표기법을 사용 하 여 이전 예제와 동일 합니다. | *true* |
| **Not( a )** | 값을 테스트 **는**합니다. 인수가 *false*이므로 반대 결과 반환 합니다. | *true* |
| **하지는** | Visual Basic 표기법을 사용 하 여 이전 예제와 동일 합니다. | *true* |
| **! a** | JavaScript 표기법을 사용 하 여 이전 예제와 동일 합니다. | *true* |
| **Len(&nbsp;s&nbsp;)&nbsp;<&nbsp;20 And&nbsp;Not&nbsp;IsBlank(&nbsp;s&nbsp;)** | 테스트 여부를 길이의 **s** 20 미만인가 없는 여부는 **빈** 값입니다. 길이가 20 보다 작으면 하는 빈 값입니다. 따라서 결과 *true*합니다. | *true* |
| **Or(&nbsp;Len(&nbsp;s&nbsp;)&nbsp;<&nbsp;10, x&nbsp;<&nbsp;100, y&nbsp;<&nbsp;100&nbsp;)** | 테스트 하는지 여부를 길이의 **s** 10 보다 작으면 여부는 **x** 100 보다 작으면 여부에 관계 없이 **y** 가 100 미만입니다. 첫 번째 및 세 번째 인수는 false 이지만 두 번째 true입니다. 따라서 함수 반환 *true*합니다. | *true* |
| **Not IsBlank(&nbsp;s&nbsp;)** | 테스트 하는지 여부를 **s** 됩니다 *빈*를 반환 하는 *false*합니다. **되지** 이 결과 반대로 반환 *true*합니다. | *true* |