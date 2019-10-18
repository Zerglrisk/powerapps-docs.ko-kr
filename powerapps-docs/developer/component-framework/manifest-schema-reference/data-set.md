---
title: DataSet 요소 | Microsoft Docs
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
ms.assetid: 9ffe8930-b290-4252-98d4-a1195b00205f
ms.openlocfilehash: adf672b036d1f49619cbc4a5ef72661fbeebf013
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346558"
---
# <a name="data-set-element"></a>데이터 집합 요소

[!INCLUDE [data-set-description](includes/data-set-description.md)]

## <a name="attributes"></a>특성

|이름|설명|유형|필수|사용 가능한|
|--|--|--|--|-------|
|`description-key`|속성에 대 한 설명을 정의 합니다.|`string`|필드|
|`display-name-key`|속성의 이름을 정의 합니다.|`string`|예|
|`name`|그리드 이름|`string`|예|
|`cds-data-set-options`|True로 설정 된 경우 Commandbar, ViewSelector, QuickFindSearch를 표시 합니다. |`boolean`|예|

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[컨트롤](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="example"></a>예

```xml
 <data-set name="dataSetGrid" display-name-key="DataSetGridProperty" cds-data-set-options="displayCommandBar:true;displayViewSelector:true;displayQuickFindSearch:true">
 </data-set>
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)