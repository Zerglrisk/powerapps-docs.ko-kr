---
title: openErrorDialog | Microsoft Docs
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
ms.assetid: 10c154b9-45a0-44ee-a621-73d6a9009c6d
ms.openlocfilehash: c3371b7c3ea8bde869acc261ab7d4fc8f28ba7da
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342441"
---
# <a name="openerrordialog"></a>openErrorDialog

[!INCLUDE [openerrordialog-description](includes/openerrordialog-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.navigation.openErrorDialog(options)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|옵션|`ErrorDialogOptions`|예|오류 대화 상자 옵션입니다. ErrorDialogOptions에는 다음과 같은 특성이 있습니다. <br/>- **세부 정보**: `String`. 오류에 대 한 세부 정보입니다. 이를 지정 하면 오류 메시지에서 **로그 파일 다운로드** 단추를 사용할 수 있으며,이 단추를 클릭 하면 사용자가이 특성에 지정 된 내용이 포함 된 텍스트 파일을 다운로드할 수 있습니다.<br/>- **errorCode**: `Number`. 오류 코드입니다. ErrorCode를 설정 하는 경우 오류 코드에 대 한 메시지가 서버에서 자동으로 검색 되 고 오류 대화 상자에 표시 됩니다. **ErrorCode** 값을 지정 하면 기본 오류 메시지가 표시 된 오류 대화 상자가 표시 됩니다.<br/>- **메시지**: `String`. 오류 대화 상자에 표시할 메시지입니다. **ErrorCode** 또는 **message** 특성 중 하나를 설정 해야 합니다.|

## <a name="return-value"></a>반환 값

형식: `Promise`

## <a name="remarks"></a>설명

[약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 및 [파일](https://developer.mozilla.org/docs/Web/API/File) 참조


### <a name="related-topics"></a>관련 항목

[탐색](../navigation.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)