---
title: getEntityMetadata | Microsoft Docs
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
ms.assetid: 6a334af7-ca5b-449c-b90f-0901824654d2
ms.openlocfilehash: 89dc2e9d567b8ff38c41df2074d2a85d6bcaf467
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340969"
---
# <a name="getentitymetadata"></a>getEntityMetadata

[!INCLUDE [getentitymetadata-description](includes/getentitymetadata-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.utils.getEntityMetadata(entityName, attributes)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|entityName|`String`|예|엔터티의 논리적 이름입니다.|
|특성|`String[]`|아니요|메타 데이터를 가져올 특성입니다.|

## <a name="return-value"></a>반환 값

형식: `Promise<EntityMetadata>`


### <a name="related-topics"></a>관련 항목

[유틸리티](../utility.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)