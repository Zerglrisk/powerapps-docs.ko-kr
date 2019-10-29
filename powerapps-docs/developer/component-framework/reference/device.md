---
title: 장치 | Microsoft Docs
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
ms.assetid: a0f9abc5-c605-4433-bf5a-f8253eeeda3b
ms.openlocfilehash: f4c8ce52907c5e49dcd782b51824ab3976ae3fcd
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025504"
---
# <a name="device"></a>장치

[!INCLUDE [device-description](includes/device-description.md)]

> [!IMPORTANT]
> 장치 API 메서드를 사용 하려면 매니페스트 파일의 [기능 사용](../manifest-schema-reference/feature-usage.md) 노드에 이러한 메서드의 사용을 선언 해야 합니다.

## <a name="syntax"></a>구문

`context.device`

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="methods"></a>메서드

|방법이 | 설명 |
| ------------- |-------------|
|[captureAudio](device/captureaudio.md)|[!INCLUDE [captureaudio-description](device/includes/captureaudio-description.md)]|
|[captureImage](device/captureimage.md)|[!INCLUDE [captureimage-description](device/includes/captureimage-description.md)]|
|[captureVideo](device/capturevideo.md)|[!INCLUDE [capturevideo-description](device/includes/capturevideo-description.md)]|
|[getBarcodeValue](device/getbarcodevalue.md)|[!INCLUDE [getbarcodevalue-description](device/includes/getbarcodevalue-description.md)]|
|[getCurrentPosition](device/getcurrentposition.md)|[!INCLUDE [getcurrentposition-description](device/includes/getcurrentposition-description.md)]|
|[pickFile](device/pickfile.md)|[!INCLUDE [pickfile-description](device/includes/pickfile-description.md)]|

## <a name="example"></a>예

```TypeScript
 private onUploadButtonClick(event: Event): void {
    this._context.device.pickFile().then(this.processFile.bind(this), this.showError.bind(this));
  }
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)