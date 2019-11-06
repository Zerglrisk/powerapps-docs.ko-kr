---
title: '그림 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 그림 컨트롤에 관한 정보
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
ms.openlocfilehash: 1970c373b7614644897620e2c6d60f4472add568
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650818"
---
# <a name="add-picture-control-in-powerapps"></a>PowerApps의 이미지 컨트롤 추가
사진을 촬영하거나 로컬 디바이스에서 이미지를 로드 합니다.

## <a name="description"></a>설명
이 컨트롤을 통해 사용자는 사진을 촬영하거나 본인의 디바이스에서 이미지 파일을 업로드하고 이 콘텐츠로 데이터 원본을 업데이트할 수 있습니다. 모바일 디바이스에서 사용자에게 사진을 촬영하거나 이미 사용 가능한 이미지 중에서 선택할지 묻는 디바이스의 선택 대화 상자가 표시됩니다.

이 컨트롤은 두 가지 컨트롤 **이미지** 및 **미디어 단추 추가**가 포함된 그룹화된 컨트롤입니다. 이미지가 업로드되지 않은 경우 **이미지** 컨트롤은 업로드된 이미지 또는 자리 표시자를 표시합니다. **미디어 단추 추가**는 이미지를 업로드할지 묻는 메시지를 표시합니다.

**Image** 속성에 대해서는 [이미지 컨트롤 참조](control-image.md)를 참조하세요.

## <a name="add-media-button-properties"></a>미디어 단추 추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다. 이미지 추가의 목적을 설명해야 합니다.

**[Align](properties-text.md)** - 컨트롤의 가로 가운데를 기준으로 한 텍스트의 위치입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**ChangePictureText** – 이미지가 업로드되었을 때 단추에 나타나는 텍스트입니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**Error** -이미지를 업로드하는 중에 문제가 있어 이 속성이 적절한 오류 문자열이 포함됩니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**[FontWeight](properties-text.md)** - 컨트롤의 텍스트 굵기입니다. **Bold**, **Semibold**, **Normal** 또는 **Lighter**로 설정합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[HoverColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**Media** – 오디오 또는 비디오 컨트롤에서 재생하는 클립에 대한 식별자입니다.

**[OnChange](properties-core.md)** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[Padding](properties-size-location.md)** – 가져오기 또는 내보내기 단추의 텍스트와 단추의 가장자리 사이의 간격입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[Reset](properties-core.md)** – 컨트롤을 기본값으로 되돌릴지 여부를 선택합니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Text](properties-core.md)** – 이미지가 업로드되지 않았을 때 단추에 나타나는 텍스트입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[VerticalAlign](properties-text.md)** – 컨트롤의 세로 가운데를 기준으로 한 텍스트의 위치입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="examples"></a>예
### <a name="add-images-to-an-image-gallery-control"></a>이미지 갤러리 컨트롤에 이미지 추가
1. **이미지 추가** 컨트롤에서 세 번 클릭합니다.
   
    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. **열기** 대화 상자에서 이미지 파일을 클릭하거나 탭한 다음, **열기**를 클릭하거나 탭합니다.
3. **[단추](control-button.md)** 컨트롤을 추가하고 **그림 추가** 컨트롤에서 이동하고 **[단추](control-button.md)** 컨트롤에 대한 **[OnSelect](properties-core.md)** 속성을 이 수식으로 설정합니다.<br>
   **Collect(MyPix, AddMediaButton1.Media)**
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
4. **이미지 갤러리** 컨트롤을 추가하고 **[Items](properties-core.md)** 속성을 **MyPix**로 설정합니다.
5. F5 키를 누르고 **[단추](control-button.md)** 컨트롤을 클릭하거나 탭합니다.
   
    **이미지 추가** 컨트롤의 이미지가 **이미지 갤러리** 컨트롤에 나타납니다. 이미지가 **Image gallery** 컨트롤에서 가로 세로 비율이 **[이미지](control-image.md)** 와 동일하지 않을 경우, **[Image](control-image.md)** 컨트롤의 **[ImagePosition](properties-visual.md)** 속성을 **Fit**로 설정합니다.
6. **이미지 추가** 컨트롤을 클릭하거나 탭하고 다른 이미지 파일을 클릭하거나 탭하고, **열기**를 클릭하거나 탭한 다음, 사용자가 추가한 **[단추](control-button.md)** 컨트롤을 클릭하거나 탭합니다.
   
    두 번째 이미지가 **이미지 갤러리** 컨트롤에 나타납니다.
7. (선택 사항) 이전 단계를 1회 이상 반복한 다음, Esc 키를 눌러 기본 작업 영역으로 돌아갑니다.

**[SaveData](../functions/function-savedata-loaddata.md)** 함수를 사용하여 이미지를 로컬에서 저장하거나, **[Patch](../functions/function-patch.md)** 함수를 사용하여 데이터 원본을 업데이트합니다.


## <a name="accessibility-guidelines"></a>접근성 지침
**[단추](control-button.md)** 및 **[이미지](control-image.md)** 에 대해 동일한 지침이 적용됩니다. 또한 다음을 고려하세요.

### <a name="color-contrast"></a>색 대비
* **미디어 단추 추가**에는 텍스트와 배경 사이에 적절한 대비가 있어야 합니다. 업로드된 이미지의 색은 다양할 수 있으므로 **미디어 단추 추가**에서 불투명 **[Fill](properties-color-border.md)** 을 사용하여 일관적인 대비를 보장합니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **미디어 단추 추가**에는 사용자에게 이미지를 추가하거나 변경할지 묻는 메시지를 표시하는 **Text** 및 **ChangePictureText**가 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* **미디어 단추 추가**에는 키보드 사용자가 탐색할 수 있도록 0 이상의 **[TabIndex](properties-accessibility.md)** 가 있어야 합니다.
* **미디어 단추 추가**에는 명확하게 표시되는 포커스 표시기가 있어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
 
