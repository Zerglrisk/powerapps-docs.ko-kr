---
title: '날짜 선택기 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 날짜 선택기 컨트롤에 관한 정보
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3275c93aea5492384727701d1074982a345fae67
ms.sourcegitcommit: fa88889cd109651d403ab03287b7f0521bb90e02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2019
ms.locfileid: "75324945"
---
# <a name="date-picker-control-in-power-apps"></a>Power Apps의 날짜 선택 컨트롤
사용자가 날짜를 지정하기 위해 클릭 또는 탭할 수 있는 컨트롤입니다.

## <a name="description"></a>설명
**[텍스트 입력](control-text-input.md)** 컨트롤 대신 **날짜 선택기** 컨트롤을 추가하면 사용자가 올바른 형식으로 날짜를 지정하는 데 도움이 됩니다.

## <a name="key-properties"></a>주요 속성
**DefaultDate** – 사용자가 변경하지 않을 경우 날짜 컨트롤 값의 초기 값입니다.

**SelectedDate** -날짜 컨트롤에서 현재 선택한 날짜입니다.  이 날짜는 현지 시간으로 표시 됩니다.

**Format** - 컨트롤이 날짜를 표시하고 사용자가 날짜를 지정하는 텍스트 형식입니다. 이 속성을 **ShortDate**(기본값) 또는 **LongDate**로 설정하여 이 컨트롤의 **날짜** 속성에 따라 날짜 형식을 지정할 수 있습니다. 또한, 언어와 상관없이 동일한 형식을 원하는 경우 이 속성을 표현식(예: **yyyy/mm/dd**)으로 설정할 수도 있습니다. 예제:

* 이 컨트롤은 사용자가 2017의 마지막 날을 클릭하거나 누르고, **Format** 형식이 **ShortDate**로 설정되어 있고 **Language** 속성이 **en-us**로 설정되어 있는 경우 **12/31/2017**을 표시합니다.
* 이 컨트롤은 사용자가 2017의 마지막 날을 클릭하거나 누르고, **Format** 형식이 **LongDate**로 설정되어 있고 **Language** 속성이 **fr-fr**로 설정되어 있는 경우 **dimanche 31 decembre 2017**을 표시합니다.

**Language** – 월 이름을 포함 하 여 날짜 형식을 지정 하는 데 사용 되는 언어를 결정 합니다. 이 속성이 지정되지 않은 경우 사용자의 디바이스 설정이 언어를 결정합니다. 지원 되는 값은 "EN-US" 및 "FR"입니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**DateTimeZone** – 날짜를 **UTC** 로 표시할지 아니면 사용자의 **현지** 시간으로 표시할지를 지정 합니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(편집)하거나, 데이터만 표시(보기)하거나 사용 안 하도록(사용 안 함) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**EndYear** – 사용자가 날짜 선택기 컨트롤의 값을 설정할 수 있는 가장 늦은 연도입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**[FontWeight](properties-text.md)** - 컨트롤의 텍스트 굵기입니다. **Bold**, **Semibold**, **Normal** 또는 **Lighter**로 설정합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**IconFill** – 날짜 선택기 아이콘의 전경색입니다.

**IconBackground** – 날짜 선택기 아이콘의 배경색입니다.

**Inputtextplaceholder** – 날짜를 입력 하지 않은 경우 표시 되는 지침 텍스트입니다.

**IsEditable** – datepicker 텍스트를 편집할 수 있는지 여부를 지정 합니다. False 이면 날짜만 달력을 사용 하 여 변경할 수 있습니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 하단 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 상단 가장자리 사이의 거리입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**StartOfWeek** – 날짜 선택 컨트롤의 첫 번째 날 열에 표시 되는 요일입니다.

**StartYear** – 사용자가 날짜 선택기 컨트롤의 값을 설정할 수 있는 가장 이른 연도입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
**[Year](../functions/function-datetime-parts.md)** ( *DateTimeValue* )

## <a name="example"></a>예
1. **날짜 선택기** 컨트롤을 추가하고 이름을 **Deadline**으로 지정합니다.

    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. **[레이블](control-text-box.md)** 컨트롤을 추가하고, **[Text](properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateDiff(Today(), Deadline.SelectedDate) & " 남은 일수!"**

    **[DateDiff](../functions/function-dateadd-datediff.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
3. F5 키를 누르고 **마감일**에서 날짜를 선택한 다음, **확인**을 클릭하거나 탭합니다.

    **[레이블](control-text-box.md)** 컨트롤은 오늘과 사용자가 선택한 날짜 사이의 일수를 보여줍니다.
4. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
* [표준 색 대비 요구 사항](../accessible-apps-color.md)이 적용됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.

> [!TIP]
> 달력이 열려 있으면 **page up** 및 **page down** 을 눌러 월 사이를 이동 하 고 **Shift + Page up** 과 **shift + page down** 을 눌러 연도 사이를 이동 합니다.
