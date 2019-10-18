---
title: FilterExpression | Microsoft Docs
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
ms.assetid: 19ad54b8-e044-4f07-a18e-b00d26b75832
ms.openlocfilehash: 7b613238f28987b688d4f2299506fa91b72a99a7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343982"
---
# <a name="filterexpression"></a>FilterExpression

[!INCLUDE [filterexpression-description](includes/filterexpression-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="conditions"></a>만족

이 필터와 연결 된 조건 집합입니다.

**유형**: [conditionexpression](conditionexpression.md)[]

### <a name="filteroperator"></a>filterOperator

이 필터의 조건을 결합 하는 데 사용 되는 연산자입니다.

**형식**: `enum`

@No__t_0 값은 다음과 같은 가능한 값을 포함 하는 열거형입니다.

|Value|구성원|
|--|--|
|0|And|
|1|Or|

### <a name="filters"></a>필터나

이 필터를 평가한 후 평가 해야 하는 모든 자식 필터입니다.

**유형**: [FilterExpression](filterexpression.md)[]<br />

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)