---
title: openAlertDialog | Microsoft Docs
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
ms.assetid: 4acd3f17-74c0-4de1-9326-3778ff413f1e
ms.openlocfilehash: f1f5a2a78faf3dd9c6a1d6d197fab61772969084
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342510"
---
# <a name="openalertdialog"></a>openAlertDialog

[!INCLUDE [openalertdialog-description](includes/openalertdialog-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.navigation.openAlertDialog(alertStrings, options)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|alertStrings|`AlertDialogStrings`|예|경고 대화 상자에 사용할 문자열입니다. AlertDialogStrings에는 다음과 같은 특성이 있습니다.<br/>- **텍스트**: `string`. 경고 대화 상자에 표시할 메시지입니다. <br/>- 로 바꾸기**Buttonlabel**: `string`. 확인 단추 레이블입니다. 단추 레이블을 지정 하지 않으면 **확인** (사용자의 기본 설정 언어)이 단추 레이블로 사용 됩니다.|
|옵션|`AlertDialogOptions`|예|대화 상자 옵션입니다. AlertDialogOptions에는 다음과 같은 특성이 있습니다.<br/>- **height**: `number` 합니다. 경고 대화 상자의 높이 (픽셀)입니다. <br/>- **width**: `number` 합니다. 경고 대화 상자의 너비 (픽셀)입니다.|

## <a name="return-value"></a>반환 값

형식: `Promise`

## <a name="remarks"></a>설명

[약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 및 [파일](https://developer.mozilla.org/docs/Web/API/File) 참조

## <a name="example"></a>예 

```TypeScript
context.navigation.openAlertDialog({text:"This is an alert.", confirmButtonLabel : "Yes",}).then(
        function success()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Alert dialog closed";
        },
        function()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Error in Alert Dialog";
        }
    );
```

### <a name="related-topics"></a>관련 항목

[탐색](../navigation.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)