---
title: Resources 요소 | Microsoft Docs
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
ms.assetid: 66599c2f-6651-4b27-92da-a38897acdfb5
ms.openlocfilehash: a7df2dde98667fd0de8489943094ad6f4ff210f0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346075"
---
# <a name="resources-element"></a>resources 요소

[!INCLUDE [resources-description](includes/resources-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[컨트롤](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="child-elements"></a>자식 요소

|요소|설명|항목과|
|--|--|--|
|[코드](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|1|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|0 개 이상|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|0 개 이상|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|0 개 이상|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|0 개 이상|

## <a name="example"></a>예

```xml
<resources>
  <code path="JS_HelloWorldControl.js" order="1" />
<css path="css/JS_HelloWorldControl.css" order="1" />
        </resources>
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)