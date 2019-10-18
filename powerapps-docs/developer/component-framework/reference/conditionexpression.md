---
title: ConditionExpression | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd90b3fd-a4b4-4999-8b53-d2a5dce4966b
ms.openlocfilehash: 10f7275643c0df4c2a4099a80b490fb5e27ce318
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345546"
---
# <a name="conditionexpression"></a>ConditionExpression

[!INCLUDE [conditionexpression-description](includes/conditionexpression-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="attributename"></a>attributeName

필터를 적용할 데이터 집합 열의 이름입니다.

**형식**: `string`

### <a name="conditionoperator"></a>conditionOperator

조건을 평가 하는 데 사용 되는 연산자입니다.

**형식**: `enum`

@No__t_0 값은 다음과 같은 가능한 값을 포함 하는 열거형입니다.

|Value|구성원|
|--|--|
|-1|없음을|
|0|다릅니다|
|1|NotEqual|
|2|GreaterThan|
|3|LessThan|
|4|사용률이|
|5|LessEqual|
|6|이와|
|20cm(8|진행|
|10|N|
|14|두번째|
|15|Today|
|x|내일|
|17@@|Last7Days|
|개가|Next7Days|
|mb|LastWeek|
|720|ThisWeek|
|가로|LastMonth|
|불가능|ThisMonth|
|가지의|Sign-on|
|26@@|OnOrBefore|
|27@@|OnOrAfter|
|~|LastYear|
|명|ThisYear|
|33|LastXDays|
|34|NextXDays|
|37|LastXMonths|
|38|NextXMonths|
|49|에서는|
|70|InFiscalPeriodAndYear|
|75|위쪽과|
|76|에서|
|77|NotUnder|
|78|AboveOrEqual|
|79|동일 하 게|
|87|ContainValues|

### <a name="entityaliasname"></a>entityAliasName

연결 된 엔터티에서 필터링을 사용할 수 있도록 엔터티 별칭 이름입니다.

**형식**: `string`

### <a name="value"></a>값

조건에 의해 평가 되는 값입니다.

**형식**: `string | string[]`

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)