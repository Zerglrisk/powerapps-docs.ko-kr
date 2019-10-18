---
title: CaptureImage | Microsoft Docs
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
ms.assetid: 1d9c0063-add2-4002-acab-1be07ca1f6b6
ms.openlocfilehash: e642af17e02334b45041df87386885536e1810af
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345684"
---
# <a name="captureimage"></a>captureImage

[!INCLUDE[./includes/captureimage-description.md](./includes/captureimage-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.device.captureImage(options)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|`options`|`Object`|아니요|이미지 캡처 옵션입니다.|

## <a name="return-value"></a>반환 값

형식: `Promise<FileObject>`

[약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 및 [FileObject](../fileobject.md) 참조

## <a name="remarks"></a>설명

@No__t_0 매개 변수 개체에는 다음과 같은 속성이 있습니다.

|이름|유형|설명|
| ---|----|-----------|
|`allowEdit`|`Boolean`|저장 하기 전에 이미지를 편집할 지 여부를 나타냅니다.|
|`height`|`Number`|캡처할 이미지의 높이입니다.|
|`preferFrontCamera`|`Boolean`|장치의 전면 카메라를 사용 하 여 이미지를 캡처할 것인지 여부를 나타냅니다.|
|`quality`|`Number`|백분율 단위로 나타낸 이미지 파일의 품질입니다.|
|`width`|`Number`|캡처할 이미지의 너비입니다.|


### <a name="related-topics"></a>관련 항목

[장치](../device.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)