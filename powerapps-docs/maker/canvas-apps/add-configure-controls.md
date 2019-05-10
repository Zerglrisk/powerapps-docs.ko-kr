---
title: 캔버스 앱 컨트롤 추가 및 구성 | Microsoft Docs
description: 도구 모음의 속성 탭 또는 수식 입력줄에서 직접 캔버스 앱 컨트롤을 추가 및 구성하기 위한 단계별 지침입니다.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3311433b3950bcf48dc6c7b7969da501e542952c
ms.sourcegitcommit: c52c1869510a9a37d9f7b127e06f07583529588b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670875"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>PowerApps에서 캔버스 앱 컨트롤 추가 및 구성

도구 모음, **속성** 탭 또는 수식 입력줄에서 직접 캔버스 앱에 다양한 UI 요소를 추가하고 모양과 동작의 측면을 구성합니다. 이러한 UI 요소는 컨트롤이라고 하며, 구성하는 측면은 속성이라고 합니다.

## <a name="prerequisites"></a>필수 조건

1. PowerApps 라이선스가 아직 없는 경우 [등록](../signup-for-powerapps.md)한 다음 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
1. **나만의 앱 만들기** 아래 **빈 페이지의 캔버스 앱**을 마우스로 선택한 후 **만들기**를 선택합니다.
1. 대화형 둘러보기가 나타나는 경우 PowerApps 인터페이스의 주요 영역을 살펴보려면 **다음**을 선택합니다(또는 **건너뛰기** 선택).

    화면의 오른쪽 위 모서리의 물음표 아이콘을 선택한 다음 **즉석 팁**을 선택하여 언제든지 나중에 둘러보기를 선택할 수 있습니다.

## <a name="add-and-select-a-control"></a>컨트롤 선택 및 추가

**삽입** 탭에서 다음의 단계 중 하나를 수행합니다.

- 여러 유형의 컨트롤 중 하나를 추가하기 위해 **레이블** 또는 **단추**를 선택합니다.
- 컨트롤의 범주를 선택한 다음 추가하려는 컨트롤 유형을 선택합니다.

예를 들어, **새 화면**을 선택한 후 앱에 빈 화면을 추가하기 위해 **비어 있음**을 선택합니다. (화면은 다른 유형의 컨트롤을 포함할 수 있는 컨트롤의 유형입니다.)

![화면 추가](./media/add-configure-controls/add-screen.png)

**Screen2**라고 새 화면이 왼쪽 탐색 창에 나타납니다. 이 창은 각 컨트롤을 쉽게 선택하고 찾을 수 있도록 앱에서 컨트롤의 계층적 목록을 보여줍니다.

![목록의 Screen2](./media/add-configure-controls/list-screen2.png)

계층적 목록을 확인하기 위해서 **삽입** 탭에서 **레이블**을 선택합니다. 계층적 목록의 **Screen2** 아래에 새 컨트롤이 나타납니다.

![목록의 Screen2](./media/add-configure-controls/add-label.png)

화면에서는 기본적으로 6개의 핸들을 가진 상자가 레이블을 둘러쌉니다. 어떤 컨트롤이 선택되면 해당 유형의 상자가 둘러쌉니다. 화면을 클릭하거나 탭(하지만 레이블 외부)하면 레이블의 상자가 사라집니다. 레이블을 선택 하 다시 클릭 하거나, 탭 또는 클릭 하거나 컨트롤의 계층적 목록에서 해당 이름을 탭 합니다.

> [!IMPORTANT]
> 컨트롤을 구성 하기 전에 항상 선택 해야 합니다.

## <a name="rename-a-control"></a>컨트롤 이름 바꾸기

계층적 목록에서 이름을 변경하려는 컨트롤 위로 마우스를 가져가고, 나타나는 줄임표 단추를 선택한 다음, **이름 바꾸기**를 선택합니다. 그런 다음 앱을 쉽게 만들 수 있도록 고유하고 기억하기 쉬운 이름을 입력할 수 있습니다.

