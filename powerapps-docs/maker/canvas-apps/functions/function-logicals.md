---
title: And, Or 및 Not 함수 | Microsoft Docs
description: Power Apps의 And, Or 및 Not 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1dae72a288c93b624d232402e32fe0e82cbaaead
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730612"
---
# <a name="and-or-and-not-functions-in-power-apps"></a>Power Apps의 and, Or 및 Not 함수

일반적으로 비교 및 테스트 결과를 조작하는 데 사용되는 부울 논리 함수입니다.

## <a name="description"></a>설명

**And** 함수는 모든 인수가 **true**인 경우 **true**를 반환합니다.

**Or** 함수는 인수 중 **true**인 항목이 있으면 **true**를 반환합니다.

**Not** 함수는 인수가 **false**이면 **true**를 반환하고 인수가 **true**이면 **false**를 반환합니다.

이러한 함수는 Excel에서와 동일한 방식으로 작동 합니다. 또한 Visual Basic 또는 JavaScript 구문을 사용 하 여 다음과 같은 작업을 수행 하는 데 [연산자](operators.md) 를 사용할 수 있습니다.

| 함수 표기법 | Visual Basic 연산자 표기법 | JavaScript 연산자 표기법 |
| -------------|------------|--------|
| **And (x, y)** | **x 및 y** | **x & & y** |
| **Or (x, y)** | **x 또는 y** | **x &#124; &#124; y** |
| **Not (x)** | **X 아님** | **! .x** |

이러한 함수는 논리 값에 작동합니다. 숫자나 문자열을 직접 전달할 수 없습니다. 대신 비교 또는 테스트를 수행 해야 합니다. 예를 들어이 논리 수식 **x > 1** 은 **x** 가 **1**보다 크면 부울 값 **true** 로 평가 됩니다. **X** 가 **1**보다 작은 경우 수식은 **false**로 평가 됩니다.

## <a name="syntax"></a>구문

**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* - 필수 항목입니다.  계산 및 연산의 대상이 되는 논리식입니다.

## <a name="examples"></a>예

이 섹션의 예제에서는 다음과 같은 전역 변수를 사용 합니다.

- ** = ** *false*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** = "Hello World"

앱에서 이러한 전역 변수를 만들려면 [**단추**](../controls/control-button.md) 컨트롤을 삽입 하 고 **onselect** 속성을 다음 수식으로 설정 합니다.

```powerapps-dot
Set( a, false ); Set( b, true ); Set( x, 10 ); Set( y, 100 ); Set( s, "Hello World" )
```

Alt 키를 누른 채 단추를 클릭 하 여 단추를 선택한 다음 [**레이블**](../controls/control-text-box.md) 컨트롤의 **Text** 속성을 다음 표의 첫 번째 열에 있는 수식으로 설정 합니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **And (a, b)** | **A** 와 **b**의 값을 테스트 합니다.  인수 중 하나가 *false*이므로 함수는 *false*를 반환 합니다. | *false* |
| **a 및 b** | 이전 예제와 동일 하며 Visual Basic 표기법을 사용 합니다. | *false* |
| **& & b** | 이전 예제와 동일 하며 JavaScript 표기법을 사용 합니다. | *false* |
| **또는 (a, b)** | **A** 와 **b**의 값을 테스트 합니다. 인수 중 하나가 *true*이므로 함수에서 *true*를 반환 합니다. | *true* |
| **a 또는 b** | 이전 예제와 동일 하며 Visual Basic 표기법을 사용 합니다. | *true* |
| **a &#124; &#124; b** | 이전 예제와 동일 하며 JavaScript 표기법을 사용 합니다. | *true* |
| **아님 (a)** | 의 **값을 테스트 합니다.** 인수가 *false*이므로 함수는 반대의 결과를 반환 합니다. | *true* |
| **아님** | 이전 예제와 동일 하며 Visual Basic 표기법을 사용 합니다. | *true* |
| **! 은** | 이전 예제와 동일 하며 JavaScript 표기법을 사용 합니다. | *true* |
| **Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;20 및&nbsp;&nbsp;IsBlank (&nbsp;s&nbsp;)** | **S** 의 길이가 20 보다 작고 **빈** 값이 아닌 지 테스트 합니다. 길이가 20 보다 작고 값이 비어 있지 않습니다. 따라서 결과는 *true*입니다. | *true* |
| **또는 (&nbsp;Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;10, x&nbsp;<&nbsp;100, y&nbsp;<&nbsp;100&nbsp;)** | **S** 의 길이가 10 보다 적은지, **x** 가 100 보다 작은 지, **y** 가 100 보다 작음을 테스트 합니다. 첫 번째 및 세 번째 인수는 false 이지만 두 번째 인수는 true입니다. 따라서이 함수는 *true*를 반환 합니다. | *true* |
| **Not IsBlank (&nbsp;s&nbsp;)** | **S** 가 *비어*있는지 여부를 테스트 하 여 *false*를 반환 합니다. **Not** 은이 결과와 반대 ( *true*)를 반환 합니다. | *true* |