---
title: RetrieveRecord | Microsoft Docs
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
ms.assetid: dddeecc9-5067-420d-8bd7-4c914218e969
ms.openlocfilehash: 9c77bf9975bd1f1f115df9385061c008975cc184
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341705"
---
# <a name="retrieverecord"></a>retrieveRecord

[!INCLUDE [retrieverecord-description](includes/retrieverecord-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.webAPI.retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

## <a name="parameters"></a>변수의

<table style="width:100%">
<tr>
<th>이름</th>
<th>유형</th>
<th>필수</th>
<th>설명</th>
</tr>
<tr>
<td>entityLogicalName</td>
<td>문자열</td>
<td>예</td>
<td>검색할 레코드의 엔터티 논리적 이름입니다. 예: &quot;account &quot;.</td>
</tr>
<tr>
<td>A-id</td>
<td>문자열</td>
<td>예</td>
<td>검색 하려는 엔터티 레코드의 GUID입니다.</td>
</tr>
<tr>
<td>옵션</td>
<td>문자열</td>
<td>아니요</td>
<td><p>OData 시스템 쿼리 옵션, <b>$select</b> 및 <b>$expand</b>데이터를 검색 합니다.</p>
<ul><li><b>$Select</b> 시스템 쿼리 옵션을 사용 하 여 쉼표로 구분 된 속성 이름 목록을 포함 하 여 반환 되는 속성을 제한할 수 있습니다. 이는 중요 한 성능 모범 사례입니다. <b>$Select</b>를 사용 하 여 속성을 지정 하지 않으면 모든 속성이 반환 됩니다.</li>
<li><b>$Expand</b> 시스템 쿼리 옵션을 사용 하 여 반환 되는 관련 엔터티의 데이터를 제어 합니다. 탐색 속성의 이름만 포함 하는 경우 관련 레코드에 대 한 모든 속성을 받게 됩니다. 탐색 속성 이름 뒤의 괄호 안에 <b>$select</b> 시스템 쿼리 옵션을 사용 하 여 관련 레코드에 대해 반환 되는 속성을 제한할 수 있습니다. 이는 <i>단일 값</i> 및 <i>컬렉션 반환</i> 탐색 속성에 모두 사용 합니다.</li>
</ul>
<p>@No__t_0 시작 하는 쿼리 옵션을 지정 합니다. 또한 <code>&amp;</code>를 사용 하 여 쿼리 옵션을 구분 하 여 여러 쿼리 옵션을 지정할 수 있습니다. 예:</p>
<code>?$select=name&amp;$expand=primarycontactid($select=contactid,fullname)</code>
<p>다양 한 검색 시나리오에 대 한 <code>options</code> 매개 변수를 정의 하는 방법을 보려면이 항목의 뒷부분에 나오는 예제를 참조 하세요.</td>
</tr>
<tr>
<td>successCallback</td>
<td>함수</td>
<td>아니요</td>
<td><p>레코드를 검색할 때 호출할 함수입니다. 검색 된 속성 및 값을 포함 하는 JSON 개체는 함수에 전달 됩니다.</p>
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>함수</td>
<td>아니요</td>
<td>작업이 실패할 때 호출할 함수입니다.</td>
</tr>
</table>

## <a name="return-value"></a>반환 값

형식: [약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[엔터티](../entity.md) >



### <a name="related-topics"></a>관련 항목

[웹 API](../webapi.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)