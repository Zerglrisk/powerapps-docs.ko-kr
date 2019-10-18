---
title: 형식 | Microsoft Docs
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
ms.assetid: d9fb178c-6cc6-48cc-99c0-9972e37dec3e
ms.openlocfilehash: 960f3aee9007c1bc8391ee7cf85a961234bbf3ae
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345960"
---
# <a name="type"></a>형식

[!INCLUDE [type-description](includes/type-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[그룹 유형](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|

## <a name="value-element"></a>Value 요소

이 요소에는 다음 값 중 하나를 사용 하는 `string` 포함 됩니다.

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="example"></a>예

```XML
<type-group name="numbers">
      <type>Whole.None</type>
      <type>Currency</type>
      <type>FP</type>
      <type>Decimal</type>
    </type-group>
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)