---
title: Acos, Acot, Asin, Atan, Atan2, Cos, Cot, Degrees, Pi, Radians, Sin 및 Tan 함수 | Microsoft Docs
description: PowerApps에서 Abs 및 Sqrt 함수에 대한 구문과 예제를 포함한 참조 정보
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
ms.openlocfilehash: b29bce3f1237c6e98376989981f68e207439dc89
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984095"
---
# <a name="acos-acot-asin-atan-atan2-cos-cot-degrees-pi-radians-sin-and-tan-functions-in-powerapps"></a>PowerApps에서 Acos, Acot, Asin, Atan, Atan2, Cos, Cot, Degrees, Pi, Radians, Sin 및 Tan 함수
삼각 값을 계산합니다.

## <a name="description"></a>설명
### <a name="primary-functions"></a>기본 함수
**Cos** 함수는 인수의 코사인을 반환하며, 각도는 라디안 단위로 지정됩니다.

**Cot** 함수는 인수의 코탄젠트를 반환하며, 각도는 라디안 단위로 지정됩니다.

**Sin** 함수는 인수의 사인을 반환하며, 각도는 라디안 단위로 지정됩니다.

**Tan** 함수는 인수의 탄젠트를 반환하며, 각도는 라디안 단위로 지정됩니다.

### <a name="inverse-functions"></a>역 함수
**Acos** 함수는 인수의 아크코사인 또는 역코사인을 반환합니다. 아크코사인은 코사인이 인수인 각도입니다.  반환된 각도는 0(영)~&pi; 범위의 라디안 단위로 지정됩니다.

**Acot** 함수는 인수의 아크탄젠트 또는 역코탄젠트의 주요 값을 반환합니다.  반환된 각도는 0(영)~&pi; 범위의 라디안 단위로 지정됩니다.

**Asin** 함수는 인수의 아크사인 또는 역사인을 반환합니다. 아크사인은 사인이 인수인 각도입니다.  반환된 각도는 -&pi;/2~&pi;/2 범위의 라디안 단위로 지정됩니다.

**Atan** 함수는 인수의 아크탄젠트 또는 역탄젠트를 반환합니다. 아크탄젠트는 탄젠트가 인수인 각도입니다. 반환된 각도는 -&pi;/2~&pi;/2 범위의 라디안 단위로 지정됩니다.

