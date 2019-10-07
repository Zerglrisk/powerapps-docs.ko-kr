---
title: Len 함수 | Microsoft Docs
description: PowerApps에서 Len 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 967d83286cd179177cfbb5558f1fc3484a332875
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984600"
---
# <a name="len-function-in-powerapps"></a>PowerApps의 Len 함수
텍스트 문자열의 길이를 반환합니다.

## <a name="description"></a>설명
단일 문자열을 인수로 지정하는 경우 반환 값은 숫자로 표현된 길이입니다.  문자열이 포함된 단일 열 [테이블](../working-with-tables.md)을 지정하면, 반환 값은 각 문자열의 길이가 포함된 단일 열 테이블입니다. 여러 열 테이블이 있는 경우 [테이블 작업](../working-with-tables.md)에 설명된 대로 단일 열 테이블로 만들 수 있습니다.

[빈](function-isblank-isempty.md) 문자열을 지정 하는 경우 **Len** 은 0을 반환 합니다.

## <a name="syntax"></a>구문
**Len**( *String* )

* *String* - 필수 항목이며, 측정할 문자열입니다.

**Len**( *SingleColumnTable* )

* *SingleColumnTable* - 필수 항목입니다. 측정할 문자열의 단일 열 테이블입니다.

## <a name="examples"></a>예
### <a name="single-string"></a>단일 문자열
이 섹션의 예제에서 [데이터 원본](../working-with-data-sources.md)은 이름이 **Author**이고 문자열 “E. E. Cummings" 문자열을 포함합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Len( Author.Text )** |**Author** 제어에서 문자열의 길이를 측정합니다. |14 |
| **Len( “” )** |빈 문자열의 길이를 측정합니다. |0 |

### <a name="single-column-table"></a>단일 열 테이블
이 섹션의 첫 번째 예제의 경우 데이터 원본은 이름이 **People**이며 다음 데이터를 포함합니다.

![](media/function-len/people-table.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Len( ShowColumns(&nbsp;People,&nbsp;“Address”&nbsp;) )** |**People** 테이블의 **Address** [열](../working-with-tables.md#columns)에서:<br><ul><li>각 문자열의 길이를 측정합니다.</li><li>각 문자열의 길이를 포함하는 단일 열 테이블을 반환합니다.</li> |<style> img { max-width: none } </style> ![](media/function-len/people-table-len.png) |
| **Len( [ “Hello”, “to the”, “World”, “” ] )** |인라인 테이블의 **[Value](function-value.md)** 열에서:<br><ul><li>각 문자열의 길이를 측정합니다.</li><li>각 문자열의 길이를 포함하는 단일 열 테이블을 반환합니다.</li> |![](media/function-len/people-table-len-inline.png) |

