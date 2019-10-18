---
title: Property 요소 | Microsoft Docs
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
ms.assetid: 45f4872d-c1d2-4c5a-8721-251b96ede370
ms.openlocfilehash: ee4e0b0259d5978f3e84757d4023827ada45f01e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346144"
---
# <a name="property-element"></a>property 요소

[!INCLUDE [property-description](includes/property-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="attributes"></a>특성

|이름|설명|유형|필수|
|--|--|--|--|
|`name`|속성의 이름입니다.|`string`|예|
|`display-name-key`|사용자 지정 화면에서 속성의 이름을 설명 하는 지역화 된 문자열로 사용 됩니다.|`string`|예|
|`of-type`|속성의 데이터 형식을 정의 합니다.|[설명](#remarks) 참조|필드|
|`usage`|Usage 특성은 속성이 구성 요소가 변경 (바인딩) 하거나 읽기 전용 값 (입력) 할 수 있는 엔터티 특성을 나타낼지 여부를 식별 합니다.|`bound` 또는 `input`|필드|
|`required`|속성이 필수 인지 여부|`boolean`|필드|
|`of-type-group`|매니페스트에 정의 된 형식 그룹의 이름입니다.|`string`|필드|
|`description-key`|사용자 지정 화면에서 속성에 대 한 설명을 설명 하는 지역화 된 문자열로 사용 됩니다.|`string`|필드|
|`default-value`|구성 요소에 제공 되는 기본 구성 값입니다. 모델 기반 앱에서이 특성은 바인딩된 매개 변수에 필드가 연결 된 것으로 간주 되기 때문에 입력에만 허용 됩니다.|`string`|필드|

### <a name="remarks"></a>설명

@No__t_0 특성 값은 다음 중 하나 여야 합니다.

[!INCLUDE [type-table](includes/type-table.md)]

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[매니페스트](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|


## <a name="example"></a>예

```xml
<property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" 
description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)
