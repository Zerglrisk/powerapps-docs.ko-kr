---
title: 팝업 | Microsoft Docs
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
ms.assetid: b0af1803-ae3a-41c2-a8a5-b15970bd6f96
ms.openlocfilehash: bb28a979ac721eded06025a56588023c211ea6f9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342211"
---
# <a name="popup"></a>팝업

[!INCLUDE [popup-description](includes/popup-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="closeonoutsideclick"></a>closeOnOutsideClick

마우스 외부 마우스 클릭에 팝업을 닫을지 여부를 나타냅니다. @No__t_0로 설정 된 경우에는 외부 마우스 클릭에서 팝업이 닫히지 않습니다.

**형식**: `boolean`

### <a name="content"></a>콘텐트가

삽입할 정적 DOM 요소입니다.

**형식**: [HTMLElement](https://developer.mozilla.org/docs/Web/API/HTMLElement)

### <a name="id"></a>A-id

앵커 구성 요소 (있는 경우)로 설정할 id입니다.

**형식**: `string`

### <a name="name"></a>이름의

팝업의 이름입니다. 팝업을 열기 위한 참조로 사용 됩니다.

**형식**: `string`

### <a name="popuptoopen"></a>popupToOpen

열 팝업의 이름입니다.

**형식**: `string`

### <a name="remarks"></a>설명

루트 popup에만 정의 해야 합니다. 중첩 된 팝업을 열려면 `rootName.nestedName.[allOtherNestedNames]`와 같은 문자열을 제공 해야 합니다. 팝업을 닫으려면 빈 문자열을 제공 해야 합니다. 이 속성은 자식에 자동으로 전파 됩니다.

## <a name="type"></a>형식

열거형 PopupType에 설명 되어 있는 팝업의 형식입니다. 각 팝업 집합에 대해 하나의 `root` popup이 있어야 합니다.

**형식**: `enum`

@No__t_0 값은 다음과 같은 가능한 값을 포함 하는 열거형입니다.

|Value|구성원|
|--|--|
|1|루트가|
|2|내포|

### <a name="remarks"></a>설명

각 팝업 집합에 대해 하나의 `Root` Popup이 있어야 합니다.

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)