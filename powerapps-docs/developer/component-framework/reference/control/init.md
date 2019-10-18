---
title: init | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: 4485b7d4-c68f-4298-8676-1820eb33c1ad
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 57a5ce0d4e930184bf42502f1dc16b6a648f1292
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345500"
---
# <a name="init"></a>Init

[!INCLUDE[./includes/init-description.md](./includes/init-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="syntax"></a>구문

`init(context,notifyOutputChanged,state,container)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|측면|[컨텍스트](../context.md)|예|매개 변수, 구성 요소 메타 데이터 및 인터페이스 함수를 포함 하는 *입력 속성* 입니다.|
|notifyOutputChanged|`function`|아니요|프레임 워크에 새 출력이 있음을 알리는 메서드입니다.|
|상태일|`Dictionary`|아니요|마지막 세션의 *Setcontrolstate* 에서 저장 된 구성 요소 상태입니다.|
|컨테이너|[HTMLDivElement](https://developer.mozilla.org/docs/Web/API/HTMLDivElement)|아니요|렌더링할 div 요소입니다.|

## <a name="example"></a>예

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.init = function (context, notifyOutputChanged, state, container) {
    this._labelElement = document.createElement("label");
    this._labelElement.setAttribute("class", "JS_HelloWorldColor");
    container.appendChild(this._labelElement);
};
```

### <a name="related-topics"></a>관련 항목

[컨트롤](../control.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)
