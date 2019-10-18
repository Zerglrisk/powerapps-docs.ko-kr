---
title: getResource | Microsoft Docs
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
ms.assetid: 5c04ba7c-acfe-4375-8dd8-6c537ded9352
ms.openlocfilehash: 919606c7b6669265a8bdd4f7b43080564e87a80f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341406"
---
# <a name="getresource"></a>getResource

[!INCLUDE [getresource-description](includes/getresource-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.resources.getResource(id, success, failure)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|A-id|`String`|예|리소스 문자열 식별자입니다.|
|성공할|`String`|아니요|성공 콜백입니다. 리소스 데이터는 기본 64 인코딩 형식으로 반환 됩니다.|
|실패로|`String`|아니요|실패 콜백입니다.|


### <a name="related-topics"></a>관련 항목

[리소스](../resources.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)