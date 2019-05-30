---
title: '바코드 스캐너 컨트롤: 참조 | Microsoft Docs'
description: 바코드 스캐너 컨트롤에 대한 속성 및 예제를 포함한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a4b2c941b5e28c462b85d3c6d54404746e22d04
ms.sourcegitcommit: 8d0ba2ec0c97be91d1350180dd6881c14dec8f2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65517353"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>캔버스 앱에 대한 바코드 스캐너 컨트롤

Android 또는 iOS 장치에서 바코드, QR 코드 및 데이터 행렬 코드를 검색합니다. 웹 브라우저에서는 지원되지 않습니다.

## <a name="description"></a>설명

컨트롤은 Android 또는 iOS 장치에서 네이티브 스캐너를 엽니다. 스캐너는 바코드, QR 코드 또는 데이터 행렬 코드가 표시되는 경우 자동으로 감지합니다. 컨트롤은 웹 브라우저에서 검색을 지원 하지 않습니다.

컨트롤은 QR 코드, 데이터 행렬 코드 및 다음 유형의 바코드를 지원합니다.

- UPC A
- UPC E
- EAN 8
- EAN 13
- 39 코드
- 코드 128
- ITF
- PDF 417

## <a name="key-properties"></a>주요 속성

**값** – 가장 최근에 검색 한 코드의 텍스트 값을 포함 하는 속성을 출력 합니다.

**텍스트** -스캐너를 활성화 하는 단추에 나타나는 텍스트입니다.

**OnScan** – 바코드를 성공적으로 스캔했을때 앱이 응답하는 방식입니다.

## <a name="additional-properties"></a>추가 속성

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**FlashlightEnabled** 는 손전등은 스캐너 열릴 때 자동으로 사용 되는지 여부를-합니다.

**[높이](properties-size-location.md) ** – 스캐너를 활성화 하는 단추의 높이입니다.

**PreferFrontCamera** -전면 카메라를 사용 가능한 경우에 사용할지 여부를 검색 합니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**형식** -가장 최근에 성공한 검색에서 검색 된 코드의 형식입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[너비](properties-size-location.md) ** – 스캐너를 활성화 하는 단추의 너비입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="accessibility-guidelines"></a>접근성 지침
스캔을 시작하는 단추이기 때문에 **바코드 스캐너** 컨트롤은 **[단추](control-button.md)** 컨트롤과 동일한 지침이 적용됩니다.

### <a name="visual-alternatives"></a>시각 신호
* 바코드 스캐너는 스캔 결과를 표시하지 않는 단추입니다. **[레이블](control-text-box.md)** 컨트롤에 스캔 결과를 표시하는 것이 좋습니다. 레이블의 **[Text](properties-core.md)** 속성을 바코드 스캐너의 **Value** 속성으로 설정합니다. 레이블의 **[Live](properties-accessibility.md)** 속성을 **Polite**로 설정하여 화면 읽기 프로그램 사용자에게 변경을 알립니다. 이 변경은 시각적 능력에 상관 없이 누구나 액세스할 수 있는 스캔한 값을 만듭니다.

* 시각 및 운동 기능 장애가 있는 사용자는 카메라로 바코드를 가리키는 것을 선호하지 않을 수 있습니다. 바코드 입력을 위해 **[텍스트 입력](control-text-input.md)** 컨트롤과 같은 다른 형태의 입력을 추가하는 것이 좋습니다.
