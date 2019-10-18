---
title: 패키지 된 라이브러리 요소 | Microsoft Docs
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
ms.assetid: 41c50db2-3096-4990-ac2b-e702c161bf4f
ms.openlocfilehash: 011aa2ab527cc2bd16fc99842e2388a3a6b0918e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346190"
---
# <a name="packaged_library-element"></a>packaged_library 요소

[!INCLUDE [packaged_library-description](includes/packaged_library-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱

## <a name="attributes"></a>특성

|이름|설명|유형|필수|사용 가능한|
|--|--|--|--|-------|
|`path`|패키지 된 라이브러리 파일이 있는 위치|`string`|예|모델 기반 앱|
|`version`|패키지 라이브러리의 현재 버전|`string`|예|모델 기반 앱|

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[라이브러리](library.md)|[!INCLUDE [library-description](includes/library-description.md)]|

## <a name="example"></a>예

```xml
<resources>
    <library name="AngularJSCore" version=">=1" order="1">
    <packaged_library path="libs/angular.min.js" version="1.5.8" />
    </library>
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)
