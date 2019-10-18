---
title: Control 요소 | Microsoft Docs
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
ms.assetid: 4dacd337-c9df-458e-86f3-bfb3ab543ea7
ms.openlocfilehash: aa02b89ce1e032a3cf2fdedca8f0fdf79cb84045
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346627"
---
# <a name="control-element"></a>control 요소

[!INCLUDE [control-description](includes/control-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="attributes"></a>특성

|이름|설명|유형|필수|사용 가능한|
|--|--|--|--|--------|
|`namespace`|구성 요소의 개체 프로토타입을 정의 합니다.|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|예|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|`constructor`|개체를 초기화 하는 방법|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|예|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|`control-type`|비표준|[!INCLUDE [controltype-description](includes/controltype-description.md)]|아니요|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|`description-key`|UI에 표시 되는 구성 요소에 대 한 설명을 정의 합니다.|`string`|아니요|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|`display-name-key`|UI에 표시 되는 컨트롤의 이름을 정의 합니다.|`string`|예|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|`preview-image`|사용자 지정 화면에서 구성 요소의 미리 보기를 표시 하는 데 사용 되는 이미지입니다.|`string`|아니요|모델 기반 앱|
|`version`|[의미 체계 버전 관리](https://semver.org) 에 정의 된 구성 요소의 버전을 정의 합니다.|`string`|예|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
<!--|`hidden`|구성 요소를 숨길지 여부를 정의 합니다.|[!INCLUDE [booleantype-description](includes/booleantype-description.md)]| 아니요|모델 기반 앱|-->

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[매니페스트](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|

## <a name="child-elements"></a>자식 요소

|요소|설명|항목과|
|--|--|--|
|[데이터 세트](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 개 이상|
|[속성](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0 개 이상|
|[리소스](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|1|
|[그룹 유형](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0 개 이상|

## <a name="example"></a>예

```xml
<control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0"
 display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key"
 control-type="standard" preview-image="img/preview.png">
</control>
  ```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)