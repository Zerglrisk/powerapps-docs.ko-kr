---
title: 핵심 속성 | Microsoft Docs
description: Disabled, Visible 및 ReadOnly 속성에 관한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 16065dc29d74655cbede25cea20148b343b790e6
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560349"
---
# <a name="core-properties-in-powerapps"></a>PowerApps의 핵심 속성
사용자가 컨트롤을 보고 상호 작용할 수 있는지 여부를 구성합니다.

### <a name="properties"></a>속성
**Default** – 사용자가 변경하기 전에 컨트롤의 초기 값입니다.

* **[Card](control-card.md)**, **[Check box](control-check-box.md)**, **[Drop down](control-drop-down.md)**, **[Gallery](control-gallery.md)**, **[List Box](control-list-box.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)** 및 **[Toggle](control-toggle.md)** 컨트롤에 적용됩니다.

**DelayOutput** – 텍스트를 입력하는 동안 작업을 지연하려면 true로 설정합니다.

* **[Text input](control-text-input.md)**, **[Card](control-card.md)** 에 적용됩니다.

**DisplayMode** – 값은 **Edit, View,** 또는 **Disabled**가 될 수 있습니다. 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 구성합니다.  **보기** 모드에서 **[텍스트 입력](control-text-input.md)**, **[드롭다운](control-drop-down.md)**, **[날짜 선택기](control-date-picker.md)** 등의 입력 컨트롤은 텍스트 값만 표시하고 다른 대화형 요소 또는 장식을 렌더링하지 않습니다.  따라서 양식 또는 읽기 가능한 출력으로 표시하기에 적합해집니다.

* **[Add picture](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Button](control-button.md)**, **[Camera](control-camera.md)**, **[Check box](control-check-box.md)**, **[Column chart](control-column-line-chart.md)**, **[Date Picker](control-date-picker.md)**, **[Drop down](control-drop-down.md)**, **[Export](control-export-import.md)**, **[Gallery](control-gallery.md)**, **[HTML text](control-html-text.md)**, **[Icon](control-shapes-icons.md)**, **[Image](control-image.md)**, **[Import](control-export-import.md)**, **[Label](control-text-box.md)**, **[Line chart](control-column-line-chart.md)**, **[List Box](control-list-box.md)**, **[Microphone](control-microphone.md)**, **[PDF viewer](control-pdf-viewer.md)**, **[Pen input](control-pen-input.md)**, **[Pie chart](control-pie-chart.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Shape](control-shapes-icons.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)**, **[Timer](control-timer.md)**, **[Toggle](control-toggle.md)** 및 **[Video](control-audio-video.md)** 컨트롤에 적용됩니다.

**Items** – 갤러리, 목록 또는 차트 등의 컨트롤에서 나타나는 데이터 원본입니다.

* **[Column chart](control-column-line-chart.md)**, **[Drop down](control-drop-down.md)**, **[Gallery](control-gallery.md)**, **[Line chart](control-column-line-chart.md)**, **[List Box](control-list-box.md)**, **[Pie chart](control-pie-chart.md)** 및 **[Radio](control-radio.md)** 컨트롤에 적용됩니다.

**OnChange** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

* **[Add picture](control-add-picture.md)**, **[Drop down](control-drop-down.md)**, **[List Box](control-list-box.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)** 및 **[Toggle](control-toggle.md)** 컨트롤에 적용됩니다.

**OnSelect** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

* **[Add picture](control-add-picture.md)**, **[Button](control-button.md)**, **[Camera](control-camera.md)**, **[Check box](control-check-box.md)**, **[Column chart](control-column-line-chart.md)**, **[Date Picker](control-date-picker.md)**, **[Drop down](control-drop-down.md)**, **[Export](control-export-import.md)**, **[HTML text](control-html-text.md)**, **[Icon](control-shapes-icons.md)**, **[Image](control-image.md)**, **[Import](control-export-import.md)**, **[Label](control-text-box.md)**, **[Line chart](control-column-line-chart.md)**, **[List Box](control-list-box.md)**, **[Microphone](control-microphone.md)**, **[PDF viewer](control-pdf-viewer.md)**, **[Pen input](control-pen-input.md)**, **[Pie chart](control-pie-chart.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Shape](control-shapes-icons.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)**, **[Timer](control-timer.md)** 및 **[Toggle](control-toggle.md)** 컨트롤에 적용됩니다.

**Reset** – 컨트롤을 기본값으로 되돌릴지 여부를 선택합니다.  또한 **[Reset](../functions/function-reset.md)** 함수도 참조하세요.

* **[Audio](control-audio-video.md)**, **[Check box](control-check-box.md)**, **[Drop down](control-drop-down.md)**, **[List Box](control-list-box.md)**, **[Microphone](control-microphone.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)**, **[Timer](control-timer.md)**, **[Toggle](control-toggle.md) ** 및 **[Video](control-audio-video.md)** 컨트롤에 적용됩니다.

**Text** – 컨트롤에 표시되는 텍스트 또는 사용자가 컨트롤에 입력하는 텍스트입니다.

* **[Add picture](control-add-picture.md)**, **[Button](control-button.md)**, **[Check box](control-check-box.md)**, **[Export](control-export-import.md)**, **[Import](control-export-import.md)**, **[Label](control-text-box.md)**, **[Text input](control-text-input.md)** 및 **[Timer](control-timer.md)** 컨트롤에 적용됩니다.

**Tooltip** – 사용자가 컨트롤을 마우스로 가리킬 때 나타나는 설명 텍스트입니다.

* **[Audio](control-audio-video.md)**, **[Button](control-button.md)**, **[Camera](control-camera.md)**, **[Check box](control-check-box.md)**, **[Drop down](control-drop-down.md)**, **[HTML text](control-html-text.md)**, **[Image](control-image.md)**, **[Label](control-text-box.md)**, **[List Box](control-list-box.md)**, **[Microphone](control-microphone.md)**, **[PDF viewer](control-pdf-viewer.md)**, **[Pen input](control-pen-input.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)**, **[Timer](control-timer.md)**, **[Toggle](control-toggle.md)** 및 **[Video](control-audio-video.md)** 컨트롤에 적용됩니다.

**Value** – 입력 컨트롤의 값입니다.

* **[Check box](control-check-box.md)**, **[Radio](control-radio.md)**, **[Slider](control-slider.md)** 및 **[Toggle](control-toggle.md)** 컨트롤에 적용됩니다.

**Visible** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

* **[Add picture](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Button](control-button.md)**, **[Camera](control-camera.md)**, **[Card](control-card.md)**, **[Check box](control-check-box.md)**, **[Column chart](control-column-line-chart.md)**, **[Date Picker](control-date-picker.md)**, **[Display form](control-form-detail.md)**, **[Drop down](control-drop-down.md)**, **[Edit form](control-form-detail.md)**, **[Export](control-export-import.md)**, **[Gallery](control-gallery.md)**, **[HTML text](control-html-text.md)**, **[Icon](control-shapes-icons.md)**, **[Image](control-image.md)**, **[Import](control-export-import.md)**, **[Label](control-text-box.md)**, **[Line chart](control-column-line-chart.md)**, **[List Box](control-list-box.md)**, **[Microphone](control-microphone.md)**, **[PDF viewer](control-pdf-viewer.md)**, **[Pen input](control-pen-input.md)**, **[Pie chart](control-pie-chart.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Shape](control-shapes-icons.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)**, **[Timer](control-timer.md)**, **[Toggle](control-toggle.md)** 및 **[Video](control-audio-video.md)** 컨트롤에 적용됩니다.

