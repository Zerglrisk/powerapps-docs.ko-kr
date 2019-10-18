---
title: RetrieveMultipleResponse | Microsoft Docs
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
ms.assetid: 08ea66d3-b4af-44af-a3ae-cb2ebad043e8
ms.openlocfilehash: 0e5b2cad047bcf91b0c63e27c4a7ceb35c1ed538
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341314"
---
# <a name="retrievemultipleresponse"></a>RetrieveMultipleResponse

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="entities"></a>엔터티

각 개체가 특성과 해당 값을 포함 하는 검색 된 엔터티 레코드를 나타내는 JSON 개체의 배열입니다.

**형식**: `Entity[]`

### <a name="nextlink"></a>nextLink

검색 되는 레코드 수가 요청의 `maxPageSize` 매개 변수에 지정 된 값 보다 많은 경우이 특성은 다음 레코드 집합을 반환 하는 URL을 반환 합니다.

**형식**: `string`


### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)