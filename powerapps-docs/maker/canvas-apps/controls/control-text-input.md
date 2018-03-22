---
title: '텍스트 입력 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 텍스트 입력 컨트롤에 관한 정보
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 4082034d843765025bb6e40cab83705582417d51
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2018
---
# <a name="text-input-control-in-powerapps"></a>PowerApps의 텍스트 입력 컨트롤
사용자가 텍스트, 숫자 및 기타 데이터를 입력할 수 있는 상자입니다.

## <a name="description"></a>설명
사용자는 텍스트 입력 컨트롤에 입력하여 데이터를 지정할 수 있습니다. 앱 구성 방식에 따라, 해당 데이터는 임시 값을 계산하는 데 사용하는 데이터 원본에 추가되거나 다른 방식으로 통합될 수 있습니다.

## <a name="key-properties"></a>주요 속성
**[Default](properties-core.md)** – 사용자가 컨트롤을 변경하기 전의 초기 값입니다.

**[Text](properties-core.md)** – 컨트롤에 표시되는 텍스트 또는 사용자가 컨트롤에 입력하는 텍스트입니다.

## <a name="additional-properties"></a>추가 속성
**[Align](properties-text.md)** - 컨트롤의 가로 가운데를 기준으로 한 텍스트의 위치입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[FocusedBorderThickness](properties-color-border.md)** - 키보드 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**Clear** – 텍스트 입력 컨트롤에 사용자가 해당 컨트롤의 내용을 지우기 위해 탭하거나 클릭할 수 있는 "X"를 표시할지 여부를 선택합니다.

**[Color](properties-color-border.md)** – 컨트롤의 텍스트 색입니다.

**DelayOutput** – true로 설정된 경우 사용자 입력은 0.5초 지연 후에 등록됩니다.  사용자가 텍스트 입력을 완료할 때까지(예: 입력이 다른 수식에서사용될 때 필터링하기 위해) 비용이 많이 드는 운영을 지연하는 데 유용합니다

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[DisabledColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 텍스트 색입니다.

**[DisabledFill](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 배경색입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Font](properties-text.md)** – 텍스트가 표시되는 글꼴의 제품군 이름입니다.

**[FontWeight](properties-text.md)** - 컨트롤의 텍스트 굵기입니다. **Bold**, **Semibold**, **Normal** 또는 **Lighter**로 설정합니다.

**Format** – 사용자 입력이 숫자로만 제한되거나 어떤 텍스트라도 입력할 수 있는지 여부를 선택합니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**HintText** – 비어 있는 경우 입력 텍스트 컨트롤에 나타나는 연회색 텍스트입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[HoverColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 텍스트 색입니다.

**[HoverFill](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 배경색입니다.

**[Italic](properties-text.md)** - 컨트롤의 텍스트를 기울임꼴로 설정할지 여부를 선택합니다.

**[LineHeight](properties-text.md)** - 예를 들어 텍스트 선 또는 목록의 항목 사이의 거리입니다.

**MaxLength** – 사용자가 텍스트 입력 컨트롤에 입력할 수 있는 문자 수입니다.

**Mode** – 컨트롤은 **SingleLine**, **MultiLine** 또는 **Password** 모드입니다.

**[OnChange](properties-core.md)** – 사용자가 컨트롤의 값을 변경할 때(예: 슬라이더 조절) 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 아래쪽 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingTop](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 위쪽 가장자리 사이의 거리입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**[PressedColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 텍스트 색입니다.

**[PressedFill](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 배경색입니다.

**[RadiusBottomLeft](properties-size-location.md)** – 컨트롤 왼쪽 아래 모서리의 둥근 정도입니다.

**[RadiusBottomRight](properties-size-location.md)** – 컨트롤 오른쪽 아래 모서리의 둥근 정도입니다.

**[RadiusTopLeft](properties-size-location.md)** – 컨트롤 왼쪽 위 모서리의 둥근 정도입니다.

**[RadiusTopRight](properties-size-location.md)** – 컨트롤 오른쪽 위 모서리의 둥근 정도입니다.

**[Reset](properties-core.md)** – 컨트롤이 기본값으로 되돌아가는지 여부입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Strikethrough](properties-text.md)** - 컨트롤에 표시되는 텍스트 중앙에 선을 표시할지 여부를 선택합니다.

**[TabIndex](properties-accessibility.md)** – 0 이외의 값으로 설정된 경우 런타임 시 컨트롤의 탭 순서를 사용자 지정합니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Underline](properties-text.md)** – 컨트롤에 표시되는 텍스트 아래에 선을 표시할지 여부를 선택합니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**DateTimeValue**( *String* )](../functions/function-datevalue-timevalue.md)

## <a name="examples"></a>예
### <a name="collect-data"></a>데이터 수집
1. 두 개의 텍스트 입력 컨트롤을 추가하고 **inputFirst** 및 **inputLast**로 이름을 지정합니다.
   
    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. 단추 컨트롤을 추가하고 **[Text](properties-core.md)** 속성을 **Add**로 설정하고 **[OnSelect](properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
   **Collect(Names, {FirstName:inputFirst.Text, LastName:inputLast.Text})**
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
3. 세로 방향으로 텍스트 갤러리를 추가하고 **[Items](properties-core.md)** 속성을 **Names**로 설정하고 **Subtitle1**의 **[Text](properties-core.md)** 속성을 **ThisItem.FirstName**으로 설정합니다.
4. (선택 사항) 템플릿 갤러리에서 맨 아래 레이블(**Body1**)을 삭제하고 갤러리의 **[TemplateSize](control-gallery.md)** 속성을 **80**으로 설정합니다.
5. F5 키를 누르고 텍스트의 문자열을 **inputFirst** 및 **inputLast**에 입력한 다음, **Add** 단추를 클릭하거나 탭합니다.
6. (선택 사항) 컬렉션에 이름을 더 추가한 다음, Esc 키를 눌러 기본 작업 영역으로 돌아갑니다.

### <a name="prompt-for-a-password"></a>암호를 묻는 메시지
1. 텍스트 입력 컨트롤을 추가하고 이름을 **inputPassword**로 지정한 다음, **Mode** 속성을 **Password**로 설정합니다.
2. 레이블을 추가하고 **[Text](properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
   **If(inputPassword.Text = "P@ssw0rd", "Access granted", "Access denied")**
   
    **[If](../functions/function-if.md)** 함수 또는 [다른 함수](../formula-reference.md)에 대해 더 알고 싶으신가요?
3. F5 키를 누르고 **inputPassword**에 **P@ssw0rd**를 입력합니다.
   
    암호 입력을 마치면 **Access denied**를 표시하는 레이블이 중지하고 **Access granted**를 표시하기 시작합니다.
4. 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.
5. (선택 사항) 화살표와 같은 컨트롤을 추가하고, 다른 화면으로 이동하도록 구성하며 사용자가 암호를 입력한 후에만 표시합니다.
6. (선택 사항) 단추를 추가하고 **Sign in**을 표시하도록 **[Text](properties-core.md)** 속성을 구성하며 사용자가 잘못된 암호를 입력한 다음 **Sign in** 단추를 클릭하거나 탭할 경우 일정 시간 동안 입력 텍스트 컨트롤을 비활성화합니다.

