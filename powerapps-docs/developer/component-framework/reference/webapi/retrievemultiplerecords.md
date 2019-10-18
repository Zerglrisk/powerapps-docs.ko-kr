---
title: retrieveMultipleRecords | Microsoft Docs
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
ms.assetid: 824a53f9-c743-435a-9de2-8128846f3191
ms.openlocfilehash: d708596e9b8e12ead8f84d31d3b35fb5b27843f8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340808"
---
# <a name="retrievemultiplerecords"></a>retrieveMultipleRecords

[!INCLUDE [retrievemultiplerecords-description](includes/retrievemultiplerecords-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.webAPI.retrieveMultipleRecords(entityLogicalName, options, maxPageSize).then(successCallback, errorCallback);`

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
<td>옵션</td>
<td>문자열</td>
<td>아니요</td>
<td><p>데이터를 검색 하는 OData 시스템 쿼리 옵션 또는 FetchXML 쿼리 </p> 
<ul>
<li>지원 되는 시스템 쿼리 옵션은 <b>$select</b>, <b>$top</b>, <b>$filter</b>, <b>$expand</b>및 <b>$orderby</b>입니다.</li>
<li>FetchXML 쿼리를 지정 하려면 <code>fetchXml</code> 특성을 사용 하 여 쿼리를 지정 합니다.</li>
</ul>
<p>참고: 항상 <b>$select</b> 시스템 쿼리 옵션을 사용 하 여 쉼표로 구분 된 속성 이름 목록을 포함 하 여 엔터티 레코드에 대해 반환 되는 속성을 제한 해야 합니다. 이는 중요 한 성능 모범 사례입니다. <b>$Select</b>를 사용 하 여 속성을 지정 하지 않으면 모든 속성이 반환 됩니다.</li>
<p>@No__t_0 시작 하는 쿼리 옵션을 지정 합니다. @No__t_0를 사용 하 여 여러 시스템 쿼리 옵션을 지정 하 여 쿼리 옵션을 구분할 수도 있습니다.
<p>여러 가지 검색 시나리오에 대 한 <code>options</code> 매개 변수를 정의 하는 방법을 보려면이 항목의 뒷부분에 나오는 예제를 참조 하세요.</td>
</tr>
<tr>
<td>maxPageSize</td>
<td>번호</td>
<td>아니요</td>
<td><p>페이지당 반환할 엔터티 레코드 수를 나타내는 양수를 지정 합니다. 이 매개 변수를 지정 하지 않으면 기본값은 5000로 전달 됩니다.</p>
<p>검색 되는 레코드 수가 지정 된 <code>maxPageSize</code> 값 보다 많은 경우 반환 된 약속 개체의 <code>nextLink</code> 특성은 다음 엔터티 집합을 검색 하는 링크를 포함 합니다. </td>
</tr>
<tr>
<td>successCallback</td>
<td>함수</td>
<td>아니요</td>
<td><p>엔터티 레코드를 검색할 때 호출할 함수입니다. 다음 특성을 가진 개체가 함수에 전달 됩니다.</p>
<ul>
<li><b>엔터티</b>: JSON 개체의 배열로, 각 개체는 특성 및 해당 값을 포함 하는 검색 된 엔터티 레코드를 <code>key: value</code> 쌍으로 나타냅니다. 엔터티 레코드의 Id는 기본적으로 검색 됩니다.</li>
<li><b>nextLink</b>: 문자열입니다. 검색 되는 레코드 수가 요청의 <code>maxPageSize</code> 매개 변수에 지정 된 값 보다 많은 경우이 특성은 다음 레코드 집합을 반환 하는 URL을 반환 합니다.</li>
</ul>
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

유형: [약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <RetrieveMultipleResponse>

설명: `RetrieveMultipleResponse`은 검색 된 엔터티 레코드를 포함 하는 JSON 개체 배열을 포함 하는 약속을 반환 하 고, 페이징 (`maxPageSize`)이 요청에 지정 된 경우 다음 레코드 집합을 가리키는 URL이 포함 된 **nextLink** 특성을 반환 합니다. 반환 된 레코드 수가 페이징 값을 초과 합니다. 다음 매개 변수가 있습니다.

|변수에|반환 값|설명|
|----|------|-------|
|엔터티|`Entity[]`|각 개체가 특성과 해당 값을 포함 하는 검색 된 엔터티 레코드를 나타내는 JSON 개체의 배열입니다.|
|nextLink|`string`|검색 되는 레코드 수가 요청의 ' maxPageSize ' 매개 변수에 지정 된 값 보다 많은 경우이 특성은 다음 레코드 집합을 반환 하는 URL을 반환 합니다.|


### <a name="related-topics"></a>관련 항목

[웹 API](../webapi.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)