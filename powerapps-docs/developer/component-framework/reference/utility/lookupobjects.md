---
title: lookupObjects | Microsoft Docs
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
ms.assetid: d213b401-cfc4-44df-b55c-f040fb6d7072
ms.openlocfilehash: 0dca29df3537389decefe2584d2fc931cea8979c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341153"
---
# <a name="lookupobjects"></a>lookupObjects

[!INCLUDE [lookupobjects-description](includes/lookupobjects-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.utils.lookupObjects(lookupOptions)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|LookupOptions|`UtilityApi.LookupOptions`|예|조회 대화 상자를 여는 옵션을 정의 합니다. LookupOptions에는 다음과 같은 특성이 있습니다.<br/>- **Allowmultiselect**: `Boolean`. 조회에서 둘 이상의 항목을 선택할 수 있는지 여부를 나타냅니다.<br/>**Defaultentitytype**: `String`를 -  합니다. 사용할 기본 엔터티 형식입니다.<br/>- **defaultViewId**: `String`. 사용할 기본 뷰입니다.<br/>- **entityTypes**: `String[]`. 표시할 엔터티 형식입니다.<br/>- **viewid**: `String[]`. 뷰 선택에서 사용할 수 있는 뷰입니다. 시스템 뷰만 지원 됩니다 (사용자 뷰 아님).|

## <a name="return-value"></a>반환 값

형식: [약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[Entityreference](../entityreference.md)[] >


### <a name="related-topics"></a>관련 항목

[유틸리티](../utility.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)