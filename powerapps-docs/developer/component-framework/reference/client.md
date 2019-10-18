---
title: 클라이언트 | Microsoft Docs
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
ms.assetid: 4ce41c82-bf4a-4d34-9344-5311c24d76de
ms.openlocfilehash: 14c9a408aee2d71d31cdd795489655f6cedef3dc
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345730"
---
# <a name="client"></a>클라이언트

[!INCLUDE [client-description](includes/client-description.md)]

## <a name="syntax"></a>구문

`context.client;`

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="properties"></a>속성

### <a name="disablescroll"></a>disableScroll

구성 요소에 대 한 스크롤 기능을 사용 하지 않도록 설정 합니다.

**형식**: `boolean`

## <a name="methods"></a>메서드

|방법이 | 설명 |사용 가능한|
| ------------- |-------------|------|
|[getClient](client/getclient.md)|[!INCLUDE [getclient-description](client/includes/getclient-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[getFormFactor](client/getformfactor.md)|[!INCLUDE [getformfactor-description](client/includes/getformfactor-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[System.web.clientservices.connectivitystatus.isoffline](client/isoffline.md)|[!INCLUDE [isoffline-description](client/includes/isoffline-description.md)]|모델 기반 앱|

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)