**Atan2** 함수는 인수로 지정된 *x* 및 *y* 좌표의 아크탄젠트 또는 역탄젠트를 반환합니다. 아크탄젠트는 *x*축부터 원점(0, 0)과 좌표(*x*, *y*)가 있는 점을 지나는 선까지의 각도입니다. 각도는 -&pi; 및 &pi; 사이의 라디안으로 지정되며 -&pi;는 제외합니다.  양수 결과는 *x*축에서 시계 반대 방향 각도를 나타내며 음수 결과는 시계 방향의 각도를 나타냅니다.  **Atan2(&nbsp;*a*,&nbsp;*b*&nbsp;)** 는 **Atan(&nbsp;*b*/*a*&nbsp;)** 와 같으며 단, ***a***는 **Atan2** 함수의 0(영)과 같을 수 있습니다.

### <a name="helper-functions"></a>도우미 함수
**Degrees** 함수는 라디안을 각도로 변환합니다.  &pi; 라디안은 180도입니다.

**Pi** 함수는 3.141592...로 시작하는 초월수 &pi;를 반환합니다.

**Radians** 함수는 각도를 라디안으로 변환합니다.  

### <a name="notes"></a>참고
이러한 함수에 단일 숫자를 전달하면 반환 값은 단일 결과입니다.  숫자가 포함된 단일 열 [테이블](../working-with-tables.md)을 전달하면 반환 값은 해당 인수 테이블의 각 레코드에 대해 하나의 결과가 있는 단일 열 테이블입니다. 여러 열 테이블이 있는 경우 [테이블 작업](../working-with-tables.md)에 설명된 대로 단일 열 테이블로 만들 수 있습니다.  

인수의 결과가 정의되지 않은 값인 경우 결과는 *빈 값*으로 표시됩니다.  예를 들어 인수가 범위를 벗어난 역 함수를 사용할 때 이런 일이 발생할 수 있습니다.

## <a name="syntax"></a>구문
### <a name="primary-functions"></a>기본 함수
**Cos**(*Radians*)<br>**Cot**(*Radians*)<br>**Sin**(*Radians*)<br>**Tan**(*Radians*)

* *Radians* - 필수. 연산을 수행할 각도입니다.

**Cos**(*SingleColumnTable*)<br>**Cot**(*SingleColumnTable*)<br>**Sin**(*SingleColumnTable*)<br>**Tan**(*SingleColumnTable*)

* *SingleColumnTable* - 필수 항목입니다. 작동할 각도의 단일 열 테이블입니다.

### <a name="inverse-functions"></a>역 함수
**Acos**(*Number*)<br>**Acot**(*Number*)<br>**Asin**(*Number*)<br>**Atan**(*Number*)

* *Number* - 필수 항목입니다. 작동할 숫자입니다.

**Acos**(*SingleColumnTable*)<br>**Acot**(*SingleColumnTable*)<br>**Asin**(*SingleColumnTable*)<br>**Atan**(*SingleColumnTable*)

* *SingleColumnTable* - 필수 항목입니다. 작동할 숫자의 단일 열 테이블입니다.

**Atan2**(*X*, *Y*)

* *X* - 필수.  *X*축 좌표입니다.
* *Y* - 필수.  *Y*축 좌표입니다.

### <a name="helper-functions"></a>도우미 함수
**Degrees**(*Radians*)

* *Radians* - 필수.  도(degree)로 변환할 라디안 각도입니다.

**Pi**()

**Radians**(*Degrees*)

* *Degrees* - 필수.  라디안으로 변환할 도(degree) 각도입니다.

## <a name="examples"></a>예
### <a name="single-number"></a>단일 숫자

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Cos(&nbsp;1.047197&nbsp;)** |1\.047197라디안 또는 60도의 코사인을 반환합니다. |0.5 |
| **Cot(&nbsp;Pi()/4&nbsp;)** |0\.785398...라디안 또는 45도의 코탄젠트를 반환합니다. |1 |
| **Sin(&nbsp;Pi()/2&nbsp;)** |1\.570796...라디안 또는 90도의 사인을 반환합니다. |1 |
| **Tan(&nbsp;Radians(60)&nbsp;)** |1\.047197...라디안 또는 60도의 탄젠트를 반환합니다. |1.732050... |
| **Acos(&nbsp;0.5&nbsp;)** |0\.5의 아크코사인을 라디안으로 반환합니다. |1.047197... |
| **Acot(&nbsp;1&nbsp;)** |1의 아크코탄젠트를 라디안으로 반환합니다. |0.785398... |
| **Asin(&nbsp;1&nbsp;)** |1의 아크사인을 라디안으로 반환합니다. |1.570796... |
| **Atan(&nbsp;1.732050&nbsp;)** |1\.732050의 아크탄젠트를 라디안으로 반환합니다. |1.047197... |
| **Atan2(&nbsp;5,&nbsp;3&nbsp;)** |*x*축에서 원점(0,0)과 좌표(5,3)를 지나는 선까지 각도(약 31도)의 아크탄젠트를 반환합니다. |0.540419... |
| **Atan2(&nbsp;4,&nbsp;4&nbsp;)** |*x*축에서 원점(0,0)과 좌표(4,4)를 지나는 선까지 각도(정확히 &pi;/4라디안 또는 45도)의 아크탄젠트를 반환합니다. |0.785398... |
| **Degrees(&nbsp;1.047197&nbsp;)** |1\.047197라디안에 해당하는 각도(degree) 수를 반환합니다. |60 |
| **Pi()** |초월수 &pi;를 반환합니다. |3.141592... |
| **Radians(&nbsp;15&nbsp;)** |15도에 해당하는 라디안 수를 반환합니다. |0.261799... |

### <a name="single-column-table"></a>단일 열 테이블
이 섹션의 예제에서는 **ValueTable**이라는 [데이터 원본](../working-with-data-sources.md)을 사용하며 다음 데이터가 포함되어 있습니다.  테이블의 마지막 레코드는 &pi;/2라디안 또는 90도입니다.

![](media/function-trig/values.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Cos(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 코사인을 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-cos.png) |
| **Cot(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 코탄젠트를 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-cot.png) |
| **Sin(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 사인을 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-sin.png) |
| **Tan(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 탄젠트를 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-tan.png) |
| **Acos(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 아크코사인을 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-acos.png) |
| **Acot(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 아크코탄젠트를 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-acot.png) |
| **Asin(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 아크사인을 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-asin.png) |
| **Atan(&nbsp;ValueTable&nbsp;)** |테이블의 각 숫자의 아크탄젠트를 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-atan.png) |
| **Degrees(&nbsp;ValueTable&nbsp;)** |각도를 라디안으로 가정하고 테이블의 각 숫자에 해당하는 각도(degree) 수를 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-degrees.png) |
| **Radians(&nbsp;ValueTable&nbsp;)** |각도를 도(degree)로 가정하고 테이블의 각 숫자에 해당하는 라디안 수를 반환합니다. |<style> img { max-width: none } </style> ![](media/function-trig/values-radians.png) |

