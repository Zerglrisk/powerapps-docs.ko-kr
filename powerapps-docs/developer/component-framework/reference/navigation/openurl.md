---
title: openUrl | Microsoft Docs
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
ms.assetid: 590078f3-c604-4bd0-ac74-9cf6d8806802
ms.openlocfilehash: 21e097c739364b6cdb3935654ae9bf2b61143a06
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342280"
---
# <a name="openurl"></a>openUrl

[!INCLUDE [openurl-description](includes/openurl-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.navigation.openUrl(url, options)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|url|`string`|예|열 Url입니다.|
|옵션|`OpenUrlOptions`|아니요|URL을 여는 옵션입니다. OpenUrlOptions에는 다음 매개 변수가 있습니다. <br/>- **height**: `Number` 합니다. 결과 페이지를 표시할 창의 높이 (픽셀)입니다.<br/>- **width**: `Number` 합니다. 결과 페이지를 표시할 창의 너비 (픽셀)입니다.|


### <a name="related-topics"></a>관련 항목

[탐색](../navigation.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)