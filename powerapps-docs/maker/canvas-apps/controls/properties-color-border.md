---
title: 색 및 테두리 속성 | Microsoft Docs
description: BorderColor, HoverBorderColor 및 PressedBorderColor와 같은 속성에 대한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 528dc54fe18971ff8971b4d0d7e87c3bf3c5367a
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986038"
---
# <a name="color-and-border-properties-in-powerapps"></a>PowerApps에서 색 및 테두리 속성

## <a name="overview"></a>개요

사용자가 상호 작용하는 방법에 따라 컨트롤의 스타일을 구성합니다.

다음과 같은 여러 가지 방법으로 색을 지정할 수 있습니다.

- [**색**](../functions/function-colors.md) 열거: 다음 예와 같이 css 스타일 시트에서 색 이름을 지정 합니다.

  - **Color.Red**
  - **Color.Indigo**

- [**Colorvalue**](../functions/function-colors.md) 함수: 다음 예와 같이 css 스타일 시트에서 색 이름과 같은 텍스트 문자열 및 16 진수 코드 표기법 ( **#** )을 지정 합니다.

  - **ColorValue ("AliceBlue")**
  - **ColorValue( "#ff00ff" )**

- [**Colorfade**](../functions/function-colors.md) 함수: 색의 밝기를 완전히 검정에서 (-100%)로 지정 합니다. 다음 예와 같이 완전히 흰색 (100%)으로

  - **ColorFade (색. 빨강, 50%)**

- [**RGBA**](../functions/function-colors.md) 함수: 이 예제와 같이 색의 빨간색, 녹색 및 파랑 구성 요소를 0에서 255 사이의 색으로 지정 하 고 0% (완전히 투명 한)에서 100% (완전히 불투명)로 알파 채널을 지정 합니다.

  - **RGBA (255, 0, 255, 25%)**

색 속성은 다른 색 속성도 참조할 수 있습니다. 예를 들어 **Label. 보도 색** 은 수식 **Label1. color**로 설정 될 수 있으며, 한 속성에서 다른 속성으로 변경 내용을 자동으로 연계 합니다.

## <a name="normal"></a>보통

이러한 속성은 사용자가 컨트롤과 상호 작용하고 있지 않는 경우 일반적으로 적용됩니다.

**BorderColor** - 컨트롤의 테두리 색입니다.

- **[Add picture](control-add-picture.md)** , **[Audio](control-audio-video.md)** , **[Button](control-button.md)** , **[Camera](control-camera.md)** , **[Card](control-card.md)** , **[Check box](control-check-box.md)** , **[Column chart](control-column-line-chart.md)** , **[Date Picker](control-date-picker.md)** , **[Display form](control-form-detail.md)** , **[Drop down](control-drop-down.md)** , **[Edit form](control-form-detail.md)** , **[Export](control-export-import.md)** , **[Gallery](control-gallery.md)** , **[HTML text](control-html-text.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[Line chart](control-column-line-chart.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[PDF viewer](control-pdf-viewer.md)** , **[Pen input](control-pen-input.md)** , **[Pie chart](control-pie-chart.md)** , **[Radio](control-radio.md)** , **[Rating](control-rating.md)** , **[Slider](control-slider.md)** , **[Text input](control-text-input.md)** , **[Timer](control-timer.md)** , **[Toggle](control-toggle.md)** 및 **[Video](control-audio-video.md)** 컨트롤에 적용됩니다.

**BorderStyle** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted** 또는 **None**입니다.

- **[Add picture](control-add-picture.md)** , **[Audio](control-audio-video.md)** , **[Button](control-button.md)** , **[Camera](control-camera.md)** , **[Card](control-card.md)** , **[Check box](control-check-box.md)** , **[Column chart](control-column-line-chart.md)** , **[Date Picker](control-date-picker.md)** , **[Display form](control-form-detail.md)** , **[Drop down](control-drop-down.md)** , **[Edit form](control-form-detail.md)** , **[Export](control-export-import.md)** , **[Gallery](control-gallery.md)** , **[HTML text](control-html-text.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[Line chart](control-column-line-chart.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[PDF viewer](control-pdf-viewer.md)** , **[Pen input](control-pen-input.md)** , **[Pie chart](control-pie-chart.md)** , **[Radio](control-radio.md)** , **[Rating](control-rating.md)** , **[Slider](control-slider.md)** , **[Text input](control-text-input.md)** , **[Timer](control-timer.md)** , **[Toggle](control-toggle.md)** 및 **[Video](control-audio-video.md)** 컨트롤에 적용됩니다.

**BorderThickness** - 컨트롤의 테두리 굵기입니다.

- **[Add picture](control-add-picture.md)** , **[Audio](control-audio-video.md)** , **[Button](control-button.md)** , **[Camera](control-camera.md)** , **[Card](control-card.md)** , **[Check box](control-check-box.md)** , **[Column chart](control-column-line-chart.md)** , **[Date Picker](control-date-picker.md)** , **[Display form](control-form-detail.md)** , **[Drop down](control-drop-down.md)** , **[Edit form](control-form-detail.md)** , **[Export](control-export-import.md)** , **[Gallery](control-gallery.md)** , **[HTML text](control-html-text.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[Line chart](control-column-line-chart.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[PDF viewer](control-pdf-viewer.md)** , **[Pen input](control-pen-input.md)** , **[Pie chart](control-pie-chart.md)** , **[Radio](control-radio.md)** , **[Rating](control-rating.md)** , **[Slider](control-slider.md)** , **[Text input](control-text-input.md)** , **[Timer](control-timer.md)** , **[Toggle](control-toggle.md)** 및 **[Video](control-audio-video.md)** 컨트롤에 적용됩니다.

**Color** – 컨트롤의 텍스트 색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Column chart](control-column-line-chart.md)** , **[Date Picker](control-date-picker.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[HTML text](control-html-text.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[Line chart](control-column-line-chart.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[Pen input](control-pen-input.md)** , **[Pie chart](control-pie-chart.md)** , **[Radio](control-radio.md)** , **[Text input](control-text-input.md)** 및 **[Timer](control-timer.md)** 컨트롤에 적용됩니다.

**Fill** - 컨트롤의 배경색입니다.

- **[Add picture](control-add-picture.md)** , **[Audio](control-audio-video.md)** , **[Button](control-button.md)** , **[Card](control-card.md)** , **[Check box](control-check-box.md)** , **[Date Picker](control-date-picker.md)** , **[Display form](control-form-detail.md)** , **[Drop down](control-drop-down.md)** , **[Edit form](control-form-detail.md)** , **[Export](control-export-import.md)** , **[Gallery](control-gallery.md)** , **[HTML text](control-html-text.md)** , **[Icon](control-shapes-icons.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[PDF viewer](control-pdf-viewer.md)** , **[Pen input](control-pen-input.md)** , **[Radio](control-radio.md)** , **[Rating](control-rating.md)** , **[Screen](control-screen.md)** , **[Shape](control-shapes-icons.md)** , **[Text input](control-text-input.md)** , **[Timer](control-timer.md)** , **[Toggle](control-toggle.md)** 및 **[Video](control-audio-video.md)** 컨트롤에 적용됩니다.

## <a name="focused"></a>Focused

이러한 속성은 컨트롤에 포커스가 있을 때 적용됩니다.

**FocusedBorderColor** – 컨트롤에 포커스가 있을 때 컨트롤 테두리의 색입니다.

**FocusedBorderThickness** - 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

- 이러한 속성은 **[그림 추가](control-add-picture.md)** , **[첨부 파일](control-attachments.md)** , **[오디오](control-audio-video.md)** , **[단추](control-button.md)** , **[카메라](control-camera.md)** , **[확인란](control-check-box.md)** , **[콤보 상자](control-combo-box.md)** , **[날짜 선택기](control-date-picker.md)** , **[드롭다운](control-drop-down.md)** , **[내보내기](control-export-import.md)** , **[갤러리](control-gallery.md)** , **[아이콘](control-shapes-icons.md)** , **[이미지](control-image.md)** , **[가져오기](control-export-import.md)** , **[레이블](control-text-box.md)** , **[목록 상자](control-list-box.md)** , **[마이크](control-microphone.md)** , **[라디오](control-radio.md)** , **[평가](control-rating.md)** , **[셰이프](control-shapes-icons.md)** , **[슬라이더](control-slider.md)** , **[텍스트 입력](control-text-input.md)** , **[타이머](control-timer.md)** , **[토글](control-toggle.md)** 및 **[비디오](control-audio-video.md)** 컨트롤에 적용됩니다.

## <a name="disabled"></a>사용 안 함

이러한 속성은 컨트롤이 사용하지 않도록 설정된 경우 적용됩니다.  **[Disabled](properties-core.md)** 속성이 *true*로 설정된 경우 컨트롤은 비활성화될 수 있습니다.

**DisabledBorderColor** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Column chart](control-column-line-chart.md)** , **[Date Picker](control-date-picker.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[HTML text](control-html-text.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[ Label](control-text-box.md)** , **[Line chart](control-column-line-chart.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[PDF viewer](control-pdf-viewer.md)** , **[Pie chart](control-pie-chart.md)** , **[Radio](control-radio.md)** , **[Slider](control-slider.md)** , **[Text input](control-text-input.md)** , **[Timer](control-timer.md)**  및 **[Toggle](control-toggle.md)** 컨트롤에 적용됩니다.

**DisabledColor** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Date Picker](control-date-picker.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[Radio](control-radio.md)** , **[Text input](control-text-input.md)** 및 **[Timer](control-timer.md)** 컨트롤에 적용됩니다.

**DisabledFill** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Date Picker](control-date-picker.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[HTML text](control-html-text.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[Radio](control-radio.md)** , **[Text input](control-text-input.md)** 및 **[Timer](control-timer.md)** 컨트롤에 적용됩니다.

## <a name="hover"></a>마우스로 가리키기

이러한 속성은 사용자가 마우스로 컨트롤을 가리킬 때 적용됩니다.

**HoverBorderColor** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Column chart](control-column-line-chart.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[HTML text](control-html-text.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[Line chart](control-column-line-chart.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[PDF viewer](control-pdf-viewer.md)** , **[Pie chart](control-pie-chart.md)** , **[Slider](control-slider.md)** , **[Text input](control-text-input.md)** , **[Timer](control-timer.md)** 및 **[Toggle](control-toggle.md)** 컨트롤에 적용됩니다.

**HoverColor** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[Radio](control-radio.md)** , **[Text input](control-text-input.md)** 및 **[Timer](control-timer.md)** 컨트롤에 적용됩니다.

**HoverFill** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[Icon](control-shapes-icons.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[Radio](control-radio.md)** , **[Shape](control-shapes-icons.md)** , **[Text input](control-text-input.md)** 및 **[Timer](control-timer.md)** 컨트롤에 적용됩니다.

## <a name="pressed"></a>누름

이러한 속성은 단추 또는 이미지 컨트롤을 누를 때 적용됩니다.

**PressedBorderColor** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Column chart](control-column-line-chart.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[Icon](control-shapes-icons.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[Line chart](control-column-line-chart.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[PDF viewer](control-pdf-viewer.md)** , **[Pie chart](control-pie-chart.md)** , **[Shape](control-shapes-icons.md)** , **[Slider](control-slider.md)** , **[Text input](control-text-input.md)** , **[Timer](control-timer.md)** 및 **[Toggle](control-toggle.md)** 컨트롤에 적용됩니다.

**PressedColor** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[Radio](control-radio.md)** , **[Text input](control-text-input.md)** 및 **[Timer](control-timer.md)** 컨트롤에 적용됩니다.

**PressedFill** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

- **[Add picture](control-add-picture.md)** , **[Button](control-button.md)** , **[Check box](control-check-box.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[Radio](control-radio.md)** , **[Text input](control-text-input.md)** 및 **[Timer](control-timer.md)** 컨트롤에 적용됩니다.

## <a name="selection"></a>선택

이러한 속성은 사용자가 컨트롤에서 항목을 선택할 때 적용됩니다.

**SelectionColor** – 목록에서 선택한 항목의 텍스트 색 또는 펜 컨트롤에서 선택 도구의 색입니다.

- **[Drop down](control-drop-down.md)** , **[List Box](control-list-box.md)** 및 **[Pen input](control-pen-input.md)** 컨트롤에 적용됩니다.

**SelectionFill** – 펜 컨트롤의 목록 또는 선택한 영역에서 선택한 항목 또는 항목의 배경색입니다.

- **[Drop down](control-drop-down.md)** 및 **[List Box](control-list-box.md)** 컨트롤에 적용됩니다.