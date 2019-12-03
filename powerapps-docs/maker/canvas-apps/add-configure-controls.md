---
title: 캔버스 앱 컨트롤 추가 및 구성 | Microsoft Docs
description: 도구 모음의 속성 탭 또는 수식 입력줄에서 직접 캔버스 앱 컨트롤을 추가 및 구성하기 위한 단계별 지침입니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b2a2aa1baf93008fa908ca3f73aebfde64c9b239
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680055"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>PowerApps에서 캔버스 앱 컨트롤 추가 및 구성

도구 모음, **속성** 탭 또는 수식 입력줄에서 직접 캔버스 앱에 다양한 UI 요소를 추가하고 모양과 동작의 측면을 구성합니다. 이러한 UI 요소는 컨트롤이라고 하며, 구성하는 측면은 속성이라고 합니다.

## <a name="prerequisites"></a>필수 조건

1. Power Apps 라이선스가 아직 없는 경우 [등록](../signup-for-powerapps.md)하 고 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
1. **자신의 앱 만들기**에서 **캔버스 앱을 빈 위치에서**마우스로 가리킨 다음 **이 앱 만들기**를 선택 합니다.
1. 소개 둘러보기를 수행 하 라는 메시지가 표시 되 면 **다음** 을 선택 하 여 Power Apps 인터페이스의 주요 영역을 파악 합니다 (또는 **건너뛰기**를 선택).

    화면 오른쪽 위 모퉁이 근처의 물음표 아이콘을 선택한 다음 **소개 둘러보기 사용**을 선택 하 여 나중에 언제 든 지 둘러보기를 수행할 수 있습니다.

## <a name="add-and-select-a-control"></a>컨트롤 추가 및 선택

**삽입** 탭에서 다음 단계 중 하나를 수행 합니다.

- **레이블** 또는 **단추** 를 선택 하 여 이러한 컨트롤 형식 중 하나를 추가 합니다.
- 컨트롤 범주를 선택한 다음 추가 하려는 컨트롤의 형식을 선택 합니다.

예를 들어 **새 화면**을 선택 하 고 **비어 있음** 을 선택 하 여 빈 화면을 앱에 추가 합니다. 화면은 다른 형식의 컨트롤을 포함할 수 있는 컨트롤의 형식입니다.

![화면 추가](./media/add-configure-controls/add-screen.png)

새 화면의 이름이 **Screen2** 이 고 왼쪽 탐색 창에 나타납니다. 이 창에는 각 컨트롤을 쉽게 찾아서 선택할 수 있도록 앱에 있는 컨트롤의 계층적 목록이 표시 됩니다.

![Screen2의 목록](./media/add-configure-controls/list-screen2.png)

이 목록의 작동 방식을 설명 하려면 **삽입** 탭에서 **레이블** 을 선택 합니다. 새 컨트롤이 계층 목록의 **Screen2** 아래에 나타납니다.

![Screen2의 목록](./media/add-configure-controls/add-label.png)

화면에서 6 개의 핸들이 있는 상자는 기본적으로 레이블을 둘러쌉니다. 해당 형식의 상자는 선택 된 컨트롤을 둘러쌉니다. 화면을 클릭 하거나 탭 하 여 화면을 선택 하는 경우 (레이블 외부에서) 상자는 레이블에서 사라집니다. 레이블을 다시 선택 하려면 해당 레이블을 클릭 하거나 탭 하거나, 컨트롤의 계층적 목록에서 해당 이름을 클릭 하거나 탭 할 수 있습니다.

> [!IMPORTANT]
> 컨트롤을 구성 하려면 항상 컨트롤을 선택 해야 합니다.

## <a name="rename-a-control"></a>컨트롤 이름 바꾸기

컨트롤의 계층적 목록에서 이름을 바꾸려는 컨트롤을 마우스로 가리키고, 표시 되는 줄임표 단추를 선택한 다음 **이름 바꾸기**를 선택 합니다. 그러면 고유한 기억 하기 쉬운 이름을 입력 하 여 앱을 더 쉽게 빌드할 수 있습니다.

