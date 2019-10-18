---
title: Property Set 요소 | Microsoft Docs
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
ms.assetid: 996f10e5-8057-40ea-9680-555e4cd682ff
ms.openlocfilehash: 98e0bcf7588e72f001e45471c87f0050dd0846ba
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346236"
---
# <a name="property-set-element"></a>속성 집합 요소

[!INCLUDE [property-set-description](includes/property-set-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱

## <a name="attributes"></a>특성

|이름|설명|유형|필수|
|--|--|--|--|
|`name`|필드의 이름입니다.|`string`|예|
|`display-name-key`|사용자 지정 화면에서 속성 이름을 설명 하는 지역화 된 문자열로 사용 됩니다.|`string`|예|
|`description-key`|사용자 지정 화면에서 속성에 대 한 설명을 설명 하는 지역화 된 문자열로 사용 됩니다.|`string`|필드|
|`of-type`|속성의 데이터 형식을 정의 합니다.|[설명](#remarks) 참조|필드|
|`required`|속성이 필수 인지 여부를 나타냅니다.|`boolean`|필드|
|`of-type-group`|매니페스트에 정의 된 형식 그룹의 이름입니다.|`string`|필드|
|`usage`|Usage 특성은 속성이 구성 요소가 변경 (바인딩) 하거나 읽기 전용 값 (입력) 할 수 있는 엔터티 특성을 나타낼지 여부를 식별 합니다.|`bound` 또는 `input`|예|

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[데이터 세트](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|

## <a name="child-elements"></a>자식 요소

|요소|설명|항목과|
|--|--|--|
|[종류](types.md)||0 개 이상|

### <a name="remarks"></a>설명

@No__t_0 특성 값은 다음 중 하나 여야 합니다.

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)