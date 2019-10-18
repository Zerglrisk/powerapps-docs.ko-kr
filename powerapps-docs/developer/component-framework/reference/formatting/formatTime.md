---
title: formatTime | Microsoft Docs
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
ms.assetid: 148964b5-106e-4f2e-8038-9086d29dc54f
ms.openlocfilehash: cc2c7dfdbe9952d69dcda9fdd4c813965f539478
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343338"
---
# <a name="formattime"></a>formatTime

[!INCLUDE [formattime-description](includes/formattime-description.md)]

## <a name="syntax"></a>구문

`context.formatting.formatTime(value, behavior);`

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|값|`Date`|예|서식을 지정할 날짜입니다.|
|행동|`DateTimeFieldBehavior`|예|서식을 지정할 datetime 개체의 동작입니다. @No__t_0에는 다음과 같은 특성이 있습니다.<br/>-  `None =0`: 알 수 없는 DateTime 동작 <br/>-  `UserLocal =1`: 사용자 현지 시간을 준수 합니다. UTC로 저장 된 날짜<br/>-  `TimeZoneIndependent =3`: UTC로 변환 하지 않고 저장 된 날짜 및 시간|

## <a name="return-value"></a>반환 값

형식: `string`


### <a name="related-topics"></a>관련 항목

[서식 지정](../formatting.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)