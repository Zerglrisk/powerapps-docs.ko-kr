---
title: setControlState | Microsoft Docs
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 1052db82-7002-44ca-ad1f-9d3d4c311817
ms.openlocfilehash: 56c2221916781db646d27b131dfc00e61e742be3
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342671"
---
# <a name="setcontrolstate"></a>setControlState

[!INCLUDE [setcontrolstate-description](includes/setcontrolstate-description.md)]

## <a name="syntax"></a>구문

`context.mode.setControlState(state);`

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) 

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|상태일|`Dictionary`|예|단일 사용자에 대해 한 세션에서 지속 되는 데이터입니다.|

## <a name="return-value"></a>반환 값

형식: `boolean`


### <a name="related-topics"></a>관련 항목

[모드](../mode.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)