![컨트롤 이름 바꾸기](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>컨트롤 삭제

컨트롤의 계층적 목록에서 삭제 하려는 컨트롤을 마우스로 가리키고, 표시 되는 줄임표 단추를 선택한 다음, **삭제**를 선택 합니다. 화면이 아닌 컨트롤을 삭제 하려면 캔버스에서 컨트롤을 선택한 다음 Delete 키를 누릅니다.

![컨트롤 삭제](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>화면 다시 정렬

컨트롤의 계층적 목록에서 위나 아래로 이동 하려는 화면을 마우스로 가리키고, 표시 되는 줄임표 단추를 선택한 다음 **위로 이동** 또는 **아래로 이동**을 선택 합니다.

![화면 다시 정렬](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> 앱을 열면 일반적으로 컨트롤의 계층 목록 맨 위에 있는 화면이 먼저 나타납니다. 그러나 **[OnStart](controls/control-screen.md)** 속성을 **[Navigate](functions/function-navigate.md)** 함수를 포함 하는 수식으로 설정 하 여 다른 화면을 지정할 수 있습니다.

## <a name="move-and-resize-a-control"></a>컨트롤 이동 및 크기 조정

컨트롤을 이동 하려면이 컨트롤을 선택 하 고 중심을 마우스로 가리켜 4 방향 화살표가 표시 되도록 한 다음 컨트롤을 다른 위치로 끕니다.

![컨트롤 이동](./media/add-configure-controls/move-control.png)

컨트롤의 크기를 조정 하려면 컨트롤을 선택 하 고 선택 상자의 핸들을 마우스로 가리켜 양방향 화살표가 표시 되도록 한 다음 핸들을 끕니다.

![컨트롤 이동](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> 이 항목의 뒷부분에서 설명 하는 것 처럼 수식 입력줄에서 **[X](controls/properties-size-location.md)** , **[Y](controls/properties-size-location.md)** , **[Height](controls/properties-size-location.md)** 및 **[Width](controls/properties-size-location.md)** 속성의 조합을 수정 하 여 컨트롤을 이동 하 고 크기를 조정할 수도 있습니다.

## <a name="change-the-text-of-a-label-or-a-button"></a>레이블 또는 단추의 텍스트를 변경 합니다.

레이블 또는 단추를 선택 하 고 컨트롤에 표시 되는 텍스트를 두 번 클릭 한 다음 원하는 텍스트를 입력 합니다.

![텍스트 변경](./media/add-configure-controls/change-text.png)

> [!NOTE]
> 이 항목에서는 나중에 설명 하는 것 처럼 수식 입력줄에서 **[텍스트](controls/properties-core.md)** 속성을 수정 하 여이 텍스트를 변경할 수도 있습니다.

## <a name="configure-a-control-from-the-toolbar"></a>도구 모음에서 컨트롤 구성

도구 모음에서 컨트롤을 구성하여 컨트롤을 직접 구성하여 할 수 있는 더 광범위한 옵션을 지정할 수 있습니다.

예를 들어 레이블을 선택 하 고, **홈** 탭을 선택한 다음, 레이블에서 텍스트의 글꼴을 변경할 수 있습니다.

![글꼴 변경](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>속성 탭에서 컨트롤 구성

**속성** 탭을 사용 하 여 도구 모음에서 컨트롤을 구성 하는 것 보다 더 광범위 한 옵션을 지정할 수 있습니다.

예를 들어 컨트롤을 선택한 다음 **Visible** 속성을 변경 하 여 컨트롤을 표시 하거나 숨길 수 있습니다.

![표시 유형 설정](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>수식 입력줄에서 컨트롤 구성

도구 모음 또는 속성 탭에서 컨트롤을 직접 구성 하는 **대신 속성 목록** 에서 속성을 선택 하 고 수식 입력줄에 값을 지정 하 여 컨트롤을 구성할 수 있습니다. 이 접근 방법을 사용하여 속성을 알파벳 순서로 검색하고, 값의 추가 유형을 지정할 수 있습니다.

예를 들어 레이블을 선택한 후 다음과 같은 방법으로 구성할 수 있습니다.

- 속성 목록에서 **X** 또는 **Y** 를 선택한 다음 수식 입력줄에서 다른 숫자를 지정 하 여 이동 합니다.

    ![X 속성 설정](./media/add-configure-controls/x-property.png)

- 속성 목록에서 **높이** 또는 **너비** 를 선택한 다음 수식 입력줄에서 다른 숫자를 지정 하 여 크기를 조정 합니다.

    ![Height 속성 설정](./media/add-configure-controls/height-property.png)

- 속성 목록에서 **텍스트** 를 선택한 다음 수식 입력줄에서 리터럴 문자열, 식 또는 수식의 조합을 지정 하 여 텍스트를 변경 합니다.

    - 리터럴 문자열은 따옴표로 묶여 있으며 입력 한 대로 정확 하 게 표시 됩니다. **"Hello, 세계"** 는 리터럴 문자열입니다.

        ![텍스트 속성을 리터럴 문자열로 설정 합니다.](./media/add-configure-controls/literal-string.png)

    - 식에는 함수가 포함 되지 않으며 다른 컨트롤의 속성을 기반으로 하는 경우가 많습니다. **Screen1** 는 **Screen1**의 높이를 표시 하는 식입니다.

        ![텍스트 속성을 식으로 설정](./media/add-configure-controls/expression.png)

    - 수식에는 하나 이상의 함수가 포함 되어 있습니다. **Now** 함수는 현지 표준 시간대의 현재 날짜 및 시간을 반환 하 고 **텍스트** 함수는 날짜, 시간 및 통화와 같은 값의 형식을 지정 합니다.

        ![텍스트 속성을 수식으로 설정](./media/add-configure-controls/formula.png)

        수식은 일반적으로 데이터를 업데이트 하 고, 정렬 하 고, 필터링 하 고, 다른 작업을 수행할 수 있도록이 예제 보다 훨씬 더 복잡 합니다. 자세한 내용은 [수식 참조](formula-reference.md)를 참조 하세요.

## <a name="next-steps"></a>다음 단계

- [화면](add-screen-context-variables.md), [목록](add-list-box-drop-down-list-radio-button.md), [갤러리](add-gallery.md), [양식](add-form.md)및 [차트](use-line-pie-bar-chart.md)와 같은 공용 컨트롤을 구성 하기 위한 단계별 절차를 찾습니다.
- [컨트롤 참조](reference-properties.md)에서 각 컨트롤 형식에 대 한 참조 정보를 찾습니다.
