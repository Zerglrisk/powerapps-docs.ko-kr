---
title: updateRecord | Microsoft Docs
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
ms.assetid: 179ced61-ff0f-45ef-aa14-835ce99532cf
ms.openlocfilehash: 96037bcd8ca43448e928abef714ae031222d8e98
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340693"
---
# <a name="updaterecord"></a>updateRecord

[!INCLUDE [updaterecord-description](includes/updaterecord-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.webAPI.updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>업데이트 하려는 레코드의 엔터티 논리적 이름입니다. 예: &quot;account &quot;.</td>
</tr>
<tr>
<td>A-id</td>
<td>문자열</td>
<td>예</td>
<td>업데이트 하려는 엔터티 레코드의 GUID입니다.</td>
</tr>
<tr>
<td>데이터로</td>
<td>개체가</td>
<td>예</td>
<td><p>@No__t_0 쌍을 포함 하는 JSON 개체입니다. 여기서 <code>key</code>은 엔터티의 속성입니다. <code>value</code> 업데이트 하려는 속성의 값입니다.</p>
<p>다양 한 업데이트 시나리오에 대 한 <code>data</code> 개체를 정의 하는 방법은이 항목의 뒷부분에 나오는 예제를 참조 하세요.</td>
</tr>
<tr>
<td>successCallback</td>
<td>함수</td>
<td>아니요</td>
<td><p>레코드가 업데이트 될 때 호출할 함수입니다. 업데이트 된 레코드를 식별 하기 위해 다음 속성을 가진 개체가 전달 됩니다.</p>
<ul>
<li><b>entityType</b>: 문자열입니다. 업데이트 된 레코드의 엔터티 형식입니다.</li>
<li><b>id</b>: 문자열입니다. 업데이트 된 레코드의 GUID입니다.</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>함수</td>
<td>아니요</td>
<td>작업이 실패할 때 호출할 함수입니다. 다음 속성을 가진 개체가 전달 됩니다.
<ul>
<li><b>errorCode</b>: Number. 오류 코드입니다.</li>
<li><b>메시지</b>: 문자열 문제를 설명 하는 오류 메시지입니다.</li>
</ul></td>
</tr>
</table>

## <a name="return-value"></a>반환 값

유형: [약속] ((dateformattinginfo) <[Entityreference](../entityreference.md) >

설명: 성공 시 **successCallback** 매개 변수 설명에서 이전에 지정 된 특성을 포함 하는 약속 개체를 반환 합니다.


### <a name="related-topics"></a>관련 항목

[웹 API](../webapi.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)