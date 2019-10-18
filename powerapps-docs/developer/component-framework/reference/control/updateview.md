---
title: updateView | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 899d6eb3-62b4-4c1f-947c-aed1f8643caa
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d7ac81ef617aa4e9e3564ade01bc469b0d7f5bc8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345339"
---
# <a name="updateview"></a>updateView

[!INCLUDE[./includes/updateview-description.md](./includes/updateview-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="syntax"></a>구문

`updateView(context)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|측면|`context`|예|매니페스트에 정의 된 이름에 매핑되고 유틸리티 함수에서 설정 된 사용자 지정 값을 포함 합니다.|

## <a name="example"></a>예

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.updateView = function (context) {
    this._labelElement.innerText = "Hello World! (JS)";
};
```

## <a name="remarks"></a>설명

필드 구성 요소의 값을 구성 된 필드의 원시 값으로 설정 합니다.


### <a name="related-topics"></a>관련 항목

[컨트롤](../control.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)