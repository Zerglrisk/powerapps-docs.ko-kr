---
title: 데이터 세트 | Microsoft Docs
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
ms.assetid: 0202d51f-e9a9-4a2e-b3e9-0bfd7f6afb86
ms.openlocfilehash: 5e9408c81fc9587b9dec30f18fc68c3112ba6125
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345316"
---
# <a name="dataset"></a>데이터 세트

[!INCLUDE [dataset-description](includes/dataset-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="addcolumn"></a>addColumn ()

Columnset에 열을 추가 합니다.

### <a name="remarks"></a>설명

이 메서드는 두 개의 매개 변수를 받아들입니다.

|이름|유형|필수|설명|
|------|-----|------|-----|
|이름의|`string`|예|데이터 집합에 추가할 열 이름입니다.|
|entityAlias|`string`|아니요| 열 이름을 추가 해야 하는 엔터티 별칭입니다.|

### <a name="columns"></a>세로

이 데이터 집합에서 사용할 수 있는 열 집합입니다.

**형식**: [Column](column.md)[]

### <a name="error"></a>메시지가

데이터 검색 중에 오류가 발생 했는지 여부를 나타냅니다.

**형식**: `boolean`

### <a name="errormessage"></a>errorMessage

마지막으로 발생 한 오류와 관련 된 오류 메시지입니다 (해당 하는 경우).

**형식**: `string`

### <a name="filtering"></a>필터링

현재 쿼리에 대 한 열 필터링입니다.

**형식**: [필터링](filtering.md)

### <a name="linking"></a>연결

연결 된 엔터티 정보를 정의 합니다.

**형식**: [연결](linking.md)

### <a name="loading"></a>로딩

데이터 집합을 로드 하 고 있는지 여부를 나타냅니다.

**형식**: `boolean`

### <a name="paging"></a>페이징

페이지 매김 상태 및 동작입니다.

**형식**: [페이징](paging.md)

### <a name="records"></a>Records

전체 레코드 개체에 Id를 매핑합니다.

**유형**: [entityrecord](entityrecord.md)

### <a name="sortedrecordids"></a>sortedRecordIds

쿼리 응답 결과에 따라 정렬 된 데이터 집합의 레코드 Id입니다.

**형식**: `string[]`

### <a name="sorting"></a>기능

현재 쿼리의 정렬 상태입니다.

**유형**: [sortstatus](sortstatus.md)

## <a name="methods"></a>메서드

|방법이 | 설명 | 
| ------------- |-------------|
|[clearSelectedRecordIds](dataset/clearselectedrecordids.md)|[!INCLUDE [clearselectedrecordids-description](dataset/includes/clearselectedrecordids-description.md)]| 
|[getSelectedRecordIds](dataset/getselectedrecordids.md)|[!INCLUDE [getselectedrecordids-description](dataset/includes/getselectedrecordids-description.md)]| 
|[getTargetEntityType](dataset/gettargetentitytype.md)|[!INCLUDE [gettargetentitytype-description](dataset/includes/gettargetentitytype-description.md)]| 
|[getTitle](dataset/gettitle.md)|[!INCLUDE [gettitle-description](dataset/includes/gettitle-description.md)]| 
|[getViewId](dataset/getviewid.md)|[!INCLUDE [getviewid-description](dataset/includes/getviewid-description.md)]| 
|[openDatasetItem](dataset/opendatasetitem.md)|[!INCLUDE [opendatasetitem-description](dataset/includes/opendatasetitem-description.md)]| 
|[고치십시오](dataset/refresh.md)|[!INCLUDE [refresh-description](dataset/includes/refresh-description.md)]| 
|[setSelectedRecordIds](dataset/setselectedrecordids.md)|[!INCLUDE [setselectedrecordids-description](dataset/includes/setselectedrecordids-description.md)]| 

## <a name="example"></a>예

데이터 집합 메서드를 구현 하는 방법에 대 한 자세한 내용은 [데이터 집합 표 구성 요소](../sample-controls/data-set-grid-control.md) 를 참조 하세요.

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)