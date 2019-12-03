---
title: 'Microsoft Stream video 컨트롤: 참조 | Microsoft Docs'
description: Microsoft Stream 비디오 컨트롤에 대 한 속성 및 예제를 포함 한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/26/2019
ms.author: fikaradz
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c9d3594ecf338c6cfa93786f56a09606b2de6296
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732008"
---
# <a name="microsoft-stream-video-control-in-power-apps"></a>Power Apps의 Microsoft Stream 비디오 컨트롤
비디오 및 채널을 Microsoft Stream 비디오 플레이어입니다.

## <a name="description"></a>설명
이 컨트롤을 사용 하면 앱 사용자가 비디오를 재생 하 고 Microsoft Stream 서비스에서 채널을 탐색할 수 있습니다.

## <a name="key-properties"></a>주요 속성
**Streamurl** – 컨트롤에 표시할 Microsoft Stream 비디오 또는 채널의 URL입니다.

**Showcontrols** – 최종 사용자에 게 비디오 재생 컨트롤을 표시할지 여부를 지정 합니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다. 비디오 또는 오디오 클립의 제목이어야 합니다.

**자동 시작** - 사용자가 해당 컨트롤이 있는 화면으로 이동할 때 오디오 또는 동영상 컨트롤이 클립 재생을 자동으로 시작할지 여부를 선택합니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**StartTime** – 클립이 재생을 시작할 때 오디오 또는 동영상 클립의 시작 후 시간입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="example"></a>예

### <a name="play-an-audio-or-video-file-from-microsoft-stream"></a>Microsoft Stream에서 오디오 또는 비디오 파일 재생

1. **파일** 메뉴에서 **삽입** 을 선택한 다음 **미디어** 드롭다운 메뉴를 엽니다. 
2. 미디어 컨트롤 목록에서 **Microsoft Stream** 을 선택 합니다.

    ![Microsoft Stream](./media/control-stream-video/stream-icon.png "Microsoft Stream")

3. 왼쪽의 **스트림 URL** 속성 내에 비디오 링크를 붙여 넣습니다.

    ![StreamUrl 속성 사용자 지정](./media/control-stream-video/stream-url.png "StreamUrl 속성 사용자 지정")

4. F5 키를 눌러 추가한 컨트롤의 재생 단추를 선택 합니다.

    > [!NOTE]
   > **Microsoft Stream** 비디오를 재생 하려면 인증이 필요 합니다. 앱 사용자에 게 필요한 권한이 있는지 확인 합니다.
5. Esc 키를 눌러 미리 보기 모드를 종료 합니다.

## <a name="browser-considerations"></a>브라우저 고려 사항

### <a name="ios"></a>Io
Power Apps iOS 플레이어는 앱에 포함 된 비디오의 직접 재생을 지원 하지 않습니다.  비디오를 시청 하려면 스트림 아이콘을 클릭 하 여 비디오 플레이어를 전체 화면 모드로 시작 합니다.

### <a name="safari"></a>Safari

Safari 브라우저에서 앱의 Microsoft Stream 비디오를 보려면 [사이트 간 추적을 방지](https://support.apple.com/guide/safari/sfri40732/mac)하는 옵션을 해제 해야 합니다.

## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="audio-and-video-alternatives"></a>오디오 및 비디오 대체 항목
* 사용자가 자신만의 속도로 멀티미디어를 듣거나 볼 수 있도록 **ShowControls**는 true여야 합니다. 이렇게 설정하면 사용자가 비디오 플레이어에서 선택 자막 및 전체 화면 모드를 토글할 수 있습니다.
* 비디오에 대한 선택 자막을 제공해야 합니다.
 * 다음 방법 중 하나를 사용하여 오디오 또는 비디오 기록을 제공하는 것이 좋습니다.
  1. **[레이블](control-text-box.md)** 에 텍스트를 넣고 멀티미디어 플레이어에 인접하게 배치합니다. 선택적으로 텍스트 표시를 전환하는 **[단추](control-button.md)** 를 만듭니다.
  2. 텍스트를 다른 화면에 넣습니다. 화면으로 이동하고 단추를 멀티미디어 플레이어에 인접하게 배치하는 **[단추](control-button.md)** 를 만듭니다.
  3. 설명이 간단하면 **[AccessibleLabel](properties-accessibility.md)** 에 설명을 넣을 수 있습니다.

### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **[FocusedBorderColor](properties-color-border.md)** 및 외부 색
* **[Fill](properties-color-border.md)** 및 멀티미디어 플레이어 컨트롤(채우기가 표시되는 경우)

비디오 콘텐츠에 색 대비 문제가 있는 경우 선택 자막 및/또는 기록을 제공합니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
* 키보드 사용자가 재생을 빠르게 중지하기 어려울 수 있으므로 **AutoStart**는 false여야 합니다.