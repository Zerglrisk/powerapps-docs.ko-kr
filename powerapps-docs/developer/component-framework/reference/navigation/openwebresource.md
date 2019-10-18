---
title: openWebResource | Microsoft Docs
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
ms.assetid: 27a1e54c-71fe-450f-8f84-b4cc125970bf
ms.openlocfilehash: 577c26dd87149fabebafe32b77395029ef4df335
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342257"
---
# <a name="openwebresource"></a>openWebResource

[!INCLUDE [openwebresource-description](includes/openwebresource-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.navigation.openWebResource(name, options, data)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|이름의|`String`|예|열려는 HTML 웹 리소스의 이름입니다.|
|옵션|`OpenWebResourceOptions`|아니요|웹 리소스를 열기 위한 창 옵션입니다. OpenWebResourceOptions에는 다음과 같은 특성이 있습니다.<br/>- **height**: `Number` 합니다. 결과 페이지를 표시할 창의 높이 (픽셀)입니다.<br/>- **width**: `Number` 합니다. 결과 페이지를 표시할 창의 너비 (픽셀)입니다.<br/>- **Openinnewwindow**: `Boolean` 합니다. 새 창에서 웹 리소스를 열지 여부를 나타냅니다.|
|데이터로|`String`|아니요|데이터 매개 변수로 전달할 데이터입니다.

### <a name="related-topics"></a>관련 항목

[탐색](../navigation.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)