---
title: '웹 바코드-스캐너 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯 한 바코드 스캐너 컨트롤 정보
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e80f34917bba942f85e141c382cf3b1caa5e6d44
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650768"
---
# <a name="web-barcode-scanner-control-experimental-in-powerapps"></a>PowerApps의 웹 바코드-스캐너 컨트롤 (실험적)

사용 되지 않지만 웹 브라우저에서 코드를 검사 하는 데 유용할 수 있는 레거시 바코드 검색 컨트롤입니다.

## <a name="description"></a>설명

컨트롤은 사용자가 모든 장치에서 바코드를 검색할 수 있도록 앱의 카메라 피드를 표시 합니다. 컨트롤이 성능 저하로 인해 사용 되지 않으며 모바일 **[바코드 스캐너](control-new-barcode-scanner.md)** 컨트롤이이 컨트롤을 대체 합니다.

## <a name="key-properties"></a>주요 속성

**바코드 스캐너** – 둘 이상의 바코드 스캐너를 사용하는 디바이스에서 앱이 사용하는 바코드 스캐너의 숫자 ID입니다.

## <a name="additional-properties"></a>추가 속성

**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**ShowLiveBarcodeDetection** – 바코드 검색 상태를 나타내기 위해 시각 신호를 표시할지 여부입니다. 노란색 사각형은 검사 중인 영역을 나타냅니다. 직사각형을 가로지르는 녹색 선은 바코드 식별 성공을 나타냅니다.

**Stream** – **StreamRate** 속성에 따라 자동으로 업데이트되는 이미지입니다.

**StreamRate** – **Stream** 속성에서 이미지를 업데이트하는 빈도(밀리초 단위)를 선택합니다.  이 값의 범위는 100(1초의 10분의 1)에서 3,600,000(1시간)입니다.

**Text** - 스캐너가 마지막으로 식별한 바코드 값입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수

[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>예

### <a name="add-photos-to-an-image-gallery-control"></a>이미지 갤러리 컨트롤에 사진 추가

1. **바코드 스캐너** 컨트롤을 추가하고 이름을 **Mybarcode scanner**로 지정합니다

    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?

1. **레이블** 컨트롤을 추가 하 고 해당 출력을 바코드 스캐너의 **Text** 속성으로 설정 합니다.

1. **BarcodeType** 속성에서 형식 집합의 바코드를 검색 합니다.

    레이블이 스캔 한 바코드를 표시 합니다.

## <a name="accessibility-guidelines"></a>접근성 지침

### <a name="video-alternatives"></a>비디오 대체 항목

* **[Text](properties-core.md)** 가 바코드 스캐너의 **Text**로 설정된 **[레이블](control-text-box.md)** 을 추가하는 것이 좋습니다. 바코드 스캐너는 식별된 바코드 값을 표시하지 않으므로 위의 작업을 수행하면 시각 장애가 있는 사용자만이 아니라 모든 사용자가 스캐너에 액세스할 수 있습니다.

### <a name="screen-reader-support"></a>화면 판독기 지원

* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

    > [!NOTE]
  > 새 바코드를 발견 하면 화면 읽기 권한자에 게 알립니다. 값을 알리지 않습니다. 바코드가 보기 상태 이면 화면 읽기 권한자는 5 초 마다 사용자에 게 동일한 바코드를 확인 하는 것을 알립니다.
