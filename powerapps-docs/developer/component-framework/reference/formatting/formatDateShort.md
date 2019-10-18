---
title: formatDateShort | Microsoft Docs
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
ms.assetid: e69a9b6c-f737-4ebb-a9c1-901923b85358
ms.openlocfilehash: d9dd72ffdcb9ad69b3aae767effd14f617c0cba9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343568"
---
# <a name="formatdateshort"></a>formatDateShort

[!INCLUDE [formatdateshort-description](includes/formatdateshort-description.md)]

## <a name="syntax"></a>구문

`context.formatting.formatDateShort(value, includeTime);`

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|값|`Date`|예|형식을 지정할 값 날짜입니다.|
|includeTime|`boolean`|예|형식이 지정 된 값에 시간을 표시할지 여부를 지정 합니다.|

## <a name="return-value"></a>반환 값

형식: `string`


### <a name="related-topics"></a>관련 항목

[서식 지정](../formatting.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)