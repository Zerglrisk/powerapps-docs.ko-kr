---
title: Manifest 요소 | Microsoft Docs
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
ms.assetid: a48831c6-133a-4747-99fa-7cc1df4558d0
ms.openlocfilehash: d62b72c43a9c77a41c0a434a723d330ffa4b890a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346259"
---
# <a name="manifest-element"></a>Manifest 요소

[!INCLUDE [manifest-description](includes/manifest-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="child-elements"></a>자식 요소

|요소|설명|항목과|사용 가능한|
|--|--|--|-------|
|[컨트롤](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|1 개 이상|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|[그룹 유형](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0 개 이상|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|[속성](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0 개 이상|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|[데이터 세트](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 개 이상|모델 기반 앱|
|[리소스나](resources.md)|[!INCLUDE [resource-description](includes/resources-description.md)]|1 개 이상|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|

## <a name="example"></a>예

```xml
<?xml version="1.0" encoding="utf-8" ?>
<manifest>
    <control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0" display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key" control-type="standard">
        <property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <resources>
            <code path="JS_HelloWorldControl.js" order="1" />
            <css path="css/JS_HelloWorldControl.css" order="1" />
        </resources>
    </control>
</manifest>
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)
