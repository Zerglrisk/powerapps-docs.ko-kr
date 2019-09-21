---
title: 속성 찾기 | Microsoft Docs
description: 컨트롤별, 범주별 또는 사전순으로 속성을 찾습니다.
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm-msft
ms.date: 9/20/2019
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dfed631c695cd764396a24311826bedc63eacffb
ms.sourcegitcommit: 7016ff837eff2cb0985fc71edab95cbf99335677
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71159849"
---
# <a name="controls-and-properties-in-powerapps"></a>PowerApps 컨트롤 및 속성

속성 중 하나를 설정하여 컨트롤의 모양과 동작을 구성합니다. 각 유형의 컨트롤에는 서로 다른 속성 집합이 있습니다. **Height** 및 **Width**와 같은 일부 속성은 거의 모든 유형의 컨트롤에 공통으로 적용되지만, **CheckboxSize**와 같은 다른 속성은 한 유형의 컨트롤에만 적용됩니다.

## <a name="controls"></a>컨트롤

**[그림 추가](controls/control-add-picture.md)** – 로컬 디바이스에서 이미지를 로드하여 데이터 원본에 업로드합니다.

**[첨부 파일](controls/control-attachments.md)** – 로컬 디바이스에서 데이터 원본으로 파일을 다운로드하고 업로드합니다.

**[오디오](controls/control-audio-video.md)** – 오디오 클립 또는 비디오 클립의 오디오 부분을 재생합니다.

**[바코드 스캐너](controls/control-new-barcode-scanner.md)** – Android 또는 iOS 장치에서 바코드, QR 코드 및 데이터 행렬 코드를 스캔 합니다.

**[단추](controls/control-button.md)** – 클릭하거나 탭하여 앱과 상호 작용합니다.

**[카메라](controls/control-camera.md)** – 앱 또는 데이터 원본에서 사진을 찍어 저장합니다.

**[카드](controls/control-card.md)** – **[편집 양식](controls/control-form-detail.md)** 또는 **[표시 양식](controls/control-form-detail.md)** 컨트롤에서 레코드의 개별 필드를 표시하고 편집합니다.

**[확인란](controls/control-check-box.md)** – **true** 또는 **false**를 지정하는 옵션을 선택하거나 선택 취소합니다.

**[세로 막대형 차트](controls/control-column-line-chart.md)** – 두 축을 기준으로 값을 세로 막대로 표시합니다.

**[열](controls/control-column.md)** - [**데이터 테이블**](controls/control-data-table.md) 컨트롤에서 단일 필드에 대한 표시 환경을 제공합니다.

**[콤보 상자](controls/control-combo-box.md)** - 사용자가 제공된 선택 항목 중에서 선택할 수 있도록 합니다. 검색 및 다중 선택을 지원합니다.

**[컨테이너 (실험적)](controls/control-container.md)** -접근성 및 응답성을 위해 중첩 계층을 만듭니다. 

**[데이터 테이블](controls/control-data-table.md)** - 데이터를 테이블 형식으로 표시합니다.

**[날짜 선택](controls/control-date-picker.md)** – 클릭하거나 탭하여 날짜를 지정합니다.

**[표시 양식](controls/control-form-detail.md)** – 양식을 사용하여 데이터 원본의 레코드를 표시합니다.

**[드롭다운](controls/control-drop-down.md)** – 갈매기형을 선택할 때까지 목록의 첫 번째 항목을 표시합니다.

**[편집 양식](controls/control-form-detail.md)** – 양식을 사용하여 데이터 원본의 레코드를 편집하고 만듭니다.

**[엔터티 폼](entity-form-control.md)** -실험적 기능: 사용자가 Common Data Service에서 관계형 데이터를 보고, 탐색 하 고, 편집할 수 있는 동적 양식을 추가 합니다.

**[내보내기](controls/control-export-import.md)** – PowerApps의 다른 위치에서 사용할 데이터를 내보냅니다.

**[갤러리](controls/control-gallery.md)** – 여러 형식의 데이터를 포함할 수 있는 레코드 목록을 표시합니다.

**[HTML 텍스트](controls/control-html-text.md)** – HTML 태그를 자동으로 변환합니다.

**[아이콘](controls/control-shapes-icons.md)** – 그래픽 효과와 시각적 효과를 추가합니다.

**[이미지](controls/control-image.md)** – 로컬 파일 또는 데이터 원본 등에서 이미지를 표시하는 컨트롤입니다.

**[가져오기](controls/control-export-import.md)** – PowerApps의 다른 위치에서 데이터를 가져옵니다.

**[꺾은선형 차트](controls/control-column-line-chart.md)** – 두 축을 기준으로 값을 데이터 요소로 표시합니다.

**[목록 상자](controls/control-list-box.md)** – 목록에서 하나 이상의 항목을 선택합니다.

**[마이크](controls/control-microphone.md)** – 앱 또는 데이터 원본에 소리를 녹음하고 저장합니다.

**[PDF 뷰어(실험적)](controls/control-pdf-viewer.md)** – 인터넷에서 PDF 파일의 내용을 표시합니다.

**[펜 입력](controls/control-pen-input.md)** – 이미지 또는 텍스트를 그리고, 앱 또는 데이터 원본에 저장합니다.

**[원형 차트](controls/control-pie-chart.md)** – 값 간의 관계를 표시합니다.

**[Power BI 타일](controls/control-power-bi-tile.md)** – 앱 내에 Power BI 타일을 표시합니다.

**[라디오](controls/control-radio.md)** – 상호 배타적인 옵션을 표시합니다.

**[등급](controls/control-rating.md)** – 1과 지정한 숫자 사이의 값을 나타냅니다.

**[서식 있는 텍스트 편집기](controls/control-richtexteditor.md)** – 앱 사용자에의 한 서식 있는 텍스트 서식 지정을 허용 합니다.

**[화면](controls/control-screen.md)** – 특정 작업에 대한 데이터를 표시하고 업데이트합니다.

**[도형](controls/control-shapes-icons.md)** – 화살표 및 기하학적 도형(예: 사각형)을 표시합니다.

