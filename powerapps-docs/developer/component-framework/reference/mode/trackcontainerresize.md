---
title: TrackContainerResize | Microsoft Docs
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
ms.assetid: c5f482c2-dde2-460b-89a7-39e0efcc5704
ms.openlocfilehash: 8f9bc1ef17bdcb762e992d9f77dcdcd7ba1e8c50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342556"
---
# <a name="trackcontainerresize"></a>trackContainerResize

[!INCLUDE [trackcontainerresize-description](includes/trackcontainerresize-description.md)]에 대한 답변에 설명되어 있는 단계를 성공적으로 완료하면 활성화됩니다.

구성 요소를 호스팅하는 부모 컨텍스트가 모델 기반 앱에서 높이에 제한을 제공 하는 경우 동일한가 자식 구성 요소에 적절히 적용 됩니다. 그러나 대부분의 시나리오에서 부모 컨텍스트는 구성 요소의 높이를 제한 하지 않으므로 더 커질 수 있음을 나타내기 위해 "-1"을 받습니다.

Canvas 앱에서 부모 컨텍스트는 항상 끌어서 놓기 편집기의 특성에 따라 높이와 너비를 구성 요소에 제공 합니다.

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.mode.trackContainerResize(value)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|값|`Boolean`|예|컨트롤이 컨테이너 크기를 추적 해야 하는 경우에는 구성 요소가 allocatedWidth 또는 Allocatedwidth를 가져옵니다. `True`|


### <a name="related-topics"></a>관련 항목

[모드](../mode.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)
