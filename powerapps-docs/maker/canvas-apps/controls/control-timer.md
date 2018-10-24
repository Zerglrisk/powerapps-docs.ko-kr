---
title: '타이머 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 타이머 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 934ab9bddfb429ae3ed96706420af002a87697fb
ms.sourcegitcommit: 87122dba00b4177ef736d87ecdde79581649ba42
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44499525"
---
# <a name="timer-control-in-powerapps"></a>PowerApps의 타이머 컨트롤
일정 시간이 지난 후 앱이 응답하는 방식을 결정할 수 있는 컨트롤입니다.

## <a name="description"></a>설명
타이머는 일정 시간이 지난 후 컨트롤이 표시되는 시간이나 컨트롤의 다른 속성 변경 등을 결정할 수 있습니다.

타이머가 디자이너에서 실행되려면 앱을 미리 보아야 합니다.  이렇게 하면 사용자가 시간 제한 없이 디자이너에서 타이머를 구성할 수 있습니다.

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

**[Reset](properties-core.md)** – 컨트롤이 기본값으로 되돌아가는지 여부입니다.

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

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

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
**타이머**는 특수화된 단추이므로 **[단추](control-button.md)** 에 대한 동일한 지침이 적용됩니다.

> [!IMPORTANT]
> 직접적인 사용자 개입 없이 **타이머**를 제어하는 기능은 접근성을 위해 지원되지 않습니다. 예를 들어 위의 다른 컨트롤을 배치하거나 **[Visible](properties-core.md)** 속성을 **false**로 설정하여 타이머를 시각적으로 숨길 수 있습니다. 타이머는 화면이 표시되면 자동으로 시작되고 몇 시간 후에 일부 작업이 자동으로 실행됩니다. 현재 이 시나리오에 액세스할 수 있는 일반적인 방법은 없습니다.

기타 접근성 지침은 다음과 같습니다.

### <a name="timing"></a>타이밍
**타이머**가 자동으로 시작되거나 중지될 경우 사용자에게 콘텐츠를 읽고 사용할 충분한 시간이 있는지를 고려하세요. 키보드 및 화면 읽기 프로그램 사용자는 시간 초과 이벤트에 반응하는 데 시간이 더 필요할 수 있습니다.

이러한 전략 중 하나면 충분합니다.
* 사용자가 시간 초과 이벤트를 취소할 수 있음
* 사용자가 시작되기 전에 시간 제한을 조정할 수 있음
* 시간 제한이 만료되기 전에 20초 동안 경고하고 제한을 쉽게 연장할 방법 제공

일부 시나리오는 이러한 요구 사항에서 제외됩니다. [WCAG 2.0 guideline for time limits](https://www.w3.org/TR/WCAG20/#time-limits)(시간 제한에 대한 WCAG 2.0 지침)에서 자세히 알아보세요.

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[Text](properties-core.md)** 가 있어야 합니다.
* 시간에 민감한 중요 정보에는 **[Text](properties-core.md)** 를 사용하지 마세요. 화면 읽기 프로그램 사용자는 **[Text](properties-core.md)** 변경 내용의 알림을 받지 않습니다.

    > [!NOTE]
  > 화면 읽기 프로그램은 5초마다 경과된 시간을 알립니다. 그러나 타이머 **[Text](properties-core.md)** 는 알림에 포함되지 않습니다.

* 경과된 시간을 표시하는 **[레이블](control-text-box.md)** 을 추가하는 것이 좋습니다. 타이머의 **[Text](properties-core.md)** 를 사용하여 사용자에게 타이머를 시작하거나 중지하도록 지시합니다.
