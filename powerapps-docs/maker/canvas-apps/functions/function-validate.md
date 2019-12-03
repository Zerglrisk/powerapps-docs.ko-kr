---
title: Validate 함수 | Microsoft Docs
description: Power Apps의 Validate 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1524b6f28d0ce5b1ed02fbd02d3c2df52e2b300f
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729845"
---
# <a name="validate-function-in-power-apps"></a>Power Apps의 Validate 함수
**Validate** 함수는 단일 [열](../working-with-tables.md#columns) 또는 전체 [레코드](../working-with-tables.md#records)의 값이 [데이터 원본](../working-with-data-sources.md)에 대해 유효한지 여부를 확인합니다.  

## <a name="description"></a>설명
사용자가 데이터 변경을 제출하기 전에 해당 제출의 유효성에 대한 즉각적인 피드백을 제공할 수 있으므로 사용자 환경이 향상됩니다.

데이터 원본은 레코드 내에서 유효한 값을 구성하는 정보를 제공할 수 있습니다. 이 정보에는 다음과 같은 많은 제약 조건이 포함될 수 있습니다.

* 열 값이 필요한지 여부
* 텍스트 문자열의 최대 길이
* 최고 및 최저 숫자
* 가장 빠른 날짜 및 느린 날짜

**Validate** 함수는 이런 정보를 사용하여 값이 유효한지 확인하고 그렇지 않은 경우 적절한 오류 메시지를 반환합니다 **[DataSourceInfo](function-datasourceinfo.md)** 함수를 사용하여 **Validate**에 사용되는 동일한 정보를 볼 수 있습니다.

데이터 원본이 제공하는 유효성 검사 정보의 양은 전혀 제공하지 않는 경우를 포함하여 다양합니다. **Validate**는 이러한 정보를 기반으로 값을 확인만 할 수 있습니다. **Validate**에서 문제를 찾지 못해도 데이터 변경 적용은 실패할 수 있습니다. **[Errors](function-errors.md)** 함수를 사용하여 오류에 대한 정보를 얻을 수 있습니다.

**Validate**에서 문제를 찾으면 함수는 앱 사용자에게 표시할 수 있는 오류 메시지를 반환합니다. 모든 값이 유효하면 **Validate**는 [공백](function-isblank-isempty.md)을 반환합니다. 유효성 검사 정보가 없는 [컬렉션](../working-with-data-sources.md#collections)으로 작업하는 경우, 값은 항상 유효합니다.

## <a name="syntax"></a>구문
**Validate**( *DataSource*, *Column*, *Value* )

* *DataSource* – 필수 항목이며, 유효성을 검사할 데이터 원본입니다.
* *Column* – 필수 항목입니다. 유효성을 검사할 열입니다.
* *Value* – 필수 항목입니다. 유효성을 검사할 선택한 열의 값입니다.

**Validate**( *DataSource*, *OriginalRecord*, *Updates* )

* *DataSource* – 필수 항목이며, 유효성을 검사할 데이터 원본입니다.
* *OriginalRecord* - 필수 항목입니다.  업데이트의 유효성을 검사할 레코드입니다.
* *Updates* - 필수 항목입니다.  원본 레코드에 적용할 변경 내용입니다.

## <a name="examples"></a>예
다음 예제의 경우 **Scores** 데이터 원본의 **Percentage** 열에 있는 값은 0과 100 사이여야 합니다. 데이터가 유효성 검사를 통과하면 함수는 *공백*을 반환합니다. 그렇지 않으면 함수는 오류 메시지를 반환합니다.

### <a name="validate-with-a-single-column"></a>단일 열로 유효성 검사

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Validate( Scores, Percentage, 10 )** |**10**이 **Scores** 데이터 원본의 **Percentage** 열에 유효한 값인지 확인합니다. |*공백* |
| **Validate( Scores, Percentage, 120 )** |**120**이 **Scores** 데이터 원본의 **Percentage** 열에 유효한 값인지 확인합니다. |"값은 0과 100 사이여야 합니다." |

### <a name="validate-with-a-complete-record"></a>전체 레코드로 유효성 검사

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Validate( Scores, EditRecord, Gallery.Updates )** |모든 열의 값이 **점수** 데이터 원본에 대해 유효한지를 확인합니다. 이 예제에서 **백분율** 열의 값은 **10**입니다. |*공백* |
| **Validate( Scores, EditRecord, Gallery.Updates )** | 모든 열의 값이 **점수** 데이터 원본에 대해 유효한지를 확인합니다. 이 예제에서 **백분율** 열의 값은 **120**입니다. |"값은 0과 100 사이여야 합니다." |

