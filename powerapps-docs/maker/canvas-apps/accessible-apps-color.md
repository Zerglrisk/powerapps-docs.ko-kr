---
title: 캔버스의 액세스 가능한 색 | Microsoft Docs
description: Power Apps의 canvas 앱에 대 한 색 대비 지침
author: tahoon
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/23/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 26fd45efc56ad03bc37635c29ddc7a6dbbe71568
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725366"
---
# <a name="accessible-colors-for-canvas-apps-in-power-apps"></a>Power Apps의 캔버스 앱에 대 한 액세스 가능한 색
캔버스 앱에서 사용되는 색은 색맹 및 저시력 사용자가 액세스할 수 있어야 합니다. 모든 Power Apps 테마는 기본적으로 액세스할 수 있습니다. 앱에서 사용되는 색을 수정할 경우 다음 지침에 따라 색에 계속 액세스할 수 있는지 확인합니다. 색 대비 문제를 식별하는 데 도움이 되는 온라인으로 사용 가능한 여러 도구가 있습니다.

## <a name="minimum-contrast-for-text"></a>텍스트에 대한 최소 대비
* 텍스트 및 배경의 대비 비율은 4.5:1 이상이어야 합니다.
* 큰 텍스트의 대비 비율은 3:1 이상이어야 합니다.
* 비활성 텍스트에는 대비 요구 사항이 없습니다.

실제로 모든 대화형 컨트롤에는 다음 사이에 적절한 색 대비가 있어야 합니다.
* **[Color](controls/properties-color-border.md)** 및 **[Fill](controls/properties-color-border.md)**
* **[PressedColor](controls/properties-color-border.md)** 및 **[PressedFill](controls/properties-color-border.md)**
* **[HoverColor](controls/properties-color-border.md)** 및 **[HoverFill](controls/properties-color-border.md)**

## <a name="minimum-contrast-for-non-text"></a>텍스트 이외 항목에 대한 최소 대비

> [!NOTE]
> [WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html) 표준에서 대비 요구 사항은 텍스트에만 적용됩니다. 접근성을 높이려면 아이콘 단추와 같은 필수 사용자 인터페이스 구성 요소에 대한 제공 예정인 [WCAG 2.1 대비 지침](https://www.w3.org/TR/WCAG21/#non-text-contrast)을 고려하세요. 이러한 구성 요소에는 최소 비율 3:1이 권장됩니다. 이 섹션에 설명 된 지침은 WCAG 2.0 규정 준수에 대 한 **선택 사항** 입니다.

### <a name="user-interface-components"></a>사용자 인터페이스 구성 요소
모든 대화형 컨트롤에는 다음 사이에 적절한 색 대비가 있어야 합니다.
* **[FocusedBorderColor](controls/properties-color-border.md)** 및 컨트롤 외부 색

추가적인 색 대비 확인은 전체 영역이 대화형이거나 참조용인 컨트롤에 적용됩니다. 예를 들어 **[단추](controls/control-button.md)** 또는 단추로 사용되는 **[아이콘](controls/control-shapes-icons.md)** 이 있습니다. 이렇게 하면 컨트롤의 경계가 분명해지고 사용자가 클릭하거나 탭할 수 있는 위치를 알 수 있습니다.

해당 컨트롤에 테두리가 있는 경우 다음 사이에 적절한 색 대비가 있어야 합니다.
* **[BorderColor](controls/properties-color-border.md)** 및 컨트롤 외부 색
* **[PressedBorderColor](controls/properties-color-border.md)** 및 컨트롤 외부 색
* **[HoverBorderColor](controls/properties-color-border.md)** 및 컨트롤 외부 색

테두리가 없는 경우 다음 사이에 적절한 색 대비가 있어야 합니다.
* **[Fill](controls/properties-color-border.md)** 및 컨트롤 외부 색
* **[PressedFill](controls/properties-color-border.md)** 및 컨트롤 외부 색
* **[HoverFill](controls/properties-color-border.md)** 및 컨트롤 외부 색

### <a name="graphical-objects"></a>그래픽 개체
이미지가 중요한 정보를 전달하는 경우 대비 문제를 확인하는 것이 좋습니다. 이 내용은 이미지가 표시될 수 있는 **[오디오](controls/control-audio-video.md)** , **[이미지](controls/control-image.md)** , **[마이크](controls/control-microphone.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

비디오 콘텐츠의 경우 대비 문제를 확인하는 것이 좋습니다. 또는 비디오를 설명하는 [선택 자막](controls/control-audio-video.md)을 추가할 수도 있습니다.

## <a name="provide-other-visual-cues"></a>다른 시각 신호 제공
앱이 색으로만 정보를 전달하지 않는지 확인합니다. 예를 들어 적록 색맹이 있는 사용자는 녹색 성공 메시지에서 빨간색 오류 메시지를 구분할 수 없습니다.

**[아이콘](controls/control-shapes-icons.md)** 같은 추가적인 신호나 **[기울임꼴](controls/properties-text.md)** 및 **[밑줄](controls/properties-text.md)** 같은 텍스트 스타일이 의미를 전달하는 데 도움이 될 수 있습니다.

## <a name="next-steps"></a>다음 단계
파워 앱 컨트롤의 [접근성 속성](controls/properties-accessibility.md) 에 대해 알아보고 [내게 필요한 옵션 검사기를](accessibility-checker.md)사용해 보세요.
