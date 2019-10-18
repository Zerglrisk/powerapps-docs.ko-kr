---
title: openConfirmDialog | Microsoft Docs
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
ms.assetid: 83f2c208-696c-48b1-b65c-2ba7374d6cfc
ms.openlocfilehash: 8b7bda89b9c8d83614a4a95281853676db9cf568
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342487"
---
# <a name="openconfirmdialog"></a>openConfirmDialog

[!INCLUDE [openconfirmdialog-description](includes/openconfirmdialog-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.navigation.openConfirmDialog(confirmStrings, options)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|는 문자열|`ConfirmDialogStrings`|예|대화 상자에 사용 되는 문자열입니다. 이 특성에는 다음과 같은 특성이 있습니다.<br/>- **제목**: `String`. 확인 대화 상자에 표시할 제목입니다. <br/>- **부제목**: `String`. 확인 대화 상자에 표시 되는 자막입니다.<br/>- **텍스트**: `String`. 확인 대화 상자에 표시할 메시지입니다.<br/>- 로 바꾸기**Buttonlabel**: `String`. 확인 단추 레이블입니다. 단추 레이블을 지정 하지 않으면 **확인** (사용자의 기본 설정 언어)이 단추 레이블로 사용 됩니다.<br/>- **Cancelbuttonlabel**: 취소 단추 레이블을 `String` 합니다. 취소 단추 레이블을 지정 하지 않으면 **취소** 가 단추 레이블로 사용 됩니다.|
|옵션|`ConfirmDialogOptions`|아니요|대화 상자에 대 한 옵션입니다. 이 옵션에는 다음과 같은 특성이 있습니다.<br/>- **height**: `Number` 합니다. 확인 대화 상자의 높이 (픽셀)입니다. <br/>- **width**: `Number` 합니다. 확인 대화 상자의 너비 (픽셀)입니다.|

## <a name="return-value"></a>반환 값

형식: `Promise<ConfirmDialogResponse>`

설명: 대화 상자를 닫기 위해 확인 단추를 클릭 했는지 여부를 나타내는 확인 됨 (부울) 특성이 전달 된 개체를 반환 합니다.

## <a name="remarks"></a>설명

[약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 참조 


### <a name="related-topics"></a>관련 항목

[탐색](../navigation.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)