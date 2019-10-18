---
title: Library 요소 | Microsoft Docs
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
ms.assetid: 90f2b4c9-7396-4ab9-bc9f-810189dc18b7
ms.openlocfilehash: bd766864e6ef971b5245afad7d49af54b9369087
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346305"
---
# <a name="library-element"></a>library 요소

[!INCLUDE [library-description](includes/library-description.md)]

## <a name="attributes"></a>특성

|이름|설명|유형|필수|
|--|--|--|--|
|`name`|라이브러리의 이름입니다.|`string`|예|
|`version`|현재 라이브러리 버전|양의 정수|예|
|`order`|라이브러리 파일이 로드 되는 순서|양의 정수|예|

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[리소스](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="child-elements"></a>자식 요소

|요소|설명|항목과|
|--|--|--|
|[packaged_library]||0 개 이상|

## <a name="example"></a>예

```xml
<resources>
<library name="AngularJSCore" version=">=1" order="1">
<packaged_library path="libs/angular.min.js" version="1.5.8" />
</library>
  </resources>
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)