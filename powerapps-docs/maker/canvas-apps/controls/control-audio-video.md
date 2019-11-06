---
title: '오디오 및 동영상 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯하여 오디오 및 동영상 컨트롤에 관한 정보
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
ms.openlocfilehash: 3b8c5ea5ee2784bc1ab97d6943045cee8da6a52f
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650775"
---
# <a name="audio-and-video-controls-in-powerapps"></a>PowerApps의 오디오 및 동영상
오디오 파일, 동영상 파일 또는 YouTube의 동영상을 재생하는 컨트롤입니다.

## <a name="description"></a>설명
**오디오** 컨트롤은 파일에서 사운드 클립, **[마이크](control-microphone.md)** 컨트롤에서 녹음, 또는 동영상 파일에서 오디오 트랙을 재생합니다.

**비디오** 컨트롤은 파일이나 YouTube 또는 Azure Media Services에서 비디오 클립을 재생합니다.  지정된 경우에는 선택적으로 선택 자막이 표시될 수 있습니다.

## <a name="key-properties"></a>주요 속성
**Loop** – 재생을 마치는 즉시 오디오 또는 동영상 클립이 자동으로 시작할지 여부를 선택합니다.

**Media** – 오디오 또는 비디오 컨트롤에서 재생하는 클립에 대한 식별자입니다.

**ShowControls** - 오디오 또는 비디오 플레이어에서 재생 단추, 볼륨 슬라이더 등을 표시하는지 및 펜 컨트롤에서 그리기, 삭제 및 지우기 아이콘 등을 표시하는지 여부입니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다. 비디오 또는 오디오 클립의 제목이어야 합니다.

**AutoPause** – 사용자가 다른 화면으로 이동할 경우 오디오 또는 동영상 클립을 자동으로 일시 중지할지 여부를 선택합니다.

**자동 시작** - 사용자가 해당 컨트롤이 있는 화면으로 이동할 때 오디오 또는 동영상 컨트롤이 클립 재생을 자동으로 시작할지 여부를 선택합니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**ClosedCaptionsUrl** – 비디오 컨트롤만 해당합니다.  WebVTT 형식인 선택 자막 파일의 URL입니다.  비디오 및 캡션 URL은 모두 HTTPS여야 합니다. 비디오 및 캡션 파일을 모두 호스팅하는 서버는 CORS를 사용하도록 설정되어야 합니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[Image](properties-visual.md)** – 이미지, 오디오 또는 마이크 컨트롤에 표시되는 이미지의 이름입니다.

**[ImagePosition](properties-visual.md)** – 이미지와 같은 크기가 아닌 경우 컨트롤 또는 화면에 있는 이미지의 위치입니다(**채우기**, **맞춤**, **늘이기**, **타일** 또는 **가운데**).

**OnEnd** - 오디오 또는 동영상 클립이 재생을 마칠 때 앱이 응답하는 방식입니다

**OnPause** - 사용자가 오디오 또는 동영상 컨트롤이 재생하는 클립을 일시 중지할 때 앱이 응답하는 방식입니다.

**OnStart** – 사용자가 마이크 컨트롤로 녹음을 시작할 때 앱이 응답하는 방식입니다.

**Paused** – 미디어 재생 컨트롤이 현재 일시 중지되면 *True*이고 그렇지 않으면 *false*입니다.

**[Reset](properties-core.md)** – 컨트롤을 기본값으로 되돌릴지 여부를 선택합니다.

**Start** – 오디오 또는 비디오 클립의 재생 여부입니다.

**StartTime** – 클립이 재생을 시작할 때 오디오 또는 동영상 클립의 시작 후 시간입니다.

**Time** – 미디어 컨트롤의 현재 위치입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**First**( *TableName* )](../functions/function-first-last.md)

