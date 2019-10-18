---
title: setFullScreen 화면 | Microsoft Docs
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
ms.assetid: 1faf3e79-969e-4c1e-ac01-8e2155c609fa
ms.openlocfilehash: b7fb38bcb0102356d8d1ea2540edf0dd1f845cbd
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342625"
---
# <a name="setfullscreen"></a>setFullScreen

[!INCLUDE [setfullscreen-description](includes/setfullscreen-description.md)]

## <a name="syntax"></a>구문

`context.mode.setControlState(mode);`

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|값|`Boolean`|예|구성 요소가 전체 화면으로 크기를 자동으로 조정 해야 하는지 여부를 `True` 합니다. 구성 요소의 크기가 할당 된 너비를 자동으로 조정 해야 하는지 여부를 `False` 합니다.|


### <a name="related-topics"></a>관련 항목

[모드](../mode.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)