**[슬라이더](controls/control-slider.md)** – 핸들을 끌어 값을 지정합니다.

**[레이블](controls/control-text-box.md)** – 텍스트, 숫자, 날짜 또는 통화와 같은 데이터를 표시합니다.

**[텍스트 입력](controls/control-text-input.md)** – 텍스트, 숫자 및 기타 데이터를 입력합니다.

**[타이머](controls/control-timer.md)** – 일정 시간이 지난 후에 응답하도록 앱을 구성합니다.

**[토글](controls/control-toggle.md)** – 핸들을 끌어 **true** 또는 **false**를 지정합니다.

**[비디오](controls/control-audio-video.md)** – 로컬 파일, 데이터 원본 또는 YouTube에서 비디오 클립을 재생합니다.

**[웹 바코드 스캐너 (실험적)](controls/control-barcodescanner.md)** – 사용 되지 않지만 웹 브라우저에서 코드를 검사 하는 데 유용할 수 있는 레거시 바코드 스캐너입니다.

## <a name="common-properties-by-category"></a>범주별 공용 속성

**[색 및 테두리](controls/properties-color-border.md)** – 사용자가 컨트롤과 상호 작용할 때 변경할 수 있는 컨트롤의 색과 테두리를 구성합니다.

**[코어](controls/properties-core.md)** – 사용자가 컨트롤을 보고 상호 작용할 수 있는지 여부를 구성합니다.

**[이미지](controls/properties-visual.md)** – 표시되는 이미지 및 컨트롤을 채우는 방법을 구성합니다.

**[크기 및 위치](controls/properties-size-location.md)** – 컨트롤(또는 컨트롤 요소)의 크기와 해당 컨트롤이 있는 화면과 관련된 위치를 구성합니다.

**[텍스트](controls/properties-text.md)** – 글꼴 특성, 맞춤, 선 높이 등과 같이 텍스트가 컨트롤에 표시되는 방식을 구성합니다.  

## <a name="all-properties"></a>모든 속성

### <a name="a"></a>A

**[ActualZoom](controls/control-pdf-viewer.md)** - 컨트롤의 실제 확대/축소이며, **Zoom** 속성으로 요청된 확대/축소와 다를 수 있습니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[Align](controls/properties-text.md)** - 컨트롤의 가로 가운데를 기준으로 한 텍스트의 위치입니다.  많은 컨트롤에 적용됩니다.

**[AllItems](controls/control-gallery.md)** – 갤러리 템플릿의 일부인 추가 컨트롤 값을 포함하는 갤러리의 모든 항목입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**AutoDisableOnSelect** – OnSelect 동작이 실행되는 동안 컨트롤을 자동으로 비활성화합니다.  **[단추](controls/control-button.md)** 및 **[이미지](controls/control-image.md)** 컨트롤에 적용됩니다.

**[AutoHeight](controls/properties-size-location.md)** – 컨트롤에서 표시할 수 있는 것보다 더 많은 문자가 해당 **[Text](controls/properties-core.md)** 속성에 포함된 경우 레이블의 높이를 자동으로 증가할지 여부입니다. **[레이블](controls/control-text-box.md)** 컨트롤에 적용됩니다.

