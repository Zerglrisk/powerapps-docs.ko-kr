---
title: '타이머 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 타이머 컨트롤에 관한 정보
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
ms.openlocfilehash: 46b5cb0761027c7e39ac95619974d2c0187225a2
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73649664"
---
# <a name="timer-control-in-powerapps"></a>PowerApps의 타이머 컨트롤
일정 시간이 지난 후 앱이 응답하는 방식을 결정할 수 있는 컨트롤입니다.

## <a name="description"></a>설명
타이머는 일정 시간이 지난 후 컨트롤이 표시되는 시간이나 컨트롤의 다른 속성 변경 등을 결정할 수 있습니다.

> [!NOTE]
> PowerApps Studio에서 타이머는 미리 보기 모드 에서만 실행 됩니다.


## <a name="key-properties"></a>주요 속성
**Duration** – 타이머가 실행되는 시간(밀리초)입니다.  최대 값이 없습니다.

**OnTimerEnd** - 타이머 실행이 완료될 때 앱이 응답하는 방식입니다.

**Repeat** – 타이머 실행 완료 후 자동으로 다시 시작할지 여부입니다.

## <a name="additional-properties"></a>추가 속성
**[Align](properties-text.md)** - 컨트롤의 가로 가운데를 기준으로 한 텍스트의 위치입니다.

**AutoPause** – 사용자가 다른 화면으로 이동하는 경우 타이머 컨트롤이 자동으로 일시 중지할지의 여부를 선택합니다.

**AutoStart** - 사용자가 해당 컨트롤이 포함된 화면으로 이동할 때 타이머 컨트롤이 자동으로 재생할지의 여부를 선택합니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

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

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**OnTimerStart** - 타이머가 실행을 시작했을 때 앱이 응답하는 방식입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[Reset](properties-core.md)** – 컨트롤을 기본값으로 되돌릴지 여부를 선택합니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**시작** – 타이머 시작 여부를 선택합니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Text](properties-core.md)** – 컨트롤에 표시되는 텍스트 또는 사용자가 컨트롤에 입력하는 텍스트입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**Refresh**( *DataSource* )](../functions/function-refresh.md)

## <a name="examples"></a>예
### <a name="show-a-countdown"></a>카운트다운 표시
1. 타이머를 추가하고 이름을 **Countdown**으로 지정합니다.

    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. 타이머의 **Duration** 속성을 **10000**, **Repeat** 및 **Autostart** 속성을 **true**로 설정합니다.
3. (선택 사항) 타이머를 더 판독하기 쉽게 **[Height](properties-size-location.md)** 속성을 **160**, **[Width](properties-size-location.md)** 속성을 **600**, **[Size](properties-text.md)** 속성을 **60**으로 설정합니다.
4. 레이블을 추가하고 **[Text](properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**"Number of seconds remaining: " & RoundUp(10-Countdown.Value/1000, 0)**

    **[RoundUp](../functions/function-round.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?

    레이블은 타이머를 다시 시작하기 전까지 남은 시간(초)을 표시합니다.

### <a name="animate-a-control"></a>컨트롤 애니메이션
1. 타이머를 추가하고 이름을 **FadeIn**으로 지정합니다.

    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. 타이머의 **Duration** 속성을 **5000**으로 설정하고, **Repeat** 속성을 **true**로 설정하고, **[Text](properties-core.md)** 속성을 **Toggle animation**으로 설정합니다.
3. (선택 사항) 타이머를 더 판독하기 쉽게 **[Height](properties-size-location.md)** 속성을 **160**, **[Width](properties-size-location.md)** 속성을 **600**, **[Size](properties-text.md)** 속성을 **60**으로 설정합니다.
4. 레이블을 추가하고 **[Text](properties-core.md)** 속성을 **Welcome!** 을 표시하도록 설정하며 **[Color](properties-color-border.md)** 속성을 다음 수식으로 설정합니다.
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    **[ColorFade](../functions/function-colors.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?

5. 타이머 단추를 선택하여 애니메이션을 시작 또는 중지합니다. 레이블의 텍스트가 흰색으로 흐려지며 전체 강도로 돌아가는 프로세스를 반복합니다.

## <a name="accessibility-guidelines"></a>접근성 지침
사용자가 조작할 수 있는 경우 **[Button](control-button.md)** 컨트롤에 대 한 동일한 지침이 **타이머** 컨트롤에 적용 됩니다.

### <a name="background-timers"></a>백그라운드 타이머
백그라운드 타이머는 자동으로 실행 되며 숨겨집니다. 사용자에 게는 경과 시간이 거의 필요 하지 않은 지원 역할에 사용 합니다. 예를 들어 1 분 마다 데이터를 새로 고치거 나 특정 기간 동안만 알림 메시지를 표시할 수 있습니다.

백그라운드 타이머는 모든 사용자가 숨길 수 있도록 **[Visible](properties-core.md)** 속성을 false로 설정 해야 합니다.

### <a name="timing-considerations"></a>타이밍 고려 사항
**타이머가** 자동으로 실행 되는 경우 사용자가 콘텐츠를 읽고 사용할 수 있는 충분 한 시간이 있는지 여부를 고려 합니다. 키보드 및 화면 판독기 사용자는 시간 제한 이벤트에 반응 하는 데 시간이 더 필요할 수 있습니다.

이러한 전략은 충분 합니다.
* 사용자가 시간 제한 이벤트를 취소할 수 있도록 허용 합니다.
* 사용자가 시작 하기 전에 시간 제한을 조정할 수 있습니다.
* 시간 제한이 만료 되기 20 초 전에 경고 하 고 제한을 확장 하는 쉬운 방법을 제공 합니다.

일부 시나리오는 이러한 요구 사항에서 제외됩니다. [WCAG 2.0 guideline for time limits](https://www.w3.org/TR/WCAG20/#time-limits)(시간 제한에 대한 WCAG 2.0 지침)에서 자세히 알아보세요.

### <a name="screen-reader-support"></a>화면 판독기 지원
* 타이머에서 현재 화면에 대 한 변경 내용을 트리거하는 경우 [라이브 지역을](../accessible-apps-live-regions.md) 사용 하 여 화면 판독기 사용자에 게 변경 내용을 알립니다.

    > [!NOTE]
    > 타이머가 표시 되 고 실행 중인 경우 화면 판독기는 5 초 마다 경과 된 시간을 알립니다.

* 시간이 중요 하 고 중요 한 정보를 보려면 컨트롤의 **[Text](properties-core.md)** 속성을 사용 하지 마세요. 화면 읽기 프로그램이 **[텍스트](properties-core.md)** 에 대 한 변경 내용을 알리지 않습니다.
* 대화형 타이머의 경우:
    * **[Text](properties-core.md)** 가 있어야 합니다.
    * 경과 된 시간을 표시 하는 **[레이블](control-text-box.md)** 컨트롤을 추가 하는 것이 좋습니다. 타이머의 **[Text](properties-core.md)** 속성을 사용 하 여 타이머를 시작 하거나 중지 하도록 사용자에 게 지시 합니다.
