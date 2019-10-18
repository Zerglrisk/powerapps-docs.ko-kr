---
title: Resx 요소 | Microsoft Docs
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
ms.assetid: 38acfda3-4adc-4aa2-bb8b-f29ba572a6e5
ms.openlocfilehash: 29c89541c2519b36559ab49d2b0483f19b545573
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346029"
---
# <a name="resx-element"></a>resx 요소

[!INCLUDE [resx-description](includes/resx-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="attributes"></a>특성

|이름|설명|유형|필수|
|--|--|--|--|
|`path`|Resx 파일이 있는 상대 경로 w .r. t 매니페스트|`string`|예|
|`version`|현재 버전의 resx 파일|`string`|예|

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[리소스](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>예

```xml
<resources>
      <code path="TS_LocalizationAPI.js" order="1" />
        <css path="css/TS_LocalizationAPI.css" order="1" />
      <resx path="strings/TSLocalizationAPI.1033.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.1035.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.3082.resx" version="1.0.0" />
    </resources>
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)
