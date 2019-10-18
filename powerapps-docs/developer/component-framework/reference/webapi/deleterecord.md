---
title: deleteRecord | Microsoft Docs
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
ms.assetid: 5c9968bf-d535-425c-b1f1-0db6b7822de1
ms.openlocfilehash: f6c8dd6ea7d156e28ab3ae54d7fe37dad6c4546a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340762"
---
# <a name="deleterecord"></a>deleteRecord

[!INCLUDE [deleterecord-description](includes/deleterecord-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.webAPI.deleteRecord(entityLogicalName, id).then(successCallback, errorCallback);`

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
<td>삭제할 레코드의 엔터티 논리적 이름입니다. 예: &quot;account &quot;. </td>
</tr>
<tr>
<td>A-id</td>
<td>문자열</td>
<td>예</td>
<td>삭제 하려는 엔터티 레코드의 GUID입니다.</td>
</tr>
<tr>
<td>successCallback</td>
<td>함수</td>
<td>아니요</td>
<td><p>레코드가 삭제 될 때 호출할 함수입니다. 삭제 된 레코드를 식별 하기 위해 다음 속성을 가진 개체가 전달 됩니다.</p>
<ul>
<li><b>entityType</b>: 문자열입니다. 레코드의 엔터티 형식입니다.</li>
<li><b>id</b>: 문자열입니다. 레코드의 GUID입니다.</li>
<li><b>이름</b>: String 레코드 이름입니다.</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>함수</td>
<td>아니요</td>
<td>작업이 실패할 때 호출할 함수입니다.</td>
</tr>
</table>

## <a name="return-value"></a>반환 값

형식: [약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[Entityreference](../entityreference.md) >

### <a name="related-topics"></a>관련 항목

[웹 API](../webapi.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)