**AutoPause** – 사용자가 다른 화면으로 이동하는 경우 오디오 또는 비디오 클립을 자동으로 일시 중지할지 여부입니다.  **[오디오](controls/control-audio-video.md)** , **[타이머](controls/control-timer.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**AutoStart** - 사용자가 해당 컨트롤이 포함된 화면으로 이동할 때 오디오 또는 비디오 컨트롤에서 클립을 자동으로 재생할지 여부입니다.  **[오디오](controls/control-audio-video.md)** , **[타이머](controls/control-timer.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

### <a name="b"></a>B

**[BackgroundImage](controls/properties-visual.md)** – 화면의 배경에 표시되는 이미지 파일의 이름입니다.  **[화면](controls/control-screen.md)** 컨트롤에 적용됩니다.

**[BorderColor](controls/properties-color-border.md)** - 컨트롤의 테두리 색입니다.  많은 컨트롤에 적용됩니다.

**[BorderStyle](controls/properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.  많은 컨트롤에 적용됩니다.

**[BorderThickness](controls/properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.  많은 컨트롤에 적용됩니다.

**[Brightness](controls/control-camera.md)** – 사용자가 이미지에서 인식할 가능성이 높은 조명의 정도를 선택합니다.  **[카메라](controls/control-camera.md)** 컨트롤에 적용됩니다.

### <a name="c"></a>C

**[CalculateOriginalDimensions](controls/control-image.md)** – **[OriginalHeight](controls/control-image.md)** 및 **[OriginalWidth](controls/control-image.md)** 속성을 사용하도록 설정합니다.  **[이미지](controls/control-image.md)** 컨트롤에 적용됩니다.

**[Camera](controls/control-camera.md)** – 둘 이상의 카메라가 있는 디바이스에서 앱이 사용하는 카메라에 대한 숫자 ID입니다.  **[카메라](controls/control-camera.md)** 컨트롤에 적용됩니다.

**[CheckboxBackgroundFill](controls/control-check-box.md)** – 확인란 컨트롤에서 확인 표시를 둘러싸는 상자의 배경색입니다.  **[확인란](controls/control-check-box.md)** 컨트롤에 적용됩니다.

**[CheckboxBorderColor](controls/control-check-box.md)** – 확인란 컨트롤에서 확인 표시를 둘러싸는 테두리의 색입니다.  **[확인란](controls/control-check-box.md)** 컨트롤에 적용됩니다.

**[CheckboxSize](controls/control-check-box.md)** – 확인란 컨트롤에서 확인 표시를 둘러싸는 상자의 너비와 높이입니다.  **[확인란](controls/control-check-box.md)** 컨트롤에 적용됩니다.

**[CheckmarkFill](controls/control-check-box.md)** – 확인란 컨트롤에 있는 확인 표시의 색입니다.  **[확인란](controls/control-check-box.md)** 컨트롤에 적용됩니다.

**[ChevronBackground](controls/control-drop-down.md)** – 드롭다운 목록에서 아래쪽 화살표의 배경색입니다.  **[드롭다운](controls/control-drop-down.md)** 컨트롤에 적용됩니다.

**[ChevronFill](controls/control-drop-down.md)** – 드롭다운 목록에서 아래쪽 화살표의 색입니다.  **[드롭다운](controls/control-drop-down.md)** 컨트롤에 적용됩니다.

**[Clear](controls/control-text-input.md)** – 텍스트 입력 컨트롤에서 사용자가 탭하거나 클릭하여 해당 컨트롤의 내용을 지울 수 있는 "X"를 표시할지 여부입니다.  **[텍스트 입력](controls/control-text-input.md)** 컨트롤에 적용됩니다.

**[Color](controls/properties-color-border.md)** – 컨트롤의 텍스트 색입니다.  많은 컨트롤에 적용됩니다.

**[Contrast](controls/control-camera.md)** – 사용자가 이미지에서 비슷한 색을 쉽게 구별할 수 있는 수준입니다.  **[카메라](controls/control-camera.md)** 컨트롤에 적용됩니다.

**[CurrentFindText](controls/control-pdf-viewer.md)** – 현재 사용 중인 검색어입니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[CurrentPage](controls/control-pdf-viewer.md)** – 실제로 표시되는 PDF 파일의 페이지 번호입니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

### <a name="d"></a>D

**[Data](controls/control-export-import.md)** - 로컬 파일에 내보내려는 컬렉션의 이름입니다.  **[내보내기](controls/control-export-import.md)** 컨트롤에 적용됩니다.

**[DataField](controls/control-card.md)** - 이 카드에서 표시하고 편집하는 레코드 내부의 필드 이름입니다.  **[카드](controls/control-card.md)** 컨트롤에 적용됩니다.

**[DataSource](controls/control-form-detail.md)** – 사용자가 표시하거나, 편집하거나, 만드는 레코드를 포함하는 데이터 원본입니다.  **[표시 양식](controls/control-form-detail.md)** 및 **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[Default](controls/properties-core.md)** – 사용자가 컨트롤을 변경하기 전의 초기 값입니다.  많은 컨트롤에 적용됩니다.

**[DefaultDate](controls/control-date-picker.md)** – 사용자가 날짜 컨트롤을 변경하기 전의 초기 값입니다.  **[날짜 선택](controls/control-date-picker.md)** 컨트롤에 적용됩니다.

**[DefaultMode](controls/control-form-detail.md)** – 양식 컨트롤의 초기 모드로서 **Edit**, **New** 또는 **View** 중 하나입니다.  **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[Direction](controls/control-gallery.md)** – 갤러리의 첫 번째 항목이 가로 방향으로 왼쪽 또는 오른쪽 가장자리 근처에 표시되는지 여부입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**[Disabled](controls/properties-core.md)** – 사용자가 컨트롤과 상호 작용할 수 있는지 여부입니다.  많은 컨트롤에 적용됩니다.

**[DisabledBorderColor](controls/properties-color-border.md)** – 컨트롤의 **[Disabled](controls/properties-core.md)** 속성이 **true**로 설정된 경우 컨트롤의 테두리 색입니다.  많은 컨트롤에 적용됩니다.

**[DisabledColor](controls/properties-color-border.md)** – 컨트롤의 **[Disabled](controls/properties-core.md)** 속성이 **true**로 설정된 경우 컨트롤의 텍스트 색입니다.  많은 컨트롤에 적용됩니다.

**[DisabledFill](controls/properties-color-border.md)** – 컨트롤의 **[Disabled](controls/properties-core.md)** 속성이 **true**로 설정된 경우 컨트롤의 배경색입니다.  많은 컨트롤에 적용됩니다.

**[DisplayName](controls/control-card.md)** – 데이터 원본의 필드에 대한 사용자에게 친숙한 이름입니다.  **[카드](controls/control-card.md)** 컨트롤에 적용됩니다.

**[DisplayMode](controls/properties-core.md)** – 값이 Edit, View 또는 Disabled일 수 있습니다. 컨트롤에서 사용자 입력을 허용하는지(Edit), 데이터만 표시하는지(View) 또는 사용하지 않는지(Disabled) 여부를 구성합니다.

**[Document](controls/control-pdf-viewer.md)** – 큰따옴표로 묶은 PDF 파일의 URL입니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[Duration](controls/control-timer.md)** – 타이머가 실행되는 시간입니다.  **[타이머](controls/control-timer.md)** 컨트롤에 적용됩니다.

### <a name="e"></a>E

**[EndYear](controls/control-date-picker.md)** – 사용자가 날짜 선택 컨트롤의 값을 설정할 수 있는 끝 연도입니다.  **[날짜 선택](controls/control-date-picker.md)** 컨트롤에 적용됩니다.

**Error** – 이 속성의 의미는 다음 컨트롤에 따라 다릅니다.

* **[그림 추가](controls/control-add-picture.md)** 컨트롤 - 이미지를 업로드하는 데 문제가 있는 경우 이 속성에 적절한 오류 문자열이 포함됩니다.
* **[카드](controls/control-card.md)** 컨트롤 - 유효성 검사가 실패할 때 이 필드에 대해 표시할 사용자에게 친숙한 오류 메시지입니다.
* **[편집 양식](controls/control-form-detail.md)** 컨트롤 – **[SubmitForm](functions/function-form.md)** 함수가 실패할 때 이 양식에 대해 표시할 사용자에게 친숙한 오류 메시지입니다.

**[ErrorKind](controls/control-form-detail.md)** – **SubmitForm**이 실행될 때 발생한 오류의 종류입니다.  **[표시 양식](controls/control-form-detail.md)** 및 **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[Explode](controls/control-pie-chart.md)** – 원형 차트에서 쐐기형 사이의 거리입니다.  **[원형 차트](controls/control-pie-chart.md)** 컨트롤에 적용됩니다.

### <a name="f"></a>350

**[Fill](controls/properties-color-border.md)** - 컨트롤의 배경색입니다.  많은 컨트롤에 적용됩니다.

**[FindNext](controls/control-pdf-viewer.md)** – 문서에서 **FindText**의 다음 인스턴스를 찾습니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[FindPrevious](controls/control-pdf-viewer.md)** – 문서에서 **FindText**의 이전 인스턴스를 찾습니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[FindText](controls/control-pdf-viewer.md)** – 문서에서 찾을 검색어입니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[Font](controls/properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.  많은 컨트롤에 적용됩니다.

**[FontWeight](controls/properties-text.md)** – 컨트롤의 텍스트 가중치입니다. **Bold**, **Semibold**, **Normal**또는 **가벼운**입니다.  많은 컨트롤에 적용됩니다.

### <a name="g"></a>EXPRESS-G

**[GridStyle](controls/control-column-line-chart.md)** – 세로 막대형 또는 꺾은선형 차트에서 x-축, y-축 또는 둘 다를 표시할지, 아니면 둘 다를 표시하지 않을지 여부입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 및 **[꺾은선형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

### <a name="h"></a>넣기

**[HandleActiveFill](controls/control-slider.md)** – 사용자가 값을 변경했을 때 슬라이더에 대한 핸들의 색입니다.  **[슬라이더](controls/control-slider.md)** 컨트롤에 적용됩니다.

**[HandleFill](controls/control-slider.md)** – 토글 또는 슬라이더 컨트롤에서 핸들(위치를 변경하는 요소)의 색입니다.  **[슬라이더](controls/control-slider.md)** 컨트롤에 적용됩니다.

**[HandleHoverFill](controls/control-slider.md)** – 사용자가 마우스 포인터를 슬라이더 위에 유지할 때 해당 슬라이더에 있는 핸들의 색입니다.  **[슬라이더](controls/control-slider.md)** 컨트롤에 적용됩니다.

**[Height](controls/properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.  많은 컨트롤에 적용됩니다.

**[HintText](controls/control-text-input.md)** – 비어 있는 경우 텍스트 입력 컨트롤에 표시되는 연회색 텍스트입니다.  **[텍스트 입력](controls/control-text-input.md)** 컨트롤에 적용됩니다.

**[HoverBorderColor](controls/properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.  많은 컨트롤에 적용됩니다.

**[HoverColor](controls/properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.  많은 컨트롤에 적용됩니다.

**[HoverFill](controls/properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.  많은 컨트롤에 적용됩니다.

**[HTMLText](controls/control-html-text.md)** – HTML 텍스트 컨트롤에 표시되며 HTML 태그를 포함할 수 있는 텍스트입니다.  **[HTML 텍스트](controls/control-html-text.md)** 컨트롤에 적용됩니다.

### <a name="i"></a>I

**[Image](controls/properties-visual.md)** – 이미지, 오디오 또는 마이크 컨트롤에 표시되는 이미지의 이름입니다.  **[오디오](controls/control-audio-video.md)** , **[이미지](controls/control-image.md)** , **[마이크](controls/control-microphone.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[ImagePosition](controls/properties-visual.md)** – 이미지와 같은 크기가 아닌 경우 컨트롤 또는 화면에 있는 이미지의 위치입니다(**채우기**, **맞춤**, **늘이기**, **타일** 또는 **가운데**).  많은 컨트롤에 적용됩니다.

**[입력](controls/control-pen-input.md)** – 입력입니다.  **[펜 입력](controls/control-pen-input.md)** 컨트롤에 적용됩니다.

**[Italic](controls/properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.  많은 컨트롤에 적용됩니다.

**[Item](controls/control-form-detail.md)** – 사용자가 표시하거나 편집할 **DataSource**의 레코드입니다.  **[표시 양식](controls/control-form-detail.md)** 및 **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[ItemBorderColor](controls/control-pie-chart.md)** – 원형 차트에서 각 쐐기형 주위의 테두리 색입니다.  **[원형 차트](controls/control-pie-chart.md)** 컨트롤에 적용됩니다.

**[ItemBorderThickness](controls/control-pie-chart.md)** – 원형 차트에서 각 쐐기형 주위의 테두리 두께입니다.  **[원형 차트](controls/control-pie-chart.md)** 컨트롤에 적용됩니다.

**ItemColorSet** – 차트의 각 데이터 요소에 대한 색입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** , **[꺾은선형 차트](controls/control-column-line-chart.md)** 및 **[원형 차트](controls/control-pie-chart.md)** 컨트롤에 적용됩니다.

**[ItemPaddingLeft](controls/control-list-box.md)** – 목록 상자의 텍스트와 왼쪽 가장자리 사이의 거리입니다.  **[목록 상자](controls/control-list-box.md)** 컨트롤에 적용됩니다.

**[Items](controls/properties-core.md)** – 갤러리, 목록 또는 차트와 같은 컨트롤에 표시되는 데이터 원본입니다.  많은 컨트롤에 적용됩니다.

**[ItemsGap](controls/control-column-line-chart.md)** – 세로 막대형 차트에서 막대 사이의 거리입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

### <a name="l"></a>L-VALUE

**[LabelPosition](controls/control-pie-chart.md)** – 원형 차트에서 해당 쐐기형을 기준으로 한 레이블의 위치입니다.  **[원형 차트](controls/control-pie-chart.md)** 컨트롤에 적용됩니다.

**[LastSubmit](controls/control-form-detail.md)** – 서버에서 생성된 필드를 포함하여 성공적으로 제출된 마지막 레코드입니다.  **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**Layout** – 사용자가 위에서 아래로(**Vertical**) 또는 왼쪽에서 오른쪽으로(**Horizontal**) 갤러리를 스크롤하거나 슬라이더를 조정할지 여부입니다.  **[갤러리](controls/control-gallery.md)** 및 **[슬라이더](controls/control-slider.md)** 컨트롤에 적용됩니다.

**[LineHeight](controls/properties-text.md)** - 예를 들어 텍스트 선 또는 목록의 항목 사이의 거리입니다.  **[목록 상자](controls/control-list-box.md)** , **[라디오](controls/control-radio.md)** , **[레이블](controls/control-text-box.md)** 및 **[텍스트 입력](controls/control-text-input.md)** 컨트롤에 적용됩니다.

**[Loop](controls/control-audio-video.md)** – 재생을 끝내는 즉시 오디오 또는 비디오 클립을 자동으로 시작할지 여부입니다.  **[오디오](controls/control-audio-video.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

### <a name="m"></a>매

**[Markers](controls/control-column-line-chart.md)** – 세로 막대형 또는 꺾은선형 차트에서 각 데이터 요소의 값을 표시할지 여부입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 및 **[꺾은선형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

**[MarkerSuffix](controls/control-column-line-chart.md)** - **[Markers](controls/control-column-line-chart.md)** 속성이 **true**로 설정된 세로 막대형 차트의 각 값 뒤에 표시되는 텍스트입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

**Max** – 사용자가 슬라이더 또는 등급을 설정할 수 있는 최대값입니다.  **[등급](controls/control-rating.md)** 및 **[슬라이더](controls/control-slider.md)** 컨트롤에 적용됩니다.

**[MaxLength](controls/control-text-input.md)** – 사용자가 텍스트 입력 컨트롤에 입력할 수 있는 문자 수입니다.  **[텍스트 입력](controls/control-text-input.md)** 컨트롤에 적용됩니다.

**Media** – 오디오 또는 비디오 컨트롤에서 재생하는 클립에 대한 식별자입니다.  **[그림 추가](controls/control-add-picture.md)** , **[오디오](controls/control-audio-video.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[Mic](controls/control-microphone.md)** – 둘 이상의 마이크가 있는 디바이스에서 앱이 사용하는 마이크에 대한 숫자 ID입니다.  **[마이크](controls/control-microphone.md)** 컨트롤에 적용됩니다.

**[Min](controls/control-slider.md)** – 사용자가 슬라이더를 설정할 수 있는 최소값입니다.  **[슬라이더](controls/control-slider.md)** 컨트롤에 적용됩니다.

**[MinimumBarWidth](controls/control-column-line-chart.md)** - 세로 막대형 차트의 열에서 가능한 가장 좁은 너비입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

**Mode** – 이 속성의 의미는 다음 컨트롤에 따라 다릅니다.

* **[편집 양식](controls/control-form-detail.md)** 컨트롤 – **Edit** 또는 **New** 모드입니다.
* **[펜 입력](controls/control-pen-input.md)** 컨트롤 - **Draw**, **Erase** 또는 **Select** 모드입니다.
* **[텍스트 입력](controls/control-text-input.md)** 컨트롤 – **SingleLine**, **MultiLine** 또는 **Password** 모드입니다.

### <a name="n"></a>개의

**[NavigationStep](controls/control-gallery.md)** – **[ShowNavigation](controls/control-gallery.md)** 속성이 **true**로 설정되어 있고 사용자가 해당 갤러리의 한쪽 끝에서 탐색 화살표를 선택하는 경우 갤러리를 스크롤하는 정도입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**[NumberOfSeries](controls/control-column-line-chart.md)** – 세로 막대형 차트 또는 꺾은선형 차트에 반영되는 데이터의 열 수입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 및 **[꺾은선형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

### <a name="o"></a>O

**[OnChange](controls/properties-core.md)** – 사용자가 컨트롤 값을 변경할 때(예: 슬라이더 조정)의 앱 동작입니다.  많은 컨트롤에 적용됩니다.

**OnCheck** - 확인란 또는 토글의 값이 **true**로 변경되었을 때의 앱 동작입니다.  **[확인란](controls/control-check-box.md)** 및 **[토글](controls/control-toggle.md)** 컨트롤에 적용됩니다.

**[OnEnd](controls/control-audio-video.md)** - 오디오 또는 비디오 클립에서 재생을 마칠 때의 앱 동작입니다.  **[오디오](controls/control-audio-video.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[OnFailure](controls/control-form-detail.md)** – 데이터 작업이 실패했을 때의 앱 동작입니다.  **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[OnHidden](controls/control-screen.md)** – 사용자가 화면에서 나갈 때의 앱 동작입니다.  **[화면](controls/control-screen.md)** 컨트롤에 적용됩니다.

**[OnPause](controls/control-audio-video.md)** - 사용자가 오디오 또는 비디오 컨트롤에서 재생 중인 클립을 일시 중지할 때의 앱 동작입니다.  **[오디오](controls/control-audio-video.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[OnReset](controls/control-form-detail.md)** – **[편집 양식](controls/control-form-detail.md)** 컨트롤이 다시 설정되었을 때의 앱 동작입니다.  **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[OnSelect](controls/properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때의 앱 동작입니다.  많은 컨트롤에 적용됩니다.

**OnStart** – 사용자가 앱을 열거나 마이크 컨트롤을 통해 녹음을 시작할 때의 앱 동작입니다. **[오디오](controls/control-audio-video.md)** , **[마이크](controls/control-microphone.md)** , **[화면](controls/control-screen.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[OnStateChange](controls/control-pdf-viewer.md)** – 컨트롤의 상태가 변경될 때의 앱 동작입니다. **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[OnStop](controls/control-microphone.md)** – 사용자가 마이크 컨트롤을 통해 녹음을 중지할 때의 앱 동작입니다. **[마이크](controls/control-microphone.md)** 컨트롤에 적용됩니다.

**[OnStream](controls/control-camera.md)** – **[Stream](controls/control-camera.md)** 속성이 업데이트될 때의 앱 동작입니다.  **[카메라](controls/control-camera.md)** 컨트롤에 적용됩니다.

**[OnSuccess](controls/control-form-detail.md)** – 데이터 작업이 성공했을 때의 앱 동작입니다.  **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[OnTimerEnd](controls/control-timer.md)** - 타이머 실행이 완료될 때의 앱 동작입니다.  **[타이머](controls/control-timer.md)** 컨트롤에 적용됩니다.

**[OnTimerStart](controls/control-timer.md)** - 타이머 실행이 시작될 때의 앱 동작입니다.  **[타이머](controls/control-timer.md)** 컨트롤에 적용됩니다.

**OnUncheck** - 확인란 또는 토글의 값이 **false**로 변경되었을 때의 앱 동작입니다.  **[확인란](controls/control-check-box.md)** 및 **[토글](controls/control-toggle.md)** 컨트롤에 적용됩니다.

**[OnVisible](controls/control-screen.md)** – 사용자가 화면을 탐색할 때의 앱 동작입니다.  **[화면](controls/control-screen.md)** 컨트롤에 적용됩니다.

**[OriginalHeight](controls/control-image.md)** – **[CalculateOriginalDimensions](controls/control-image.md)** 속성으로 활성화된 이미지의 원래 높이입니다.  **[이미지](controls/control-image.md)** 컨트롤에 적용됩니다.

**[OriginalWidth](controls/control-image.md)** – **[CalculateOriginalDimensions](controls/control-image.md)** 속성으로 활성화된 이미지의 원래 높이입니다.  **[이미지](controls/control-image.md)** 컨트롤에 적용됩니다.

**[Overflow](controls/control-text-box.md)** – **[Wrap](controls/control-text-box.md)** 속성이 **true**로 설정되고, 컨트롤에서 한 번에 표시할 수 있는 것보다 더 많은 문자가 해당 컨트롤의 **[Text](controls/properties-core.md)** 속성 값에 포함된 경우 스크롤 막대를 레이블에 표시할지 여부입니다.  **[레이블](controls/control-text-box.md)** 컨트롤에 적용됩니다.

### <a name="p"></a>P

**[Padding](controls/properties-size-location.md)** – 가져오기 또는 내보내기 단추의 텍스트와 단추의 가장자리 사이의 간격입니다.  **[그림 추가](controls/control-add-picture.md)** , **[내보내기](controls/control-export-import.md)** 및 **[가져오기](controls/control-export-import.md)** 컨트롤에 적용됩니다.

**[PaddingBottom](controls/properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 아래쪽 가장자리 사이의 거리입니다.  많은 컨트롤에 적용됩니다.

**[PaddingLeft](controls/properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.  많은 컨트롤에 적용됩니다.

**[PaddingRight](controls/properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.  많은 컨트롤에 적용됩니다.

**[PaddingTop](controls/properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 위쪽 가장자리 사이의 거리입니다.  많은 컨트롤에 적용됩니다.

**[Page](controls/control-pdf-viewer.md)** – 표시하려는 페이지의 수입니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[PageCount](controls/control-pdf-viewer.md)** -문서에 있는 페이지의 수입니다.  **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.

**[Paused](controls/control-audio-video.md)** – 미디어 재생 컨트롤이 현재 일시 중지되면 *true*이고, 그렇지 않으면 *false*입니다.  **[오디오](controls/control-audio-video.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[Photo](controls/control-camera.md)** – 사용자가 사진을 찍을 때 캡처된 이미지입니다.  **[카메라](controls/control-camera.md)** 컨트롤에 적용됩니다.

**[Pressed](controls/control-button.md)** – 컨트롤을 누르고 있으면 *true*이고, 그렇지 않으면 *false*입니다.  **[단추](controls/control-button.md)** 컨트롤에 적용됩니다.

**[PressedBorderColor](controls/properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.  많은 컨트롤에 적용됩니다.

**[PressedColor](controls/properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.  많은 컨트롤에 적용됩니다.

**[PressedFill](controls/properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.  많은 컨트롤에 적용됩니다.

### <a name="r"></a>R

**[RadioBackgroundFill](controls/control-radio.md)** – 라디오 단추 컨트롤에 있는 원의 배경색입니다.  **[라디오](controls/control-radio.md)** 컨트롤에 적용됩니다.

**[RadioBorderColor](controls/control-radio.md)** - 라디오 단추 컨트롤에 있는 각 옵션에 대한 원의 색입니다.  **[라디오](controls/control-radio.md)** 컨트롤에 적용됩니다.

**[RadioSelectionFill](controls/control-radio.md)** – 라디오 단추 컨트롤에서 선택한 옵션의 원 안에 표시되는 색입니다.  **[라디오](controls/control-radio.md)** 컨트롤에 적용됩니다.

**[RadioSize](controls/control-radio.md)** – 라디오 단추 컨트롤에 있는 원의 지름입니다.  **[라디오](controls/control-radio.md)** 컨트롤에 적용됩니다.

**[RadiusBottomLeft](controls/properties-size-location.md)** – 컨트롤 왼쪽 아래 모서리의 둥근 정도입니다.  많은 컨트롤에 적용됩니다.

**[RadiusBottomRight](controls/properties-size-location.md)** – 컨트롤 오른쪽 아래 모서리의 둥근 정도입니다.  많은 컨트롤에 적용됩니다.

**[RadiusTopLeft](controls/properties-size-location.md)** – 컨트롤 왼쪽 위 모서리의 둥근 정도입니다.  많은 컨트롤에 적용됩니다.

**[RadiusTopRight](controls/properties-size-location.md)** – 컨트롤 오른쪽 위 모서리의 둥근 정도입니다.  많은 컨트롤에 적용됩니다.

**RailFill** – 토글 컨트롤의 값이 **false**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 오른쪽의 선 색입니다.  **[슬라이더](controls/control-slider.md)** 및 **[토글](controls/control-toggle.md)** 컨트롤에 적용됩니다.

**RailHoverFill** – 토글 컨트롤 또는 슬라이더에 마우스를 가져가는 경우, 토글 컨트롤의 값이 **false**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 오른쪽의 선 색입니다.  **[슬라이더](controls/control-slider.md)** 및 **[토글](controls/control-toggle.md)** 컨트롤에 적용됩니다.

**[RatingFill](controls/control-rating.md)** – 등급 컨트롤에 있는 별의 색입니다.  **[등급](controls/control-rating.md)** 컨트롤에 적용됩니다.

**ReadOnly** – 사용자가 슬라이더 또는 등급 컨트롤의 값을 변경할 수 있는지 여부입니다.  **[등급](controls/control-rating.md)** 및 **[슬라이더](controls/control-slider.md)** 컨트롤에 적용됩니다.

**[Repeat](controls/control-timer.md)** – 타이머 실행이 완료되면 타이머를 자동으로 다시 시작할지 여부입니다.  **[타이머](controls/control-timer.md)** 컨트롤에 적용됩니다.

**[Required](controls/control-card.md)** – 데이터 원본의 필드를 편집하는 카드에서 값을 포함해야 하는지 여부입니다.  **[카드](controls/control-card.md)** 컨트롤에 적용됩니다.

**[Reset](controls/properties-core.md)** – 컨트롤이 기본값으로 되돌아가는지 여부입니다.  많은 컨트롤에 적용됩니다.  **[Reset](functions/function-reset.md)** 함수도 참조하세요.

### <a name="s"></a>삭제

**Selected** – 선택한 항목입니다.  **[드롭다운](controls/control-drop-down.md)** 및 **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**[SelectedDate](controls/control-date-picker.md)** - 날짜 컨트롤에서 현재 선택한 날짜입니다.  **[날짜 선택](controls/control-date-picker.md)** 컨트롤에 적용됩니다.

**[SelectionColor](controls/properties-color-border.md)** – 목록에서 선택한 항목의 텍스트 색 또는 펜 컨트롤에 있는 선택 도구의 색입니다.  **[드롭다운](controls/control-drop-down.md)** , **[목록 상자](controls/control-list-box.md)** 및 **[펜 입력](controls/control-pen-input.md)** 컨트롤에 적용됩니다.

**[SelectionFill](controls/properties-color-border.md)** – 목록에서 선택한 항목 또는 펜 컨트롤에서 선택한 영역의 배경색입니다.  **[드롭다운](controls/control-drop-down.md)** 및 **[목록 상자](controls/control-list-box.md)** 컨트롤에 적용됩니다.

**[SelectionThickness](controls/control-pen-input.md)** – 펜 입력 컨트롤에 대한 선택 도구의 두께입니다.  **[펜 입력](controls/control-pen-input.md)** 컨트롤에 적용됩니다.

**[SelectMultiple](controls/control-list-box.md)** – 사용자가 목록 상자에서 둘 이상의 항목을 선택할 수 있는지 여부입니다.  **[목록 상자](controls/control-list-box.md)** 컨트롤에 적용됩니다.

**[SeriesAxisMax](controls/control-column-line-chart.md)** - 세로 막대형 차트 또는 꺾은선형 차트에 대한 y-축의 최대값입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

**[SeriesAxisMin](controls/control-column-line-chart.md)** - 세로 막대형 차트에 대한 y-축의 최소값을 결정하는 숫자입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

**ShowControls** - 오디오 또는 비디오 플레이어에서 재생 단추, 볼륨 슬라이더 등을 표시하는지 및 펜 컨트롤에서 그리기, 삭제 및 지우기 아이콘 등을 표시하는지 여부입니다.  **[오디오](controls/control-audio-video.md)** , **[PDF 뷰어](controls/control-pdf-viewer.md)** , **[펜 입력](controls/control-pen-input.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[ShowLabels](controls/control-pie-chart.md)** – 원형 차트에서 각 쐐기형과 관련된 값을 표시하는지 여부입니다.  **[원형 차트](controls/control-pie-chart.md)** 컨트롤에 적용됩니다.

**[ShowNavigation](controls/control-gallery.md)** – 사용자가 화살표를 클릭하거나 탭하여 갤러리에서 항목을 스크롤할 수 있도록 갤러리의 각 끝 부분에 화살표를 표시하는지 여부입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**[ShowScrollbar](controls/control-gallery.md)** – 사용자가 마우스로 갤러리를 가리킬 때 스크롤 막대를 표시하는지 여부입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**ShowValue** – 사용자가 해당 값을 변경하거나 마우스로 컨트롤을 가리킬 때 슬라이더 또는 등급의 값을 표시하는지 여부입니다.  **[등급](controls/control-rating.md)** 및 **[슬라이더](controls/control-slider.md)** 컨트롤에 적용됩니다.

**[Size](controls/properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.  많은 컨트롤에 적용됩니다.

**[Snap](controls/control-gallery.md)** – 사용자가 갤러리를 스크롤할 때 다음 항목이 완전히 표시되도록 자동으로 맞출지 여부입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**Start** – 오디오 또는 비디오 클립의 재생 여부입니다.  **[오디오](controls/control-audio-video.md)** , **[타이머](controls/control-timer.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[StartTime](controls/control-audio-video.md)** – 클립이 재생되기 시작할 때 오디오 또는 비디오 클립을 시작한 이후의 시간입니다.  **[오디오](controls/control-audio-video.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[StartYear](controls/control-date-picker.md)** – 사용자가 날짜 선택 컨트롤의 값을 설정할 수 있는 시작 연도입니다.  **[날짜 선택](controls/control-date-picker.md)** 컨트롤에 적용됩니다.

**[Stream](controls/control-camera.md)** – **[StreamRate](controls/control-camera.md)** 속성에 따라 자동으로 업데이트되는 이미지입니다.  **[카메라](controls/control-camera.md)** 컨트롤에 적용됩니다.

**[StreamRate](controls/control-camera.md)** – **[Stream](controls/control-camera.md)** 속성에서 이미지를 업데이트하는 빈도(밀리초)입니다.  이 값의 범위는 100(1초의 1/10)에서 3,600,000(1시간)까지입니다.  **[카메라](controls/control-camera.md)** 컨트롤에 적용됩니다.

**[Strikethrough](controls/properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.  많은 컨트롤에 적용됩니다.

### <a name="t"></a>T

**[TemplateFill](controls/control-gallery.md)** – 갤러리의 배경색입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**[TemplatePadding](controls/control-gallery.md)** – 갤러리에 있는 항목 사이의 거리입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**[TemplateSize](controls/control-gallery.md)** - 세로 방향 갤러리에 대한 템플릿의 높이 또는 가로 방향 갤러리에 대한 템플릿의 너비입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**[Text](controls/properties-core.md)** – 컨트롤에 표시되는 텍스트 또는 사용자가 컨트롤에 입력하는 텍스트입니다.  많은 컨트롤에 적용됩니다.

**[Time](controls/control-audio-video.md)** – 미디어 컨트롤의 현재 위치입니다.  **[오디오](controls/control-audio-video.md)** 및 **[비디오](controls/control-audio-video.md)** 컨트롤에 적용됩니다.

**[Tooltip](controls/properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.  많은 컨트롤에 적용됩니다.

**[Transition](controls/control-gallery.md)** – 사용자가 갤러리에서 항목을 가리킬 때 표시되는 시각적 효과입니다(**Pop**, **Push** 또는 **None**).  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

**[Transparency](controls/control-image.md)** – 이미지 뒤의 컨트롤이 보이도록 하는 표시 수준입니다.  **[이미지](controls/control-image.md)** 컨트롤에 적용됩니다.

### <a name="u"></a>U

**[Underline](controls/properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.  많은 컨트롤에 적용됩니다.

**[Unsaved](controls/control-form-detail.md)** – **[편집 양식](controls/control-form-detail.md)** 컨트롤에 저장되지 않은 사용자 변경 내용이 포함되어 있으면 true입니다.  **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[Update](controls/control-card.md)** – 필드의 데이터 원본에 쓰기 저장하는 값입니다.  **[카드](controls/control-card.md)** 컨트롤에 적용됩니다.

**[Updates](controls/control-form-detail.md)** – 양식 컨트롤에 로드된 레코드의 데이터 원본에 쓰기 저장하는 값입니다.  **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

### <a name="v"></a>V

**Valid** – **[카드](controls/control-card.md)** 또는 **[편집 양식](controls/control-form-detail.md)** 컨트롤에 올바른 항목이 있고 데이터 원본에 제출할 준비가 되었는지 여부입니다.  **[카드](controls/control-card.md)** 및 **[편집 양식](controls/control-form-detail.md)** 컨트롤에 적용됩니다.

**[Value](controls/properties-core.md)** – 입력 컨트롤의 값입니다.  **[확인란](controls/control-check-box.md)** , **[라디오](controls/control-radio.md)** , **[슬라이더](controls/control-slider.md)** 및 **[토글](controls/control-toggle.md)** 컨트롤에 적용됩니다.

**ValueFill** – 토글 컨트롤의 값이 **true**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 왼쪽의 선 색입니다.  **[슬라이더](controls/control-slider.md)** 및 **[토글](controls/control-toggle.md)** 컨트롤에 적용됩니다.

**ValueHoverFill** – 토글 컨트롤 또는 슬라이더 위에 마우스 포인터를 두고 있는 경우, 토글 컨트롤의 값이 **true**일 때 해당 컨트롤의 사각형 배경색이거나 슬라이더 컨트롤에 있는 핸들 왼쪽의 선 색입니다.  **[슬라이더](controls/control-slider.md)** 및 **[토글](controls/control-toggle.md)** 컨트롤에 적용됩니다.

**[VerticalAlign](controls/properties-text.md)** – 컨트롤의 세로 가운데를 기준으로 한 텍스트의 위치입니다.  많은 컨트롤에 적용됩니다.

**[Visible](controls/properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.  많은 컨트롤에 적용됩니다.

### <a name="w"></a>W

**[Width](controls/properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.  많은 컨트롤에 적용됩니다.

**[WidthFit](controls/properties-size-location.md)** – **[편집 양식](controls/control-form-detail.md)** 컨트롤처럼 컨테이너 컨트롤의 빈 공간을 채우기 위해 컨트롤이 가로 방향으로 자동으로 확장하는지 여부입니다. 여러 카드에서 이 속성이 **true**로 설정되면 카드 사이의 공간이 분할됩니다. 자세한 내용은 [데이터 양식 레이아웃 이해](working-with-form-layout.md)를 참조하세요.

**[Wrap](controls/control-text-box.md)** – 레이블에 비해 너무 긴 텍스트가 다음 줄로 줄 바꿈하는지 여부입니다.  **[레이블](controls/control-text-box.md)** 컨트롤에 적용됩니다.

**[WrapCount](controls/control-gallery.md)** – 갤러리의 각 항목에 표시되는 레코드의 수입니다.  **[갤러리](controls/control-gallery.md)** 컨트롤에 적용됩니다.

### <a name="x"></a>X

**[X](controls/properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다. 많은 컨트롤에 적용됩니다. 여러 열이 있는 컨테이너의 **[카드](controls/control-card.md)** 컨트롤에서 이 속성은 카드가 표시되는 열을 결정합니다.

**[XLabelAngle](controls/control-column-line-chart.md)** - 세로 막대형 차트 또는 꺾은선형 차트의 x-축 아래에 있는 레이블의 각도입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 및 **[꺾은선형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

### <a name="y"></a>Y

**[Y](controls/properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다. 많은 컨트롤에 적용됩니다. 여러 행이 있는 컨테이너의 **[카드](controls/control-card.md)** 컨트롤에서 이 속성은 카드가 표시되는 행을 결정합니다.

**[YAxisMax](controls/control-column-line-chart.md)** - 꺾은선형 차트에 대한 y-축의 최대값입니다.  **[꺾은선형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

**[YAxisMin](controls/control-column-line-chart.md)** - 꺾은선형 차트에 대한 y-축의 최소값입니다.  **[꺾은선형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

**[YLabelAngle](controls/control-column-line-chart.md)** – 꺾은선형 차트 또는 세로 막대형 차트의 y-축 옆에 있는 레이블의 각도입니다.  **[세로 막대형 차트](controls/control-column-line-chart.md)** 및 **[꺾은선형 차트](controls/control-column-line-chart.md)** 컨트롤에 적용됩니다.

### <a name="z"></a>Z

**Zoom** – 카메라의 이미지 확대 비율 또는 PDF 뷰어의 파일 보기입니다.  **[카메라](controls/control-camera.md)** 및 **[PDF 뷰어](controls/control-pdf-viewer.md)** 컨트롤에 적용됩니다.
