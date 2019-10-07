---
title: '이미지 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 이미지 컨트롤에 대한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cc25c16e9d79a80a5a21f793e66ce1cbc38960cb
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993469"
---
# <a name="image-control-in-powerapps"></a>PowerApps의 이미지 컨트롤
로컬 파일이나 데이터 원본 등으로부터 이미지를 표시하는 컨트롤입니다.

## <a name="description"></a>설명
앱에 하나 이상의 **이미지** 컨트롤을 추가할 경우 데이터 집합에 속하지 않은 개별 이미지를 표시하거나 데이터 웝노의 레코드에서 이미지를 통합할 수 있습니다.

## <a name="key-properties"></a>주요 속성
**[Image](properties-visual.md)** – 이미지, 오디오 또는 마이크 컨트롤에 표시되는 이미지의 이름입니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**ApplyEXIFOrientation** – 이미지에 포함된 EXIF 데이터에 지정된 방향을 자동으로 적용할지 여부입니다.

**AutoDisableOnSelect** – OnSelect 동작이 실행되는 동안 컨트롤을 자동으로 비활성화합니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**CalculateOriginalDimensions** – **OriginalHeight** 및 **OriginalWidth** 속성을 사용하도록 설정합니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**FlipHorizontal** – 이미지를 표시하기 전에 이미지를 좌우 대칭 이동할지 여부입니다.

**FlipVertical** – 이미지를 표시하기 전에 이미지를 상하 대칭 이동할지 여부입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[ImagePosition](properties-visual.md)** – 이미지와 같은 크기가 아닌 경우 컨트롤 또는 화면에 있는 이미지의 위치입니다(**채우기**, **맞춤**, **늘이기**, **타일** 또는 **가운데**).

**ImageRotation** – 이미지를 표시하기 전에 회전시키는 방법입니다.  값은 없음, 시계 방향(CW) 90도, 시계 반대 방향(CCW) 90도 및 시계 방향 180도로 설정할 수 있습니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**OriginalHeight** – **CalculateOriginalDimensions** 속성으로 활성화된 이미지의 원래 높입니다.

**OriginalWidth** – **CalculateOriginalDimensions** 속성으로 활성화된 이미지의 원래 높입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 하단 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingTop](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 위쪽 가장자리 사이의 거리입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[RadiusBottomLeft](properties-size-location.md)** – 컨트롤 왼쪽 아래 모서리의 둥근 정도입니다.

**[RadiusBottomRight](properties-size-location.md)** – 컨트롤 오른쪽 아래 모서리의 둥근 정도입니다.

**[RadiusTopLeft](properties-size-location.md)** – 컨트롤 왼쪽 위 모서리의 둥근 정도입니다.

**[RadiusTopRight](properties-size-location.md)** – 컨트롤 오른쪽 위 모서리의 둥근 정도입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**Transparency** –이미지 뒤의 컨트롤을 그대로 표시하는 수준입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**Remove**( *DataSource*, ThisItem )](../functions/function-remove-removeif.md)

## <a name="examples"></a>예
### <a name="show-an-image-from-a-local-file"></a>로컬 파일에서 이미지 표시
1. **파일** 메뉴에서 **미디어**를 클릭하거나 탭한 다음, **찾아보기**를 클릭하거나 탭합니다.
2. 추가할 이미지 파일을 클릭하거나 터치하고, **열기**를 클릭하거나 터치한 다음, 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.
3. **이미지** 컨트롤을 추가하고 **이미지** 속성을 추가한 파일의 이름으로 설정합니다.

    [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 방법을 모르시나요?

    **이미지** 컨트롤은 사용자가 지정한 이미지를 보여 줍니다.

### <a name="show-a-set-of-images-from-a-data-source"></a>데이터 원본에서 이미지 집합 표시
1. 이 [Excel 파일](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx)을 다운로드하고 로컬 디바이스에 저장합니다.
2. PowerApps Studio에서 앱을 만들거나 연 다음 오른쪽 창에서 **데이터 원본 추가**를 클릭하거나 터치합니다.

    **데이터 원본 추가**가 오른쪽 창에 표시되지 않으면 왼쪽 탐색 표시줄에서 화면을 클릭하거나 터치합니다.
3. **앱에 정적 데이터 추가**를 클릭하거나 탭하고, 다운로드한 Excel 파일을 클릭하거나 탭한 다음 **열기**를 클릭하거나 탭합니다.
4. **FlooringEstimates** 확인란을 선택한 다음 **연결**을 클릭하거나 터치합니다.
5. 이미지가 있는 **갤러리** 컨트롤을 추가하고 **[Items](properties-core.md)** 속성을 **FlooringEstimates**로 설정합니다.

    [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 방법을 모르시나요?

    **갤러리** 컨트롤은 다운로드한 Exccel 파일의 링크를 기준으로 카페트, 하드우드에어 및 타일 제품의 이미지를 보여줍니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
* 그래픽이 단추로 사용되는 경우 [표준 색 대비 요구 사항](../accessible-apps-color.md)이 적용됩니다.
* 장식용으로만 사용되지 않는 경우 이미지 내에서 대비 문제를 확인하는 것이 좋습니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* 그래픽이 단추로 사용되거나 장식용으로만 사용되지 않는 경우에는 **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.
* 그래픽이 장식용으로만 사용되는 경우 **[AccessibleLabel](properties-accessibility.md)** 은 비어 있거나 빈 문자열 **""** 이어야 합니다. 이렇게 하면 화면 읽기 프로그램이 그래픽을 무시합니다.
* 그래픽이 중복 정보를 제공하는 경우 **[AccessibleLabel](properties-accessibility.md)** 은 비어 있거나 빈 문자열 **""** 일 수 있습니다.
  * 예를 들어 **[AccessibleLabel](properties-accessibility.md)** 이 **설정**으로 설정된 기어의 **이미지**가 있습니다. 이 이미지는 단추로 사용되지 않습니다. **설정**으로도 표시된 **[레이블](control-text-box.md)** 옆에 있습니다. 화면 읽기 프로그램은 이미지를 **설정**으로 읽고 레이블을 다시 **설정**으로 읽습니다. 이는 불필요하게 자세한 정보입니다. 이 경우 **이미지**에는 **[AccessibleLabel](properties-accessibility.md)** 이 필요하지 않습니다.

    > [!IMPORTANT]
    > 화면 읽기 프로그램은 **[AccessibleLabel](properties-accessibility.md)** 이 비어 있는 경우에도 항상 0 이상의 **[TabIndex](properties-accessibility.md)** 가 있는 **이미지**를 읽습니다. 이는 이미지가 단추로 렌더링되기 때문입니다. **[AccessibleLabel](properties-accessibility.md)** 이 제공되지 않으면 화면 읽기 프로그램은 그래픽을 **단추**로만 읽습니다.

### <a name="keyboard-support"></a>키보드 지원
* 그래픽이 단추로 사용되는 경우 **[TabIndex](properties-accessibility.md)** 는 0 이상이어야 합니다. 이 경우 키보드 사용자가 이미지로 이동할 수 있습니다.
* 그래픽이 단추로 사용되는 경우 포커스 표시기는 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.

    > [!NOTE]
  > **[TabIndex](properties-accessibility.md)** 가 0 이상이면 **이미지**가 단추로 렌더링됩니다. 시각적 모양은 변경되지 않지만 화면 읽기 프로그램은 이미지를 단추로 올바르게 식별합니다. **[TabIndex](properties-accessibility.md)** 가 0보다 작으면 **이미지**가 이미지로 식별됩니다.