![컨트롤 이름 바꾸기](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>컨트롤 삭제

계층적 목록에서 삭제하려는 컨트롤 위로 마우스를 가져가고, 나타나는 줄임표 단추를 선택한 다음, **삭제** 선택합니다. 화면에 없는 컨트롤을 삭제하려면 캔버스에서 컨트롤을 선택한 후 Delete 키를 누릅니다.

![컨트롤 삭제](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>화면을 다시 정렬

계층적 목록에서 위로 또는 아래로 이동하려는 화면에 마우스를 가져가고, 나타나는 줄임표 단추를 선택한 다음, **위로 이동** 하거나 **아래로 이동**을 선택합니다.

![화면을 다시 정렬](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> 앱을 열 때 컨트롤의 계층적 목록 맨 위에 있는 화면이 일반적으로 첫 번째로 나타납니다. 하지만 **[Navigate](functions/function-navigate.md)** 함수를 포함하는 수식으로 **[OnStart](controls/control-screen.md)** 속성을 설정하여 다른 화면을 지정할 수 있습니다.

## <a name="move-and-resize-a-control"></a>컨트롤 크기 조정 및 이동

컨트롤을 이동하려면 십자형 화살표가 표시되도록 컨트롤 중심 위로 마우스를 가져간 다음 다른 위치로 컨트롤을 끌어 옵니다.

![컨트롤 이동](./media/add-configure-controls/move-control.png)

컨트롤의 크기를 조정하려면 선택 상자에 임의 핸들 위로 마우스를 가져가고 나타나는 양방향 화살표의 핸들을 끕니다.

![컨트롤 이동](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> 이 항목 뒷부분 설명처럼, 수식 입력줄에서 **[X](controls/properties-size-location.md)**, **[Y](controls/properties-size-location.md)**, **[Height](controls/properties-size-location.md)** 및 **[Width](controls/properties-size-location.md)** 속성의 여러 조합을 수정하여 컨트롤의 크기를 조정하거나 이동할 수 있습니다.

## <a name="change-the-text-of-a-label-or-a-button"></a>레이블 또는 단추 텍스트 변경

레이블 또는 단추를 선택하고, 컨트롤에서 표시되는 텍스트를 두 번 클릭한 후 원하는 텍스트를 입력합니다.

![텍스트 변경](./media/add-configure-controls/change-text.png)

> [!NOTE]
> 항목 뒷부분 설명처럼, 수식 입력줄에서 **[Text](controls/properties-core.md)** 속성을 수정하여 텍스트를 변경할 수도 있습니다.

## <a name="configure-a-control-from-the-toolbar"></a>도구 모음에서 컨트롤 구성

도구 모음에서 컨트롤을 구성하여 컨트롤을 직접 구성하는 것보다 더 광범위한 옵션을 지정할 수 있습니다.

예를 들어, **홈** 탭에서 레이블을 클릭한 다음 레이블의 텍스트 글꼴을 변경합니다.

![글꼴 변경](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>속성 탭에서 컨트롤 구성

**속성** 탭을 사용하여, 도구 모음에서 컨트롤을 구성하는 것보다 더 광범위한 여러 가지 옵션을 지정할 수 있습니다.

예를 들어, 컨트롤을 선택한 다음 **Visible** 속성을 변경하여 컨트롤을 표시하거나 숨길 수 있습니다.

![표시 설정](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>수식 입력줄에서 컨트롤 구성

컨트롤을 직접, 도구 모음, **속성** 탭에서 구성하는 것 대신 속성 목록의 속성을 선택한 다음 수식 입력줄에서 값을 지정하여 컨트롤을 구성할 수 있습니다. 이 접근 방법을 사용하여 속성을 알파벳 순서로 검색하고, 값의 추가 유형을 지정할 수 있습니다.

예를 들어, 레이블을 선택하고 다음과 같은 방법으로 구성할 수 있습니다.

- 속성 목록에서 **X** 또는 **Y**를 선택한 다음 수식 입력줄에 다른 수를 지정하여 컨트롤을 이동할 수 있습니다.

    ![X 설정 속성](./media/add-configure-controls/x-property.png)

- 속성 목록에서 **Height** 또는 **Width**를 선택한 다음 수식 입력줄에 다른 수를 지정하여 컨트롤의 크기를 조정할 수 있습니다.

    ![높이 속성 설정](./media/add-configure-controls/height-property.png)

- 속성 목록에서 **Text**를 선택한 다음 수식 입력줄에서 리터럴 문자열, 식 또는 수식의 조합을 지정하여 해당 텍스트를 변경할 수 있습니다.

    - 리터럴 문자열은 따옴표로 둘러싸고 입력한 대로 정확하게 표시됩니다. **"Hello, world"** 는 리터럴 문자열입니다.

        ![리터럴 문자열을 텍스트 속성을 설정 합니다.](./media/add-configure-controls/literal-string.png)

    - 식은 함수를 포함하지 않고 종종 다른 컨트롤의 속성에 기반합니다. **Screen1.Height**는 **Screen1**의 높이를 보여주는 식입니다.

        ![식 텍스트 속성을 설정 합니다.](./media/add-configure-controls/expression.png)

    - 수식에는 하나 이상의 함수가 포함됩니다. **Now** 함수에서 현지 표준 시간대의 현재 날짜 및 시간을 반환하며, **Text** 함수에서 날짜, 시간 및 통화 값과 같은 값들의 서식을 지정합니다.

        ![수식에 텍스트 속성을 설정 합니다.](./media/add-configure-controls/formula.png)

        수식은 일반적으로 이 예제 보다 훨씬 더 복잡하므로 데이터 업데이트, 정렬, 필터링 및 다른 작업을 수행할 수 있습니다. 자세한 내용은 [수식 참조](formula-reference.md)를 확인합니다.

## <a name="next-steps"></a>다음 단계

- [스크린](add-screen-context-variables.md), [목록](add-list-box-drop-down-list-radio-button.md), [갤러리](add-gallery.md), [양식](add-form.md) 및 [차트](use-line-pie-bar-chart.md)와 같은 공용 컨트롤을 구성하기 위한 단계별 절차를 확인합니다.
- [속성 참조](reference-properties.md)에서 컨트롤의 각 유형에 대한 참조 정보를 확인합니다.
