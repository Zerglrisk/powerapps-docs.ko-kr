---
title: '바코드-스캐너 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯 한 바코드 스캐너 컨트롤 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: fikaradz
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 56d8ca116b4b683d7096ef08f550dfa11c32d3c6
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986439"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>Canvas 앱에 대 한 바코드 스캐너 컨트롤

Android 또는 iOS 장치에서 바코드, QR 코드 및 데이터 행렬 코드를 스캔 합니다. 웹 브라우저에서는 지원 되지 않습니다.

## <a name="description"></a>설명

컨트롤은 Android 또는 iOS 장치에서 네이티브 스캐너를 엽니다. 스캐너는 보기에서 바코드, QR 코드 또는 데이터 행렬 코드를 자동으로 검색 합니다. 컨트롤은 웹 브라우저에서 검색을 지원 하지 않습니다.

컨트롤은 QR 코드, 데이터 행렬 코드 및 이러한 종류의 바코드를 지원 합니다.

- UPC
- UPC E
- E 8
- E 13
- 코드 39
- 코드 128
- ITF
- PDF 417

## <a name="key-properties"></a>주요 속성

**Value** – 가장 최근에 검색 된 코드의 텍스트 값을 포함 하는 출력 속성입니다.

스캐너를 활성화 하는 단추에 표시 되는 **텍스트** 텍스트입니다.

**Onscan** – 바코드가 성공적으로 검색 될 때 앱이 응답 하는 방식입니다.

## <a name="additional-properties"></a>추가 속성

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**FlashlightEnabled** -스캐너가 열릴 때 손전등가 자동으로 사용 되는지 여부입니다.

**[Height](properties-size-location.md)** – 스캐너를 활성화 하는 단추의 높이입니다.

**PreferFrontCamera** -사용 가능한 경우 전면 카메라가 검색에 사용 되는지 여부를 나타냅니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**유형** -가장 최근에 성공한 검색에서 검색 된 코드의 유형입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 스캐너를 활성화 하는 단추의 너비입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="accessibility-guidelines"></a>접근성 지침
**[단추](control-button.md)** 컨트롤에 대 한 동일한 지침은 스캔을 시작 하는 단추인 **바코드 스캐너** 컨트롤에 적용 됩니다.

### <a name="visual-alternatives"></a>시각적 개체 대체
* 바코드 스캐너는 스캔 결과를 표시 하지 않는 단추입니다. **[레이블](control-text-box.md)** 컨트롤을 사용 하 여 검사 결과를 표시 하는 것이 좋습니다. 레이블의 **[Text](properties-core.md)** 속성을 바코드 스캐너의 **Value** 속성으로 설정 합니다. 화면 판독기 사용자에 게 변경 내용을 알릴 수 있도록 레이블의 **[라이브](properties-accessibility.md)** 속성을 **처리 완료 후** 로 설정 합니다. 이렇게 변경 하면 시각적 기능에 관계 없이 모든 사용자가 검색 된 값에 액세스할 수 있습니다.

* 시각적 및 화물 장애가 있는 사용자는 바코드에서 카메라를 가리키지 않는 것이 좋습니다. 사용자가 바코드를 입력할 수 있도록 **[텍스트 입력](control-text-input.md)** 컨트롤과 같은 다른 형식의 입력을 추가 하는 것이 좋습니다.
