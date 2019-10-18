---
title: FormatCurrency | Microsoft Docs
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
ms.assetid: 87e433e6-573f-414f-b49d-1213f2bd8cf4
ms.openlocfilehash: 6089e88ce5814ca24c8310435726bff07cc97894
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343246"
---
# <a name="formatcurrency"></a>formatCurrency

[!INCLUDE [formatcurrency-description](includes/formatcurrency-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="syntax"></a>구문

`context.formatting.formatCurrency(value, precision, symbol)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|값|`number`|예| 서식을 지정할 값입니다.|
|소수|`number`|예| 소수점이 하 자릿수입니다.|
|화살표|`string`|예| 통화 값을 사용 하 여 더할 통화 기호/코드입니다.|

## <a name="return-value"></a>반환 값

형식: `string`


### <a name="related-topics"></a>관련 항목

[서식 지정](../formatting.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)