## <a name="examples"></a>예
### <a name="play-an-audio-or-video-file"></a>오디오 또는 동영상 파일 재생
1. **파일** 메뉴에서 **미디어**를 클릭하거나 탭하고 **동영상** 또는 **오디오**를 클릭하거나 탭한 다음, **찾아보기**를 클릭하거나 탭합니다.
2. 사용하려는 파일로 이동하여 클릭하거나 탭한 다음, **열기**를 클릭하거나 탭합니다.
3. Esc 키를 눌러 기본 작업 영역으로 돌아가 **오디오** 또는 **비디오** 컨트롤을 추가하고 **Media** 속성을 사용자가 추가한 파일로 설정합니다.

    [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 방법을 모르시나요?
4. F5 키를 누르고 사용자가 추가한 컨트롤의 재생 단추를 클릭하거나 탭하여 클립을 재생합니다.

    > [!TIP]
   > **동영상** 컨트롤의 재생 단추는 컨트롤을 마우스로 가리킬 때 나타납니다.
5. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

### <a name="play-a-youtube-video"></a>YouTube 동영상을 재생합니다
1. **비디오** 컨트롤을 추가하고 **Media** 속성을 YouTube 비디오의 URL(큰따옴표로 묶인)로 설정합니다.
2. F5 키를 누르고 **동영상** 컨트롤의 재생 단추를 클릭하거나 탭하여 클립을 재생합니다.
3. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

### <a name="play-a-video-from-azure-media-services"></a>Azure Media Services에서 비디오 재생
1. 비디오가 AMS에 게시된 후 매니페스트 URL을 복사합니다. 아직 시작되지 않은 경우 서비스의 스트리밍 엔드포인트를 시작합니다.
1. **비디오** 컨트롤을 추가하고 **Media** 속성을 AMS 비디오의 URL(큰따옴표로 묶인)로 설정합니다.
2. F5 키를 누르고 **동영상** 컨트롤의 재생 단추를 클릭하거나 탭하여 클립을 재생합니다.
3. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="audio-and-video-alternatives"></a>오디오 및 비디오 대체 항목
* 사용자가 자신만의 속도로 멀티미디어를 듣거나 볼 수 있도록 **ShowControls**는 true여야 합니다. 이렇게 설정하면 사용자가 비디오 플레이어에서 선택 자막 및 전체 화면 모드를 토글할 수 있습니다.
* 비디오에 대한 선택 자막을 제공해야 합니다.
  *  YouTube 비디오의 경우 YouTube에서 제공하는 작성 도구를 사용하여 자막을 추가합니다.
  *  다른 비디오의 경우 WebVTT 형식으로 자막을 만들어 업로드하고 **ClosedCaptionsUrl**을 URL 위치로 설정합니다. 몇 가지 제한 사항이 있습니다. 비디오 및 자막을 호스트하는 서버는 CORS를 지원해야 하고 HTTPS 프로토콜을 사용하여 비디오 및 자막을 제공해야 합니다. Internet Explorer에서는 자막이 작동하지 않습니다.
* 다음 방법 중 하나를 사용하여 오디오 또는 비디오 기록을 제공하는 것이 좋습니다.
  1. **[레이블](control-text-box.md)** 에 텍스트를 넣고 멀티미디어 플레이어에 인접하게 배치합니다. 선택적으로 텍스트 표시를 전환하는 **[단추](control-button.md)** 를 만듭니다.
  2. 텍스트를 다른 화면에 넣습니다. 화면으로 이동하고 단추를 멀티미디어 플레이어에 인접하게 배치하는 **[단추](control-button.md)** 를 만듭니다.
  3. 설명이 간단하면 **[AccessibleLabel](properties-accessibility.md)** 에 설명을 넣을 수 있습니다.

### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **[FocusedBorderColor](properties-color-border.md)** 및 외부 색
* **[Image](properties-visual.md)** 및 멀티미디어 플레이어 컨트롤(해당하는 경우)
* **[Fill](properties-color-border.md)** 및 멀티미디어 플레이어 컨트롤(채우기가 표시되는 경우)

비디오 콘텐츠에 색 대비 문제가 있는 경우 선택 자막 및/또는 기록을 제공합니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
* 키보드 사용자가 재생을 빠르게 중지하기 어려울 수 있으므로 **AutoStart**는 false여야 합니다.
