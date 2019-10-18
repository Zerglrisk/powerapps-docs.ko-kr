---
title: Paging | Microsoft Docs
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
ms.assetid: 12891e96-972c-4289-bbde-2bc261cd1f12
ms.openlocfilehash: ccf68c94e0b11f8a1227199609a9c21c1923ad7b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342188"
---
# <a name="paging"></a>Paging

[!INCLUDE [paging-description](includes/paging-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="totalresultcount"></a>totalResultCount

현재 쿼리에 대 한 서버에 있는 총 결과 수입니다.

**형식**: `number`

### <a name="hasnextpage"></a>hasNextPage

결과 집합을 뒤로 페이징할 수 있는지 여부를 나타냅니다.

**형식**: `boolean`

### <a name="haspreviouspage"></a>hasPreviousPage

결과 집합을 뒤로 페이징할 수 있는지 여부를 나타냅니다.

**형식**: `boolean`

## <a name="methods"></a>메서드

|방법이 | 설명 |
| ------|-------------|
|[loadNextPage](paging/loadnextpage.md)|[!INCLUDE [loadnextpage-description](paging/includes/loadnextpage-description.md)]|
|[loadPreviousPage](paging/loadpreviouspage.md)|[!INCLUDE [loadpreviouspage-description](paging/includes/loadpreviouspage-description.md)]|
|[다시 설정](paging/reset.md)|[!INCLUDE [reset-description](paging/includes/reset-description.md)]|
|[setPageSize](paging/setpagesize.md)|[!INCLUDE [setpagesize-description](paging/includes/setpagesize-description.md)]|
|pageSize|데이터 집합 페이지당 반환할 레코드 수입니다. 폼에서 데이터 집합 pageSize는 서식 (행 수)과 함께 사용 되며, 다른 사용자는 개인 옵션을 선택할 수 있습니다.|


### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)