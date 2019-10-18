---
title: CSS 요소 | Microsoft Docs
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
ms.assetid: b6119424-c0a4-4412-b25c-8239da6cbe36
ms.openlocfilehash: b7c96ba2bbb3e5d6d20df92e58ef0bc4005e7d37
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346581"
---
# <a name="css-element"></a>css 요소

[!INCLUDE [css-description](includes/css-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="attributes"></a>특성

|이름|설명|유형|필수|사용 가능한|
|--|--|--|--|-----|
|`path`|CSS 파일이 있는 상대 경로 w .r. t 매니페스트|`string`|예|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|`order`|CSS 파일을 로드 하는 순서입니다.|`Positive integer`|필드|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[리소스](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>예

```xml
<css path="css/JS_HelloWorldControl.css" order="1" />
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)
